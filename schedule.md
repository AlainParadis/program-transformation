---
layout: schedule
title: Weekly Graphic Design Schedule
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
{%- assign days = "Monday,Tuesday,Wednesday,Thursday,Friday" | split: "," -%}

<h2>Asynchronous Courses</h2>
<ul class="async">
  {% for item in site.data.schedule.async %}
    <li class="async-item">
      <ul>
        <li><strong>{{ item.name }}</strong></li>
        <li>{{ item.modality }}</li>
        <li>Level: {{ item.level }}</li>
        <li>{{ item.instructor }}</li>
      </ul>
    </li>
  {% endfor %}
</ul>

<h2>In-Person Courses</h2>
<p>
  Skip to:
  <a href="#Monday">Monday</a> |
  <a href="#Tuesday">Tuesday</a> |
  <a href="#Wednesday">Wednesday</a> |
  <a href="#Thursday">Thursday</a> |
  <a href="#Friday">Friday</a>
</p>

{% for day in days %}
  <h3><a name="{{ day }}" href="{{ '/schedule-' | append: day | downcase | replace: ' ', '-' | append: '/' | relative_url }}">{{ day }}</a></h3>

  {% assign day_classes = site.data.schedule.classes | where: "day", day %}
  {% assign classes = day_classes %}
  {% assign room_count = rooms | size %}
  {% assign time_count = times | size %}

  <div role="table"
       aria-label="Weekly class schedule for {{ day }}"
       class="table-container"
       style="grid-template-columns: auto repeat({{ room_count }}, 1fr); grid-template-rows: auto repeat({{ time_count }}, auto);">

    <div class="table-header" style="grid-column: 1; grid-row: 1;"></div>
    {% for room in rooms %}
      {% assign col = forloop.index0 | plus: 2 %}
      <div class="table-header" style="grid-column: {{ col }}; grid-row: 1;">
        {{ room }}
      </div>
    {% endfor %}

    {% for time in times %}
      {% assign row = forloop.index0 | plus: 2 %}
      {% assign time_index = forloop.index0 %}

      <div class="time-label" style="grid-column: 1; grid-row: {{ row }};">
        {{ time }}
      </div>

      {% for room in rooms %}
        {% assign col = forloop.index0 | plus: 2 %}

        {% assign class_here = nil %}
        {% for c in classes %}
          {% if c.start == time %}
            {% if c.room == room or c.room contains room %}
              {% assign class_here = c %}
              {% break %}
            {% endif %}
          {% endif %}
        {% endfor %}

        {% if class_here %}
          <div class="table-cell"
               style="
                 grid-column: {{ col }};
                 grid-row: {{ row }} / span {{ class_here.duration }};
               ">
            <div class="class-block {{ class_here.group }}">
              <div class="class-room">
                {{ class_here.room }}
              </div>

              <div class="class-level-group">
                {% assign parts = class_here.group | remove: "l" | split: "g" %}
                Level {{ parts[0] }}, Group {{ parts[1] }}
              </div>

              <div class="class-name">
                {{ class_here.name }}
              </div>

              {% if class_here.instructor %}
                <div class="instructor-name">
                  {% if class_here.email %}
                    <a href="mailto:{{ class_here.email }}">{{ class_here.instructor }}</a>
                  {% else %}
                    {{ class_here.instructor }}
                  {% endif %}
                </div>
              {% endif %}
            </div>
          </div>

        {% else %}
          {% assign covered = false %}
          {% for c in classes %}
            {% assign room_list = c.room %}
            {% if room_list != nil %}
              {% if room_list == room or room_list contains room %}
                {% assign start_index = nil %}
                {% for t in times %}
                  {% if t == c.start %}
                    {% assign start_index = forloop.index0 %}
                    {% break %}
                  {% endif %}
                {% endfor %}
                {% if start_index != nil %}
                  {% assign end_index = start_index | plus: c.duration %}
                  {% if time_index > start_index and time_index < end_index %}
                    {% assign covered = true %}
                    {% break %}
                  {% endif %}
                {% endif %}
              {% endif %}
            {% endif %}
          {% endfor %}

          {% unless covered %}
            <div class="table-cell" style="grid-column: {{ col }}; grid-row: {{ row }};"></div>
          {% endunless %}
        {% endif %}

      {% endfor %}
    {% endfor %}

  </div>
{% endfor %}
