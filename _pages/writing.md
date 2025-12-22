---
layout: page
title: Writing
permalink: /writing
---

<heading>
  <h1>Writing</h1>
</heading>

<article>
  <ul class="writing-list tabular-nums">
    {% assign writing_notes = site.notes | sort: "last_modified_at_timestamp" | reverse %}
    {% for note in writing_notes %}
      {% assign stamp_source = note.date | default: note.last_modified_at %}
      {% if stamp_source %}
        {% assign stamp = stamp_source | date: "%Y : %m" %}
      {% else %}
        {% assign stamp = "—" %}
      {% endif %}
      <li>
        <a class="internal-link plain" href="{{ site.baseurl }}{{ note.url }}">
          <div class="flex align-baseline">
            <span class="note-date">{{ stamp }}</span>
            <u>{{ note.title }}</u>
          </div>
        </a>
      </li>
    {% endfor %}
  </ul>
</article>
