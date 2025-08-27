---
layout: default
role: notes
title: Notes
order:
--- 
<h4>
	Useful Contacts 
</h4>
<ul class="linkslist">
	{% assign sorted-contacts = site.data.sitewide.algonquin-contacts | sort: "lastname" %} {% for person in sorted-contacts %} 
	<li><a href="mailto:{{ person.email }}">{{ person.lastname }}, {{ person.firstname }} </a>, {{ person.title }}</li>
	{% endfor %} 
</ul>
<h4>
	Downloads 
</h4>
<ul>
	<li><a href="downloads/edu-dual-credit-programs-policy-program-requirements-2020-en-2021-12-13.pdf">Ontario: Micro-Credentials</a> [PDF]</li>
</ul>
<h3>
	Exploratory Stage 
</h3>
<p>
	Share the site and explore ideas. 
</p>
<ul>
    <li>With a pathway from university, often 50% advanced entry is preferred. This means university students would enter our program half-way through </li>
	<li>Ensure that our program aligns well with a post-secondary area of study, SIP code.</li>
	<li>There's no option to change our title because it's a program standard.</li>
	<li>Talk to Jed.</li>
</ul>
