---
title: Team
permalink: /contact/team/
slug: team
type: text
---

Current members of the Research Software Engineering team are listed below. Previous members of the team can be found on our [Alumni](../alumni) page.

{% assign people = site.people | sort: 'othernames' | sort: 'surname' | sort: 'level'  %}
<div class="people-list row">
{% for person in people %}
  {% if person.alumnum == false %}
    <div class="col-sm-12 col-md-6 col-lg-4 mb-4 d-flex">
      <div class="card w-100">
        <a href="{{person.url}}" class="d-block w-100">
        {% if person.image %}
          <img src="{{person.image}}" alt="Picture of {{person.othernames}} {{person.surname}}" class="card-img-top"/>
        {% else %}
          <img src="/assets/images/willfurnass.png" alt="Placeholder image" class="card-img-top"/>
        {% endif %}
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
    <!-- {{ person.content }} -->
  {% endif %}
{% endfor %}
</div>
