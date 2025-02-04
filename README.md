
### Step 1. Construct Preference Data. 
First, prepare the COCO-2014 train images in the **'./data/images/'**. Then complete the following steps in sequence.
```Shell
cd ./CSR/inference_csr
bash ./step1.sh
```
```Shell
bash ./step2.sh
```
```Shell
bash ./step3.sh
```
You now have the preference dataset.
This process takes a long time. We provide our preference datasets in huggingface.

### Step 2. Direct Preference Optimization (DPO). 

```Shell
bash ./CSR/scripts/run_train.sh
```

### Step 3. Iterative Learning. 
After completing a round of CSR training, you need to merge the current LoRA checkpoint. Use the merged checkpoint as the base model and proceed with **Step 1** and **Step 2** sequentially.

```Shell
python ./scripts/merge_lora_weights.py --model-path "your LoRA checkpoint path" --model-base "your llava 1.5 checkpoint path --> your Iter-1 path --> your Iter-2 path ...." --save-model-path "xxx"
```
