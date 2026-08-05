---
title: Documents
lede: Shared papers, notes, reports, slides, and reference links for Rubin Future planning.
---

{% assign documents_by_category = site.data.documents | group_by: "category" | sort: "name" %}
{% assign relative_root = "" %}
{% assign url_segments = page.url | split: "/" %}
{% for segment in url_segments %}
  {% if segment != "" %}
    {% assign relative_root = relative_root | append: "../" %}
  {% endif %}
{% endfor %}

{% for group in documents_by_category %}
## {{ group.name }}

<div class="item-list">
  {% assign docs = group.items | sort: "title" %}
  {% for doc in docs %}
    <article class="list-item">
      <div>
        {% if doc.type or doc.year %}
          <p class="item-meta">{% if doc.type %}{{ doc.type }}{% endif %}{% if doc.type and doc.year %} &middot; {% endif %}{% if doc.year %}{{ doc.year }}{% endif %}</p>
        {% endif %}
        {% if doc.url and doc.url != "#" %}
          {% if doc.url contains "://" or doc.url contains "mailto:" %}
            {% assign document_url = doc.url %}
          {% else %}
            {% assign document_path = doc.url | remove_first: "/" %}
            {% assign document_url = relative_root | append: document_path %}
          {% endif %}
          <h2><a href="{{ document_url }}">{{ doc.title }}</a></h2>
        {% else %}
          <h2>{{ doc.title }}</h2>
        {% endif %}
        {% if doc.description %}<p>{{ doc.description }}</p>{% endif %}
      </div>
    </article>
  {% endfor %}
</div>
{% endfor %}
