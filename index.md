---
layout: default
---

<div class="home">
  <div class="text-center mb-4">
    <h1>Welcome to Weekly Cloud</h1>
    <p>Your source for cloud computing insights, tutorials, and weekly updates from the rapidly evolving world of cloud technology.</p>
  </div>

  {%- if site.posts.size > 0 -%}
  <h2>Latest Posts</h2>

  <ul class="post-list">
    {%- for post in site.posts -%}
    <li>
      <div class="post-meta">{{ post.date | date: "%B %-d, %Y" }}</div>
      <a class="post-link" href="{{ post.url | relative_url }}">
        {{ post.title | escape }}
      </a>
      <div class="post-excerpt">{{ post.excerpt | strip_html | truncatewords: 30 }}</div>
    </li>
    {%- endfor -%}
  </ul>
  {%- else -%}
  <div class="text-center">
    <h2>Coming Soon</h2>
    <p>New posts and weekly cloud updates will be published here soon. Stay tuned!</p>
  </div>
  {%- endif -%}

  <div class="text-center mt-4">
    <p><a href="{{ "/feed.xml" | relative_url }}">Subscribe via RSS</a></p>
  </div>
</div>