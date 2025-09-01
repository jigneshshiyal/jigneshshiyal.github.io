---
layout: default
title: "Building a Face Matching System for Identity Verification"
date: 2025-09-01
---

<div class="container page-content">
    <h1>{{ page.title }}</h1>
    <p class="post-meta">{{ page.date | date_to_string }}</p>

    <p>In digital lending, verifying customer identity is a critical step. A common requirement is ensuring that the selfie a customer takes during onboarding matches their government-issued ID (like Aadhaar). But before we could even compare faces, we faced a different challenge: making sure the selfie captured at the frontend was of good enough quality for verification.</p>

    <p>Customers often clicked pictures that were blurry, poorly lit, tilted, or with their face partially covered. These issues led to false mismatches and frustrated both the customer and the system.</p>

    <h2>First Challenge: Capturing a Good Selfie</h2>
    <p>The face matching algorithm is only as good as the input photo. So instead of running expensive corrections later, we decided to guide customers while they were taking their selfies.</p>
    <p>To achieve this, we:</p>
    <ul>
        <li>Used <strong>Mediapipe</strong> to detect face position and landmarks</li>
        <li>Trained a custom edge-device model to classify issues like:</li>
        <ul>
            <li>Face too far from the camera</li>
            <li>Eyes closed</li>
            <li>Head tilted left/right</li>
            <li>Face covered or wearing glasses (when not allowed)</li>
        </ul>
    </ul>
    <p>These checks ran directly in the frontend, so customers received real-time guidance like <em>“Move closer to the camera”</em>, <em>“Open your eyes”</em>, or <em>“Adjust your face straight”</em>. Only when all checks were passed did we allow the user to capture the picture.</p>

    <h2>Face Matching</h2>
    <p>Once a proper selfie was captured, it was sent to the backend for face matching against the Aadhaar photo. The matching itself used a <strong>CNN-based face embedding approach</strong>, which handled variations in lighting and minor angles while still being strict enough to prevent impersonation.</p>

    <h2>Tech Stack</h2>
    <ul>
        <li><strong>Frontend</strong>: JavaScript + Mediapipe (real-time selfie guidance)</li>
        <li><strong>Edge Models</strong>: Custom Mediapipe classifiers for face covering & glasses detection</li>
        <li><strong>Backend</strong>: Python + FastAPI for face matching inference</li>
    </ul>

    <h2>Key Learnings</h2>
    <ul>
        <li><strong>Quality input matters</strong>: Guiding users at capture time reduced false mismatches significantly.</li>
        <li><strong>Edge-device models improve UX</strong>: Running checks in the frontend avoided unnecessary server calls and gave instant feedback.</li>
        <li><strong>Balancing strictness vs usability</strong>: Too many warnings frustrated users, so we carefully tuned thresholds for “acceptable” selfies.</li>
    </ul>

    <h2>Conclusion</h2>
    <p>By combining real-time selfie guidance with face matching, we built a system that not only verifies customer identity but also ensures a smooth onboarding experience.</p>
</div>
