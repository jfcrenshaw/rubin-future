---
title: Meetings
lede: Past and future workshops, and associated documents.
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
        {% if meeting.url and meeting.url != "#" %}
          <h2><a href="{% include link-target.html url=meeting.url %}">{{ meeting.title }}</a></h2>
        {% else %}
          <h2>{{ meeting.title }}</h2>
        {% endif %}
        {% if meeting.host %}<p>Host: {{ meeting.host }}</p>{% endif %}
      </div>
      {% if meeting.materials %}
        <ul class="inline-links" aria-label="Meeting materials">
          {% for material in meeting.materials %}
            {% if material.url and material.url != "#" %}
              <li><a href="{% include link-target.html url=material.url %}">{{ material.title }}</a></li>
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
          <h2><a href="{% include link-target.html url=meeting.url %}">{{ meeting.title }}</a></h2>
        {% else %}
          <h2>{{ meeting.title }}</h2>
        {% endif %}
        {% if meeting.host %}<p>Host: {{ meeting.host }}</p>{% endif %}
      </div>
      {% if meeting.materials %}
        <ul class="inline-links" aria-label="Meeting materials">
          {% for material in meeting.materials %}
            {% if material.url and material.url != "#" %}
              <li><a href="{% include link-target.html url=material.url %}">{{ material.title }}</a></li>
            {% else %}
              <li><span>{{ material.title }}</span></li>
            {% endif %}
          {% endfor %}
        </ul>
      {% endif %}
    </article>
{% endfor %}
</div>
