---
layout: schedule
title: Friday schedule
day: Friday
---
<style>
* { box-sizing: border-box; }

body
{
  font-family: "IBM Plex Mono", serif;
  font-weight: 400;
  font-style: normal;
  font-size: clamp(0.9rem, 0.8rem + 0.5vw, 1.4rem);
  margin: 0.5rem;
  padding: 0;
}

/* Outer grid for each day */
.table-container
{
  display: grid;
  gap: 1px;
  grid-template-columns: auto;
  background-color: #ccc;
  border: solid 1px #e0e0e0;
  max-width: 95%;
  overflow-x: auto;
}

/* Header cells, generic cells, and time labels */
.table-header,
.table-cell,
.time-label
{
  background-color: #fff;
  padding: 10px;
  text-align: center;
  min-width: 110px;

  /* Flex row so multiple class blocks in the same cell sit side by side */
  display: flex;
  flex-direction: row;
  align-items: stretch;
  justify-content: stretch;
  gap: 4px;
}

/* Time column */
.time-label
{
  background-color: #f0f0f0;
  font-weight: bold;
}

/* Top headers */
.table-header { background-color: #e0e0e0; }

/* Individual class entry */
.class-block
{
  display: flex;
  flex-direction: column;
  flex: 1 1 0;
  align-items: stretch;
  justify-content: center;
  font-weight: bold;
  color: #001533;
  border-radius: 4px;
  padding: 4px 6px;
  margin: 0;
  border: 1px solid rgba(0, 0, 0, 0.12);
  background-color: #e5e5e5; /* fallback */
}

/* Slightly denser type if a cell has multiple classes */
.class-block.is-overlap
{
  font-size: 0.85em;
}

/* Text inside a class block */
.class-room
{
  font-size: 0.8em;
  font-weight: normal;
  margin-bottom: 2px;
  color: #111111;
}

.class-level-group
{
  font-size: 0.78em;
  font-weight: normal;
  margin-bottom: 2px;
  color: #333333;
}

.class-name
{
  font-size: 0.88em;
  margin-bottom: 2px;
}

.instructor-name
{
  font-weight: normal;
  font-size: 0.8em;
  margin-top: 4px;
  color: #222222;
}

/* Typography for headings and links */
h2
{
  margin-top: 48px;
  font-weight: bold;
}

h3
{
  margin-top: 48px;
  font-weight: bold;
}

a {
  text-decoration: none;
  color: #003366;
  border-bottom: 1px solid #003366;
}
a:hover { border-bottom: 1px solid #0433FF; }

/* Asynchronous list */
.async {
  list-style: none;
  padding: 0;
  margin: 0;
  display: flex;
  flex-wrap: wrap;
  gap: 2rem;
}

.async-item {
  flex: 1 1 250px;
  max-width: 400px;
  background: #EBEBEB;
  padding: 1rem;
  border-radius: 8px;
}

.async-item ul {
  list-style-type: none;
  margin: 0;
  padding-left: 1.5rem;
}

/* Group-based colour coding (l2/l4/l6) */

.class-block.l2g1 { background-color: #d0eaff !important; border-color: #7ab4f0 !important; }
.class-block.l2g2 { background-color: #ffd7e0 !important; border-color: #f28aa1 !important; }
.class-block.l2g3 { background-color: #fff0d0 !important; border-color: #f2b46a !important; }

.class-block.l4g1 { background-color: #d8ffd8 !important; border-color: #83c783 !important; }
.class-block.l4g2 { background-color: #fff4c5 !important; border-color: #e0b958 !important; }
.class-block.l4g3 { background-color: #f0ddff !important; border-color: #b291f0 !important; }

.class-block.l6g1 { background-color: #d8f8ff !important; border-color: #7fc1e0 !important; }
.class-block.l6g2 { background-color: #ffe9d6 !important; border-color: #e49d68 !important; }

/* Fallback */
.class-block[class*="l"][class*="g"]
{
  background-color: #ececec !important;
  border-color: #bbbbbb !important;
}

</style>
{%- assign rooms = site.data.schedule.rooms -%}
{%- assign times = site.data.schedule.times -%}
{%- assign classes = site.data.schedule.classes | where: "day", page.day -%}

<h2>{{ page.day }} – detailed schedule</h2>

<p><a href="{{ '/schedule/' | relative_url }}">Back to weekly overview</a></p>

{% for room in rooms %}
  <h3>{{ room }}</h3>

  {% assign room_classes = classes | where: "room", room %}
  {% assign room_classes = room_classes | sort: "start" %}

  <div class="table-container" style="grid-template-columns: auto 1fr; grid-template-rows: auto;">
    <div class="table-header" style="grid-column: 1; grid-row: 1;">Time</div>
    <div class="table-header" style="grid-column: 2; grid-row: 1;">Classes</div>

    {% for c in room_classes %}
      <div class="time-label" style="grid-column: 1; grid-row: {{ forloop.index | plus: 1 }};">
        {{ c.start }}
      </div>
      <div class="table-cell" style="grid-column: 2; grid-row: {{ forloop.index | plus: 1 }};">
        <div class="class-block {{ c.group }}">
          <div class="class-level-group">
            {% assign parts = c.group | remove: "l" | split: "g" %}
            Level {{ parts[0] }}, Group {{ parts[1] }}
          </div>
          <div class="class-name">
            {{ c.name }}
          </div>
          {% if c.instructor %}
            <div class="instructor-name">
              {% if c.email %}
                <a href="mailto:{{ c.email }}">{{ c.instructor }}</a>
              {% else %}
                {{ c.instructor }}
              {% endif %}
            </div>
          {% endif %}
        </div>
      </div>
    {% endfor %}
  </div>
{% endfor %}
