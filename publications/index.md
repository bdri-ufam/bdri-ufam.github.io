---
layout: default
title: Publications
permalink: /publications/
---
# Publications

Recent publications by the group leaders (2021 onwards). Complete lists: Edleno Silva de Moura on [DBLP](https://dblp.org/pid/m/EdlenoSilvadeMoura) and [Lattes](http://lattes.cnpq.br/4737852130924504); Altigran Soares da Silva on [DBLP](https://dblp.org/pid/s/ASdaSilva) and [Lattes](http://lattes.cnpq.br/3405503472010994).

{% assign years = site.data.publications | map: "year" | uniq | sort | reverse %}
{% for y in years %}
## {{ y }}

<ol class="pubs">
{% for p in site.data.publications %}{% if p.year == y %}
  <li>
    {{ p.authors }}.
    <a href="{{ p.url }}">{{ p.title }}</a>.
    <span class="venue"><em>{{ p.venue }}</em>{% if p.volume %}, {{ p.volume }}{% endif %}{% if p.pages %}, pp. {{ p.pages }}{% endif %}, {{ p.year }}.</span>
    {% if p.type == "p" %}<span class="tag">preprint</span>{% endif %}
  </li>
{% endif %}{% endfor %}
</ol>
{% endfor %}
