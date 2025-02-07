# TextAtlas5M
![Head](https://github.com/user-attachments/assets/5e2c5c85-d38d-4a11-8872-e527c3ee8799)

<h3 align="center"> A Large-scale Dataset for Dense Text Image Generation</h3>

## Introduction
TextAtlas5M includes a diverse and complex range of data. It spans from interleaved documents and synthetic data to real world images containing dense text, offering a more varied and challenging set of examples. Moreover, our dataset features longer text captions, which pose additional challenges for models, and includes human annotations for particularly difficult examples, ensuring a more thorough evaluation of model capabilities. The synthetic subset progresses through three levels of complexity, starting with simple text on clean backgrounds. It then advances to interleaved data, blending text with visual elements, and culminates in synthetic natural images, where realistic scenes integrate seamlessly with text. The real image subset captures diverse, real-world dense text scenarios. It includes filtered samples from datasets like AnyText and TextDiffuser, detailed descriptions from PowerPoint slides, book covers, and academic PDF papers. To enrich diversity, we also gather dense-text images guided by predefined topics from CommonCrawl1 and LAION-5B. To assess the capability of model in dense text image generation, we introduce a dedicated test set, TextAtlas5MEval, designed for comprehensive evaluation. This test set spans four distinct data types, ensuring diversity across domains and enhancing the relevance of TextAtlas5M for real-world applications.

## Topic Distribution
![topic_pie_chart](https://github.com/user-attachments/assets/9e3d97f6-7bc0-45a5-80a2-6cf090c0e9bd)

## Generation Pipeline
TextScenesHQ Pipeline
![HQpipeline](https://github.com/user-attachments/assets/15e8b4be-9c8e-40f4-8314-2b7ce8f8cdac)
StyledTextSynth Pipeline
![MQpipeline](https://github.com/user-attachments/assets/f51ef948-3947-441d-9065-89e23c11ec7c)



## Dataset Comparison with Existing Text-Rich Image Generation Datasets

| Dataset Name                                                 | Samples | Annotations | Domain               | Labels     | Token Length |
| ------------------------------------------------------------ | ------- | ----------- | -------------------- | ---------- | ------------ |
| TextCaps ([Sidorov et al., 2020](https://www.overleaf.com/project/679204c527e67755f9016e54#cite.textcaps)) | 28K     | Caption     | Real Image           | Human      | 26.36        |
| SynthText ([Gupta et al., 2016](https://www.overleaf.com/project/679204c527e67755f9016e54#cite.SynthText)) | 0.8M    | OCR         | Synthetic Image      | Auto       | 13.75        |
| Marion10M ([Chen et al., 2024a](https://www.overleaf.com/project/679204c527e67755f9016e54#cite.textdiffuser)) | 10M     | Caption+OCR | Real Image           | Auto       | 16.13        |
| AnyWords3M ([Tuo et al., 2023](https://www.overleaf.com/project/679204c527e67755f9016e54#cite.anytext)) | 3M      | Caption+OCR | Real Image           | Auto       | 9.92         |
| RenderedText ([Wendler](https://www.overleaf.com/project/679204c527e67755f9016e54#cite.renderedtext)) | 12M     | Text        | Synthetic Image      | Auto       | 21.21        |
| TextAtlas5M                                                  | 5M      | Caption/OCR | Real&Synthetic Image | Auto/Human | 148.82       |

## Examples
![MQpipeline](https://github.com/Carrot0729/hwmsRepo/blob/main/data-display-overall-w-ann-v2.svg)
