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

