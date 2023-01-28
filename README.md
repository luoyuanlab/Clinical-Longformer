# Clinical-Longformer

<span style="font-size:larger;">**Clinical-Longformer**</span> is a clinical knowledge enriched version of Longformer that was further pre-trained using MIMIC-III clinical notes. It allows up to 4,096 tokens as the model input. Clinical-Longformer consistently out-performs ClinicalBERT across 10 baseline dataset for at least 2 percent. Those downstream experiments broadly cover named entity recognition (NER), question answering (QA), natural language inference (NLI) and text classification tasks. For more details, please refer to [our paper](https://academic.oup.com/jamia/article/30/2/340/6855145).

### Pre-training
We initialized Clinical-Longformer from the pre-trained weights of the base version of Longformer. The pre-training process was distributed in parallel to 6 32GB Tesla V100 GPUs. FP16 precision was enabled to accelerate training. We pre-trained Clinical-Longformer for 200,000 steps with batch size of 6×3. The learning rates were 3e-5 for both models. The entire pre-training process took more than 2 weeks. 

### Usage
You can load the model directly from HuggingFace Transformers:
```
# !pip install transformers
from transformers import AutoTokenizer, AutoModelForMaskedLM
tokenizer = AutoTokenizer.from_pretrained("yikuan8/Clinical-Longformer")
model = AutoModelForMaskedLM.from_pretrained("yikuan8/Clinical-Longformer")
```
[Here](https://huggingface.co/yikuan8/Clinical-Longformer) is the homepage of our model on HuggingFace model hub.
We also provide the usage examples of [classification](https://github.com/luoyuanlab/Clinical-Longformer/tree/main/classification), [named entity recognition](https://github.com/luoyuanlab/Clinical-Longformer/tree/main/NER) and [question answering](https://github.com/luoyuanlab/Clinical-Longformer/tree/main/Question%20Answering) tasks.

### Citing
If you find our implementation helps, please consider citing this :)
```
@article{li2023comparative,
  title={A comparative study of pretrained language models for long clinical text},
  author={Li, Yikuan and Wehbe, Ramsey M and Ahmad, Faraz S and Wang, Hanyin and Luo, Yuan},
  journal={Journal of the American Medical Informatics Association},
  volume={30},
  number={2},
  pages={340--347},
  year={2023},
  publisher={Oxford University Press}
}
```

### Questions
Please email yikuanli2018@u.northwestern.edu (Yikuan) or raise a issue.



