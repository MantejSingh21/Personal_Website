---
layout: page
title: Home
id: home
permalink: /
---

<heading>
  <h1>Welcome</h1>
</heading>

<article>
  <p class="muted font-ui">Writing</p>
  <ul class="writing-list tabular-nums">
    {% assign recent_notes = site.notes | sort: "last_modified_at_timestamp" | reverse %}
    {% for note in recent_notes limit: 6 %}
      {% assign stamp_source = note.date | default: note.last_modified_at %}
      {% if stamp_source %}
        {% assign stamp = stamp_source | date: "%Y · %m" %}
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

  <p class="small muted">See everything in the <a class="internal-link" href="{{ site.baseurl }}/writing">Writing</a> list.</p>
</article>
