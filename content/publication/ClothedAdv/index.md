---
title: "3D Clothed Human Reconstruction from Single In-the-wild RGB Image"
authors:
- admin
- Benchuang Chen
- Xinrong Chen
author_notes:
- ""
- ""
- "Corresponding Author"
date: "2024-02-16T00:00:00Z"
doi: ""

# Schedule page publish date (NOT publication's date).
publishDate: "2024-02-16T00:00:00Z"

# Publication type.
# Accepts a single type but formatted as a YAML list (for Hugo requirements).
# Enter a publication type from the CSL standard.
publication_types: ["article-journal"]

# Publication name and optional abbreviated publication name.
publication: "(Submitted)"
publication_short: ""

abstract: 3D clothed human reconstruction has achieved much progress in recent years. However, many methods complete reconstruction based on model trained on synthetic datasets, which can cause high costs for obtaining data and constraints on poses of human. The domain gap between synthetic data and natural data also severely restricts arrangement of these methods in real world. Moreover, some researches on 3D clothed human reconstruction from wild images are facing challenges due to complex background and pose in the image. In this paper, we design a modular model to perform 3D clothed human reconstruction with high quality based on one single-view in-the-wild image. In detail, our model consists of Cloth Encoder which extracts feature of clothes, Body Prediction which obtains parameters of human body and Cloth Generation Module which generates cloth on human model. Specifically, we propose to utilize a adaptive integration of convolution neural network and self-attention to extract both local and global features of clothes from the input image. Moreover, to eliminate the distraction of the background, we utilize the segmentation of the input image to supervise our training process. Our method is compared with various previous works on MSCOCO and 3DPW datasets. The quantitative and qualitative results both demonstrate our method can reconstruct more accurate clothed human model than other methods. This work will probably allow us to apply more efficient, convenient and accurate technology of 3D clothed human reconstruction into the real world. The preimilary work has been published on <a href='https://sites.google.com/view/t4v-cvpr23/papers'>CVPR 2023 Workshop, Transformers for Vision</a>. Moreover, the advanced work is currently submitted to <b>2024 International Conference on Image Processing(ICIP 2024)</b>.

# Summary. An optional shortened abstract.
summary: 

tags:
- 3D Human Reconstruction
featured: true

# links:
# - name: ""
#   url: ""
url_pdf: ''
url_code: ''
url_dataset: ''
url_poster: ''
url_project: ''
url_slides: ''
url_source: ''
url_video: ''

# Featured image
# To use, add an image named `featured.jpg/png` to your page's folder. 
image:
  caption: ''
  focal_point: ""
  preview_only: false

# Associated Projects (optional).
#   Associate this publication with one or more of your projects.
#   Simply enter your project's folder or file name without extension.
#   E.g. `internal-project` references `content/project/internal-project/index.md`.
#   Otherwise, set `projects: []`.
projects: []

# Slides (optional).
#   Associate this publication with Markdown slides.
#   Simply enter your slide deck's filename without extension.
#   E.g. `slides: "example"` references `content/slides/example/index.md`.
#   Otherwise, set `slides: ""`.
slides: ""
---


