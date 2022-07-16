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
4. Git Clone the [Transformer repo](https://github.com/huggingface/transformers/tree/v4.9.0). 
5. Download the [squad.py](https://github.com/luoyuanlab/Clinical-Longformer/blob/main/Question%20Answering/squad.py) and change [file directories](https://github.com/luoyuanlab/Clinical-Longformer/blob/9988755254333d04ac7c18f655bd938aa018eea5/Question%20Answering/squad.py#L55) as your own.
6. We will run this [script](https://github.com/huggingface/transformers/blob/v4.9.0/examples/pytorch/question-answering/run_qa.py) of the Transformers repo for a QA task training. Replace [here](https://github.com/huggingface/transformers/blob/72aee83ced5f31302c5e331d896412737287f976/examples/pytorch/question-answering/run_qa.py#L264) to: 
```
raw_datasets = load_dataset('/YOUR/PATH/squad.py')
```
7. RUN
```
CUDA_VISIBLE_DEVICES=5 python run_qa.py \
  --model_name_or_path yikuan8/Clinical-Longformer\
  --dataset_name emrQA \
  --do_train \
  --do_eval \
  --do_predict\
  --per_device_train_batch_size 4 \
  --fp16 \
  --fp16_backend amp \
  --per_device_eval_batch_size 8 \
  --learning_rate 3e-5 \
  --num_train_epochs 4 \
  --max_train_samples 128 \
  --max_eval_samples 128 \
  --max_predict_samples 128 \
  --max_seq_length 4096 \
  --ignore_data_skip \
  --evaluation_strategy epoch \
  --save_strategy epoch \
  --overwrite_output_dir \
  --overwrite_cache \
  --output_dir /YOUR/PATH/emrQA_cb/
```
