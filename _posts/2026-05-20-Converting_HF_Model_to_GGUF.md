---
layout: post
comments: true
title:  "Converting Any hugging face Model to GGuf Format"
excerpt: "In this post we will learn how we can convert any hugging face model to the gguf format, that we can use to get the optimization speed of the ggml lib."
date:   2026-05-20 20:00:00
---


> This post is among the first where we learn how we can convert any hugging face model to the gguf format. Coming in the future we will learn how ggml library make inference this fast, will write code for some model to do inference on that, Now for this post: 


<!-- ## What is gguf format -->


# How to Change any Hugging Face model to gguf format.

### First download the model from hugging face: 
Use the Below script for downloading the model, choosing the `model_name` and `model_save_path` where to save that.

```python
from huggingface_hub import snapshot_download

model_name = "Qwen/Qwen3-0.6B"
model_save_path = "qwen-hf"

snapshot_download(repo_id=model_id, local_dir=model_save_path,local_dir_use_symlinks=False, revision="main")

```

Before running the above script make sure you have huggingface_hub installed. You can use this to install it.
`pip install huggingface_hub`.

Now After running the script you will have model downloaded now to convert it to gguf format we will use llama.cpp git repo.
<!-- explain what is llama.cpp lib -->
```python
# Clone llama.cpp lib:
git clone https://github.com/ggml-org/llama.cpp.git

# Install all the dependencies:
pip install -r llama.cpp/requirements.txt
```

Now to convert the model to gguf use this: 
```bash
python llama.cpp/convert_hf_to_gguf.py qwen-hf --outfile qwen-hf.gguf
```
Above I have used the saved model path as qwen-hf, and output file name as qwen-hf.gguf. To use more of suck arguments related to your use case, like quantization, or many more use this to get all the arguments one can use: 
```bash
python llama.cpp/convert_hf_to_gguf.py -h
```

You will get the model now, as qwen-hf.gguf. you can also push that to hugging face. More blogs about ggml lib will come soon.

[git-hub]: https://github.com

