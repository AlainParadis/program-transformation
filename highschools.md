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
	{% if school.name %}<li style="margin-top: 1rem;"><strong>{{ school.name }}</strong></li>{% endif %}
	<ul>
		{% if school.contact.name %}<li>{{ school.contact.name }}, {% endif %}{% if school.contact.title %} {{ school.contact.title }}</li>{% endif %}
		{% if school.contact.address %}<li>{{ school.contact.address }}</li>{% endif %}
		{% if school.contact.email %}<li><a href="mailto:{{ school.contact.email }}">{{ school.contact.email }}</a></li>{% endif %}
		{% if school.contact.phone %}<li><a href="tel:{{ school.contact.phone }}">{{ school.contact.phone }}</a></li>{% endif %}
		{% if school.contact.url %}<li><a href="{{ school.contact.url }}" target="_blank">{{ school.contact.url }}</a></li>{% endif %}
	</ul>
</ul>
{% endfor %}