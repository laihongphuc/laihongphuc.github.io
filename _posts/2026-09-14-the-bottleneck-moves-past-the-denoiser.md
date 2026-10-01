---
layout: post
title: "The Bottleneck Moves Past the Denoiser"
date: 2026-09-14
tags: [research, diffusion models]
description: A note on where high-resolution generation actually spends its time, from PixelRush to UltraFlash.
---

Most of the work on fast image generation still treats the denoiser as the whole problem. If sampling takes fifty steps, make it four. If the model was trained at 1024, find a way to run it at 4K. That framing is right until it stops being the expensive part.

[PixelRush](https://qualcomm-ai-research.github.io/PixelRush/) sits in the first half of that story. Pretrained diffusion models are stuck at their training resolution, and training-free upscaling methods often spend minutes on a single 4K image because they invert and regenerate over and over. PixelRush keeps the patch-based idea, drops the repeated inversion cycles, and refines in a low-step regime. With a distilled backbone, 4K generation lands around twenty seconds, and the visual result stays coherent instead of falling into seams and repeated structure. The denoiser, in that setting, is no longer the thing you wait on.

Once sampling is that cheap, the next cost shows up somewhere less obvious: decoding. Cascaded high-resolution pipelines still run a VAE decoder over a huge latent, and that decode can dominate the wall clock even after the sampler has been squeezed. UltraFlash starts from that observation. A latent upscaler moves megapixel synthesis past the denoiser, and a caching scheme cuts decoder latency relative to a standard implementation. The practical result is about 2× faster 4K generation, with better image quality than a strong cascaded baseline.

The pattern I keep coming back to is simple. Speedup is not a property of one module. It is whatever is left after the previous bottleneck has been removed. PixelRush makes few-step, training-free high resolution practical. UltraFlash treats the decoder as the new critical path. The next project in this line should start by measuring that path again, not by assuming the denoiser is still the answer.
