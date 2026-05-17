---
layout: post
title: "Why I Study Efficient Generative Models"
date: 2026-05-18
tags: [research, diffusion models]
description: A short note on the motivation behind my research direction.
---

Large generative models have reached a level of quality that would have seemed unreasonable just a few years ago. Yet most of them are still impractical to deploy: too slow for interactive use, too memory-hungry for edge devices, or misaligned after the initial training run.

My research starts from a simple observation: **the bottleneck is rarely the model architecture itself**. More often, it lives in the surrounding pipeline — the sampler, the decoder, the alignment procedure — and these are places where targeted algorithmic work can have outsized impact without requiring a full retraining cycle.

This is the thread that connects my work on Diffusion Models, Flow Matching, and Reinforcement Learning. Each project asks the same question in a different context: *where exactly does the pipeline break down, and what is the lightest intervention that fixes it?*

I plan to use this blog to share ideas, paper notes, and lessons from ongoing research. If something here is useful to you, feel free to reach out.
