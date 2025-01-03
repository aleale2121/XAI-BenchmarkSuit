# BeXAI
This is a benchmark suite for selected explainable AI (XAI).
<p>The benchmark suite consists of Target machine learning models that are to be explained. These models are trained across text, image and tabular datasets. Two prominent model-agnostic, post-hoc local explainers are used to generate interpretations of predictions made by the target models: LIME(Local Interpretable Model-agnostic Explanation) and SHAP(SHapley Additive exPlanation). To evaluate the performance of these explainers, fidelity and monotonicity metrics are used. Fidelity measures how well the exlanations match with the model prediction. Monotonicity(consistency) is desirabe characterstic that feature importance based explainers like SHAP and LIME to have. Monotonicity checks if the explanation has this property </p>

## Installation
Install the required dependencies in ```requirement.txt``` using the following command
```
pip install -r requirements.txt
```

## Sample Usage
Use the following command to test the performance of SHAP and LIME explainers in interpreting three regression models: Linear Regression, Random Forest Regression and SVM Regression when trained on boston dataset.
```
python3 main.py --mode regression --dataset boston
```

or edit the script ```run.sh``` and run it as 
```
./run.sh
```

NB for ```regression``` mode the available dataset options are ```boston```, ```superconductivity``` and ```diabetes``` datasets. And for ```classification``` mode, the available dataset options are ```wine``` and ```breast_cancer```(for tabular dataset), ```image``` and ```text``` for image and text datasets resp. Passing different arguments will cause the application throw exceptions.

## Target Models

**Regression Models**:

- Linear Regression

- Random Forest Regression

- Support Vector Machine Regression


**Classification Models**:

- Logistic Regression

- Random Forest Classification

- Support Vector Machine Classification

- CNN Image Classification

- RNN Text Classification

## Datasets:

**Tabular Datasets**:

For Regression Task

- Boston Housing Dataset-available on Scikit Learn Library

- Superconductivity-available on UCI ML dataset repository [Superconductivty Data Data Set](https://archive.ics.uci.edu/ml/datasets/superconductivty+data)

- Diabetes Dataset- available on Scikit Learn Library

For Classification Task

- Wine Dataset-available on Scikit Learn Library

- Breast Cancer Dataset-available on Scikit Learn Library


**Image Dataset**:

- MNist handwritten digit dataset-available on Keras Library

**Text Dataset**:

- IMDB -available on Keras Library
## Explainers

**SHAP**: proposed by Lundberg et al, SHAP explainer uses coalition game theory to calculate the contributions of each feature to the prediction.

Paper: [Lundberg, Scott M., and Su-In Lee. “A unified approach to interpreting model predictions” Advances in Neural Information Processing Systems. 2017](https://arxiv.org/abs/1705.07874)

**LIME**:  creates explanation by building proxy linear model(like Linear reg and Decision tree) that approximates the target model around the instance of interest and assigning importance of features according to the coefficients of the proxy model 

Paper: [Ribeiro, Marco Tulio, Sameer Singh, and Carlos Guestrin. “Why should I trust you?: Explaining the predictions of any classifier.” Proceedings of the 22nd](https://arxiv.org/abs/1602.04938) 

## Evaluation metrics

**Fidelity**: is measured by first by removing each feature by replacing it with its mean value and get prediction for this instance. Then measure the correlation between its importance and the change in prediction.
 

**Monotonicity**: is measured by adding features in order of their importance then observe if the prediction value does not decrease with each introduction of features.

