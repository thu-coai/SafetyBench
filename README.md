# SafetyBench

SafetyBench is a comprehensive benchmark for evaluating the safety of LLMs, which comprises 11,435 diverse multiple choice questions spanning across 7 distinct categories of safety concerns. SafetyBench also incorporates parallel Chinese-English data, facilitating the evaluation in both languages. Please visit our [website]() or check our [paper]() for more details. 

## Leaderboard
The up-to-date leaderboard is on our [website](). We have two leaderboards for Chinese and English respectively.

## Data
### Download

## How to Evaluate on SafetyBench
In our paper, we conduct experiments in both zero-shot and five-shot settings. And we extract the predicted answers from models' responses. Examples of evaluation code could be found at [code](). We don’t include CoT-based evaluation officially currently because SafetyBench is less reasoning-intensive than benchmarks testing the model’s
general capabilities such as MMLU. But feel free to submit your results based on CoT. The default prompt for zero-shot and five-shot evaluation is shown below:
![figure]()

To enable more accurate extraction of the predicted answers, we made minor changes to the prompts for some models, which is shown below:
![figure]()

## How to Submit
You need to first prepare a UTF-8 encoded JSON file with the following format, please refer to [submission_example.json]() for details.

Then you can submit the JSON file to our [website](). 

## Citation

