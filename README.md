# SafetyBench

- [SafetyBench](#safetybench)
  - [Leaderboard](#leaderboard)
  - [Data](#data)
    - [Download](#download)
  - [How to Evaluate on SafetyBench](#how-to-evaluate-on-safetybench)
  - [How to Submit](#how-to-submit)
  - [Citation](#citation)


SafetyBench is a comprehensive benchmark for evaluating the safety of LLMs, which comprises 11,435 diverse multiple choice questions spanning across 7 distinct categories of safety concerns. SafetyBench also incorporates parallel Chinese-English data, facilitating the evaluation in both languages. Please visit our [website]() or check our [paper]() for more details. 

## Leaderboard
The up-to-date leaderboard is on our [website](). We have two leaderboards for Chinese and English respectively.

## Data
### Download

`test_zh` and `test_en` contain test questions for Chinese and English respectively. `dev_zh` and `dev_en` contain 5 examples for each safety category, which can be used as few-shot demonstrations.

Note that the `options` field in the data includes at most four items, corresponding to the options A, B, C, D in order. For the `answer` field in the dev data, the mapping rule is: 0->A, 1->B, 2->C, 3->D.

## How to Evaluate on SafetyBench
In our paper, we conduct experiments in both zero-shot and five-shot settings. And we extract the predicted answers from models' responses. Examples of evaluation code could be found at [code](). We don’t include CoT-based evaluation officially currently because SafetyBench is less reasoning-intensive than benchmarks testing the model’s
general capabilities such as MMLU. But feel free to submit your results based on CoT. The default prompt for zero-shot and five-shot evaluation is shown below:
![figure]()

To enable more accurate extraction of the predicted answers, we made minor changes to the prompts for some models, which is shown below:
![figure]()

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

Then you can submit the JSON file to our [website](). 

## Citation
