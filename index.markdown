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
      <p>"Turning data into decisions"</p>
      <div class="cta-buttons">
        <a href="#projects" class="btn">View Projects</a>
        <a href="/assets/cv/jignesh_shiyal_cv.pdf" class="btn secondary" target="_blank">Download CV</a>
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
          I’m a Data Scientist with expertise in NLP, Computer Vision, and Document Intelligence. 
          My work spans across the lending industry, conversational AI, and predictive analytics. 
        </p>
        <p>
          Previously, I built credit scoring models for loan lending, automated KYC onboarding with 
          face recognition, and deployed multilingual chatbots to serve thousands of users daily.
        </p>
      </div>
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

  <!-- Contact Section -->
  <section id="contact">
    <h2>Contact Me</h2>
    <form class="contact-form" action="https://formspree.io/f/yourformid" method="POST">
      <input type="text" name="name" placeholder="Your Name" required>
      <input type="email" name="_replyto" placeholder="Your Email" required>
      <textarea name="message" placeholder="Your Message" required></textarea>
      <button type="submit" class="btn">Send</button>
    </form>
    <div class="social-links">
      <a href="https://www.linkedin.com/in/jigneshshiyal" target="_blank"><i class="fab fa-linkedin"></i></a>
      <a href="https://github.com/jigneshshiyal" target="_blank"><i class="fab fa-github"></i></a>
      <a href="https://www.kaggle.com/jigneshshiyal" target="_blank"><i class="fab fa-kaggle"></i></a>
    </div>
  </section>

</div>
