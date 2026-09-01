# Publications

<div class="publications">
  <ol class="bibliography" reversed start="{{ site.data.publications.main | size }}">
    {% for link in site.data.publications.main %}
    {% assign authors = link.authors | split: ", " %}
    <li>
      <span class="publication-number" aria-hidden="true">{% if forloop.rindex < 10 %}0{% endif %}{{ forloop.rindex }}</span>
      <article class="publication-record">
        <h3 class="publication-title">{{ link.title }}</h3>

        <p class="publication-authors">
          {% for author in authors %}{% assign coauthor = site.data.coauthors.main | where: "name", author | first %}{% if author == site.title %}<strong class="self-author">{{ author }}</strong>{% elsif coauthor and coauthor.homepage %}<a href="{{ coauthor.homepage }}" target="_blank" rel="noopener noreferrer">{{ author }}</a>{% else %}{{ author }}{% endif %}{% unless forloop.last %}, {% endunless %}{% endfor %}
        </p>

        {% if link.conference %}<p class="publication-venue"><em>{{ link.conference }}</em></p>{% endif %}

        <div class="publication-details">
          <div class="publication-links">
            {% if link.arxiv %}<a href="https://arxiv.org/abs/{{ link.arxiv }}" target="_blank" rel="noopener">arXiv</a>{% endif %}
            {% if link.doi %}<a href="https://doi.org/{{ link.doi }}" target="_blank" rel="noopener">Journal</a>{% endif %}
            {% if link.code %}<a href="{{ link.code }}" target="_blank" rel="noopener">Code</a>{% endif %}
            {% if link.page %}<a href="{{ link.page }}" target="_blank" rel="noopener">Project page</a>{% endif %}
            {% if link.bibtex %}<a href="{{ link.bibtex }}" target="_blank" rel="noopener">BibTeX</a>{% endif %}
          </div>

          {% if link.journal %}<div class="publication-journal">{{ link.journal | markdownify | remove: '<p>' | remove: '</p>' }}</div>{% endif %}
          {% if link.notes %}<div class="publication-note">{{ link.notes | markdownify | remove: '<p>' | remove: '</p>' }}</div>{% endif %}
          {% if link.others %}<div class="publication-note">{{ link.others }}</div>{% endif %}
        </div>
      </article>
    </li>
    {% endfor %}
  </ol>
</div>
