---
layout: default
role: nav
title: Brainstorming
order: 2
---
These are very preliminary ideas about possible program transformation.

The central idea the faculty have agreed upon is de-streaming the curriculum. Currently, our courses are based on distinct disciplines. We have four semesters of typography, and four semesters of user experience design. What we envision is a more multi-disciplinary approach, where courses include some of each discipline. For instance, elements of user experience design and typography would be in a course where assignments include web pages and printed collateral to support a brand. The latest automated production processes would be used rather than tedious, repetitive methods. See what's possible, with this <a href="#pos">re-imagined program of study</a>.

That said, we cannot ignore the craft aspect of design. Software training and basic coding, including fundamentals about pixels, vectors, page layout, and HTML/CSS will be necessary for the foreseeable future.

> Graphic designers are no longer editors; we're directors.

With automation supplanting production tasks, we're left space for higher level, conceptual thinking. This is where the focus of the new curriculum must be. The most valuable designers are going to be those who blend creative direction with strategic thinking. We will guide the A.I.-assisted generation of assets to create original concepts that elicit emotional connections. While routine technical jobs are declining, demand is rising for unique creative thinking, strategy, and design leadership. This is where we need to be.

> A.I. is not replacing creativity. It is amplifying it.

As designers, we'll use A.I. to generate initial concepts, spark inspiration, explore new visual directions, and tailor content for diverse audiences. By analysing design trends and user feedback, A.I. tools can also offer predictive insights that help designers make more informed, innovative decisions.

If we're to remain relevant and competitive, we'll need to master conceptual thinking, brand strategy, user experience analysis, and creative leadership. The future is going to require a blend of creativity, empathy, and the ability to guide and refine A.I.-generated work.

A.I. levels the technical playing field, but the ability of humans to conjure novel ideas through deep understanding of a client's needs will remain irreplaceable.

<h4>
	<a name="pos">Reimagined Program of Study</a>
</h4>
<div class="top-link">
  <a href="#top">↑ Top</a>
</div>
This program of study was created (with A.I. assistance). It's not meant for implementation. It's meant to demonstrate what could be possible for our program.

{% for item in site.data.pos.semesters %}
  <h5>{{ item.title }}</h5>
  <ul>
    {% for course in item.courses %}
      <li>
        <strong>{{ course.title }}</strong><br>
        {{ course.description }}
      </li>
    {% endfor %}
  </ul>
{% endfor %}
