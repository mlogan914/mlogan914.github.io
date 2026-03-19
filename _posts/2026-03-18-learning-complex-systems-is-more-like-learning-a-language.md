---
title: "Learning Complex Systems Is More Like Learning a Language"
permalink: /learning-complex-systems-is-more-like-learning-a-language/
excerpt_separator: "<!--more-->"
categories:
  - Career Development
tags:
  - Platform Engineering

layout: single
# classes: wide

header:
  teaser: /assets/images/learning_complex_systems_language_.png
---

<div class="notice--info">
    This article is meant to highlight the complexity behind modern technical systems and to offer a reminder: for those learning, it takes time, and for those with experience, much of what feels obvious now was once unfamiliar.
</div>

---

<img src="/assets/images/learning_complex_systems_language_.png" alt="learning complex systems language" class="center-image" />

<p align="center">Image created by the author</p>

Many technical domains that involve complex systems share a common challenge.

The tools and specifications are only part of the picture. Much of the real expertise comes from the surrounding context and edge cases that are gradually absorbed through experience.

Over time, people begin to recognize how pieces fit together, which decisions matter most, and how systems behave in production. This understanding often develops slowly and is difficult to capture fully in documentation.

I was reminded of this idea while watching a talk at DevOps Days 2026 by **Josh Lee** titled *DevOps is a Foreign Language*. At one point, he showed the [CNCF Cloud Native Landscape](https://landscape.cncf.io/) to illustrate the scale and complexity of what engineers are expected to navigate.

In the talk, Lee frames DevOps as something closer to a language than a set of tools. He connects DevOps learning to research on second-language acquisition, suggesting that becoming effective in DevOps requires absorbing a large amount of implicit knowledge about systems, workflows, and operational culture.

> You can watch the full talk [HERE.](https://www.youtube.com/watch?v=058eX3byv6s)

One example from the talk illustrated this idea particularly well. Lee asked the audience a simple question:

**How do you check the Docker version installed on your system?**

People immediately suggested different commands. Some said `docker --version`, while others said `docker version`.

These seem interchangeable, but they actually behave differently.

`docker --version` reports the version of the Docker CLI.  
`docker version` queries the Docker daemon and returns both client and server information. Because of that, it only works when the Docker daemon is running.

When Lee asked the audience how they knew which command to use, most people simply knew from experience.

This is exactly the kind of knowledge that accumulates over time when working in complex systems. It is not always captured explicitly in documentation, but it becomes part of the mental model people develop through *repeated exposure*.

This is what makes learning feel difficult. Much of what is required is not immediately visible, and often only becomes clear through experience.

Although the talk focuses on DevOps, the idea applies to many technical fields that involve complex systems and similar learning curves. Learning technologies such as Kubernetes, CI/CD tooling, or infrastructure platforms is only one part of the process. The deeper challenge is building the mental models that allow these tools to make sense together.

Many engineers find that expertise develops as fluency. Over time, patterns become easier to recognize, trade-offs become clearer, and decisions that once felt confusing begin to feel intuitive.

This is one reason learning complex technical systems often takes time. Like learning a language, fluency tends to emerge gradually as exposure and experience accumulate.

Understanding this can also change how we think about learning and mentorship in technical fields. Documentation and courses are helpful, but they don't replace the value of practical experience, guidance from others who have navigated the same systems, and time spent working within the environment itself.

For those learning, this can help set expectations. Struggling early on is not necessarily a reflection of ability, but often a reflection of how much implicit knowledge is involved.

For those with experience, it can be a useful reminder that much of what now feels obvious was once unfamiliar. That perspective can make it easier to support others as they navigate the same learning curve.