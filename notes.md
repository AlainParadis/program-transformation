---
layout: default
role: notes
title: Notes
order:
---
<h3>
	College Contacts
</h3>
<ul class="linkslist">
	{% assign sorted-contacts = site.data.sitewide.algonquin-contacts | sort: "lastname" %} {% for person in sorted-contacts %} 
	<li><a href="mailto:{{ person.email }}">{{ person.lastname }}, {{ person.firstname }} </a>, {{ person.title }}</li>
	{% endfor %} 
</ul>
<h3>
	Exploratory Stage 
</h3>
<p>
	Meet with Alanna MacDonald to show her the site and explore ideas. 
</p>
