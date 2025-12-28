---
layout: page
title: Topics
permalink: /topics
---

<heading>
  <h1>Topics</h1>
</heading>

{% assign raw_topics = site.notes | map: "topics" | join: "," | split: "," | uniq | sort %}

<article class="line-height-loose">
  <p class="muted font-ui">Topics are pulled from each note’s front matter.</p>

  {% for topic in raw_topics %}
    {% assign topic_clean = topic | strip %}
    {% if topic_clean != "" %}
      <div class="topic-block" id="{{ topic_clean | slugify }}" data-topic="{{ topic_clean | slugify }}">
        <p><strong>{{ topic_clean }}</strong></p>
      {% assign notes_with_topic = site.notes | where_exp: "note", "note.topics contains topic_clean" | sort: "last_modified_at_timestamp" | reverse %}
      {% if notes_with_topic and notes_with_topic != empty %}
        <ul class="list-plain">
          {% for note in notes_with_topic %}
            <li>
              <a href="{{ site.baseurl }}{{ note.url }}" class="internal-link">
                {{ note.title }}
              </a>
            </li>
          {% endfor %}
        </ul>
      {% else %}
        <p class="muted small">No notes yet.</p>
      {% endif %}
      </div>
    {% endif %}
  {% endfor %}
</article>

<script>
  (function () {
    function filterTopics() {
      var hash = window.location.hash.replace("#", "").trim();
      var blocks = document.querySelectorAll(".topic-block");
      if (!hash) {
        blocks.forEach(function (block) {
          block.style.display = "";
        });
        return;
      }
      blocks.forEach(function (block) {
        if (block.dataset.topic === hash) {
          block.style.display = "";
        } else {
          block.style.display = "none";
        }
      });
    }

    window.addEventListener("hashchange", filterTopics);
    document.addEventListener("DOMContentLoaded", filterTopics);
  })();
</script>
