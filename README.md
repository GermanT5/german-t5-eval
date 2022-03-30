# German T5 Model Evaluation
This project documents the results of our evaluation of German [T5 models](https://arxiv.org/pdf/1910.10683.pdf).

## Summarization Task - max_source_length 800 max_target_length: 96

### Setup
- train data: [Swisstext](https://www.swisstext.org/2019/shared-task/german-text-summarization-challenge.html)
- test data: [MLSUM](https://huggingface.co/datasets/mlsum)
- GPUs: 4 (V100)
- batch size / GPU: 2
- batch size total: 8
- warmup_ratio: 0.3
- epochs: 10
- max_source_length: 800
- max_target_length: 96
- learning rate: 5e-5 (default)

### Result
Higher metric is better.

| Model                                                                           | rouge1 | rouge2 | rougeL | rougeLsum
|---------------------------------------------------------------------------------|--------|--------|--------|----------
| [google/mt5-small](https://huggingface.co/google/mt5-small) | 16.7323    | 3.5629    | 12.65    | 14.6898
| philschmid/test-german-t5-prompted-germanquad | 15.7629    | 2.8154    | 11.898    | 13.9223
| [stefan-it/t5-base-secret](https://huggingface.co/stefan-it/t5-base-secret) package3 | 15.7427    | 2.9186    | 12.0224    | 13.8726
| [stefan-it/t5-base-secret](https://huggingface.co/stefan-it/t5-base-secret) epoch2-package2 | 15.4757    | 2.7629    | 11.978    | 13.5326
| [GermanT5/t5-base-german-3e](https://huggingface.co/GermanT5/t5-base-german-3e) | 14.5525    | 2.0007    | 11.1617    | 12.9124
| [GermanT5/t5-efficient-oscar-german-small-el32](https://huggingface.co/GermanT5/t5-efficient-oscar-german-small-el32) last CP | 16.6277 | 3.404 | 12.6183 | 14.5772
| [GermanT5/t5-efficient-oscar-german-small-el32](https://huggingface.co/GermanT5/t5-efficient-oscar-german-small-el32) 2nd last CP | 16.6886 | 3.4468 | 12.666 | 14.6423

## Summarization Task - max_source_length 512 max_target_length: 96 epochs: 8

### Setup
- train data: [Swisstext](https://www.swisstext.org/2019/shared-task/german-text-summarization-challenge.html)
- test data: [MLSUM](https://huggingface.co/datasets/mlsum)
- GPUs: 4 (V100)
- batch size / GPU: 2
- batch size total: 8
- warmup_ratio: 0.3
- epochs: 8
- max_source_length: 512
- max_target_length: 96
- learning rate: 5e-5 (default)

### Result
Higher metric is better.

| Model                                                                           | rouge1 | rouge2 | rougeL | rougeLsum
|---------------------------------------------------------------------------------|--------|--------|--------|----------
| [google/mt5-small](https://huggingface.co/google/mt5-small) (FP32) | 16.0354 | 3.2689 | 12.2063 | 14.1225
| [GermanT5/t5-efficient-oscar-german-small-el32](https://huggingface.co/GermanT5/t5-efficient-oscar-german-small-el32) (FP32) | 16.2004 | 3.2372 | 12.3031 | 14.2256
| [GermanT5/t5-efficient-gc4-german-small-el32](https://huggingface.co/GermanT5/t5-efficient-gc4-german-small-el32) (FP32) | 17.1507 | 3.8038 | 13.0836 | 15.1671
| [GermanT5/t5-efficient-gc4-german-base-nl36-old](https://huggingface.co/GermanT5/t5-efficient-gc4-german-base-nl36-old) (FP16) | 9.3494 | 1.3531 | 7.4037 | 8.5473
| [GermanT5/t5-efficient-gc4-german-base-nl36](https://huggingface.co/GermanT5/t5-efficient-gc4-german-base-nl36) ([DeepSpeed](https://github.com/microsoft/DeepSpeed) with [ZeRO-3 Example](https://huggingface.co/docs/transformers/main_classes/deepspeed#zero3-example) `auto` config) | 17.9501 | 3.9247 | 13.3758 | 15.6139
