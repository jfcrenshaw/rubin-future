---
title: Rubin2036 Workshop Proceedings
lede: Science cases and technical upgrades explored at the August 2026 workshop
---

Page under construction...

{% assign docs_by_date = site.data.Rubin2036proceedings | sort: "date" | reverse %}

<div class="item-list">
  {% for doc in docs_by_date %}
    <article class="list-item">
      <div>
        <p class="item-meta">{{ doc.date | date: "%B %-d, %Y" }}</p>
        {% if doc.url and doc.url != "#" %}
          <h2><a href="{% include link-target.html url=doc.url %}">{{ doc.title }}</a></h2>
        {% else %}
          <h2>{{ doc.title }}</h2>
        {% endif %}
        {% if doc.authors %}<p>Authors: {{ doc.authors }}</p>{% endif %}
        {% if doc.description %}<p>{{ doc.description }}</p>{% endif %}
      </div>
    </article>
  {% endfor %}
</div>

## Contributing

To add your document:
1. Upload your document to Zenodo and save the DOI.
2. In a branch or fork of this repository, edit `_data/Rubin2036proceedings.yml` to add a card for your document, including the Zenodo DOI.
3. Make a Pull Request to this repository.

The admins will review your document for consistency with the template and coherence and merge in your changes.
