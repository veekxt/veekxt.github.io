---
layout: post
title: "BrainFuck，一个极小化的语言"
categories:
- 计算机语言
tags: Fuck 烧脑


---
Brainfuck，是一种极小化的计算机语言，目标是创建一种简单的、可以用最小的编译器来实现的、符合图灵完全思想的编程语言。这种语言仅由八种运算符构成，见下表：


<table class="gridtable">
<tbody><tr>
<th>字符</th>
<th>含义</th>
</tr>
<tr>
<td><code>&gt;</code></td>
<td>指针加一</td>
</tr>
<tr>
<td><code>&lt;</code></td>
<td>指针减一</td>
</tr>
<tr>
<td><code>+</code></td>
<td>指针指向的字节的值加一</td>
</tr>
<tr>
<td><code>-</code></td>
<td>指针指向的字节的值减一</td>
</tr>
<tr>
<td><code>.</code></td>
<td>输出指针指向的单元内容（ASCII码）</td>
</tr>
<tr>
<td><code>,</code></td>
<td>输入内容到指针指向的单元（ASCII码）</td>
</tr>
<tr>
<td><code>[</code></td>
<td>如果指针指向的单元值为零，向后跳转到对应的<code>]</code>指令的次一指令处</td>
</tr>
<tr>
<td><code>]</code></td>
<td>如果指针指向的单元值不为零，向前跳转到对应的<code>[</code>指令的次一指令处</td>
</tr>
</tbody>
</table>

按照更节省时间的简单说法，]也可以说成“向前跳转到对应的[状态”。这两解释是一样的。
第三种同价的说法，[意思是"向后跳转到对应的]"，]意思是"向前跳转到对应的[指令的次一指令处，如果指针指向的字节非零。"
Brainfuck程序可以用下面的替换方法翻译成C语言（假设ptr是char*类型）：


<table class="gridtable">
<tbody><tr>
<th>Brainfuck</th>
<th>C</th>
</tr>
<tr>
<td align="center"><code>&gt;</code></td>
<td><code>++ptr;</code></td>
</tr>
<tr>
<td align="center"><code>&lt;</code></td>
<td><code>--ptr;</code></td>
</tr>
<tr>
<td align="center"><code>+</code></td>
<td><code>++*ptr;</code></td>
</tr>
<tr>
<td align="center"><code>-</code></td>
<td><code>--*ptr;</code></td>
</tr>
<tr>
<td align="center"><code>.</code></td>
<td><code>putchar(*ptr);</code></td>
</tr>
<tr>
<td align="center"><code>,</code></td>
<td><code>*ptr =getchar();</code></td>
</tr>
<tr>
<td align="center"><code>[</code></td>
<td><code>while (*ptr) {</code></td>
</tr>
<tr>
<td align="center"><code>]</code></td>
<td><code>}</code></td>
</tr>
</tbody></table>

### 输出Hello World!

<pre>
<code>
++++++++++[>+++++++>++++++++++>+++>+<<<<-]
>++.>+.+++++++..+++.>++.<<+++++++++++++++.
>.+++.------.--------.>+.>.
</code>
</pre>
或者

<pre>
<code>
>+++++++[<++++++++++>-]<++.
>++[<++++++++++>-]<+++++++++.
><+++++++..
><+++.
>++++++[<---------->-]<-------.
>++++[<++++++++++>-]<+++.
>++[<++++++++++>-]<++++.
><+++.><------.><--------.
>++++++[<---------->-]<-------.
</code>
</pre>

自行思考如何实现四则运算，条件指令等？BrainFuck挺有意思的，不过好像并没有什么实用价值，可以装逼？打算写几个工具或使bf易用化

+  解释器，分别用C、Python和JS实现。
+  把bf转换成其他语言，比如C。
+  字符串转换器，输出这样的brainfuck语句：它的运行结果是输出指定的字符串。
+  找到循环、判断、运算的一般方法。

轮子已补完<https://gitcafe.com/one-point/BrainFuck>

### 链接

这里有很多关于bf的程序，在线解释器等东西（官网？）<http://www.muppetlabs.com/~breadbox/bf/>  
某在线编辑器<http://www.bf.doleczek.pl/>