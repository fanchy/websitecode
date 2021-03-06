---
layout: post
title:  UtraEdit 支持Lua高亮
categories: tech
tagline: UtraEdit 支持Lua高亮
tags:
    - UtraEdit
    - lua
excerpt: >
    UtraEdit 支持Lua高亮
---

#### 方法记录

UtraEdit  支持Lua高亮，网上已经有很多方法，但是都是基于相对老一点的
UE，在15.10版本中，UE支持Lua高亮的方法如下：

从网上Down下支持Lua的wordfiles，lua.uew
新建一个目录如D:\wordfiles，

将UE安装目录下的所有wordfiles文件都复制到D:\wordfiles，再将自己的lua.uew拷贝到此，
设置UE 高级-》配置-》编辑器显示-》语法高亮
将”文档的完整目录名称“一项改成D:\wordfiles
确定即可生效。
网上的Lua对require和for好像没有支持可以自己添加高亮关键字：
如下是我的Lua wordfiles文件：

```
/L20"Lua" Line Comment = -- Block Comment On = [[ Block Comment Off = ]] String Chars = "' Escape Char = \ File Extensions = LUA BIN
/Colors = 0,8421376,8421376,8421504,255,
/Colors Back = 16777215,16777215,16777215,16777215,16777215,
/Colors Auto Back = 1,1,1,1,1,
/Font Style = 0,0,0,0,0,
/Delimiters = ~!@%^&*()-+=|\/{}[]:;"'<> , .?
/Function String 1 = "function[ ]++[a-zA-Z]*)"
/Function String 2 = "function[ ]++([ a-zA-Z]*)"
/Open Fold Strings = "function" "if" "while" "for"
/Close Fold Strings = "end"
/C1 "key words" Colors = 16711680 Colors Back = 16777215 Colors Auto Back = 1 Font Style = 0
and
break
do
else 
elseif 
end
function
require
if in
local
nil not
or
repeat return
then
until
while
for
/C2 Colors = 255 Colors Back = 16777215 Colors Auto Back = 1 Font Style = 0
abs acos appendto ascii asin assert atan atan2
call ceil clock collectgarbage copytagmethods cos
date deg dofile dostring
error execute exit
false find floor foreach foreachvar format frexp
getbinmethod getenv getglobal gettagmethod gfind gmatch gsub
insert ipairs
ldexp log log10
match max min mod
newtag next nextvar
os
pairs print
rad random randomseed rawgetglobal rawgettable rawsetglobal rawsettable read
readfrom remove rename
seterrormethod setglobal setlocale settag settagmethod sin sqrt strbyte sub
strchar strfind string strlen strlower strrep strsub strupper
table tag tan tmpname tonumber tostring true type
write writeto
/C3 Colors = 33023 Colors Back = 16777215 Colors Auto Back = 1 Font Style = 0
$debug
$else
$end
$endinput
$if
$ifnot
$nodebug
/C4 Colors = 32768 Colors Back = 16777215 Colors Auto Back = 1 Font Style = 0
PI
_INPUT _OUTPUT _STDERR _STDIN _STDOUT
/C5 Colors = 4210816 Colors Back = 16777215 Colors Auto Back = 1 Font Style = 0
+
-
*
// /
^
<
>
=
~
%
.
:
/C6 Colors = 16711680 Colors Back = 16777215 Colors Auto Back = 1 Font Style = 0
;
,
(
)
{
}
[
]
/C7 Colors = 16711680 Colors Back = 16777215 Colors Auto Back = 1 Font Style = 0
cgi cgilua cgilua_url char2hexa chdir
dbluaerrorfb dblua_escape decode default_script
encodecgi encodetable escape
filetype
getvalue
hexa hexa2char html_mask
includehtml insertfield
lua_mask
maketable map mkurl
nopipe
preprocess
redirect relativeurl relative_url
saveluavar savestate script_path script_pdir script_vdir stateerrormethod
statefile stdin strsplit
unescape
/C8 Colors = 16711680 Colors Back = 16777215 Colors Auto Back = 1 Font Style = 0
DBClose DBExec DBOpen DBRow
```

