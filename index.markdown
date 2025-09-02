---
layout: default
title: "Jignesh Shiyal | Data Scientist"
---

<div class="container home">

  <!-- Hero Section -->
  <section id="hero" class="hero">
    <div class="hero-left">
        <img src="https://media.licdn.com/dms/image/v2/D4D03AQEZDawGhxxJEw/profile-displayphoto-scale_400_400/B4DZjx4dZ7H4Ag-/0/1756404767044?e=1759363200&v=beta&t=SCc4Wuq3_CcgnZ1RqqFT3Ep-WPiIKzVnPKVeQJ_4sG0" 
       alt="Profile Photo" 
       class="hero-photo">
    </div>
    <div class="hero-right">
      <h1>Hi, I'm <span class="highlight">Jignesh Shiyal</span></h1>
      <h2>Data Scientist | AI Builder</h2>
      <!-- <p>"Transforming Data into Scalable AI Products that Drive Real Business Impact"</p> -->
      <div class="cta-buttons">
        <a href="#projects" class="btn">View Projects</a>
        <a href="/assets/cv/JigneshShiyal_Resume.pdf" class="btn secondary" target="_blank">Download CV</a>
      </div>
    </div>
  </section>

  <!-- About Section -->
  <section id="about">
    <h2>About Me</h2>
    <div class="about-grid">
      <div class="about-image">
        <img src="https://media.licdn.com/dms/image/v2/D4D03AQEZDawGhxxJEw/profile-displayphoto-scale_400_400/B4DZjx4dZ7H4Ag-/0/1756404767044?e=1759363200&v=beta&t=SCc4Wuq3_CcgnZ1RqqFT3Ep-WPiIKzVnPKVeQJ_4sG0" alt="About Jignesh">
      </div>
      <div class="about-text">
        <p>
          I’m a Data Scientist & AI Engineer with 3+ years of experience in NLP, vision, speech, and document intelligence. I enjoy building AI systems that are not only accurate but also fast, scalable, and cost-effective.
        </p>
        <p>
          At Creditt+, I created solutions that cut KYC time by 40%, boosted compliance accuracy by 20%, and eliminated reliance on third-party APIs. Earlier, at Cybercom Creation, I worked on demand forecasting, product image classification, and catalog automation—improving efficiency by up to 50%.
        </p>
      </div>
    </div>
  </section>

  <section id="github">
  <h2>GitHub Contributions</h2>
  <p>Here’s my activity on GitHub:</p>

  <div class="github-stats">
    <!-- GitHub Stats -->
    <img src="https://github-readme-stats.vercel.app/api?username=jigneshshiyal&show_icons=true&theme=radical" alt="GitHub Stats" />

    <!-- Contribution Graph -->
    <img src="https://github-readme-activity-graph.vercel.app/graph?username=jigneshshiyal&theme=radical" alt="Contribution Graph" />
  </div>
</section>

  <!-- Skills Section -->
  <section id="skills">
    <h2>Skills & Tech Stack</h2>
    <div class="skills-grid">
      {% for skill in site.data.skills %}
      <div class="skill-card">
        <i class="{{ skill.icon }}"></i>
        <p>{{ skill.name }}</p>
      </div>
      {% endfor %}
    </div>
  </section>

  <!-- Projects Section -->
  <section id="projects">
    <h2>Projects</h2>
    <div class="projects-grid">
      {% for project in site.data.projects %}
      <div class="project-card">
        <h3>{{ project.title }}</h3>
        <p>{{ project.description }}</p>
        <p><strong>Tags:</strong> {{ project.tags | join: ", " }}</p>
        <div class="project-links">
          <a href="{{ project.github }}" target="_blank" class="btn small">GitHub</a>
          {% if project.demo %}
          <a href="{{ project.demo }}" target="_blank" class="btn small secondary">Demo</a>
          {% endif %}
        </div>
      </div>
      {% endfor %}
    </div>
  </section>

  <!-- Experience Section -->
  <section id="experience">
    <h2>Experience</h2>
    <div class="timeline">
      {% for exp in site.data.experience %}
      <div class="timeline-item">
        <span class="timeline-period">{{ exp.period }}</span>
        <h3>{{ exp.role }} @ {{ exp.company }}</h3>
        <ul>
          {% for point in exp.points %}
          <li>{{ point }}</li>
          {% endfor %}
        </ul>
      </div>
      {% endfor %}
    </div>
  </section>

  <!-- Blog Section -->
  <section id="blog">
    <h2>Latest Articles</h2>
    <div class="blog-grid">
      {% for post in site.posts limit:4 %}
      <div class="blog-card">
        <h3><a href="{{ post.url }}">{{ post.title }}</a></h3>
        <p class="post-meta">{{ post.date | date_to_string }}</p>
        <p>{{ post.excerpt }}</p>
        <a href="{{ post.url }}" class="read-more">Read More →</a>
      </div>
      {% endfor %}
    </div>
    <a href="/blog.html" class="btn secondary">See all posts</a>
  </section>

</div>
