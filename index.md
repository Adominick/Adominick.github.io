---
layout: page
title: 甄谨言的博客
tagline: 化整为零
---
{% include JB/setup %}

<section role="banner">
  <img src="/images/banner.jpg" />
</section>
{% comment %}<!--
这是一个开放的个人主页，如果您对网页设计有什么想法，欢迎留言^_^。（点击"[Feedback](https://github.com/Adominick/Feedback/issues/new)”按钮）

<form action="https://github.com/Adominick/Feedback/issues/new" align="right" target="_blank">
    <input class="btn" type="submit" value="Feedback">
</form>
-->{% endcomment %}

{% comment %}<!--
  ## Sample Posts

This blog contains sample posts which help stage pages and blog data.
When you don't need the samples anymore just delete the `_posts/core-samples` folder.


    $ rm -rf _posts/core-samples


Here's a sample "posts list".

<ul class="posts">
  {% for post in site.posts %}
    <li><span>{{ post.date | date_to_string }}</span> &raquo; <a href="{{ BASE_PATH }}{{ post.url }}">{{ post.title }}</a></li>
  {% endfor %}
</ul>
-->{% endcomment %}



  {% for post in site.posts %}
  <table>
      <tr>
       <a href="{{ BASE_PATH }}{{ post.url }}"><h2>{{ post.title }}</h2></a></li>
       <span>{{ post.date| date: "%Y-%m-%d" }} | 分类:<a href="{{ BASE_PATH }}/categories.html" style="color:grey">{{ post.category }}</a> | 标签:{% for tag in post.tags %} <a href="{{ BASE_PATH }}/tags.html" style="color:grey">{{ tag }}</a> {% if forloop.last != true %} {% endif %} {% endfor %}
      &raquo;</span>
      {{ post.content | split : '<!-- more -->' | first }}...
    </tr>
  {% endfor %}
</table>
