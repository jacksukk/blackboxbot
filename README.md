# Blackbox
This is the official implementation of the paper [Learning to Generate Prompts for Dialogue Generation through Reinforcement Learning
](https://arxiv.org/abs/2206.03931)
## Installation
1. Conda: ```conda create --name <env> --file environment.yml```


## Train Models
### Pretrain
1. Word
```
    python main.py \
            --task None \
            --mode pretrain \
            --prompt DialogGPT \
            --bot blenderbot \
            --type word \
            --exp_name test \
            --save_path test \
            --model microsoft/DialoGPT-medium \
            --log_interval 25 \
            --seed 100 \
            --bz 8 \
            --k_epoch 5 \
            --discount_r 0.99 \
            --end_batch 500 \
            --sample_time 8 \
            --max_pt_len 10 \
            --init_step 0 \
            --tags finetune \
            --save_interval 50
            --extra_label test_word_list.txt

```
2. Emotion
```
    python main.py \
            --task None \
            --mode pretrain \
            --prompt DialogGPT \
            --bot blenderbot \
            --type word \
            --exp_name test \
            --save_path test \
            --model microsoft/DialoGPT-medium \
            --log_interval 25 \
            --seed 100 \
            --bz 8 \
            --k_epoch 5 \
            --discount_r 0.99 \
            --end_batch 500 \
            --sample_time 8 \
            --max_pt_len 10 \
            --init_step 0 \
            --tags finetune \
            --save_interval 50
```

### Finetune
1. Word
```
    python main.py \
            --task [Please refer to test_word_list] \
            --mode finetune \
            --prompt DialogGPT \
            --bot blenderbot \
            --type word \
            --exp_name test \
            --save_path test \
            --model microsoft/DialoGPT-medium \
            --log_interval 25 \
            --seed 100 \
            --bz 8 \
            --k_epoch 5 \
            --discount_r 0.99 \
            --end_batch 500 \
            --sample_time 8 \
            --max_pt_len 10 \
            --init_step 0 \
            --tags finetune \
            --save_interval 50
            --extra_label test_word_list.txt

```
2. Emotion
```
    python main.py \
            --task [annoyance/pride/joy/sadness/approval/confusion] \
            --mode finetune \
            --prompt DialogGPT \
            --bot blenderbot \
            --type word \
            --exp_name test \
            --save_path test \
            --model microsoft/DialoGPT-medium \
            --log_interval 25 \
            --seed 100 \
            --bz 8 \
            --k_epoch 5 \
            --discount_r 0.99 \
            --end_batch 500 \
            --sample_time 8 \
            --max_pt_len 10 \
            --init_step 0 \
            --tags finetune \
            --save_interval 50
```

## Test
1. Word
```
CUDA_VISIBLE_DEVICES=0 python main.py \
                       --task [Please refer to test_word_list] \
                       --mode test \
                       --prompt DialogGPT \
                       --bot blenderbot \
                       --type word \
                       --exp_name test \
                       --save_path test \
                       --model microsoft/DialoGPT-medium \
                       --log_interval 25 \
                       --seed 100 \
                       --bz 8 \
                       --k_epoch 5 \
                       --discount_r 0.99 \
                       --end_batch 500 \
                       --sample_time 8 \
                       --max_pt_len 10 \
                       --init_step 0 \
                       --tags finetune \
                       --save_interval 50
                       --extra_label test_word_list.txt
```
2. Emotion
```
CUDA_VISIBLE_DEVICES=0 python main.py \
                       --task  [annoyance/pride/joy/sadness/approval/confusion] \
                       --mode test \
                       --prompt DialogGPT \
                       --bot blenderbot \
                       --type emotion \
                       --exp_name test \
                       --save_path test \
                       --model microsoft/DialoGPT-medium \
                       --log_interval 25 \
                       --seed 100 \
                       --bz 8 \
                       --k_epoch 5 \
                       --discount_r 0.99 \
                       --end_batch 500 \
                       --sample_time 8 \
                       --max_pt_len 10 \
                       --init_step 0 \
                       --tags finetune \
                       --save_interval 50
```
