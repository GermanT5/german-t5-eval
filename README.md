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
| [GermanT5/t5-base-german-3e](https://huggingface.co/GermanT5/t5-base-german-3e) | ???    | ???    | ???    | ???
