We used emrQA as an example to illustrate how Clinical-Longformer can be applied to extractive question answering tasks.

1. Download emrQA dataset at: https://portal.dbmi.hms.harvard.edu/projects/n2c2-nlp/. N2C2 access should be requested.
2. Pre-process emrQA and formulate the dataset to SQuAD format. We used this [repo](https://github.com/sunlab-osu/CliniRC). Please also cite there ACL paper, if you think it is useful.
3. On running the previous 2 steps, you shall have such directory structure. We use the medication subset as an example.
```
emrQA  
│   medication-dev.json
│   medication-test.json
│   medication-train.json
│   relation-dev.json
│   relation-test.json
│   relation-train.json
│   risk-dataset-dev.json
│   risk-dataset-test.json
│   risk-dataset-train.json
└───us
│   │   medication-train-sampled-0.2.json
│   │   relation-train-sampled-0.05.json
``` 
4. Git Clone the [Transformer repo](https://github.com/huggingface/transformers). 
5. Download the [squad.py](https://github.com/luoyuanlab/Clinical-Longformer/blob/main/Question%20Answering/squad.py) and change [file directories] as your own.
6. 
