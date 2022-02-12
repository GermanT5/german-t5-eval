# German T5 Model Evaluation
This project documents the results of our evaluation of German [T5 models](https://arxiv.org/pdf/1910.10683.pdf).

## Summarization Task

### Setup
- train data: [Swisstext](https://www.swisstext.org/2019/shared-task/german-text-summarization-challenge.html)
- test daten: [MLSUM](https://huggingface.co/datasets/mlsum)
- batch size / GPU: 2
- GPUs: 4 (V100)
- warmup_ratio: 0.3
- epochs: 10
- max_source_length: 800
- max_target_length: 96
- learning rate: 5e-5 (default)

### Result
| Model                                                                           | rouge1 | rouge2 | rougeL | rougeLsum
|---------------------------------------------------------------------------------|--------|--------|--------|----------
| [google/mt5-small](https://huggingface.co/google/mt5-small) | 16.7323    | 3.5629    | 12.65    | 14.6898
| philschmid/test-german-t5-prompted-germanquad | 15.7629    | 2.8154    | 11.898    | 13.9223
| [stefan-it/t5-base-secret](https://huggingface.co/stefan-it/t5-base-secret) package3 | 15.7427    | 2.9186    | 12.0224    | 13.8726
| [stefan-it/t5-base-secret](https://huggingface.co/stefan-it/t5-base-secret) epoch2-package2 | 15.4757    | 2.7629    | 11.978    | 13.5326
| [GermanT5/t5-base-german-3e](https://huggingface.co/GermanT5/t5-base-german-3e) | ???    | ???    | ???    | ???
