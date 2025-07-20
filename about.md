---
layout: page
title: About
permalink: /about/
current_lang: en
languages:
  - code: en
    name: EN
    url: /about/
  - code: zh
    name: 中文
    url: /about/zh/
---

<div class="about-header animate-on-scroll" style="text-align: center; margin-bottom: 3rem; padding: 2rem 0;">
  <h1 style="font-size: 2.5rem; margin-bottom: 1rem; color: #8B1538; font-weight: 700;">
    About Me
  </h1>
  <div style="width: 60px; height: 2px; background: linear-gradient(90deg, #8B1538, #B91C4D); margin: 1rem auto;"></div>
  <p class="lead" style="font-size: 1.2rem; color: #5A4A4E; max-width: 600px; margin: 0 auto;">
    Thank you for dropping by ✨
  </p>
</div>

<div class="static-card animate-on-scroll" style="text-align: center; padding: 3rem; border-top: 1px solid #E8D4D8; border-bottom: 1px solid #E8D4D8; margin: 3rem 0; border-radius: 8px;">
  <h2 style="color: #5A4A4E; margin-bottom: 1rem; font-size: 1.8rem;">About Content Coming Soon ✨</h2>
  <p style="color: #8B7B7E; font-size: 1.1rem; max-width: 500px; margin: 0 auto;">
    I'm working on updating this page with more details about my background and interests. 
    Stay tuned!
  </p>

</div>

<style>
/* Static card without hover transforms */
.static-card {
  transition: all 0.25s cubic-bezier(0.4, 0, 0.2, 1);
  border-radius: 8px;
}

.static-card:hover {
  box-shadow: 0 2px 8px rgba(139, 21, 56, 0.08);
  background: rgba(253, 245, 247, 0.7);
}

@media (max-width: 768px) {
  .about-header h1 {
    font-size: 2rem;
  }
  
  .about-header .lead {
    font-size: 1rem;
  }
  
  .static-card {
    padding: 2rem 1rem !important;
  }
}
</style> 