---
title: People
permalink: /people/
---

{% assign people_sorted = (site.people | sort: 'joined' %}
<!--{% assign people_array = "pi|gradstudent|alumni" | split: "|" %}-->

{% assign people_array = "pi|postdoc|gradstudent|visiting|others|alumni" | split: "|" %}

{% for item in people_array %}

<!--
<div class="pos_header">
{% if item == 'postdoc' %}
<h4>Postdoctoral Fellows</h4>
 {% elsif item == 'pi' %}
<h4>Principal Investigator</h4>
 {% elsif item == 'gradstudent' %}
<h4>Graduate Students</h4>
 {% elsif item == 'visiting' %}
<h4>Visiting Scholars</h4>
 {% elsif item == 'others' %}
<h4>Honorary Members</h4>
 {% elsif item == 'alumni' %}
<h4>Alumni</h4>
{% endif %}
</div>
-->

<div class="content list people">
  {% for profile in people_sorted %}
    {% if profile.position contains item %}
    <div class="list-item-people">
      <p class="list-post-title">
        {% if profile.avatar %}
        <a href="{{ site.baseurl }}{{ profile.url }}"><img   style="border-radius: 50%;" width="200" src="{{site.baseurl}}/images/people/{{profile.avatar}}"></a>
        {% else %}
        <a href="{{ site.baseurl }}{{ profile.url }}"><img width="200" src="https://www.speakingtigerbooks.com/wp-content/uploads/2018/07/no-avatar.jpg"></a>
        {% endif %}
        <a class="name" href="{{ site.baseurl }}{{ profile.url }}">{{ profile.name }}</a>
      </p>
      <p>
        {% if profile.position == "pi" %}
          Principal Investigator
        {% elsif profile.position == "postdoc" %}
            PostDoc
        {% elsif profile.position == "gradstudent" %}
            PhD Student
        {% else %}
          {{profile.position}}
        {% endif %}
      </p>
      {% if profile.email %}<a class="fa fa-envelope-o" href="mailto:{{profile.email}}"></a>{% endif %}
      {% if profile.gscholar %}<a class="fa fa-bar-chart" href="{{profile.gscholar}}"></a>{% endif %}
      {% if profile.linkedin %}<a class="fa fa-linkedin" href="{{profile.linkedin}}"></a>{% endif %}
      {% if profile.researchgate %}<a class="fa fa-researchgate" href="{{profile.researchgate}}"></a>{% endif %}
      {% if profile.twitter %}<a class="fa fa-twitter" href="{{profile.twitter}}"></a>{% endif %}
    </div>    
    {% endif %}
  {% endfor %}
</div>
<hr>
{% endfor %}