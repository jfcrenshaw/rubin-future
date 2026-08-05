---
title: Meetings
lede: Workshops, discussion sessions, agendas, notes, and links for the Rubin Future planning effort.
---

{% assign meetings_by_date = site.data.meetings | sort: "date" %}
{% assign upcoming_meetings = meetings_by_date | where: "status", "upcoming" %}
{% assign past_meetings = meetings_by_date | where: "status", "past" | reverse %}

## Upcoming

{% if upcoming_meetings.size > 0 %}
<div class="item-list">
{% for meeting in upcoming_meetings %}
    <article class="list-item">
      <div>
        <p class="item-meta">{{ meeting.date | date: "%B %-d, %Y" }}{% if meeting.location %} &middot; {{ meeting.location }}{% endif %}</p>
        <h2>{% if meeting.url and meeting.url != "#" %}<a href="{{ meeting.url }}">{{ meeting.title }}</a>{% else %}{{ meeting.title }}{% endif %}</h2>
        {% if meeting.host %}<p>Host: {{ meeting.host }}</p>{% endif %}
      </div>
      {% if meeting.materials %}
        <ul class="inline-links" aria-label="Meeting materials">
          {% for material in meeting.materials %}
            <li><a href="{{ material.url }}">{{ material.title }}</a></li>
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
        <h2>{% if meeting.url and meeting.url != "#" %}<a href="{{ meeting.url }}">{{ meeting.title }}</a>{% else %}{{ meeting.title }}{% endif %}</h2>
        {% if meeting.host %}<p>Host: {{ meeting.host }}</p>{% endif %}
      </div>
      {% if meeting.materials %}
        <ul class="inline-links" aria-label="Meeting materials">
          {% for material in meeting.materials %}
            <li><a href="{{ material.url }}">{{ material.title }}</a></li>
          {% endfor %}
        </ul>
      {% endif %}
    </article>
{% endfor %}
</div>
