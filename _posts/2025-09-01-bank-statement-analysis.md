---
layout: default
title: "AI-Powered Bank Statement Analysis: From PDF Chaos to Scalable Automation"
date: 2025-09-01
---

<div class="container page-content">
    <h1>{{ page.title }}</h1>
    <p class="post-meta">{{ page.date | date_to_string }}</p>

    <p>In the lending industry, one of the most crucial steps in evaluating a loan application is reviewing a customer’s bank statement. Lenders rely on these documents to understand spending patterns, income sources, and repayment ability. At first glance, this sounds simple—but when you process hundreds of statements a day in different formats, manual review becomes slow, inconsistent, and error-prone. We knew we had to automate.</p>

    <h2>Our First Attempt</h2>
    <p>We began with a straightforward approach using PDF extraction libraries like <code>pdfplumber</code> and <code>pypdf</code>. This worked for a few formats, but as we received more diverse statements, the system started breaking down. Tables had different structures, headers weren’t consistent, and rows weren’t aligned properly. What seemed like a simple extraction task quickly became a bottleneck.</p>
    <p>It was clear—we needed something smarter.</p>

    <h2>The Breakthrough: Dynamic Table Extraction</h2>
    <p>Instead of hard-coding every format, we turned to deep learning. Our hybrid pipeline used:</p>
    <ul>
        <li>A Table Transformer model to detect rows and columns</li>
        <li>An image classifier to determine table structure (row-based or column-based)</li>
        <li>Text classification models to identify headers and map columns correctly</li>
    </ul>
    <p>This dynamic approach gave us a robust extraction system that could handle almost any bank statement format. For the first time, we felt confident in building something scalable.</p>

    <h2>Making Sense of Transactions</h2>
    <p>Extracting tables was only half the battle. Next, we had to classify each transaction—salary, rent, shopping, loan repayment, etc.—so lenders could analyze patterns. We fine-tuned <strong>DistilBERT</strong>, a lightweight NLP model, on our custom dataset. With optimizations like FP16 precision and ONNX export, we achieved a 4× speedup without sacrificing accuracy. This made real-time analysis possible.</p>

    <h2>Scaling Challenges</h2>
    <p>Our first deployment was a monolithic setup (18 GB RAM, 24 GB storage). It worked initially, but as load increased, requests began to drop. To fix this, we moved to a microservices design, splitting into separate Docker containers for:</p>
    <ol>
        <li>Static extraction</li>
        <li>Dynamic extraction</li>
        <li>Transaction analysis</li>
        <li>Controller</li>
    </ol>
    <p>We introduced RabbitMQ for communication between services, ensuring smooth task flow. Finally, deploying on AWS EKS (Kubernetes) with Grafana + Loki monitoring allowed us to scale effortlessly under heavy load.</p>

    <h2>The Outcome</h2>
    <p>By combining AI-driven extraction, optimized NLP models, and a scalable architecture, we built a system that:</p>
    <ul>
        <li>Processes diverse bank statements automatically</li>
        <li>Classifies transactions with high accuracy</li>
        <li>Scales reliably under heavy workloads</li>
        <li>Delivers insights in near real-time</li>
    </ul>
    <p>What once took hours of manual effort now happens in minutes.</p>

    <h2>Key Lessons</h2>
    <ul>
        <li>Don’t rely on static logic—real-world documents are messy.</li>
        <li>Model optimization (FP16, ONNX) makes AI production-ready.</li>
        <li>Microservices + queues = scalable pipelines.</li>
        <li>Monitoring (Grafana + Loki) is essential for visibility.</li>
    </ul>

    <h2>Conclusion</h2>
    <p>Our journey wasn’t linear—we stumbled, iterated, and re-architected multiple times. But each challenge pushed us to build something stronger. Today, our AI-powered system helps lenders make faster, more accurate decisions while reducing manual workload.</p>
    <p><strong>Biggest takeaway?</strong> In real-world AI projects, success isn’t just about the model—it’s about engineering, optimization, and scalability working together.</p>
</div>
