## RecSys2024_CTR_Challenge

The RecSys 2024 Challenge: https://www.recsyschallenge.com/2024/

The Ekstra Bladet RecSys Challenge aims to predict which article a user will click on from a list of articles that were seen during a specific impression. Utilizing the user's click history, session details (like time and device used), and personal metadata (including gender and age), along with a list of candidate news articles listed in an impression log, the challenge's objective is to rank the candidate articles based on the user's personal preferences. 

This baseline is built on top of [FuxiCTR](https://github.com/reczoo/FuxiCTR), a configurable, tunable, and reproducible library for CTR prediction. The library has been selected among [the list of recommended evaluation frameworks](https://github.com/ACMRecSys/recsys-evaluation-frameworks) by the ACM RecSys Conference. By using FuxiCTR, we develop a simple yet strong baseline (AUC: 0.7154) without heavy tuning. We open source the code to help beginers get familar with FuxiCTR and quickly get started on this task.

🔥 If you find our code helpful in your competition, please cite the following paper:

+ Jieming Zhu, Jinyang Liu, Shuai Yang, Qi Zhang, Xiuqiang He. [Open Benchmarking for Click-Through Rate Prediction](https://arxiv.org/abs/2009.05794). *The 30th ACM International Conference on Information and Knowledge Management (CIKM)*, 2021.

This repository was adapted from the [Github Repo](https://github.com/reczoo/RecSys2024_CTR_Challenge). This was given as the baseline for the competition.
---

## Usage

1. Download the datasets at: https://recsys.eb.dk/#dataset

2. Unzip the data files to the following

    ```bash
    cd ~/2024-Recsys-Challenge/fuxcitr_dir/data/
    .
    ./train
    ./train/history.parquet
    ./train/articles.parquet
    ./train/behaviors.parquet
    ./validation
    ./validation/history.parquet
    ./validation/behaviors.parquet
    ./test
    ./test/history.parquet
    ./test/articles.parquet
    ./test/behaviors.parquet
    ./image_embeddings.parquet
    ./contrastive_vector.parquet
    ./prepare_data_v1.py
    ./prepare_data_v2.py
    ```

3. Convert the data to csv format

    ```bash
    cd ~/2024-Recsys-Challenge/fuxcitr_dir/data/
    python prepare_data_v1.py
    ```
4. Model training
    ```bash
    python run_param_tuner.py --config config/DIN_ebnerd_large_x1_tuner_config_01.yaml --gpu 0
    ```
5. Predictions
    ```bash
    python submit.py --config config/DIN_ebnerd_large_x1_tuner_config_01 --expid DIN_ebnerd_large_x1_001_1860e41e --gpu 1
    ```

---


