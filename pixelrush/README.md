# PixelRush: Ultra-Fast, Training-Free High-Resolution Image Generation via One-step Diffusion

**Hong-Phuc Lai**, **Phong Nguyen**, **Anh Tran**

*IEEE/CVF Conference on Computer Vision and Pattern Recognition (**CVPR 2026**) — Highlight Presentation*

Qualcomm AI Research
*(Qualcomm AI Research is an initiative of Qualcomm Technologies, Inc.)*

---

## Abstract

Pre-trained diffusion models excel at generating high-quality images but remain inherently limited by their native training resolution. Recent training-free approaches have attempted to overcome this constraint; however, these methods incur substantial computational overhead, often requiring **more than five minutes** to produce a single 4K image.

We present **PixelRush**, the first tuning-free framework for practical high-resolution text-to-image generation. Our method builds upon patch-based inference but eliminates multiple inversion-regeneration cycles. Instead, PixelRush enables efficient patch-based denoising in a **low-step regime**. To address artifacts from few-step patch blending we propose Gaussian feathering; to combat oversmoothing we introduce a noise injection mechanism.

PixelRush generates 4K images in approximately **20 seconds** — a **10–35× speedup** over state-of-the-art — while maintaining superior visual fidelity across all quantitative metrics.

---

## Project Page

The interactive project page is available at [`./index.html`](./index.html).

## License

This project page was built using the [Academic Project Page Template](https://github.com/eliahuhorwitz/Academic-project-page-template), adopted from the [Nerfies](https://nerfies.github.io/) project page. The website is licensed under a [Creative Commons Attribution-NonCommercial-ShareAlike 4.0 International License](https://creativecommons.org/licenses/by-nc-sa/4.0/).
