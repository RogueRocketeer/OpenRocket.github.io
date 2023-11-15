---
layout: default
title: Tutorials
permalink: /tutorials/
---

<!-- Introduction -->
<div class="tutorial-introduction" markdown="1">
  <h1>Welcome to Our Tutorials!</h1>
  Here you'll find a curated list of tutorials to help you __master OpenRocket__.

  Whether you're just starting our, or looking to refine your knowledge, there's something here for everyone. Dive in and happy learning! 😊🚀

  <br>
  Do you have a <u>request for a new tutorial</u> or want to <u>improve an existing tutorial</u>? Then please mail us at <a href="mailto:{{ site.email }}" target="_blank">{{ site.email }}</a>.
  
</div>

<hr style="width: 80%">

<!-- Difficulty filter -->
<div class="difficulty-filter">
  <span class="label-select-difficulty">Select difficulty level:</span>

  <input type="checkbox" id="beginner" value="beginner" onchange="filterTutorials()">
  <label for="beginner" data-difficulty="beginner">Beginner</label>

  <input type="checkbox" id="intermediate" value="intermediate" onchange="filterTutorials()">
  <label for="intermediate" data-difficulty="intermediate">Intermediate</label>

  <input type="checkbox" id="advanced" value="advanced" onchange="filterTutorials()">
  <label for="advanced" data-difficulty="advanced">Advanced</label>
</div>

<div class="tutorial-container">
  <!-- This will be our button to show the tutorial list on mobile -->
  <div id="mobile-toggle" class="mobile-toggle" onclick="toggleList()">Tutorials List ▼</div>

  <!-- Tutorial content -->
  <div class="tutorials">
    {% assign sorted_tutorials = site.tutorials | sort: "date" | reverse %}
    {% for tutorial in sorted_tutorials %}
      <a href="{{ tutorial.url }}" class="tutorial-tile">
            {% if tutorial.thumbnail %}
                <div class="tutorial-thumbnail">
                    <img src="{{ tutorial.thumbnail }}" alt="{{ tutorial.title }}">
                </div>
            {% endif %}
            <div class="tutorial-title">
                <h3>{{ tutorial.title }}</h3>
            </div>
            <div class="date-difficulty-wrapper">
              <div class="tutorial-date">{{ tutorial.date | date: "%B %d, %Y" }}</div>
              <div class="tutorial-difficulty" data-difficulty="{{ tutorial.difficulty }}" title="{{ site.data.tutorial_difficulties[tutorial.difficulty].tooltip }}">{{ tutorial.difficulty }}</div>
          </div>
      </a>
    {% endfor %}
  </div>

  <!-- Sidebar with expandable/collapsible list -->
  <div class="tutorial-selection">
    <div class="toggle-list">
      <div class="toggle-header" onclick="toggleList()">
        Tutorials List ▼
      </div>
      <ul id="tutorialsList" class="collapsed">
        {% for tutorial in site.tutorials reversed %}
          <li><a href="{{ tutorial.url }}">{{ tutorial.title }}</a></li>
        {% endfor %}
      </ul>
    </div>
  </div>
</div>
