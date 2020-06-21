---
layout: default
title: Assessment
permalink: /assessment/
---
<form id="assessment">
  <div class="form-group">
    <label for="name">Your name</label>
    <input type="text" class="form-control" id="name" aria-describedby="emailHelp" placeholder="Enter your name">
    <small id="emailHelp" class="form-text text-muted">This data stays in your browser. We do not collect any of it.</small>
  </div>
  
  <div class="form-group">

{% assign competencies = site.competencies | sort: "category" %}

<script>var competencyGroups = [];</script>

{% for c in competencies %}

 
      <h2>{{ c.title }}</h2>
      <p>{{ c.description }}</p>
<table id="competencies" width="100%" class="table table-bordered table-striped">
  <thead class="thead-dark">
    <th class="all">Sub-category</th>
    <th class="min-tablet-l" width="30%">Level 1</th>
    <th class="min-tablet-l" width="30%">Level 2</th>
    <th class="min-tablet-l" width="30%">Level 3</th>
  </thead>
  <tbody>
    {% for item in c.items %}
<script>competencyGroups.push(["{{ c.ID }}_{{ item.ID }}",""]);</script>
  <tr>
    <td class="align-top">
        <p>{{ item.name }}</p>
    </td>
    <td class="align-top">
        <p>{{ item.L1 }}</p>
    </td>
    <td class="align-top">
        <p>{{ item.L2 }}</p>
    </td>
    <td class="align-top">
        <p>{{ item.L3 }}</p>
    </td>
  </tr>
  <tr>
    <td class="align-top text-center">
        <label for="{{ item.ID }}">Clear</label>
        <input type="radio" id="{{ c.ID }}_{{ item.ID }}" name="{{ c.ID }}_{{ item.ID }}" value="0">
    </td>
    <td class="align-top text-center">
        <input type="radio" id="{{ c.ID }}_{{ item.ID }}" name="{{ c.ID }}_{{ item.ID }}" value="1">
    </td>
    <td class="align-top text-center">
        <input type="radio" id="{{ c.ID }}_{{ item.ID }}" name="{{ c.ID }}_{{ item.ID }}" value="2">
    </td>
    <td class="align-top text-center">
        <input type="radio" id="{{ c.ID }}_{{ item.ID }}" name="{{ c.ID }}_{{ item.ID }}" value="3">
    </td>
  </tr>
  {% endfor %}
  </tbody>
</table>
{% endfor %}


  </div>
  <button type="submit" class="btn btn-primary">Submit</button>
</form>