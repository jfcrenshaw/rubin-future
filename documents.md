---
title: Documents
lede: Shared papers, notes, reports, slides, and reference links for Rubin Future planning.
---

{% assign documents_by_category = site.data.documents | group_by: "category" | sort: "name" %}

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
        <h2>{% if doc.url and doc.url != "#" %}<a href="{{ doc.url }}">{{ doc.title }}</a>{% else %}{{ doc.title }}{% endif %}</h2>
        {% if doc.description %}<p>{{ doc.description }}</p>{% endif %}
      </div>
    </article>
  {% endfor %}
</div>
{% endfor %}
