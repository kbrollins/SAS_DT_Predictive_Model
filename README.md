# SAS_DT_Predictive_Model
Predictive modeling with Decision Trees using various options for growing and pruning

This SAS program creates a predictive decision tree model for binary classification of life expectancy as "short" or "long" using data on age at death, age at CHD diagnosis, diastolic blood pressure, systolic blood pressure, smoking status, cholesterol level, and MRW (metabolic risk weight).

The program begins by creating a temporary dataset called WORK.HEART_DEAD_LIFEXP_TEMP from the input dataset WORK.HEART_DEAD. It calculates the life expectancy for each observation by subtracting the age at CHD diagnosis from the age at death, if the age at CHD diagnosis is not missing. If the age at CHD diagnosis is missing, the life expectancy is set to missing. Then, the program creates a filtered dataset called WORK.HEART_DEAD_LIFEXP_FILTER, excluding records with missing life expectancy.

Next, the program creates a new variable called cat_LifeExp, which categorizes life expectancy as "short" if it is less than 8.3 years, and "long" otherwise. The resulting dataset is named WORK.HEART_DEAD_LIFEXP.

The program then builds several decision tree models using the hpsplit procedure. Each model predicts cat_LifeExp using age at CHD diagnosis, diastolic blood pressure, systolic blood pressure, smoking status, cholesterol level, and MRW as predictor variables. The first model (v1) uses the default values for the grow and prune options and entropy as the splitting criterion. The second model (v2) has a maximum tree depth of 4. The third model (v3) uses CHAID as the splitting criterion and allows a maximum of 2 branches per node. The fourth model (v4) uses the fastCHAID splitting criterion and a maximum tree depth of 4. The fifth model (v5) uses CHI-SQUARE as the splitting criterion and a maximum tree depth of 4.

All models are partitioned using 20% of the data for validation and saved as rules files. The resulting decision trees can be used to predict whether an individual has a "short" or "long" life expectancy based on their age at CHD diagnosis, blood pressure, smoking status, cholesterol level, and MRW.

The third model (v3) seems to be the most reliable, as it minimizes the difference in sensitivity/specificity of the predictive metrics.
