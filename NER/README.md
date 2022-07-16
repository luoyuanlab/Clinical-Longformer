We used i2b2 as an example to illustrate how Clinical-Longformer can be applied to NER tasks.
1. Download i2b2 2006, 2010, 2012, 2014 dataset at: https://portal.dbmi.hms.harvard.edu/projects/n2c2-nlp/. N2C2 access should be requested.
2. Pre-process i2b2 and formulate the dataset to .json format. We used this [repo](https://github.com/EmilyAlsentzer/clinicalBERT/tree/master/downstream_tasks/i2b2_preprocessing). Please also cite there NAACL paper, if you think it is useful.
3. On running the previous 2 steps, you shall have such directory structure
```
NER  
|
└───I2B2_2006
│   │   train.json
│   │   test.json
│   │   dev.json
└───I2B2_2010
│   │   train.json
│   │   test.json
│   │   dev.json
└───I2B2_2012
│   │   train.json
│   │   test.json
│   │   dev.json
└───I2B2_2014
│   │   train.json
│   │   test.json
│   │   dev.json
``` 
4. Download run_ner.py
5. RUN
```
CUDA_VISIBLE_DEVICES=1,2,3,4 \
python run_ner.py \
  --model_name_or_path yikuan8/Clinical-Longformer \
  --num_train_epochs 4 \
  --do_train \
  --do_eval \
  --do_predict \
  --evaluation_strategy epoch \
  --train_file NER/I2B2_2014/train.json \
  --validation_file NER/I2B2_2014/dev.json \
  --test_file NER/I2B2_2014/test.json \
  --per_device_train_batch_size 4 \
  --per_device_eval_batch_size 8 \
  --output_dir /YOUR/PATH/OUTPUTDIR/ \
  --learning_rate 2e-5 \
  --fp16 \
  --fp16_backend amp \
  --overwrite_cache \
  --overwrite_output_dir

```
