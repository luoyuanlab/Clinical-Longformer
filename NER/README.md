We used i2b2 as an example to illustrate how Clinical-Longformer can be applied to NER tasks.
1. Download i2b2 2006, 2010, 2012, 2014 dataset at: https://portal.dbmi.hms.harvard.edu/projects/n2c2-nlp/. N2C2 access should be requested.
2. Pre-process i2b2 and formulate the dataset to .json format. We used this [repo](https://github.com/EmilyAlsentzer/clinicalBERT/tree/master/downstream_tasks/i2b2_preprocessing). Please also cite there NAACL paper, if you think it is useful.
3. On running the previous 2 steps, you shall have such directory structure
```
i2b2  
|
└───I2B2_2006
│   │   train.json
│   │   test.json
│   │   dev.json
└───I2B2_2006
│   │   train.json
│   │   test.json
│   │   dev.json
└───I2B2_2006
│   │   train.json
│   │   test.json
│   │   dev.json
└───I2B2_2006
│   │   train.json
│   │   test.json
│   │   dev.json
``` 
