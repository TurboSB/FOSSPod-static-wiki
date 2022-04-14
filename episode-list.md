---
---
# Episode List

{% assign seasons = "" | split: ',' %}

{%- for episode in site.episodes -%}
  {% assign seasons = seasons | push: episode.season %}
{%- endfor -%}

{% assign seasons = seasons | uniq | sort%}

{% for season_num in seasons %}
  {% assign season_eps = "" | split: ',' %}

  <h2 id="Season {{ tag }}">Season {{ season_num }}</h2>
  <ol>

  {% for episode in site.episodes %}
    {% if episode.season == season_num %}
      {% assign season_eps = season_eps | push: episode %}
    {% endif %}
  {% endfor %}

  {% for episode in season_eps %}
    <li><a href="{{ tagged.url }}">{{ episode.title }}</a></li>
  {% endfor %}

  </ol>
{% endfor %}