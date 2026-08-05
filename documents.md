---
title: Documents
#lede: Shared papers, notes, reports, slides, and reference links for Rubin Future planning.
---

{% assign documents_by_year = site.data.documents | sort: "year" | reverse %}

<div class="item-list">
  {% for doc in documents_by_year %}
  <article class="list-item">
    <div>
      {% if doc.type or doc.year %}
        <p class="item-meta">{% if doc.type %}{{ doc.type }}{% endif %}{% if doc.type and doc.year %} &middot; {% endif %}{% if doc.year %}{{ doc.year }}{% endif %}</p>
      {% endif %}
      {% if doc.url and doc.url != "#" %}
        <h2><a href="{% include link-target.html url=doc.url %}">{{ doc.title }}</a></h2>
      {% else %}
        <h2>{{ doc.title }}</h2>
      {% endif %}
      {% if doc.description %}<p>{{ doc.description }}</p>{% endif %}
      {% if doc.materials %}
        <ul class="inline-links document-links" aria-label="{{ doc.title | escape }} documents">
          {% for material in doc.materials %}
            <li>
              {% if material.url and material.url != "#" %}
                <a href="{% include link-target.html url=material.url %}">{{ material.title }}</a>
              {% else %}
                <span>{{ material.title }}</span>
              {% endif %}
            </li>
          {% endfor %}
        </ul>
      {% endif %}
    </div>
  </article>
  {% endfor %}
</div>
