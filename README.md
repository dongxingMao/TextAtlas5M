


# TextAtlas5M

<p align="center">
  <img src="https://github.com/user-attachments/assets/5e2c5c85-d38d-4a11-8872-e527c3ee8799" width="300">
</p>

<h3 align="center"> A Large-scale Dataset for Dense Text Image Generation</h3>

[**🌐 Homepage**](https://textatlas5m.github.io/) | [**🏆 Leaderboard**](https://textatlas5m.github.io/#leaderboard) | [**🤗 TextAtlas**]() | [**📖 TextAtlas arXiv**]()

This repo contains the evaluation code for the paper "[TextAtals]()" 

## Updates

- released TextAtlas5M version 1.0 :fire:

## Introduction


## Accessing TextAtlas

TextAtlas was meticulously designed to challenge and evaluate text-rich image generation. For more detailed information, please refer to our Hugging Face datasets:
- [**🤗 TextAtlas Dataset**]()

## Evaluation
Please refer to our evaluation folders for detailed information on evaluating with TextAtlas benchmark:

- [**TextAtlas Evaluation**](evaluation)


## Data Format

The TextAtlas annotation documentation is available in two versions:

- **Version 1**: Contains image paths and pre-integrated prompts, making it suitable for direct training or evaluation.
- **Version 2**: Includes all the data from Version 1, along with additional intermediate results such as bounding boxes (bbox), font size, and other related information, which can be used for further data analysis or processing.

### Version 1 Example
```json
{
  "image_path": "path to the Image",
  "annotation": "A formal presentation hall with an audience attentively listening to a speaker at a podium, with a large screen displaying the text: 'Furthermore, the research highlighted the critical role of climate-resilient infrastructure, such as irrigation systems and storage facilities, in supporting agricultural production and food security in the face of climate-related'."
}
```

| entry                 | description                                                                                                                                                                            |
|-----------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `image_path`          | `str`, path to png                                                                                                                                                                     |
| `total_image_caption` | `str`, Full Description                                                                                                                                                                | 

In addition to the data from Version 1, Version 2 includes intermediate results retained during the processing of different subsets. These results provide useful metadata for further analysis, such as bounding boxes (bbox), font size, and other processing details.

Please refer to the [**TextAtlas Detailed Annotation**] for more comprehensive details on the second version annotations.

### For 2nd version
Please refer to our detial annotion folders for detailed information on 2nd verision anntation:
- [**TextAtlas Detailed Annotation**]


## Data Level, Datasets, and Annotations Overview

| Data Split       | Dataset Name      | #Samples  | Annotations                  | Type             | Token Length | Contain Structured info|
|------------------|-------------------|-----------|------------------------------|------------------|--------------|--------------|
| Synthetic Images | CleanTextSynth    | 1,907,721 | Real Text                    | Pure Text        | 70.70        |       ❌       |
| Synthetic Images | TextVisionBlend   | 547,837   | Parsed json+BLIP Caption     | Pure Text        | 265.62       |       ✅       | 
| Synthetic Images | StyledTextSynth   | 426,755   | Human+ QWEN+Intern-VL        | Synthetic Image  | 90.00        |       ✅      |
| -                | -                 | -         | -                            | -                | -            | -            |
| Real Images      | PPT2Details       | 298565    | QWEN2-VL Caption             | Powerpoint Image | 121.97       |       ❌       |
| Real Images      | PPT2Structured    | 96457     | Parsed json+QWEN2-VL Caption | Powerpoint Image | 774.67       |       ✅       |
| Real Images      | LongWordsSubset-A | 266534    | Caption + OCR                | Real Image       | 38.57        |       ❌       |
| Real Images      | LongWordsSubset-M | 1299992   | Caption + OCR                | Real Image       | 34.07        |        ❌      |
| Real Images      | Cover Book        | 207566    | Name + Author + Category     | Real Image       | 28.01        |        ❌      |
| Real Images      | Paper2Text        | 356,658       | PyMuPdf phrased Text         | Pure Text        | 28.01        |      ❌        |
| Real Images      | TextScenesHQ      | 36,576     | Human+Llama+Qwen+GPT4o       | Real Image       | 120.81       |         ✅     |
| In Total         | TextAtlas5M 5M    | ～ 5M        | -                            | -                | 148.82       |              |


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


## License

- the new contributions of TextAtlas are released under [ODC-BY](https://opendatacommons.org/licenses/by/1-0/).
- By using TextAtlas, be aware of that you are also bound by the [Common Crawl terms of use](https://commoncrawl.org/terms-of-use/).

## Citation

If you found our work useful, please consider citing:
```
  @inproceedings{wang2025large,
            title={A Large-scale Dataset for Dense Text Image Generation},
            author={ Alex Jinpeng Wang and  Jiawei Zhang and Dongxing Mao and weiming Han and Zhuobai Dong and Linjie Li and Yiqi Lin and Zhengyuan Yang and Libo Qin and Fuwei Zhang and Lijuan Wang and Min Li},
            booktitle={Arxiv},
            year={2024},
        }
```

[//]: # (@article{zhu2023multimodal,)

[//]: # (  title={{Multimodal C4}: An Open, Billion-scale Corpus of Images Interleaved With Text},)

[//]: # (  author={Wanrong Zhu and Jack Hessel and Anas Awadalla and Samir Yitzhak Gadre and Jesse Dodge and Alex Fang and Youngjae Yu and Ludwig Schmidt and William Yang Wang and Yejin Choi},)

[//]: # (  journal={arXiv preprint arXiv:2304.06939},)

[//]: # (  year={2023})

[//]: # (})

