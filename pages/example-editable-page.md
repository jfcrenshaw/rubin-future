---
title: Example Editable Page
lede: This page is an example of a document entry that lives directly on the Rubin Future website.
---

This is a normal Markdown page in the repository. Edit this file to update the page content, then commit and push to publish the changes through GitHub Pages.

Use pages like this when the material should be public, lightweight, and easy to revise without managing a separate PDF or external document.

## Example Content

- Add a short meeting summary.
- Record action items.
- Link to related documents, slides, or notes.
- Replace this example with a real planning page when ready.

## Building Content From YAML

The cards below are rendered from `_data/meetings.yml`. Pages can use the same pattern with another file in `_data/`, but the fields in the loop should match the fields in that YAML file.

{% assign meetings_by_date = site.data.meetings | sort: "date" | reverse %}

<div class="item-list">
  {% for meeting in meetings_by_date %}
    <article class="list-item">
      <div>
        <p class="item-meta">{{ meeting.date | date: "%B %-d, %Y" }}{% if meeting.location %} &middot; {{ meeting.location }}{% endif %}</p>
        <h2>{{ meeting.title }}</h2>
        {% if meeting.host %}<p>Host: {{ meeting.host }}</p>{% endif %}
      </div>
    </article>
  {% endfor %}
</div>
