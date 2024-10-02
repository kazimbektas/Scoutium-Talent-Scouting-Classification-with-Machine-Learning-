<p align="center">
  <a href="https://github.com/kazimbektas">
    <img src="https://i.redd.it/the-8-0-beta-is-here-player-detailed-tactic-positions-gk-lb-v0-hun98s4gl65b1.png?width=1917&format=png&auto=webp&s=3235ed78e739f0113b428154e99aa9b105285943"/>
  </a>
</p>

# Scoutium Talent Scouting Classification with Machine Learning

## 1. Introduction

In the world of professional football, scouting plays a critical role in identifying talent and evaluating player potential. Scoutium, a platform used by scouts, provides detailed player evaluations based on various attributes. This project aims to develop a machine learning model that predicts a player's class (either "average" or "highlighted") based on the ratings given by scouts.

### 1.1 Business Problem
The main objective of this project is to predict the class of football players (either "average" or "highlighted") based on the ratings given by scouts to various player attributes. This prediction can help clubs and scouts focus their attention on players with the most potential for success.

### 1.2 Dataset Story
The dataset contains information about the ratings given by scouts to players during matches. These ratings assess a wide range of player attributes, and the dataset includes the scouts' final decisions on each player, marking them as either "average" or "highlighted."

#### scoutium_attributes.csv (Independent Variables):
- **task_response_id**: The set of evaluations by a scout for all players in a team's lineup in a match.
- **match_id**: The ID of the respective match.
- **evaluator_id**: The ID of the evaluator (scout).
- **player_id**: The ID of the respective player.
- **position_id**: The ID of the position the respective player played in that match.
  - 1: Goalkeeper
  - 2: Center-back
  - 3: Right-back
  - 4: Left-back
  - 5: Defensive midfielder
  - 6: Central midfielder
  - 7: Right winger
  - 8: Left winger
  - 9: Attacking midfielder
  - 10: Forward
- **analysis_id**: The set of attribute evaluations by a scout for a player in a match.
- **attribute_id**: The ID of each attribute that players are evaluated on.
- **attribute_value**: The value (rating) given by a scout to a player's attribute.

#### scoutium_potential_labels.csv (Target Variable):
- **task_response_id**: The set of evaluations by a scout for all players in a team's lineup in a match.
- **match_id**: The ID of the respective match.
- **evaluator_id**: The ID of the evaluator (scout).
- **player_id**: The ID of the respective player.
- **potential_label**: The label indicating a scout's final decision about a player in a match. (The target variable indicating whether a player is "average" or "highlighted.")

## 2. Project Steps

1. **Data Loading**:
   - Load the `scoutium_attributes.csv` and `scoutium_potential_labels.csv` files.
   
2. **Data Merging**:
   - Merge the two datasets using the variables: `task_response_id`, `match_id`, `evaluator_id`, and `player_id`.

3. **Data Cleaning**:
   - Remove the "Goalkeeper" position (position_id = 1) from the dataset.
   - Remove the "below_average" class from the potential_label column (since it constitutes only 1% of the dataset).

4. **Data Transformation**:
   - Create a pivot table where each row represents a player.
   - Include columns for the player's `position_id`, `potential_label`, and their respective `attribute_id` values.
   - Use the `reset_index` function to ensure no index errors and convert `attribute_id` column names to strings.

5. **Encoding Labels**:
   - Encode the "potential_label" column (average, highlighted) into numerical form using the Label Encoder function.

6. **Feature Scaling**:
   - Save the numerical variable columns into a list called `num_cols`.
   - Apply `StandardScaler` to scale the data in the numerical columns.

7. **Model Development**:
   - Develop a machine learning model to predict the potential labels of players with minimum error.
   - Models used:
     - **Logistic Regression**
     - **K-Nearest Neighbors (KNN)**
     - **Decision Tree Classifier**
     - **Random Forest Classifier**
     - **Gradient Boosting Classifier**
     - **Adaboost**
     - **SVC**
     - **XGBoost**
     - **LightGBM**

8. **Feature Importance**:
   - Use the `feature_importance` function to plot the importance of each feature, helping identify which attributes are most significant in predicting player potential.

## 3. Objective
The project aims to predict player classes (either "average" or "highlighted") based on scout ratings using machine learning models. By comparing the performance of several algorithms, the best-performing model will be selected for this task. Additionally, feature importance analysis will help identify the most critical player attributes for evaluation.
