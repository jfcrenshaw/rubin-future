---
title: Meetings
lede: Workshops, discussion sessions, agendas, notes, and links for the Rubin Future planning effort.
---

{% assign meetings_by_date = site.data.meetings | sort: "date" %}
{% assign upcoming_meetings = meetings_by_date | where: "status", "upcoming" %}
{% assign past_meetings = meetings_by_date | where: "status", "past" | reverse %}
{% assign relative_root = "" %}
{% assign url_segments = page.url | split: "/" %}
{% for segment in url_segments %}
  {% if segment != "" %}
    {% assign relative_root = relative_root | append: "../" %}
  {% endif %}
{% endfor %}

## Upcoming

{% if upcoming_meetings.size > 0 %}
<div class="item-list">
{% for meeting in upcoming_meetings %}
    <article class="list-item">
      <div>
        <p class="item-meta">{{ meeting.date | date: "%B %-d, %Y" }}{% if meeting.location %} &middot; {{ meeting.location }}{% endif %}</p>
        {% if meeting.url and meeting.url != "#" %}
          {% if meeting.url contains "://" or meeting.url contains "mailto:" %}
            {% assign meeting_url = meeting.url %}
          {% else %}
            {% assign meeting_path = meeting.url | remove_first: "/" %}
            {% assign meeting_url = relative_root | append: meeting_path %}
          {% endif %}
          <h2><a href="{{ meeting_url }}">{{ meeting.title }}</a></h2>
        {% else %}
          <h2>{{ meeting.title }}</h2>
        {% endif %}
        {% if meeting.host %}<p>Host: {{ meeting.host }}</p>{% endif %}
      </div>
      {% if meeting.materials %}
        <ul class="inline-links" aria-label="Meeting materials">
          {% for material in meeting.materials %}
            {% if material.url and material.url != "#" %}
              {% if material.url contains "://" or material.url contains "mailto:" %}
                {% assign material_url = material.url %}
              {% else %}
                {% assign material_path = material.url | remove_first: "/" %}
                {% assign material_url = relative_root | append: material_path %}
              {% endif %}
              <li><a href="{{ material_url }}">{{ material.title }}</a></li>
            {% else %}
              <li><span>{{ material.title }}</span></li>
            {% endif %}
          {% endfor %}
        </ul>
      {% endif %}
    </article>
{% endfor %}
</div>
{% else %}
No upcoming meetings are listed yet.
{% endif %}

## Past Meetings

<div class="item-list">
{% for meeting in past_meetings %}
    <article class="list-item">
      <div>
        <p class="item-meta">{{ meeting.date | date: "%B %-d, %Y" }}{% if meeting.location %} &middot; {{ meeting.location }}{% endif %}</p>
        {% if meeting.url and meeting.url != "#" %}
          {% if meeting.url contains "://" or meeting.url contains "mailto:" %}
            {% assign meeting_url = meeting.url %}
          {% else %}
            {% assign meeting_path = meeting.url | remove_first: "/" %}
            {% assign meeting_url = relative_root | append: meeting_path %}
          {% endif %}
          <h2><a href="{{ meeting_url }}">{{ meeting.title }}</a></h2>
        {% else %}
          <h2>{{ meeting.title }}</h2>
        {% endif %}
        {% if meeting.host %}<p>Host: {{ meeting.host }}</p>{% endif %}
      </div>
      {% if meeting.materials %}
        <ul class="inline-links" aria-label="Meeting materials">
          {% for material in meeting.materials %}
            {% if material.url and material.url != "#" %}
              {% if material.url contains "://" or material.url contains "mailto:" %}
                {% assign material_url = material.url %}
              {% else %}
                {% assign material_path = material.url | remove_first: "/" %}
                {% assign material_url = relative_root | append: material_path %}
              {% endif %}
              <li><a href="{{ material_url }}">{{ material.title }}</a></li>
            {% else %}
              <li><span>{{ material.title }}</span></li>
            {% endif %}
          {% endfor %}
        </ul>
      {% endif %}
    </article>
{% endfor %}
</div>
