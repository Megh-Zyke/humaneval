# HumanEval: Configured for Windows execution

## Requirements

- Ensure python version 3.9 or greater
- Install all the necessary requirements in your environment

## jsonl Format

- Create a script that uses your language model to generate answers to the questions given in the benchamark
- View the script below to understand how to extract the questions from the benchmark

```
import json
import gzip

human_eval_path = "human-eval/data/HumanEval.jsonl.gz"
with gzip.open(human_eval_path, "r") as f:
    problems = [json.loads(line) for line in f]
```

- Ensure this is the format that is followed :
  ```
  {"task_id":"HumanEval/{question_number}","completion": {code generated by ai} }
  ```
- Save a copy of your jsonl file in the data folder.

## Running the code

- Once all the prequisites are done, head to the terminal and write the following code:

```
python human_eval/evaluate_functional_correctness.py data/{name of your jsonl file}
```

- Ensure you are in the main directory of this file and run this. You will get your pass@1 score in a few minutes
