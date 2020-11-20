<img class="fit-picture" 
     src="https://media-fastly.hackerearth.com/media/hackathon/hackerearth-machine-learning-challenge-predict-burnout-rate/images/8beab99412-Burnout_Cover_Image.png"  alt='Burnout_Cover_Image' style="width:100%">

<a href="https://www.hackerearth.com/challenges/competitive/hackerearth-machine-learning-challenge-predict-burnout-rate/">Link to Hackathon</a>
### Approach

My approach was simple. My final model consists of aweighted average of three models:gradientboost, catboost and lightgbm regressors.
Predictions were made using a 10-fold crossvalidation technique.

### Feature Engineering

1. I did an Exploratory data analysis of the training set. I discovered that three variables had some missing values. The target too. Because we can't use the missing values in the target for modelling, I dropped rows that were missing from the target variable.

2. The remaining variables with missing values- Mental Fatigure Score and Resource Allocation- were handled by filling in with their mean values.

3. The mean values were gotten by aggreagating them across designations and taking the mean, as there was a difference in these variables across designations.

4. From the date feature (Date of joining), I found that the dataset consists of employees employed in the same year (2008). To introduce variations in this variable, I calculated the total number of months an employee has stayed with the company, till present.

5. As a baseline, I used all the features provided to build a model. Four different models were built separately, consisting of a randomforest, gradientboost, catboost and lightgbm algorithms. The best was catboost, with ¬93% on the leaderboard.

6. No hyperparameter optimisation was made, the hyperparameters were set manually.

7. The top tree (3) features were Mental fatigue score, resources allocation and the designations.

8. I created further features which are combinations of designations and resource allocation and designations and home setup type. I dropped two variables- the company type and the months in service as they weren't important in burn rate, from the EDA. These created features were beneficial as they improved the evaluation metric used.

9. The best three models in the leaderboard-the boosting algorithms- were aggregated. Their predictions were averaged using a weight, according to their performance on the leaderboard and used as the final model, securing a score of 93.093%.

Tools  used and their versions are in the requirements.txt
