---
layout: page
title: Blog
permalink: /blog/
---

<div class="blog-header" style="text-align: center; margin-bottom: 3rem; padding: 2rem 0;">
  <h1 style="font-size: 2.5rem; margin-bottom: 1rem; color: #8B1538; font-weight: 700;">
    Thoughts & Research
  </h1>
  <div style="width: 60px; height: 2px; background: linear-gradient(90deg, #8B1538, #B91C4D); margin: 1rem auto;"></div>
  <p class="lead" style="font-size: 1.2rem; color: #5A4A4E; max-width: 600px; margin: 0 auto;">
    Random thoughts, research notes, and the occasional 2 AM breakthrough 💡
  </p>
</div>

<div class="blog-intro" style="margin-bottom: 3rem; text-align: center;">
  <p style="font-size: 1.1rem; line-height: 1.6; color: #5A4A4E; max-width: 700px; margin: 0 auto;">
    Welcome to my digital notebook. Here you'll find my thoughts on anything.
  </p>
</div>

{% if site.posts.size > 0 %}
<div class="posts-grid" style="display: grid; gap: 1rem;">
  {% for post in site.posts %}
  <article class="post-card" style="padding: 2rem; border-left: 3px solid #8B1538; background: #FDF5F7; transition: all 0.2s ease;">
    
    <div>
      <!-- Post metadata -->
      <div style="display: flex; align-items: center; gap: 1rem; margin-bottom: 1.5rem; flex-wrap: wrap;">
        <span style="background: #8B1538; color: white; padding: 0.3rem 0.85rem; border-radius: 2px; font-size: 0.8rem; font-weight: 500;">
          {{ post.date | date: "%B %d, %Y" }}
        </span>
        
        {% if post.categories %}
          {% for category in post.categories %}
          <span class="tag">{{ category | replace: '-', ' ' | capitalize }}</span>
          {% endfor %}
        {% endif %}
        
        {% if post.tags %}
          {% for tag in post.tags limit:2 %}
          <span class="tag">#{{ tag }}</span>
          {% endfor %}
        {% endif %}
      </div>

      <!-- Post title -->
      <h2 style="margin: 0 0 1rem 0; font-size: 1.5rem; font-weight: 600; line-height: 1.3;">
        <a href="{{ post.url }}" style="text-decoration: none; color: #8B1538;">
          {{ post.title }}
        </a>
      </h2>

      <!-- Post excerpt -->
      {% if post.excerpt %}
      <div style="margin-bottom: 1.5rem;">
        <p style="color: #5A4A4E; line-height: 1.5; font-size: 1rem; margin: 0;">
          {{ post.excerpt | strip_html | truncatewords: 35 }}...
        </p>
      </div>
      {% endif %}

      <!-- Reading time and read more -->
      <div style="display: flex; justify-content: space-between; align-items: center; margin-top: 1.5rem;">
        <div style="color: #8B7B7E; font-size: 0.85rem; display: flex; align-items: center; gap: 1rem;">
          <span>{{ post.content | number_of_words | divided_by: 200 }} min read</span>
          {% if post.comments != false %}
          <span>💬 Comments welcome</span>
          {% endif %}
        </div>
        
        <a href="{{ post.url }}" class="elegant-button" style="font-size: 0.9rem; padding: 0.5rem 1.25rem;">
          Read more →
        </a>
      </div>
    </div>
  </article>
  {% endfor %}
</div>

{% else %}
<div class="no-posts" style="text-align: center; padding: 3rem 2rem; border-top: 1px solid #E8D4D8; border-bottom: 1px solid #E8D4D8;">
  <h2 style="color: #5A4A4E; margin-bottom: 1rem; font-size: 1.5rem;">No posts yet 📝</h2>
  <p style="color: #8B7B7E; font-size: 1rem;">
    Content is coming soon! In the meantime, feel free to explore my projects or reach out for a chat.
  </p>
  <div style="margin-top: 2rem;">
    <a href="/" class="elegant-button">
      Back to Home
    </a>
  </div>
</div>
{% endif %}

<style>
.post-card:hover {
  border-left-color: #B91C4D;
  transform: translateX(5px);
  transition: all 0.2s ease;
}

.post-card:hover h2 a {
  color: #B91C4D;
}

@media (max-width: 768px) {
  .blog-header h1 {
    font-size: 2rem;
  }
  
  .blog-header .lead {
    font-size: 1rem;
  }
  
  .post-card {
    padding: 1.5rem;
  }
  
  .post-card div[style*="justify-content: space-between"] {
    flex-direction: column;
    align-items: flex-start;
    gap: 1rem;
  }
}
</style> 