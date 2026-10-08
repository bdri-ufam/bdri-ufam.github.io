---
layout: default
title: Pessoas
permalink: /pessoas/
---
# Pessoas

## Líderes

<ul class="people">
{% for p in site.data.people.leaders %}
  <li>
    <strong>{{ p.name }}</strong><br>
    <span class="role">{{ p.role }}</span>
    {% if p.interests != "" %}<br><span class="muted">{{ p.interests }}</span>{% endif %}
    <br>
    <a href="mailto:{{ p.email }}">{{ p.email }}</a>
    {% if p.lattes != "" %} · <a href="{{ p.lattes }}">Lattes</a>{% endif %}
    {% if p.dblp != "" %} · <a href="{{ p.dblp }}">DBLP</a>{% endif %}
  </li>
{% endfor %}
</ul>

## Membros atuais

{% assign order = "posdoc,doutorado,mestrado,ic" | split: "," %}
{% assign titles = "Pós-doutorado,Doutorado,Mestrado,Iniciação científica" | split: "," %}
{% for g in order %}
{% assign idx = forloop.index0 %}
{% capture block %}
{% for m in site.data.people.members %}
{% if m.group == g %}
{% if m.public == "yes" or m.public == "pending" and site.show_pending %}
  <li>{{ m.name }} <span class="role">· desde {{ m.since }}</span>{% if m.public == "pending" %}<span class="badge">a confirmar{% if m.confirmar %}: {{ m.confirmar }}{% endif %}</span>{% endif %}</li>
{% endif %}
{% endif %}
{% endfor %}
{% endcapture %}
{% assign trimmed = block | strip %}
{% if trimmed != "" %}
### {{ titles[idx] }}

<ul class="people">
{{ block }}
</ul>
{% endif %}
{% endfor %}

{% if site.show_alumni %}
## Egressos

Títulos defendidos sob orientação dos líderes do grupo, com o ano de defesa.

### Doutorado

<ul class="people">
{% for a in site.data.people.alumni_doctorate %}<li>{{ a.name }} <span class="role">· {{ a.year }}</span></li>
{% endfor %}
</ul>

### Mestrado

<ul class="people">
{% for a in site.data.people.alumni_masters %}<li>{{ a.name }} <span class="role">· {{ a.year }}</span></li>
{% endfor %}
</ul>
{% endif %}
