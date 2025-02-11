# Evaluation Guidelines
We provide detailed instructions for evaluation. 
To execute our evaluation script, please ensure that the structure of your model outputs is the same as ours.

## Json format
If you want to get the evaluation score of your generation result.

You can provide all the outputs in *one file* in the following format:

```
{
    "image_path": " ", # path to your generation image
    "original_image_path": " ", # path to the GT image
    "prompt": " ", #  prompt to generate the image
    "raw_text": " ", # GT text show in the image (used for OCR score)
},
....
```

## calculate FID score


## calculate CLIP score

## calculate OCR related score
