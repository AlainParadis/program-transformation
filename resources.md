---
layout: default
role: nav
title: Resources
order: 4
---
<h4>
	Useful Links 
</h4>
{% assign sorted-links = site.data.sitewide.links | sort: "title" %} 
<ul class="linkslist">
	{% for linkitem in sorted-links %} 
	<li><a href="{{linkitem.url}}" target="_blank">{{ linkitem.title }}</a></li>
	{% endfor %} 
</ul>

<h4>
	Useful Contacts 
</h4>
<ul class="linkslist">
	{% assign sorted-contacts = site.data.sitewide.algonquin-contacts | sort: "lastname" %} {% for person in sorted-contacts %} 
	<li><a href="mailto:{{ person.email }}">{{ person.lastname }}, {{ person.firstname }} </a>, {{ person.title }}</li>
	{% endfor %} 
</ul>

<h4>Degree Programs</h4>
<ul class="linkslist">
	{% assign sorted-programs = site.data.sitewide.degree-programs | sort: "title" %}
	{% for program in sorted-programs %} 
	<li><a href="{{ program.url }}">{{ program.title }}</a>, {{ program.institution }}</li>
	{% endfor %} 
</ul>