# RecSys Challenge 2024
The Ekstra Bladet RecSys Challenge aims to predict which article a user will click on from a list of articles that were seen during a specific impression. Utilizing the user's click history, session details (like time and device used), and personal metadata (including gender and age), along with a list of candidate news articles listed in an impression log, the challenge's objective is to rank the candidate articles based on the user's personal preferences. This involves developing models that encapsulate both the users and the articles through their content and the users' interests. The models are to estimate the likelihood of a user clicking on each article by evaluating the compatibility between the article's content and the user's preferences. The articles are ranked based on these likelihood scores, and the precision of these rankings is measured against the actual selections made by users. 

This repository contains the implementation, configuration, and experiments for the 2024 Recsys Challenge. It includes datasets, model configurations, scripts, and documentation to facilitate reproducibility and understanding. Reproducing the steps in this repository achieves a ~top 50 placement on the leaderboard (AUC ~0.72).

---

## Repository Structure

This repository contains the following directories and files:

```plaintext

├── notebooks/                              # Jupyter notebooks for exploratory data analysis (EDA) / modeling
    ├── 2024_Recsys_Challenge_EDA/          # Jupyter notebook for EDA
    ├── 2024_Recsys_Challenge_Modeling/     # Jupyter notebook for Modeling
|── requirements.txt                        # Dependencies required for the project
├── README.md                               # Overview of the repository (this file)
├── fuxcitr_dir/                            # Configurable, tunable, and preoducible library for CTR prediction
    ├── config/                             # Configuration files for the project
    ├── data/                               # Datasets used in the project
       ├── train/                           # Training set
       ├── validation/                      # Validation set
       ├── testing/                         # Testing set
       ├── processed/                       # Cleaned and processed datasets
       |── prepare_data_v1.py               # Data preprocessing. (V1 - smaller subset of data)
       |── prepare_data_v2.py               # Data preprocessing. (V2 - larger subset of data)
    └── LICENSE                             # Licensing information for the repository
    ├── exp_results/                        # Output of experiments (e.g., metrics, plots)
    ├── src/                                # ML model (DIN)
       ├── din.py                           # Deep Interest Network model
       ├── dcn.py                           # Deep Cross Network model
       
├── run_expid.py                            # Logs the experiment run
├── run_param_tuner.py                      # Extracts the model and data configs and trains and validates the model
├── submit.py                               # Makes predictions on the testing set
```

---

## Getting Started

Follow these steps to set up the project:

1. **Clone the Repository**
   ```bash
   git clone https://github.com/SulmanK/2024-Recsys-Challenge.git
   cd 2024-Recsys-Challenge
   ```

2. **Set Up the Environment**
   Ensure you have Python 3.11 installed. Create and activate a virtual environment:
   ```bash
   python -m venv venv
   source venv/bin/activate  # On Windows, use `venv\Scripts\activate`
   ```

3. **Install Dependencies**
   Install the required Python libraries:
   ```bash
   pip install -r requirements.txt
   ```
4. **Create environmental variables**
   Setup a path to the FUXICTR library
   ```
   FUICR_DIR="~\\2024 Recsys Challenge\\venv\\Lib\\site-packages"
   ```

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

## License

This project is licensed under the terms of the MIT License. See the `LICENSE` file for details.

