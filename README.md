# RecSys Challenge 2024
The Ekstra Bladet RecSys Challenge aims to predict which article a user will click on from a list of articles that were seen during a specific impression. Utilizing the user's click history, session details (like time and device used), and personal metadata (including gender and age), along with a list of candidate news articles listed in an impression log, the challenge's objective is to rank the candidate articles based on the user's personal preferences. This involves developing models that encapsulate both the users and the articles through their content and the users' interests. The models are to estimate the likelihood of a user clicking on each article by evaluating the compatibility between the article's content and the user's preferences. The articles are ranked based on these likelihood scores, and the precision of these rankings is measured against the actual selections made by users. 

This repository contains the implementation, configuration, and experiments for the 2024 Recsys Challenge. It includes datasets, model configurations, scripts, and documentation to facilitate reproducibility and understanding.

---

## Repository Structure

This repository contains the following directories and files:

```plaintext
├── config/             # Configuration files for the project
├── data/               # Datasets used in the project
│   ├── raw/            # Raw datasets before preprocessing
│   ├── processed/      # Cleaned and processed datasets
├── docs/               # Documentation, including user guides and design notes
├── experiments/        # Scripts and notebooks for experimental runs
├── models/             # Saved models and checkpoints
├── notebooks/          # Jupyter notebooks for exploratory data analysis (EDA) / modeling
├── scripts/            # Python scripts for data preprocessing, training, etc.
├── tests/              # Unit and integration test scripts
├── results/            # Output of experiments (e.g., metrics, plots)
├── requirements.txt    # Dependencies required for the project
├── README.md           # Overview of the repository (this file)
└── LICENSE             # Licensing information for the repository
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

4. **Run Tests (Optional)**
   Validate the installation by running the tests:
   ```bash
   python -m unittest discover tests/
   ```

---

## Usage

- **Configuration**: Modify the YAML files in the `config/` directory to set up experiments.
- **Data**: Place raw datasets in the `data/raw/` directory. Processed datasets will be saved to `data/processed/`.
- **Training**: Use the provided scripts to train models. For example:
  ```bash
  python scripts/train_model.py --config config/DIN_ebnerd_large_x2.yaml
  ```
- **Evaluation**: Generate evaluation metrics by running:
  ```bash
  python scripts/evaluate_model.py --config config/DIN_ebnerd_large_x2.yaml
  ```

---

## License

This project is licensed under the terms of the MIT License. See the `LICENSE` file for details.

