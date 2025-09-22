---
layout: default
title: All Posts
permalink: /posts/
---

<div class="posts-archive">
  <h1>All Posts</h1>

  {%- if site.posts.size > 0 -%}
    <p class="archive-subtitle">{{ site.posts.size }} {% if site.posts.size == 1 %}post{% else %}posts{% endif %} total</p>

    <div class="posts-by-year">
      {%- assign posts_by_year = site.posts | group_by_exp: "post", "post.date | date: '%Y'" -%}

      {%- for year_group in posts_by_year -%}
        <div class="year-section">
          <h2 class="year-heading">{{ year_group.name }}</h2>

          <ul class="post-list">
            {%- for post in year_group.items -%}
            <li class="post-item">
              <div class="post-meta">
                <time datetime="{{ post.date | date_to_xmlschema }}">
                  {{ post.date | date: "%B %-d" }}
                </time>
                {%- if post.categories.size > 0 -%}
                  <span class="post-categories">
                    {%- for category in post.categories -%}
                      <span class="category">{{ category }}</span>
                    {%- endfor -%}
                  </span>
                {%- endif -%}
              </div>

              <h3 class="post-title">
                <a href="{{ post.url | relative_url }}">{{ post.title | escape }}</a>
              </h3>

              {%- if post.excerpt -%}
                <div class="post-excerpt">
                  {{ post.excerpt | strip_html | truncatewords: 25 }}
                </div>
              {%- endif -%}
            </li>
            {%- endfor -%}
          </ul>
        </div>
      {%- endfor -%}
    </div>
  {%- else -%}
    <div class="no-posts">
      <h2>No Posts Yet</h2>
      <p>Posts will appear here once they are published. Check back soon for cloud computing insights and weekly updates!</p>
    </div>
  {%- endif -%}
</div>