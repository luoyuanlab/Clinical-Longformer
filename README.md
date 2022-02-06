# Clinical-Longformer

<span style="font-size:larger;">**Clinical-Longformer**</span> is a clinical knowledge enriched version of Longformer that was further pre-trained using MIMIC-III clinical notes. It allows up to 4,096 tokens as the model input. Clinical-Longformer consistently out-performs ClinicalBERT across 10 baseline dataset for at least 2 percent. Those downstream experiments broadly cover named entity recognition (NER), question answering (QA), natural language inference (NLI) and text classification tasks. For more details, please refer to [our paper](https://arxiv.org/pdf/2201.11838.pdf).

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

### Citing
If you find our implementation helps, please consider citing this :)
```
@article{li2022clinical,
  title={Clinical-Longformer and Clinical-BigBird: Transformers for long clinical sequences},
  author={Li, Yikuan and Wehbe, Ramsey M and Ahmad, Faraz S and Wang, Hanyin and Luo, Yuan},
  journal={arXiv preprint arXiv:2201.11838},
  year={2022}
}
```

### Questions
Please email yikuanli2018@u.northwestern.edu or raise a issue.



