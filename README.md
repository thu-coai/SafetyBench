![SafetyBench](figs/cover.png)

<p align="center">
   🌐 <a href="https://llmbench.ai/safety" target="_blank">Website</a> • 🤗 <a href="https://huggingface.co/datasets/thu-coai/SafetyBench" target="_blank">Hugging Face</a> • ⏬ <a href="#data" target="_blank">Data</a> •   📃 <a href="https://arxiv.org/abs/2309.07045" target="_blank">Paper</a>
</p>

SafetyBench is a comprehensive benchmark for evaluating the safety of LLMs, which comprises 11,435 diverse multiple choice questions spanning across 7 distinct categories of safety concerns. SafetyBench also incorporates both Chinese and English data, facilitating the evaluation in both languages. Please visit our [website](https://llmbench.ai/safety) or check our [paper](https://arxiv.org/abs/2309.07045) for more details. 

![SafetyBench](./figs/overview.png)

## Table of Contents <!-- omit from toc -->
- [Leaderboard](#leaderboard)
- [Data](#data)
  - [Download](#download)
  - [Description](#description)
- [How to Evaluate on SafetyBench](#how-to-evaluate-on-safetybench)
- [How to Submit](#how-to-submit)
- [Citation](#citation)


## Leaderboard
The up-to-date leaderboards are on our [website](https://llmbench.ai/safety). We have three leaderboards for Chinese, English and Chinese subset respectively. We remove questions with highly sensitive keywords and downsample 300 questions for each category to construct the Chinese subset. Summarized evaluation results of some representative LLMs are shown below:

![Result](./figs/res.png)

## Data
### Download
You can download the test questions and few-shot examples through `wget` directly. Just run the script [`download_data.sh`](./code/download_data.sh)

Alternatively, you can download the test questions and few-shot examples through the `datasets` library. Just run the code [`download_data.py`](./code/download_data.py)

### Description
`test_zh`, `test_en` ann `test_zh_subset` contain test questions for Chinese, English and Chinese subset respectively. `dev_zh` and `dev_en` contain 5 examples for each safety category, which can be used as few-shot demonstrations. 

Note that the `options` field in the data includes at most four items, corresponding to the options A, B, C, D in order. For the `answer` field in the dev data, the mapping rule is: 0->A, 1->B, 2->C, 3->D.

## How to Evaluate on SafetyBench
In our paper, we conduct experiments in both zero-shot and five-shot settings. And we extract the predicted answers from models' responses. An example of evaluation code could be found at [code](./code/evaluate_baichuan.py). We don’t include CoT-based evaluation because SafetyBench is less reasoning-intensive than benchmarks testing the model’s
general capabilities such as MMLU. But feel free to submit your results based on CoT. The default prompt for zero-shot and five-shot evaluation is shown below:
![figure](./figs/eva_prompts.png)

To enable more accurate extraction of the predicted answers, we made minor changes to the prompts for some models, which is shown below:
![figure](./figs/prompt_change.png)

## How to Submit
You need to first prepare a UTF-8 encoded JSON file with the following format, please refer to [submission_example.json](./submission_example.json) for details.

```
## key is the "id" field of the test questions
## value is the predicted answer: 0->A, 1->B, 2->C, 3->D
{
    "0": 0,
    "1": 1,
    "2": 3,
    "3": 2 
}
```

Then you can submit the JSON file to our [website](https://llmbench.ai/safety). 

## Citation
```
@article{zhang2023safetybench,
      title={SafetyBench: Evaluating the Safety of Large Language Models with Multiple Choice Questions}, 
      author={Zhexin Zhang and Leqi Lei and Lindong Wu and Rui Sun and Yongkang Huang and Chong Long and Xiao Liu and Xuanyu Lei and Jie Tang and Minlie Huang},
      journal={arXiv preprint arXiv:2309.07045},
      year={2023}
}
```