---
layout: default
title: Assessment
permalink: /assessment/
---
{% assign competencies = site.competencies | sort: "category" %}
<script>var competencyGroups = [];</script>

<div id="smartwizard">
    <!-- Setup tabs -->
    <ul class="nav" id="Tabs" role="tablist">

    {% for c in competencies %}
        <li role="presentation">
        <a class="nav-link" id="{{ c.ID }}-tab" href="#{{ c.ID }}-pane" role="tab" aria-controls="{{ c.ID }}" aria-selected="true">{{ c.title }}</a>
      </li>
    {% endfor %}
</ul>
    

<form id="assessment">
    

    <div class="tab-content">

    {% for c in competencies %}

        <div class="tab-pane" id="{{ c.ID }}-pane" role="tabpanel" aria-labelledby="{{ c.ID }}-tab">
            <h2>{{ c.title }}</h2>
            <div class="form-group">
      
                <p>{{ c.description }}</p>
                <table width="100%" class="table table-bordered table-striped">
                    <thead class="thead-dark">
                        <th class="all">Sub-category</th>
                        <th class="min-tablet-l" width="30%">Level 1</th>
                        <th class="min-tablet-l" width="30%">Level 2</th>
                        <th class="min-tablet-l" width="30%">Level 3</th>
                    </thead>
                    <tbody>
                        {% for item in c.items %}
                        <script>competencyGroups.push(["{{ c.title }}","{{ c.ID }}_{{ item.ID }}",0]);</script>
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
                                <label for="{{ item.ID }}">Unset</label>
                                <input type="radio" id="{{ c.ID }}_{{ item.ID }}_0" name="{{ c.ID }}_{{ item.ID }}" value="0" checked="checked">
                            </td>
                            <td class="align-top text-center">
                                <input type="radio" id="{{ c.ID }}_{{ item.ID }}_1" name="{{ c.ID }}_{{ item.ID }}" value="1">
                            </td>
                            <td class="align-top text-center">
                                <input type="radio" id="{{ c.ID }}_{{ item.ID }}_2" name="{{ c.ID }}_{{ item.ID }}" value="2">
                            </td>
                            <td class="align-top text-center">
                                <input type="radio" id="{{ c.ID }}_{{ item.ID }}_3" name="{{ c.ID }}_{{ item.ID }}" value="3">
                            </td>
                        </tr>
                        {% endfor %}
                    </tbody>
                </table>
            </div><!-- end of form group: {{ c.title }}-->
        </div><!-- end of tab pane -->

        {% endfor %}
    </div> <!--- end of tab content -->

<div class="text-center"><button type="submit" class="btn btn-primary">Produce assessment graph</button></div>  
  

</form>


</div> <!-- end of smartwizard -->
<canvas id="radarChart"></canvas>