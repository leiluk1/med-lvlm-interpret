# Medical LVLM-Interpret: An interpretability tool for medical VLM

This repository provides the implementation for LVLM-Interpret tool specifically adapted for use with the LLaVA model's medical version - LLaVA-Med.

## Project structure

- `notebooks/demo_llava_med.ipynb` — Main notebook for running the interpretability experiment.
- `LLaVA-Med/` — LLaVA-Med model submodule.
- `lvlm-interpret/` — LVLM-Interpret supporting components.

## Set up for the interpretability part

1.  Clone this repository and navigate to `lvlm-interpret` folder.
2. Install packages. Create conda environment:
```
    cd lvlm-interpret
    conda create -n med-llava-lvlm python=3.10 -y
    conda activate med-llava-lvlm
    git submodule update --init --recursive
    pip install -r requirements.txt
```
4.  Navigate to `LLaVA-Med` folder and install the following packages:
```
    cd LLaVA-Med
    pip install -e .
    pip uninstall bitsandbytes
    pip uninstall bitsandbytes-windows 
    pip install evaluate peft==0.10.0 radgraph timm==1.0.13 flash_attn==2.3.4 deepspeed==0.14.5 transformers==4.37.0 numpy==1.23.5
    pip install accelerate --upgrade
```

### Fixing bugs

1. Update some libraries if needed:
```
    pip install transformers --upgrade
    apt-get install build-essential
    conda install -c nvidia cuda-compiler
    pip install pydantic -U
```

2. For LLaVA-Med part: Add `cache_position=None` to `forward()` method in `LlavaMistralForCausalLM`. Path: `LLaVA-Med/llava/model/language_model/llava_mistral.py`.

3. For LLaVA-Med part: `conv_mistral_instruct` change to `sep="<s>"`.


## Related projects

- [LVLM-Interpret](https://github.com/IntelLabs/lvlm-interpret)

- [LLaVA-Med](https://github.com/microsoft/LLaVA-Med)
