---
layout: default
role: nav
title: Links
order: 0
---
{% assign sorted-links = site.data.sitewide.links | sort: "title" %}
<ul class="linkslist">
	{% for linkitem in sorted-links %} 
	<li><a href="{{linkitem.url}}" target="_blank">{{ linkitem.title }}</a></li>
	{% endfor %} 
</ul>