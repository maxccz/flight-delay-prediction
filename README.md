# Flight Arrival Delay Prediction

## Dependencies

Use Google Colab with Google Drive mounted. Install the packages in a Colab code cell:

```python
%pip install scikit-learn==1.6.1 pandas==2.2.3 numpy==2.4.6 kagglehub pyarrow matplotlib seaborn
```

The three pinned versions were verified in the November 10 baseline runtime.

## Data access

`setup.ipynb` downloads [US Flight Delays 2025 - BTS On-Time Performance](https://www.kaggle.com/datasets/a7madmostafa/us-flight-delays-2025-bts-on-time-performance) from Kaggle and saves files under `/content/drive/MyDrive/ML Final` in your own Google Drive. The final setup cell saves `train_monthly.parquet`, `validation_monthly.parquet`, and `test_monthly.parquet` in the `processed` folder. You do not need access to the team's shared folder. Data are not included in this repository. If you change the folder location, update the paths in both notebooks.

## Run order

1. Download `setup.ipynb` and `Experiments.ipynb` from this repository and open them in Google Colab.
2. Install the dependencies above, then run `setup.ipynb` from top to bottom to download and process the data. Authorize your own Drive mount when prompted.
3. In the `Experiments.ipynb` runtime, install the same dependencies. Run the cell beginning `# Load the monthly partitions saved by setup.ipynb.` to mount Drive and load the three saved partitions. Run setup's final cell first so these files exist.
4. Run the dummy baseline and logistic regression cells immediately below it, in that order. The earlier experiment cells contain the original split results and can be skipped.

## Baseline results

Monthly split: 70% training, 15% validation, and 15% testing, with seed 42. Results below use 1,031,921 validation flights. Logistic regression trains on 300,000 flights and uses threshold 0.5. Precision, recall, and F1 refer to delayed flights.

| Model | Accuracy | Precision | Recall | F1 |
| --- | ---: | ---: | ---: | ---: |
| Majority | 0.7769 | 0.0000 | 0.0000 | 0.0000 |
| Stratified random | 0.6532 | 0.2229 | 0.2231 | 0.2230 |
| Logistic regression | 0.7776 | 0.5286 | 0.0278 | 0.0529 |
