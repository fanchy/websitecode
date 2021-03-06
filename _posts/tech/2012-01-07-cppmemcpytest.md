---
layout: post
title:  C++执行内存memcpy的效率测试
categories: tech
tagline: 测试了一下单线程中执行memcpy的效率，这个结果对于配置TCP epoll中的work thread数量有指导意义。
tags:
    - c++
    - memcpy
excerpt: >
    在进行memcpy操作时，虽然是内存操作，但是仍然是耗一点点CPU的，今天测试了一下单线程中执行memcpy的效率，这个结果对于配置TCP epoll中的work thread
    数量有指导意义。
---
### C++执行内存memcpy的效率测试
在进行memcpy操作时，虽然是内存操作，但是仍然是耗一点点CPU的，今天测试了一下单线程中执行memcpy的效率，这个结果对于配置TCP epoll中的work thread
数量有指导意义。如下基于8K的内存快执行memcpy， 1个线程大约1S能够拷贝500M，如果服务器带宽或网卡到上限是1G,那么网络io的work thread 开2个即可，考虑到消息的解析损耗，3个线程足以抗住硬件的最高负载。
在我到测试机器上到测试结果是：
```
Intel(R) Xeon(R) CPU           E5405  @ 2.00GHz
do memcpy speed:12.27 ms/MB
each thread can do memcpy 667.645 MB
```

```cpp
#include <iostream>
#include <sys/time.h>
#include <string.h>

using namespace std;

int main(int argc, char* argv[])
{
    long len = 8192;
    int  loop = 200;
    char* p = new char[len];
    char* q = p;
    struct timeval start, end;
    gettimeofday(&start, NULL);
    for (int i =0; i < loop; ++i)
    {
            char* p = new char[len];
            *p = char(i);
            memcpy(p, q, len);
            delete [] p;
    }
    gettimeofday(&end, NULL);
    cout <<"do memcpy speed:" << ((end.tv_sec - start.tv_sec)*1000 + double(end.tv_usec - start.tv_usec) / (len*loop/1000/1000) ) / loop<<" ms/MB\n";
    cout <<"each thread can do memcpy "<< double(len)*loop/1000/1000 / ((end.tv_sec - start.tv_sec) + double(end.tv_usec - start.tv_usec) / 1000/1000) <<" MB\n";

}
```


