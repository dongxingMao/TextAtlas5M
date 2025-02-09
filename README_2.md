# TextAtlas5M

![Head](https://github.com/user-attachments/assets/5e2c5c85-d38d-4a11-8872-e527c3ee8799)

<h3 align="center"> A Large-scale Dataset for Dense Text Image Generation</h3>

## Updates

- released TextAtlas5M version 1.0 :fire:

## Data Level, Datasets, and Annotations Overview

| Data Split       | Dataset Name        | #Samples    | Annotations                    | Type               | Token Length      |
|------------------|---------------------|-------------|--------------------------------|--------------------|-------------------|
| Synthetic Images | CleanTextSynth      | 1,907,721   | Real Text                      | Pure Text          | 70.70             |
| Synthetic Images | TextVisionBlend     | 0.5M        | Parsed json+BLIP Caption       | Pure Text          | 265.62            | 
| Synthetic Images | StyledTextSynth     | ∼ 0.5M      | Human+ QWEN+Intern-VL          | Synthetic Image    | 90.00             |
| ---------------- | ------------------- | ----------- | ------------------------------ | ------------------ | ----------------- |
| Real Images      | PPT2Details         | 298565      | QWEN2-VL Caption               | Powerpoint Image   | 121.97            |
| Real Images      | PPT2Structured      | 96457       | Parsed json+QWEN2-VL Caption   | Powerpoint Image   | 774.67            |
| Real Images      | LongWordsSubset-A   | 266534      | Caption + OCR                  | Real Image         | 38.57             |
| Real Images      | LongWordsSubset-M   | 1299992     | Caption + OCR                  | Real Image         | 34.07             |
| Real Images      | Cover Book          | 207566      | Name + Author + Category       | Real Image         | 28.01             |
| Real Images      | Paper2Text          | 2M          | PyMuPdf phrased Text           | Pure Text          | 28.01             |
| Real Images      | TextScenesHQ        | ∼ 0.5M      | Human+Llama+Qwen+GPT4o         | Real Image         | 120.81            |
| In Total         | TextAtlas5M 5M      | 5M          | -                              | -                  | 148.82            |

## Accessing TextAtlas5M

### Documents

You can directly download TextAtlas5M at urls like this:

`url`


## Format

The file merged_data.json contains JSON Lines data, where each line is a single JSON object representing a prediction
result. Each object includes fields such as image_path, plain_caption, total_image_caption, image_text (an array of
text-related information), and topic.

```json
{
  "image_path": "path to png",
  "plain_caption": "A formal presentation hall with an audience attentively listening to a speaker at a podium, with a large screen displaying the text : <>.",
  "total_image_caption": "A formal presentation hall with an audience attentively listening to a speaker at a podium, with a large screen displaying the text : 'Furthermore, the research highlighted the critical role of climate-resilient infrastructure, such as irrigation systems and storage facilities, in supporting agricultural production and food security in the face of climate-related'.",
  "image_text": [
    {
      "bbox": [
        177,
        113,
        828,
        335
      ],
      "text": "Furthermore, the research highlighted the critical role of climate-resilient infrastructure, such as irrigation systems and storage facilities, in supporting agricultural production and food security in the face of climate-related",
      "text_font": "DejaVuSansCondensed.ttf",
      "text_size": 44
    }
  ],
  "topic": "academic report"
}
```

| entry                 | description                                                                                                                                                                            |
|-----------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `image_path`          | `str`, path to png                                                                                                                                                                     |
| `plain_caption`       | `str`, Replace render text in description with <>                                                                                                                                      | 
| `total_image_caption` | `str`, Full Description                                                                                                                                                                | 
| `image_text`          | `list(dict)`, extracted text regions from the image. Each dictionary contains 4 elements: ["bbox (list of 4 integers)", "text (string)", "text_font (string)", "text_size (integer)"]. | 
| `topic`               | `str`, The topic to which the current data belongs                                                                                                                                     | 

[//]: # (## Introduction)

[//]: # (TextAtlas5M includes a diverse and complex range of data. It spans from interleaved documents and synthetic data to real world images containing dense text, offering a more varied and challenging set of examples. Moreover, our dataset features longer text captions, which pose additional challenges for models, and includes human annotations for particularly difficult examples, ensuring a more thorough evaluation of model capabilities. The synthetic subset progresses through three levels of complexity, starting with simple text on clean backgrounds. It then advances to interleaved data, blending text with visual elements, and culminates in synthetic natural images, where realistic scenes integrate seamlessly with text. The real image subset captures diverse, real-world dense text scenarios. It includes filtered samples from datasets like AnyText and TextDiffuser, detailed descriptions from PowerPoint slides, book covers, and academic PDF papers. To enrich diversity, we also gather dense-text images guided by predefined topics from CommonCrawl1 and LAION-5B. To assess the capability of model in dense text image generation, we introduce a dedicated test set, TextAtlas5MEval, designed for comprehensive evaluation. This test set spans four distinct data types, ensuring diversity across domains and enhancing the relevance of TextAtlas5M for real-world applications.)

[//]: # ()

[//]: # (## Topic Distribution)

[//]: # (![topic_pie_chart]&#40;https://github.com/user-attachments/assets/9e3d97f6-7bc0-45a5-80a2-6cf090c0e9bd&#41;)

[//]: # (## Generation Pipeline)

[//]: # (TextScenesHQ Pipeline)

[//]: # (![HQpipeline]&#40;https://github.com/user-attachments/assets/15e8b4be-9c8e-40f4-8314-2b7ce8f8cdac&#41;)

[//]: # (StyledTextSynth Pipeline)

[//]: # (![MQpipeline]&#40;https://github.com/user-attachments/assets/f51ef948-3947-441d-9065-89e23c11ec7c&#41;)


[//]: # (## Dataset Comparison with Existing Text-Rich Image Generation Datasets)

[//]: # ()

[//]: # (| Dataset Name                                                 | Samples | Annotations | Domain               | Labels     | Token Length |)

[//]: # (| ------------------------------------------------------------ | ------- | ----------- | -------------------- | ---------- | ------------ |)

[//]: # (| TextCaps &#40;[Sidorov et al., 2020]&#40;https://www.overleaf.com/project/679204c527e67755f9016e54#cite.textcaps&#41;&#41; | 28K     | Caption     | Real Image           | Human      | 26.36        |)

[//]: # (| SynthText &#40;[Gupta et al., 2016]&#40;https://www.overleaf.com/project/679204c527e67755f9016e54#cite.SynthText&#41;&#41; | 0.8M    | OCR         | Synthetic Image      | Auto       | 13.75        |)

[//]: # (| Marion10M &#40;[Chen et al., 2024a]&#40;https://www.overleaf.com/project/679204c527e67755f9016e54#cite.textdiffuser&#41;&#41; | 10M     | Caption+OCR | Real Image           | Auto       | 16.13        |)

[//]: # (| AnyWords3M &#40;[Tuo et al., 2023]&#40;https://www.overleaf.com/project/679204c527e67755f9016e54#cite.anytext&#41;&#41; | 3M      | Caption+OCR | Real Image           | Auto       | 9.92         |)

[//]: # (| RenderedText &#40;[Wendler]&#40;https://www.overleaf.com/project/679204c527e67755f9016e54#cite.renderedtext&#41;&#41; | 12M     | Text        | Synthetic Image      | Auto       | 21.21        |)

[//]: # (| TextAtlas5M                                                  | 5M      | Caption/OCR | Real&Synthetic Image | Auto/Human | 148.82       |)

[//]: # (## Examples)

[//]: # (![MQpipeline]&#40;https://github.com/Carrot0729/hwmsRepo/blob/main/data-display-overall-w-ann-v2.svg&#41;)
