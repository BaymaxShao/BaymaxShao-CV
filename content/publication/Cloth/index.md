---
title: "3D Clothed Human Model Reconstruction Based on Single-view In-the-wild Image Data"
authors:
- admin
- Benchuang Chen
- Ziqun Zhang
- Xinrong Chen
author_notes:
- ""
- ""
- ""
- "Corresponding Author"
date: "2024-01-02T00:00:00Z"
doi: ""

# Schedule page publish date (NOT publication's date).
publishDate: "2024-01-02T00:00:00Z"

# Publication type.
# Accepts a single type but formatted as a YAML list (for Hugo requirements).
# Enter a publication type from the CSL standard.
publication_types: ["article-journal"]

# Publication name and optional abbreviated publication name.
publication: "Accepted by *IEEE Sensors Journal*"
publication_short: ""

abstract: 3D clothed human reconstruction has gained great development recently. However, many methods complete reconstruction based on model trained on the synthetic data with artificial appearance or the 3D scan data with high costs. The difference between synthetic data, 3D scan data and in-the-wild data severely restricts application of these methods in real world. Moreover, due to complex background and pose in the image, some researches on the 3D clothed human reconstruction from single-view in-the-wild images are facing challenges. In this paper, a modular model is designed to perform the 3D clothed human reconstruction with high quality based on one single-view in-the-wild image. In detail, the model consists of Cloth Encoder which extracts the feature of clothes, Body Encoder which obtains the parameters of human body and Cloth Generation Module which generates the clothes on the human model. Specifically, an adaptive integration of convolution neural network and self-attention is proposed to extract features of the input image. Moreover, to eliminate the distraction of the background, the segmentation of the input image is utilized to supervise our training process.The proposed method is compared with the mainstream methods on the two datasets, MSCOCO and 3DPW. The quantitative and qualitative results demonstrate that our method is more accurate in reconstructing clothed human model than the previous methods. Based on the experiment results, our work provides a more convenient and accurate 3D clothed human reconstruction technique in the real world.

# Summary. An optional shortened abstract.
summary: 

tags:
- 3D Human Reconstruction
featured: false

# links:
# - name: ""
#   url: ""
url_pdf: 'https://www.aimspress.com/article/doi/10.3934/mbe.2024073'
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


