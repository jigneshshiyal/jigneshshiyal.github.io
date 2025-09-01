---
layout: default
title: "Building a Video-Audio Verification System with AI: Our Journey"
date: 2025-09-01
---

<div class="container page-content">
    <h1>{{ page.title }}</h1>
    <p class="post-meta">{{ page.date | date_to_string }}</p>

    <p>In digital lending, fraud prevention is just as important as credit risk analysis. One critical challenge is verifying that the person applying for a loan is who they claim to be—and that they are genuinely present during verification.</p>
    <p>Our goal was twofold:</p>
    <ul>
        <li>Match a customer’s profile photo with their live video</li>
        <li>Verify that the customer reads a given sentence aloud (as per regulatory guidelines)</li>
        <li>Ensure the spoken text matches the expected script</li>
    </ul>
    <p>What sounds straightforward turned out to be a multi-step AI challenge.</p>

    <h2>Breaking Down the Problem</h2>
    <p>We realized the system had two main parts:</p>
    <ol>
        <li><strong>Face Matching</strong> – confirm the person in the video is the same as the profile photo.</li>
        <li><strong>Audio-to-Text Verification</strong> – ensure the customer actually speaks the required text.</li>
    </ol>

    <h2>Face Matching: Getting Identity Right</h2>
    <p>Face matching isn’t just comparing two pictures. Lighting, angles, and video quality can make the same person look very different. To solve this, we used a CNN-based face recognition model. Instead of comparing raw pixels, the model generated <strong>facial embeddings</strong>, which made matches more reliable even under real-world noise and variations.</p>
    <p>This gave us a strong foundation for the “is this the right person?” step.</p>

    <h2>Audio-to-Text: The Bigger Challenge</h2>
    <p>The second step was trickier: checking if the customer actually spoke the expected line.</p>

    <h3>Attempt 1: Google Speech-to-Text</h3>
    <p>We first tried Google’s API. Accuracy was decent, but latency was too high. In real-time verification, every extra second hurts the user experience.</p>

    <h3>The Breakthrough: Whisper</h3>
    <p>We switched to <strong>OpenAI Whisper</strong> (small model) deployed on our local server. Suddenly, transcription became faster and more reliable. We then fine-tuned Whisper on our own dataset—banking-related sentences, regional accents, and noisy conditions. Finally, we optimized it with <strong>CTranslate2</strong>, which cut inference time dramatically. This made the system not just accurate, but fast enough for production.</p>

    <h2>Text Matching: Final Verification</h2>
    <p>Once we had the transcribed audio, the last step was simple: compare it against the predefined script. This ensured that:</p>
    <ul>
        <li>The person matched the profile photo</li>
        <li>They were physically present in the video</li>
        <li>They actually spoke the correct verification sentence</li>
    </ul>
    <p>With all three checks combined, fraudsters had a much harder time bypassing the system.</p>

    <h2>Deployment & Learnings</h2>
    <p>By the end, we had built a pipeline that was:</p>
    <ul>
        <li><strong>Accurate</strong>: CNN-based face recognition + Whisper fine-tuning</li>
        <li><strong>Fast</strong>: Optimized with CTranslate2 for low latency</li>
        <li><strong>Practical</strong>: Integrated seamlessly into customer verification workflows</li>
    </ul>

    <h3>Key Lessons</h3>
    <ul>
        <li>Don’t rely on APIs blindly—latency can make or break user experience.</li>
        <li>Local deployment ensures both speed and data security.</li>
        <li>Fine-tuning on domain-specific data gives big accuracy gains.</li>
        <li>Optimization tools like CTranslate2 turn research models into production-ready systems.</li>
    </ul>

    <h2>Conclusion</h2>
    <p>What started as a simple idea—“match a face and check if they said the right thing”—turned into a journey through face recognition, speech-to-text, fine-tuning, and deployment optimizations.</p>
    <p>Today, our AI-powered verification system ensures a safer, smoother loan application process for customers while helping businesses fight fraud more effectively.</p>
</div>
