---
layout: page
title: Seminars
permalink: /seminars/
semesters:
  - 2017s1
  - 2016s2
  - 2016s1
---

<h2> Optimization and Numerical Analysis </h2>

This semester the seminars will take place on the Anfiteatro A, at 15h30,
Fridays.

Older seminars:
<ul class="list-inline">
{% for semester in page.semesters %}
<li><button class="btn btn-primary" onclick="seminarShow('{{semester}}')">
{{semester}}
</button></li>
{% endfor %}
</ul>

<hr>

{% for semester in page.semesters %}
<div class="container-fluid seminar-show" id="{{ semester }}">
<h3> {{ semester }} </h3>
{% assign events = site.data.seminars | where: 'semester', semester | sort: 'date' %}
{% assign lastdate = "" %}

{% for pres in events %}
<div class="row">
{% if pres.date != lastdate %}
  <div class="col-md-2">
  <em> {{ pres.date | date: "%b. %d, %Y" }}: </em> <br>
  </div>
  <div class="col-md-10">
{% else %}
  <div class="col-md-offset-2 col-md-10">
{% endif %}
{% if pres.author == "TBA" %}
  <span><strong> Free Spot </strong></span>
  <p> Contact us if you'd like to give a talk </p>
{% else %}
  <span><strong> {{ pres.author }} </strong></span> - 
  <span> {{ pres.affiliation }} </span><br>
{% if pres.title %}
  <p>
  <span><em> {{ pres.title }} </em></span><br>
    {% if pres.abstract %}
  <small>{{ pres.abstract }}</small><br>
    {% endif %}
  </p>
{% else %}
<br>
{% endif %}
    {% endif %}
  </div>
{% assign lastdate = pres.date %}
</div>
{% endfor %}
</div> <!-- end div id=semeter -->

{% endfor %}
