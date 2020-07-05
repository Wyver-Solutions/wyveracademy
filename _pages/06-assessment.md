---
layout: default
title: Self-assessment
permalink: assessment
---

{% assign competencies = site.elearning-competencies | sort: "category" %}
<script>var competencyGroups = [];</script>

<div class="row mt-5">
      <div class="col-12">

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
                <p><a href="https://github.com/Wyver-Solutions/wyveracademy/issues" target="_blank">Comment on Github</a> (opens in a new tab)</p>
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
                                <p><strong>{{ item.name }}</strong></p>
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


<!--<div class="text-center"><button type="submit" class="btn btn-primary">Produce assessment graph</button></div>-->

<!-- Button trigger modal -->
<div class="text-center">
<button type="submit" class="btn btn-primary" data-toggle="modal" data-target="#exampleModal">
  Show summary chart
</button>
</div>


</form>


</div> <!-- end of smartwizard -->

</div> <!-- End of column -->

<!-- Modal -->
<div class="modal fade" id="exampleModal" tabindex="-1" role="dialog" aria-labelledby="exampleModalLabel" aria-hidden="true">
  <div class="modal-dialog modal-xl" role="document">
    <div class="modal-content">
      <div class="modal-header">
        <h5 class="modal-title" id="exampleModalLabel"></h5>
        <button type="button" class="close" data-dismiss="modal" aria-label="Close">
          <span aria-hidden="true">&times;</span>
        </button>
      </div>
      <div class="modal-body">
        <canvas id="radarChart"></canvas>
      </div>
      <div class="modal-footer">
        <button type="button" class="btn btn-secondary" data-dismiss="modal">Close</button>
        <a type="button" id="downloadChart" class="btn btn-primary" download="competency-assessment">Download summary</a>
      </div>
    </div>
  </div>
</div>









</div><!-- end of row-->
<div class="text-center">
    <p>We can <a href="{{ site.baseurl }}/coaching">coach</a> you to the next level, or to improve where you have gaps.</p>
</div>
