---
layout: default
role: notes
title: Local Arts High Schools
---
<p>
	These are arts high schools to approach. They all participate in the SHSM Program. This is a preliminary list that can be built upon with time. <a href="https://www.ontario.ca/document/specialist-high-skills-major-policy-and-implementation-guide/arts-and-culture" target="_target">Read more about the SHSM program here</a>.
</p>
{% assign sorted-schools = site.data.sitewide.schools | sort: "name" %}
{% for school in sorted-schools %} 
<ul>
	<li style="margin-top: 1rem;"><strong>{{ school.name }}</strong>, {{ school.mission }}</li>
	<ul>
		<li>{{ school.contact.name }}, {{ school.contact.title }}</li>
		<li>{{ school.contact.address }}</li>
		<li><a href="mailto:{{ school.contact.email }}">{{ school.contact.email }}</a></li>
		<li><a href="tel:{{ school.contact.phone }}">{{ school.contact.phone }}</a></li>
		<li><a href="{{ school.contact.url }}" target="_blank">{{ school.contact.url }}</a></li>
	</ul>
</ul>
{% endfor %} 