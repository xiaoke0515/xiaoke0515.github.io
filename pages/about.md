---
layout: page
title: About
description: About Me
keywords: Yilong Zhao
comments: false
menu: 关于
permalink: /about/
---

<!--<p>About <a href="{{"/resume/resume/index.html" | prepend: site.baseurl}}">ME</a></p>-->
## About Me

<p>My name is Yilong Zhao, and I am working as a research assistant in Shanghai Qizhi Institute.</p>
<p>My <a href="{{"/page/" | prepend: site.baseurl}}"><u>Personal Page</u></a></p>

## Contact Me

<ul>
{% for website in site.data.social %}
<li>{{website.sitename }}：<a href="{{ website.url }}" target="_blank"><u>{{ website.name }}</u></a></li>
{% endfor %}
</ul>


## Skill Keywords

{% for skill in site.data.skills %}
### {{ skill.name }}
<div class="btn-inline">
{% for keyword in skill.keywords %}
<button class="btn btn-outline" type="button">{{ keyword }}</button>
{% endfor %}
</div>
{% endfor %}
