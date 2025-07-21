---
layout: page
title: Blog
permalink: /blog/
---

<div class="blog-header animate-on-scroll" style="text-align: center; margin-bottom: 3rem; padding: 2rem 0;">
  <h1 style="font-size: 2.5rem; margin-bottom: 1rem; color: #8B1538; font-weight: 700;">
    Thoughts & Research
  </h1>
  <div style="width: 60px; height: 2px; background: linear-gradient(90deg, #8B1538, #B91C4D); margin: 1rem auto;"></div>
  <p class="lead" style="font-size: 1.2rem; color: #5A4A4E; max-width: 600px; margin: 0 auto;">
    Random thoughts, research notes, and the occasional 2 AM breakthrough 💡
  </p>
</div>

<div class="blog-intro animate-on-scroll" style="margin-bottom: 3rem; text-align: center;">
  <p style="font-size: 1.1rem; line-height: 1.6; color: #5A4A4E; max-width: 700px; margin: 0 auto;">
    Welcome to my digital notebook. Here you'll find my thoughts on anything.
  </p>
</div>

{% if site.posts.size > 0 %}
<div class="posts-grid" style="display: grid; gap: 1rem;">
  {% for post in site.posts %}
  {% unless post.path contains '.ipynb' and post.url contains '.ipynb.html' %}
  <article class="post-card hover-card no-animation" style="padding: 2rem; border-left: 3px solid #8B1538; background: #FDF5F7;">
    
    <div>
      <!-- Post metadata -->
      <div style="display: flex; align-items: center; gap: 1rem; margin-bottom: 1.5rem; flex-wrap: wrap;">
        <span class="tag" style="background: #8B1538; color: white;">
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
        
        <!-- Multilingual indicator -->
        {% if post.multilingual and post.languages.size > 1 %}
        <span class="tag" style="background: #F8E8EC; color: #8B1538;">
          🌐 {{ post.languages.size }} languages
        </span>
        {% endif %}
      </div>

      <!-- Post title (will be dynamically updated for multilingual posts) -->
      <h2 style="margin: 0 0 1rem 0; font-size: 1.5rem; font-weight: 600; line-height: 1.3;"
          {% if post.multilingual %}class="dynamic-post-title" data-post-languages="{{ post.languages | jsonify | escape }}" data-default-title="{{ post.title | escape }}"{% endif %}>
        <a href="{{ post.url }}" style="text-decoration: none; color: #8B1538; transition: all 0.3s cubic-bezier(0.4, 0, 0.2, 1);">
          {{ post.title }}
        </a>
      </h2>

      <!-- Reading time and read more -->
      <div style="display: flex; justify-content: space-between; align-items: center; margin-top: 1.5rem;">
        <div style="color: #8B7B7E; font-size: 0.85rem; display: flex; align-items: center; gap: 1rem;">
          {% unless post.path contains '.ipynb' %}<span>{{ post.content | number_of_words | divided_by: 200 }} min read</span>{% endunless %}
          {% if post.comments != false %}
          <span>💬 Comments welcome</span>
          {% endif %}
        </div>
        
        <a href="{{ post.url }}" class="elegant-button elegant-button-small">
          Read more →
        </a>
      </div>
    </div>
  </article>
  {% endunless %}
  {% endfor %}
</div>

{% else %}
<div class="no-posts animate-on-scroll" style="text-align: center; padding: 3rem 2rem; border-top: 1px solid #E8D4D8; border-bottom: 1px solid #E8D4D8;">
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

<!-- Multilingual Blog Support Script -->
<script>
document.addEventListener('DOMContentLoaded', function() {
  // Always default to English first, then check saved preference
  let preferredLang = 'en';
  const savedLang = localStorage.getItem('preferred-lang');
  if (savedLang) {
    preferredLang = savedLang;
  }
  
  // Update multilingual post previews
  const dynamicTitles = document.querySelectorAll('.dynamic-post-title');
  const dynamicExcerpts = document.querySelectorAll('.dynamic-post-excerpt');
  
  dynamicTitles.forEach(titleElement => {
    try {
      const languagesAttr = titleElement.getAttribute('data-post-languages');
      if (!languagesAttr) return;
      
      const languages = JSON.parse(languagesAttr);
      const defaultTitle = titleElement.getAttribute('data-default-title');
      
      // Find the preferred language version, defaulting to English
      let langVersion = languages.find(lang => lang.code === preferredLang);
      if (!langVersion && preferredLang !== 'en') {
        langVersion = languages.find(lang => lang.code === 'en');
      }
      
      if (langVersion && langVersion.title) {
        const linkElement = titleElement.querySelector('a');
        if (linkElement) {
          linkElement.textContent = langVersion.title;
        }
      }
    } catch (e) {
      console.log('Error parsing language data for title:', e);
    }
  });
  
  dynamicExcerpts.forEach(excerptElement => {
    try {
      const languagesAttr = excerptElement.getAttribute('data-post-languages');
      if (!languagesAttr) return;
      
      const languages = JSON.parse(languagesAttr);
      const defaultExcerpt = excerptElement.getAttribute('data-default-excerpt');
      
      // Find the preferred language version, defaulting to English
      let langVersion = languages.find(lang => lang.code === preferredLang);
      if (!langVersion && preferredLang !== 'en') {
        langVersion = languages.find(lang => lang.code === 'en');
      }
      
      if (langVersion && langVersion.excerpt) {
        excerptElement.textContent = langVersion.excerpt + '...';
      }
    } catch (e) {
      console.log('Error parsing language data for excerpt:', e);
    }
  });
});
</script>

<style>
.post-card {
  transition: all 0.3s cubic-bezier(0.4, 0, 0.2, 1);
}

.post-card:hover {
  border-left-color: #B91C4D;
  transform: translateY(-2px);
}

.post-card:hover h2 a {
  color: #B91C4D;
}

.post-card h2 a:hover {
  transform: translateY(-0.5px);
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
  
  .elegant-button {
    width: 100%;
    justify-content: center;
  }
}
</style> 