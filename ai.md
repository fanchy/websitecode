---
layout: page
title: AI
tagline: 游戏开发相关的技术总结。
permalink: /ai.html
ref: ai
order: 2
---

这里汇总游戏开发相关的技术总结。

## ai


*   [主页](/).
*   [神经网络的数学推导和Python实现](/mynnmath.html).
*   [SVM 的数学推导和Python 实现](/svm.html).


<h2>汇总</h2>

<div>&nbsp;</div>
<ul class="post-list">
    {% for post in site.categories.ai %}
      <li>

        {% assign date_format = site.cayman-blog.date_format | default: "%b %-d, %Y" %}
        

        <h2>
          <a class="post-link" href="{{ post.url | absolute_url }}" title="{{ post.title }}">{{ post.title | escape }} <span class="post-meta">{{ post.date | date: date_format }}</span></a>
          
        </h2>

        {{ post.excerpt | markdownify | truncatewords: 30 }}

      </li>
    {% endfor %}
  </ul>