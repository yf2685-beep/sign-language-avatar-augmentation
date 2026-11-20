# Sign Language Avatar Augmentation

**面向手语合成数据研究的数字人动作处理与可视化工作流，基于 Taobao3D / HRM2Avatar。**

Research context: NYU Abu Dhabi AIR Lab, supervised by Yi Fang. The project explores how motion captured from real signing videos can be prepared for avatar replay, with the goal of creating more varied examples for sign-language recognition.

This repository is a portfolio fork of [Alibaba Taobao3D](https://github.com/alibaba/Taobao3D). The avatar and rendering foundations belong to their original authors. The original project introduction and publication links are preserved in [UPSTREAM.md](UPSTREAM.md).

## Research workflow

```mermaid
flowchart LR
    V[Signing video] --> F[Frames and segmentation masks]
    F --> T[EHM body and FLAME face tracking]
    T --> P[SMPL-X overlay inspection]
    P --> A[Avatar replay research]
    A --> D[Candidate synthetic training data]
```

The final two stages describe the research direction. This README does not claim a completed recognition benchmark or a measured downstream accuracy gain.

## My contribution

I worked on adapting custom signing videos to the EHM tracking workflow: preparing per-frame images and segmentation masks, extracting body and facial tracking parameters, and producing SMPL-X overlay previews to inspect body and hand alignment frame by frame.

| Work | Ability demonstrated |
| --- | --- |
| Preparing video, frame and mask inputs | Building consistent data interfaces between vision components |
| Working with EHM and FLAME parameter outputs | Understanding body/face representation formats and preprocessing requirements |
| Inspecting SMPL-X overlays | Visual diagnosis of tracking quality, especially hands and body alignment |
| Connecting tracking outputs to avatar research | Reading research code and identifying interfaces between separate systems |

## What is available here

- [HRM2Avatar implementation and setup](HRM2Avatar/README.md): the upstream avatar/rendering foundation relevant to this research.
- [Dens3R](Dens3R/README.md): a separate upstream reconstruction project distributed in Taobao3D.
- This project overview and the preserved [upstream introduction](UPSTREAM.md).

The default branch currently contains the upstream foundation. Project-specific EHM preprocessing scripts, signing-video datasets and generated tracking outputs are not included in this public snapshot. The contribution description documents the research work; it is not a claim that cloning this repository alone reproduces the full signing-video pipeline.

## Getting started

```bash
git clone https://github.com/yf2685-beep/sign-language-avatar-augmentation.git
cd sign-language-avatar-augmentation
```

Continue with the [HRM2Avatar instructions](HRM2Avatar/README.md) for supported platforms, dependencies, assets and rendering steps. Follow the upstream requirements for model/data access.

## Interview discussion points

- Why hand alignment deserves separate inspection in a signing workflow.
- How frame extraction, masks and coordinate conventions affect downstream tracking.
- How to distinguish a visually plausible overlay from evidence of useful training data.
- What additional evaluation would be needed before claiming better sign-language recognition.

## Attribution

Taobao3D and HRM2Avatar are upstream research projects by their respective authors. Preserve their licenses, citations and attribution when using the code or assets; see [UPSTREAM.md](UPSTREAM.md) and the component documentation.
