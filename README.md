# Flight Arrival Delay Prediction

## Dependencies

Use Google Colab with Google Drive mounted. Required packages: pandas, NumPy, scikit-learn, kagglehub, pyarrow, matplotlib, and seaborn.

## Data access

`setup.ipynb` downloads [US Flight Delays 2025 - BTS On-Time Performance](https://www.kaggle.com/datasets/a7madmostafa/us-flight-delays-2025-bts-on-time-performance) from Kaggle. Data are stored in `/content/drive/MyDrive/ML Final` and are not included in this repository. If using the shared folder, add its shortcut to My Drive. Otherwise, update the folder paths in both notebooks.

## Run order

1. Run `setup.ipynb` from top to bottom to download and process the data.
2. Open `Experiments.ipynb` and run the first code cell to mount Drive and load the processed files.
3. Run the monthly split, dummy baseline, and logistic regression cells below the monthly-split note, in that order. The earlier experiment cells contain the original split results.

## Baseline results

Monthly split: 70% training, 15% validation, and 15% testing, with seed 42. Results below use 1,031,921 validation flights. Logistic regression trains on 300,000 flights and uses threshold 0.5. Precision, recall, and F1 refer to delayed flights.

| Model | Accuracy | Precision | Recall | F1 |
| --- | ---: | ---: | ---: | ---: |
| Majority | 0.7769 | 0.0000 | 0.0000 | 0.0000 |
| Stratified random | 0.6532 | 0.2229 | 0.2231 | 0.2230 |
| Logistic regression | 0.7776 | 0.5286 | 0.0278 | 0.0529 |
