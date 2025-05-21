---
layout: page
title: "ID-Booth: Identity-consistent Face Generation with Diffusion Models"
description: ""
importance: 1
category: work
related_publications: false

authors:
  - name: Darian Tomašević
    aff: [1]
    url: https://scholar.google.com/citations?user=QI6W5MMAAAAJ
  - name: Fadi Boutros
    aff: [2]
    url: https://scholar.google.com/citations?user=C-zewBgAAAAJ
  - name: Chenhao Lin
    aff: [3]
    url: https://scholar.google.com/citations?user=YK0G990AAAAJ
  - name: Naser Damer
    aff: [2,4]
    url: https://scholar.google.com/citations?user=bAyT17sAAAAJ
  - name: Vitomir Štruc
    aff: [5]
    url: https://scholar.google.com/citations?user=kr52cmAAAAAJ
  - name: Peter Peer
    aff: [1]
    url: https://scholar.google.com/citations?user=-h43hWoAAAAJ

affiliations:
  - affid: 1
    name: University of Ljubljana, Faculty of Computer and Information Science, Ljubljana, Slovenia
  - affid: 2 
    name: Fraunhofer Institute for Computer Graphics Research IGD, Darmstadt, Germany
  - affid: 3
    name: Xi’an Jiaotong University, School of Cyber Science and Engineering, Xi’an, China
  - affid: 4 
    name: Department of Computer Science, TU Darmstadt, Germany
  - affid: 5 
    name: University of Ljubljana, Faculty of Electrical Engineering, Ljubljana, Slovenia
---

<style>
.btn-dark,.btn-dark:hover {
  box-shadow: none !important;
  color: white;
  font-size: 1.00rem;
  text-transform: none;
}
.btn-dark:hover {
  background-color: #e03127 !important;         /* Bootstrap's "danger" red */
  transition: background-color 0.3s ease;
}
p {
  margin-top: 1rem;
  margin-bottom: 1.5rem; /* adjust spacing as needed */
}
h2 {
  margin-top: 2.5rem;
  margin-bottom: 1rem; /* adjust spacing as needed */
}
h3 {
  margin-top: 1.25rem;
  margin-bottom: 1rem; /* adjust spacing as needed */
}
</style>



<p>
  {% for author in page.authors %}
    {% if author.url %}
      <a href="{{ author.url }}">
        {{ author.name }}
      </a>
    {% else %}
      {{ author.name }}
    {% endif %}
    <sup>{{ author.aff | join: "," }}</sup>{% unless forloop.last %}, {% endunless %}
  {% endfor %}
</p>

<p>
  {% for aff in page.affiliations %}
  <div><sup>{{ aff.affid }} </sup> {{ aff.name }} </div>
{% endfor %}
</p>

### Poster at [FG 2025](https://fg2025.ieee-biometrics.org/)

<div class="d-flex flex-wrap gap-2 mt-3 mb-3">
  <a href="https://arxiv.org/abs/2504.07392" class="btn btn-dark rounded-pill px-3 py-2">
    <i class="fas fa-file-alt"></i> arXiv
  </a>
  <a href="/assets/pdf/ID-Booth_Poster.pdf" class="btn btn-dark rounded-pill px-3 py-2" style="text-transform: none; font-size: 1.00rem;">
   <i class="fas fa-chalkboard-teacher me-2"></i> Poster
  </a>
  <a href="https://github.com/dariant/ID-Booth" class="btn btn-dark rounded-pill px-3 py-2">
    <i class="fab fa-github"></i> GitHub
  </a>
  <a href="https://huggingface.co/spaces/user/demo" class="btn btn-dark rounded-pill px-3 py-2">
    <i class="fas fa-robot"></i> Demo
  </a>

</div>


<p>
We introduce the ID-Booth framework, which: <br>
 🔥 generates in-the-wild images of consenting identities captured in a constrained environment <br>
 🔥 uses a triplet identity loss to fine-tune Stable Diffusion for identity-consistent yet diverse image generation <br>
 🔥 can augment small-scale datasets to improve their suitability for training face recognition models <br>
</p>

<div class="w-75 mx-auto image">
    {% include figure.liquid loading="eager" path="assets/img/publications/ID-Booth/ID-Booth_teaser.jpg" title="ID-Booth teaser" class="img-fluid rounded" %}
</div>

## Abstract

<p style="text-align: justify;">
Recent advances in generative modeling have enabled the generation of high-quality synthetic data that is applicable in a variety of domains, including face recognition. Here, state-of-the-art generative models typically rely on conditioning and fine-tuning of powerful pretrained diffusion models to facilitate the synthesis of realistic images of a desired identity. Yet, these models often do not consider the identity of subjects during training, leading to poor consistency between generated and intended identities. In contrast, methods that employ identity-based training objectives tend to overfit on various aspects of the identity, and in turn, lower the diversity of images that can be generated. To address these issues, we present in this paper a novel generative diffusion-based framework, called ID-Booth. ID-Booth consists of a denoising network responsible for data generation, a variational auto-encoder for mapping images to and from a lower-dimensional latent space and a text encoder that allows for prompt-based control over the generation procedure. The framework utilizes a novel triplet identity training objective and enables identity-consistent image generation while retaining the synthesis capabilities of pretrained diffusion models. Experiments with a state-of-the-art latent diffusion model and diverse prompts reveal that our method facilitates better intra-identity consistency and inter-identity separability than competing methods, while achieving higher image diversity. The produced data allows for effective augmentation of small-scale datasets and training of better-performing recognition models in a privacy-preserving manner.
</p>

## Overview

<p style="text-align: justify;">
To fine-tune a pretrained Stable Diffusion model on a specific identity, the ID-Booth framework utilizes three training objectives: reconstruction loss, prior preservation loss, and the novel triplet identity loss. The first two are aimed at the reconstruction of training and prior images, respectively. The latter focuses on the identity similarity between generated samples and both training and prior samples to improve identity consistency without impacting the capabilities of the pretrained model. 
</p>

<div class="w-100">
    {% include figure.liquid loading="eager" path="assets/img/publications/ID-Booth/ID-Booth_framework.jpg" title="ID-Booth framework" class="img-fluid rounded" %}
</div>
<div class="caption">
    Overview of the fine-tuning process performed by the proposed ID-Booth framework.  
</div>

## Comparison with existing methods  

The proposed ID-Booth framework achieves better identity consistency than DreamBooth and better image diversity
than PortraitBooth. In turn, it enables better augmentation of small-scale lab-setting recognition datasets. 


<div class="w-75 mx-auto">
    {% include figure.liquid loading="eager" path="assets/img/publications/ID-Booth/ID-Booth_samples_full.jpg" title="ID-Booth samples full" class="img-fluid rounded" %}
</div>
<div class="caption">
    ID-Booth generates in-the-wild synthetic images of consenting identities from the Tufts Face Database (TFD) with a larger variety of face characteristics, including the pose, age, hair and accessories.
</div>


<div class="w-75 mx-auto">
    {% include figure.liquid loading="eager" path="assets/img/publications/ID-Booth/ID-Booth_samples_face.jpg" title="ID-Booth samples face" class="img-fluid rounded" %}
</div>
<div class="caption">
    ID-Booth facilitates better consistency with the target identity while achieving better intra-identity diversity compared to existing methods. Reported is the cosine similarity of synthetic and real identity features extracted with the pretrained ArcFace recognition model.
</div>




## BibTex

```html
@article{tomasevic2025IDBooth,
  title={ID-Booth: Identity-consistent Face Generation with Diffusion Models},
  author={Toma{\v{s}}evi{\'c}, Darian and Boutros, Fadi and Lin, Chenhao and Damer, Naser and {\v{S}}truc, Vitomir and Peer, Peter},
  journal={arXiv preprint arXiv:2504.07392},
  year={2025}
}
```