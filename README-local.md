## Local test

reference url:[https://huggingface.co/lerobot/act_aloha_sim_transfer_cube_human](https://huggingface.co/lerobot/act_aloha_sim_transfer_cube_human)


### download model
```shell
GIT_LFS_SKIP_SMUDGE=1 git clone https://huggingface.co/lerobot/act_aloha_sim_transfer_cube_human lerobot/act_aloha_sim_transfer_cube_human 
```


### train
```shell
HYDRA_FULL_ERROR=1 \
python lerobot/scripts/train.py \
hydra.job.name=act_aloha_sim_transfer_cube_human \
hydra.run.dir=outputs/train/act_aloha_sim_transfer_cube_human \
policy=act \
policy.use_vae=true \
env=aloha \
env.task=AlohaTransferCube-v0 \
dataset_repo_id=lerobot/aloha_sim_transfer_cube_human \
training.eval_freq=10000 \
training.log_freq=250 \
training.offline_steps=100000 \
+training.save_model=true \
training.save_freq=25000 \
eval.n_episodes=50 \
eval.batch_size=50 \
wandb.enable=true \
device=cuda
```

## eval
```shell
python lerobot/scripts/eval.py \
-p outputs/train/act_aloha_sim_transfer_cube_human/checkpoints/100000/pretrained_model \
eval.n_episodes=4 \
eval.batch_size=4 \
env.episode_length=300 \
device=cuda
```


## demo run
```shell
python lerobot/scripts/visualize_dataset.py \
--repo-id lerobot/pusht \
--episode-index 0 \
--save 1 \
--output-dir .cache/result
```

## image
![image](https://github.com/Samge0/lerobot/assets/17336101/a1c44a5e-c28d-453a-8d8d-f636e56e4bdf)
![image](https://github.com/Samge0/lerobot/assets/17336101/d74d5892-14d3-4547-a985-25f630352707)


## log
[wandb log 20240621](https://wandb.ai/samge/lerobot/runs/jhy9hmpq/logs?nw=nwusersamge)
step_10000_eval (84%):

success:


https://github.com/Samge0/lerobot/assets/17336101/52d300d6-5311-4367-94c3-d88b597d62c5



https://github.com/Samge0/lerobot/assets/17336101/f45882ce-e40b-4b12-8313-4d25f06ac81c



https://github.com/Samge0/lerobot/assets/17336101/27e9db6c-0ca1-4e71-8c5d-ae7ec314fa7c


fail:


https://github.com/Samge0/lerobot/assets/17336101/80f751a7-2570-4b9c-a1c0-737c34d15522