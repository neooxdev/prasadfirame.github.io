---
title: "Experience"
draft: false
---

<!-- Entire page in HTML -->
<!-- Experience Timeline Page with logos inline -->

<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <title>Experience</title>
  <link rel="stylesheet" href="/css/custom.css">
  <style>
    body {
      font-family: 'Segoe UI', sans-serif;
      background-color: #121212;
      color: #eee;
      margin: 0;
      padding: 0;
    }

    .timeline-container {
      max-width: 900px;
      margin: 3rem auto;
      padding: 0 1rem;
      position: relative;
    }

    h1 {
      text-align: center;
      margin-bottom: 2rem;
      font-size: 2rem;
    }

    /* Timeline items */
    .timeline-item {
      position: relative;
      width: 50%;
      padding: 1rem 2rem;
      box-sizing: border-box;
      opacity: 0;
      transform: translateY(50px);
      transition: all 0.6s ease-out;
    }

    .timeline-item.left { left: 0; text-align: right; }
    .timeline-item.right { left: 50%; text-align: left; }

    /* Content styling */
    .timeline-content {
      background-color: #1a1a1a;
      padding: 0.8rem 1rem;
      border-radius: 8px;
      font-size: 0.9rem;
      line-height: 1.4rem;
      box-shadow: 0 4px 10px rgba(0,0,0,0.3);
      display: inline-block;
      max-width: 350px;
      position: relative;
      z-index: 2;
    }

    /* Logo inline with title */
    .timeline-content h3 {
      display: flex;
      align-items: center;
      gap: 0.6rem;
      font-size: 1.1rem;
      margin-bottom: 0.5rem;
    }

    .timeline-content h3 img {
      width: 40px;
      height: 40px;
      object-fit: contain;
      border-radius: 4px;
      background-color: #111;
      padding: 2px;
    }

    /* Segmented vertical line */
    .timeline-segment {
      position: absolute;
      left: 50%;
      transform: translateX(-50%);
      width: 3px;
      background-color: #00ffcc;
      top: 0;
      z-index: 1;
      transition: height 0.5s ease-out;
    }

    /* Scroll hint */
    .scroll-hint {
      text-align: center;
      margin-top: 2rem;
      font-size: 1rem;
      color: #00ffcc55;
      animation: bounce 1.5s infinite;
    }

    @keyframes bounce {
      0%, 100% { transform: translateY(0); }
      50% { transform: translateY(10px); }
    }
  </style>
</head>
<body>

<div class="timeline-container">
  
  <!-- Timeline items -->
  <div class="timeline-item left" data-segment-start>
    <div class="timeline-content">
      <h3>
        <img src="/images/coreco-logo.png" alt="CoreCo Logo">
        Associate Software Engineer (2024–Present)
      </h3>
      <p>Worked on <a href="https://bettrlabs.com/" target="_blank">BettrLabs</a>, an AI-powered B2B SaaS platform. Built the MVP from scratch, delivered POCs, and improved system performance</p>
      <p>Built APIs, ETL pipelines, and multi-tenant AI systems including <a href="https://instinctiq.com/" target="_blank">Nexus</a>. Delivered multiple POCs improving scalability and automation.</p>
      <p>Created RAG chatbots, voice agents, and AWS Lambda reporting engines, generating measurable impact.</p>
    </div>
  </div>

  <div class="timeline-item right">
    <div class="timeline-content">
      <h3>
        <img src="/images/coreco-logo.png" alt="CoreCo Logo">
        Software Engineer Intern (2024 - Nov 2024)
      </h3>
      <p>Worked on a scalable parking automation system using React, Node.js, and MySQL.</p>
      <p>Developed REST APIs, dashboards, and RAG chatbots for POCs, improving performance and user experience.</p>
      <p>Learned full-stack best practices, multi-tenancy, security performed well got selected for full time role.</p>
    </div>
  </div>

  <div class="timeline-item left">
    <div class="timeline-content">
      <h3>
        <img src="/images/buildspace-logo.png" alt="Buildspace Logo">
        Exploration & Learning (2023)
      </h3>
      <p>
      Explored various technologies via <strong>Buildspace</strong>, joined communities, and absorbed knowledge. Learned communication, scaling ideas, and building concepts while dreaming big.
      </p>
    </div>
  </div>

  <div class="scroll-hint">⬇ Scroll to see more</div>
</div>

<script>
  const items = document.querySelectorAll('.timeline-item');

  // Segmented vertical line between items
  items.forEach((item, i) => {
    if(i < items.length - 1){
      const nextItem = items[i+1];
      const segment = document.createElement('div');
      segment.classList.add('timeline-segment');
      document.querySelector('.timeline-container').appendChild(segment);

      function updateSegment() {
        const top = item.getBoundingClientRect().top + item.offsetHeight/2;
        const bottom = nextItem.getBoundingClientRect().top + nextItem.offsetHeight/2;
        const containerTop = document.querySelector('.timeline-container').getBoundingClientRect().top;
        segment.style.top = (top - containerTop) + 'px';
        segment.style.height = (bottom - top) + 'px';
      }
      window.addEventListener('scroll', updateSegment);
      window.addEventListener('resize', updateSegment);
      window.addEventListener('load', updateSegment);
      updateSegment();
    }
  });

  // Reveal items on scroll
  function revealTimeline() {
    const triggerBottom = window.innerHeight * 0.85;
    items.forEach(item => {
      const top = item.getBoundingClientRect().top;
      if(top < triggerBottom) {
        item.style.opacity = 1;
        item.style.transform = 'translateY(0)';
      }
    });
  }

  window.addEventListener('scroll', revealTimeline);
  window.addEventListener('load', revealTimeline);
</script>

</body>
</html>
