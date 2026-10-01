---
layout: post
title: "Post-Training After the Model Is Already Fast"
date: 2026-09-28
tags: [research, flow matching, post-training]
description: Why alignment still matters once a flow model has already been distilled to a few steps.
---

Distillation and post-training solve different problems, and it is easy to treat the second as a rerun of the first. Distillation makes a sampler short. Post-training makes the samples agree with a preference the original training run never quite captured. Doing the second by repeating the first is expensive, and it throws away a model you may already be serving.

That is the setting behind SwiftAlign. Few-step flow models are already distilled. At inference they follow a deterministic ODE, and that path is part of what makes them fast. Changing the reward — a new preference model, a new product constraint — should not require reward gradients through the sampler or a fresh distillation from the teacher. SwiftAlign treats the deployed sampler as a black box and adapts it to the new reward while leaving that inference path intact.

The same idea shows up in a different modality. Next3DGen is a post-training framework for text- and image-conditioned 3D generation, covering both single-stage and multi-stage models. The pretrained generator already exists. The remaining gap is quality, condition alignment, and 3D consistency, and the goal is to close that gap without a training budget that looks like pretraining.

I find the shared constraint more interesting than the specific reward. Once a model is fast enough to deploy, further progress has to respect the thing you already shipped: the number of steps, the decoder, the interface another system calls. Post-training is attractive exactly when it is a small edit on that interface, not a new model with a new serving stack.

These notes are sketches of work that is still moving. I will keep the longer arguments in papers, and use this blog for the shorter version: where the pipeline actually breaks, and what the lightest fix looks like.
