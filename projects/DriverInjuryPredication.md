# Crash Severity Prediction Project

## Project Overview

The goal of the project is to predict whether a crash involves a suspected serious injury using combined U.S. crash datasets from 2019 to 2021.

The work combines domain research, data integration, preprocessing, feature engineering, class balancing, and model comparison. The final task is a binary classification problem where the target indicates whether a serious injury occurred.

## Problem Statement

Predict suspected serious injury outcomes in traffic crashes using structured crash, vehicle, occupant, and distraction-related data.

### Target
- `MAXSEV_IM`
- Binary outcome:
  - `1` = suspected serious injury
  - `0` = non-serious injury

### Why this matters
A usable prediction model can help identify high-risk crash conditions and surface the factors most associated with severe outcomes. That can support road safety analysis, policy decisions, and preventive interventions.

## Domain Motivation

Two strands of prior research motivated the project:

1. Vehicle damage severity is related to occupant injury severity, but injury outcomes are also shaped by broader crash context and human factors.
2. Vehicle-only crash severity metrics are not enough on their own to explain serious injuries, especially when restraint use, crash pulse, and occupant-level factors are ignored.

Because of that, the project extends the provided accident data with additional datasets that capture driver, vehicle, and occupant information before and during the crash.

## Data Sources

The project combines crash data from 2019, 2020, and 2021.

### Core datasets used
- Accident
- Vehicle
- Distract
- Person

### Combined tables created
- `accident_combined`
- `vehicle_combined`
- `distract_combined`
- `person_combined`

### Added data value
These tables contribute features such as:
- vehicle body type
- initial contact point / area of impact
- driver alcohol involvement
- hit-and-run status
- number injured in vehicle
- maximum injury severity in vehicle
- occupant age and sex
- distraction-related variables
- restraint and airbag-related information
- vehicle model year / vehicle age

## Data Understanding and Preprocessing

## Schema consistency across years

The yearly tables were not fully consistent across 2019–2021:
- accident columns changed across years
- vehicle columns increased slightly after 2019
- person columns increased after 2019
- distract kept the same structure overall, but some column names changed

### Key preprocessing decisions
- removed accident columns that only existed in 2019 and would create large null-heavy fields after merging
- removed certain columns that appeared only in 2020/2021 but added limited value to the predictive task
- standardized naming inconsistencies across years
- merged same-type yearly files into single combined tables
- reviewed metadata / user guides to understand discontinued and newly introduced variables

## Data preparation choices

Before modeling, the data was prepared as follows:
- handled missing values with reference to CRSS metadata
- converted coded numeric fields into clearer categorical labels where appropriate
- treated categorical and interval variables differently
- binned selected variables such as age / time-related information when useful
- built a modeling table centered on the target variable `MAXSEV_IM`

### Example feature groups highlighted in the report
- time-related variables
- restraint use
- vehicle deformation / damage
- alcohol involvement
- manner of collision
- number of injuries in vehicle
- airbag information
- vehicle age

## Modeling Strategy

## Candidate models reviewed
The report discusses several common classifiers for binary prediction:
- Logistic Regression
- Support Vector Machines
- Random Forest
- Decision Tree
- Neural Networks
- Gradient Boosting Machines

## Final models tested
The project focused on these three:
- Random Forest Classifier
- Decision Tree Classifier
- Logistic Regression

### Why these three
- suitable for binary classification
- practical for mixed structured data
- interpretable enough for feature-level discussion
- easy to compare under the same preprocessing pipeline

## Evaluation Metrics

The report reviews several evaluation metrics and ultimately emphasizes:

- Accuracy
- Precision
- Recall
- F1 Score
- ROC / AUC
- Confusion Matrix

### Main evaluation priority
Because the project is more concerned with correctly identifying serious injuries, recall for the minority class is especially important.  
Accuracy alone is not sufficient because the original dataset is imbalanced.

## Class Imbalance Handling

The original class distribution was highly imbalanced.

### Before resampling
- approximately `21 / 79`

### Resampling approach
- stratified downsampling
- event level retained at 100%
- majority class sampled down to 50%

### Data partition
- Training: 60%
- Validation: 20%
- Test: 20%

This balancing step reduced headline accuracy but substantially improved sensitivity to serious injury cases.

## Model Results Summary

## 1. Random Forest

### Non-sampled
- Accuracy: `79.8%`
- Recall: `0.0475`
- Precision: `0.73`
- F1: `0.0891`

### Down-sampled
- Accuracy: `66.4%`
- Recall: `0.65`
- Precision: `0.67`
- F1: `0.65`

### Tuning note
The number of trees was increased and compared across runs. Performance gains became marginal after larger tree counts, and the selected final version used `600` trees.

## 2. Decision Tree

### Non-sampled
- Accuracy: `80.0%`
- Recall: `0.044`
- Precision: `0.60`
- F1: `0.081`

### Down-sampled
- Accuracy: `65.5%`
- Recall: `0.64`
- Precision: `0.66`
- F1: `0.65`

### Tuning note
Different splitting criteria were compared. The final selected version used the entropy-based criterion.

## 3. Logistic Regression

### One-hot encoded, non-sampled
- Accuracy: `80.0%`
- Recall: `0.14`
- Precision: `0.59`
- F1: `0.23`

### One-hot encoded, down-sampled
- Accuracy: `67.4%`
- Recall: `0.65`
- Precision: `0.67`
- F1: `0.66`

### Label-encoded, non-sampled
- Accuracy: `80.1%`
- Recall: `0.14`
- Precision: `0.61`
- F1: `0.23`

### Label-encoded, down-sampled
- Accuracy: `66.0%`
- Recall: `0.64`
- Precision: `0.66`
- F1: `0.65`

### Tuning note
The report concludes that the one-hot encoded version performed slightly better than the label-encoded version.

## Champion Model

The report identifies **Random Forest** as the best overall model.

### Why it was chosen
- strongest overall ROC behavior among the tested models
- balanced precision and recall after downsampling
- competitive overall accuracy
- better performance on the serious-injury class than the non-sampled alternatives

## Interpretation

The report highlights several variables as especially important for predicting suspected serious injury:

- `DEFORMED`
- `REST_USE`
- `MANCOL_IM`
- `NO_INJ_IM`
- `AIR_BAG`
- `V_ALCH_IM`

These results suggest that injury severity is strongly associated with crash impact severity, restraint use, collision type, occupant injury context, airbag-related conditions, and alcohol involvement.

## Recommendations

## For drivers
- always use seat belts properly
- choose vehicles with functioning airbags
- never drive after drinking or taking impairing substances
- stay cautious about road conditions throughout the day
- be extra careful with older vehicles

## For car makers
- improve vehicle robustness
- include and maintain strong safety systems
- develop intelligent driving systems that detect and reduce crash risks

## For authorities
- strengthen enforcement against drunk and dangerous driving
- improve public education on safe driving and emergency response

## Limitations

- the original dataset was highly imbalanced
- downsampling improved recall but may have introduced bias
- the available structured data still misses some potentially useful context
- limited temporal and geo-spatial feature engineering was performed
- only a small set of classification models was explored in depth

## Future Improvements

If the project were extended, the report suggests:
- testing boosting or stacking methods
- trying SMOTE or other resampling techniques
- adding finer temporal features such as rush-hour patterns
- incorporating geo-spatial features
- integrating real-time traffic or camera data
- adding post-accident medical outcome data
- using NLP on police / insurance narrative text
- expanding stakeholder consultation to identify higher-value variables

## Deliverable Summary

This project shows that:
- crash severity prediction is feasible with structured crash data
- class balancing is essential when severe injury cases are rare
- Random Forest performs best among the three final tested models
- the most important predictors align well with domain expectations around restraint use, impact severity, airbags, collision type, and alcohol involvement
