---
layout: default
title: Weekly News
permalink: /weekly/
---

<div class="weekly-archive">
  <h1>Weekly Cloud News</h1>

  {%- assign weekly_posts = site.posts | where_exp: "post", "post.categories contains 'weekly'" -%}

  {%- if weekly_posts.size > 0 -%}
    <p class="archive-subtitle">{{ weekly_posts.size }} weekly {% if weekly_posts.size == 1 %}roundup{% else %}roundups{% endif %} published</p>

    <div class="weekly-intro">
      <p>Stay updated with the latest developments in cloud computing. Our weekly roundups cover major announcements, new services, industry trends, and insights from AWS, Azure, Google Cloud, and other cloud providers.</p>
    </div>

    <div class="posts-by-year">
      {%- assign weekly_by_year = weekly_posts | group_by_exp: "post", "post.date | date: '%Y'" -%}

      {%- for year_group in weekly_by_year -%}
        <div class="year-section">
          <h2 class="year-heading">{{ year_group.name }}</h2>

          <ul class="post-list">
            {%- for post in year_group.items -%}
            <li class="post-item weekly-item">
              <div class="post-meta">
                <time datetime="{{ post.date | date_to_xmlschema }}">
                  {{ post.date | date: "%B %-d" }}
                </time>
                <span class="weekly-badge">Weekly Roundup</span>
                {%- assign other_categories = post.categories | where_exp: "cat", "cat != 'weekly'" -%}
                {%- if other_categories.size > 0 -%}
                  <span class="post-categories">
                    {%- for category in other_categories -%}
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
                  {{ post.excerpt | strip_html | truncatewords: 30 }}
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
      <h2>Weekly Roundups Coming Soon</h2>
      <p>Our weekly cloud news roundups will be published here every week, covering the latest developments in cloud computing, new service announcements, industry trends, and insights from major cloud providers.</p>
      <div class="coming-soon-features">
        <h3>What to Expect:</h3>
        <ul>
          <li>🌩️ Major cloud service announcements from AWS, Azure, and Google Cloud</li>
          <li>📊 Industry trends and market analysis</li>
          <li>🔧 New tools and technologies</li>
          <li>💡 Best practices and insights</li>
          <li>📈 Performance improvements and cost optimizations</li>
        </ul>
      </div>
    </div>
  {%- endif -%}
</div>