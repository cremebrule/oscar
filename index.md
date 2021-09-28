---
layout: main
title: OSCAR
subtitle: 
project_tagline: "Data-Driven <u>O</u>perational <u>S</u>pace <u>C</u>ontrol for <u>A</u>daptative and <u>R</u>obust Robot Manipulation"
videoId: "oscar_video.mp4"
---

<figure class="figure"><div class="figure__main">
<video autoplay loop muted playsinline controls class="postimagefullwidth">
  <source src="{{ site.baseurl }}/assets/oscar_video.mp4" type="video/mp4">
</video>
</div></figure>

# Overview

Learning performant robot manipulation policies can be challenging due to high-dimensional continuous actions and complex physics-based dynamics. This can be alleviated through intelligent choice of action space. Operational Space Control (OSC) has been used as an effective task-space controller for manipulation. Nonetheless, its strength depends on the underlying modeling fidelity, and is prone to failure when there are modeling errors. In this work, we propose <u>OSC</u> for <u>A</u>daptation and <u>R</u>obustness (**OSCAR**), a data-driven variant of OSC that compensates for modeling errors by inferring relevant dynamics parameters from online trajectories. **OSCAR** decomposes dynamics learning into task-agnostic and task-specific phases, decoupling the dynamics dependencies of the robot and the extrinsics due to its environment. This structure enables robust zero-shot performance under out-of-distribution and rapid adaptation to significant domain shifts through additional finetuning. We evaluate our method on a variety of simulated manipulation problems, and find substantial improvements over an array of controller baselines. 


# Algorithm

![pull figure]({{ 'assets/images/model_figure.png' | absolute_url }})

**OSCAR** learns a dynamics model in two-steps:

1. <b>Task-Agnostic Pretraining:</b> An initial reference model is learned, using free-space trajectories with no end-effector weight or dynamics randomization. This <i>decouples</i> the effect of task-specific dynamics from robot-specific dynamics.

2. <b>Task-Specific Finetuning:</b> Our dynamics model is finetuned via a residual network that perturbs the original base prediction. This residual receives recent state-action history and can <i>infer</i> task-relevant dynamics. We learn this dynamics model <i>simultaneously</i> with a task policy.

# Performance
<figure class="figure"><div class="figure__main">
<video autoplay loop muted playsinline class="postimagefullwidth">
  <source src="{{ site.baseurl }}/assets/videos/path_tracing.mp4" type="video/mp4">
</video>
</div></figure>


<figure class="figure"><div class="figure__main">
<video autoplay loop muted playsinline class="postimagefullwidth">
  <source src="{{ site.baseurl }}/assets/videos/cup_pouring.mp4" type="video/mp4">
</video>
</div></figure>


<figure class="figure"><div class="figure__main">
<video autoplay loop muted playsinline class="postimagefullwidth">
  <source src="{{ site.baseurl }}/assets/videos/puck_pushing.mp4" type="video/mp4">
</video>
</div></figure>


# Team

{% include members.html %}

# Citation

```bibtex
@inproceedings{wong2021oscar,
  title={OSCAR: Data-Driven Operational Space Control for Adaptive and Robust Robot Manipulation},
  author={Josiah Wong and Viktor Makoviychuk and Anima Anandkumar and Yuke Zhu},
  booktitle={arXiv preprint arXiv:TBD},
  year={2021}
}
```
