---
layout: default
title: People
permalink: /people/
---
# People

## Group leaders

<ul class="people">
{% for p in site.data.people.leaders %}
  <li>
    <strong>{{ p.name }}</strong><br>
    <span class="role">{{ p.role }}</span>
    {% if p.bio != "" %}<br>{{ p.bio }}{% endif %}
    {% if p.interests != "" %}<br><span class="muted">Research interests: {{ p.interests }}</span>{% endif %}
    <br>
    <a href="mailto:{{ p.email }}">{{ p.email }}</a>
    {% if p.homepage != "" %} · <a href="{{ p.homepage }}">Homepage</a>{% endif %}
    {% if p.lattes != "" %} · <a href="{{ p.lattes }}">Lattes</a>{% endif %}
    {% if p.dblp != "" %} · <a href="{{ p.dblp }}">DBLP</a>{% endif %}
    {% if p.orcid != "" %} · <a href="{{ p.orcid }}">ORCID</a>{% endif %}
  </li>
{% endfor %}
</ul>

## Current members

{% assign order = "posdoc,doutorado,mestrado,ic" | split: "," %}
{% assign titles = "Postdoctoral researchers,PhD students,MSc students,Undergraduate researchers" | split: "," %}
{% for g in order %}
{% assign idx = forloop.index0 %}
{% capture block %}
{% for m in site.data.people.members %}
{% if m.group == g %}
{% if m.public == "yes" or m.public == "pending" and site.show_pending %}
  <li>{{ m.name }} <span class="role">· since {{ m.since }}</span>{% if m.topic %}<br><span class="muted topic">{{ m.topic }}</span>{% endif %}{% if m.public == "pending" %}<span class="badge">to be confirmed{% if m.confirmar %}: {{ m.confirmar }}{% endif %}</span>{% endif %}</li>
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
## Alumni

Degrees completed under the supervision of the group leaders, with year of defense.

### PhD

<ul class="people">
{% for a in site.data.people.alumni_doctorate %}<li>{{ a.name }} <span class="role">· {{ a.year }}</span></li>
{% endfor %}
</ul>

### MSc

<ul class="people">
{% for a in site.data.people.alumni_masters %}<li>{{ a.name }} <span class="role">· {{ a.year }}</span></li>
{% endfor %}
</ul>
{% endif %}
