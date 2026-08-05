---
title: Rubin2036 Workshop Proceedings
lede: The science cases and technical upgrades explored at the August 2026 workshop
---

TBD

## The science cases and technical discussions

{% assign docs_by_date = site.data.Rubin2036proceedings | sort: "date" | reverse %}

<div class="item-list">
  {% for doc in docs_by_date %}
    <article class="list-item">
      <div>
        <p class="item-meta">{{ doc.date | date: "%B %-d, %Y" }}</p>
        <h2>{{ doc.title }}</h2>
        {% if doc.authors %}<p>Authors: {{ doc.authors }}</p>{% endif %}
      </div>
    </article>
  {% endfor %}
</div>

## Instructions

To add your document:
1. Upload your materials to Zenodo and save the DOI.
2. In a branch or fork of this repository, edit `_data/Rubin2036proceedings.yml` to add a card for your document, including the Zenodo DOI.
3. Make a Pull Request to this repository.

The admins will review your document for consistency with the template and coherence and merge in your changes.
