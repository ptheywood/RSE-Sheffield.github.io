---
title: Team
permalink: /contact/team/
slug: team
type: text

placeholder_colours:
  - background: "var(--uos-dark-violet)"
    color: "var(--uos-wave-white)"
  - background: "var(--uos-purple)"
    color: "var(--uos-wave-white)"
  - background: "var(--uos-teal)"
    color: "var(--uos-wave-white)"
  - background: "var(--uos-peak-green)"
    color: "var(--uos-wave-white)"

---

Current members of the Research Software Engineering team are listed below. Previous members of the team can be found on our [Alumni](../alumni) page.

{% assign people = site.people | sort: 'othernames' | sort: 'surname' | sort: 'level'  %}
{% assign placeholder_idx = 0 %}
<div class="people-list row">
{% for person in people %}
  {% if person.alumnum == false %}
    <div class="col-12 col-sm-6 col-lg-4 mb-4 d-flex">
      <div class="card w-100">
        <a href="{{person.url}}" class="d-block w-100">
        {% if person.image %}
          <img src="{{person.image}}" alt="Picture of {{person.othernames}} {{person.surname}}" class="card-img-top"/>
        {% else %}
          {% assign colour_idx = placeholder_idx | modulo: page.placeholder_colours.size %}
          {% assign colours = page.placeholder_colours[colour_idx] %}
          {% assign initials = "" %}
          {% for word in person.othernames %}
              {% assign first_letter = word | slice: 0 %}
              {% assign initials = initials | append: first_letter %}
          {% endfor %}
          {% for word in person.surname %}
              {% assign first_letter = word | slice: 0 %}
              {% assign initials = initials | append: first_letter %}
          {% endfor %}
          <svg width="100" height="100" viewbox="0 0 100 100" class=" card-img-top img-fluid" style="color: {{ colours.color }}; background: {{ colours.background }}">
              <text x="50%" y="50%" dominant-baseline="middle" text-anchor="middle" fill="currentColor" font-size="1.5em">{{ initials }}</text>    
          </svg>
        {% endif %}
        {% assign placeholder_idx = placeholder_idx | plus: 1 %}

        </a>
        <div class="card-body p-2">
          {% if person.othernames and person.surname %}
            <h3><a href="{{person.url}}">{{person.othernames}} {{person.surname}}</a></h3>
          {% endif %}
          {% if person.role%}
            <p><strong>{{person.role}}</strong></p>
          {% endif %}
          {% if person.links %}
            <ul style="padding-left: 0.5em; list-style: none">
            {% for link in person.links %}
              {% if link.label and link.url %}
                <li><a href="{{ link.url }}">{{ link.label }}</a></li>
              {% endif %}
            {% endfor %}
            </ul>
          {% endif %}
        </div>
        <!-- @todo - stretched link might be bs5 only?  -->
        <!-- <a href="{{person.url}}" class="btn btn-primary mt-auto stretched-link">Read more</a> -->
      </div>
    </div>
  {% endif %}
{% endfor %}
</div>
