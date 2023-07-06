# Capstone Project - AWS Machine Learning Engineer Nanodegree

Welcome to the Capstone Project for the AWS Machine Learning Engineer Nanodegree. This repository contains all the resources related to the project.

## Project Resources

- **Source Code**: The complete codebase for the project is located in the [source folder](src/).
- **Project Report**: The comprehensive report detailing the project's findings and methodology can be found [here](docs/capstone_project_report.pdf).
- **Nanodegree certificate**: The nanodegree completion certificate can be found [here](docs/certificate.pdf).

## Project Overview
The focal point of this project is the analysis of customer behavior within the Starbucks rewards mobile app. The aim is to comprehend the reaction of customers to various promotional offers, taking into account their unique demographics and historical interactions. This understanding will enable Starbucks to fine-tune its marketing strategies, boost customer engagement, and augment revenue. 

The issue at hand is the recognition of demographic groups that exhibit a positive response to specific promotional offers from Starbucks. Given the variety of offers Starbucks sends to its rewards mobile app users, the response rate can differ among customer segments. The task is to delve into customer demographics and preferences, utilizing these insights to predict the probability of a user completing a promotional offer post-viewing.

## Proposed Solution
To tackle the issue, a machine learning model will be developed to predict the probability of a user completing a promotional offer after viewing it, taking into account their demographic details and past interaction history. The model will utilize customer data to determine which specific promotional offer features will be most effective for a particular customer segment. 

A heuristic benchmark will be set by examining the historical response rate data. While this rule-based approach offers basic insights into the effectiveness of various offers for each customer segment, it lacks the precision and refinement of a machine learning model that considers a wider range of features and individual user interaction history.

## Project Methodology 

The methodology for this project involves several crucial steps. Initially, the data will be cleaned, preprocessed, and formatted. Subsequently, exploratory data analysis will be conducted to identify trends, correlations, and potential features for the machine learning model. This will be followed by feature engineering to enhance the model's predictive performance. SageMaker AutoGluon will be employed for automated model selection, comparing multiple algorithms on the validation set to identify the optimal model. This model will be trained and its hyperparameters fine-tuned using SageMaker's capabilities. The model's performance will be assessed on the test set and compared to a benchmark model. Lastly, the findings will be discussed, offering insights into customer behavior and their response to different offers.

## Conclusions

The LightGBM model developed, which was designed to predict if a customer will complete an offer, exhibits substantial effectiveness. By setting a threshold at roughly 0.35, optimized for the F1-score, the model successfully identifies 83% of customers who finalize an offer, as evidenced by a high recall rate of 0.83. However, the model's precision is 0.55, indicating that the model's prediction of a customer completing an offer is accurate 55% of the time. The model's overall accuracy stands at 0.68.

The Precision-Recall and ROC curves further corroborate the model's performance, assessing its capacity to differentiate between customers who will and will not complete an offer. The model has achieved a PR AUC score of about 0.644 and an ROC AUC score of around 0.780. These scores suggest a high proficiency in identifying customers who will finalize an offer after viewing it, and a superior ability to distinguish between customers who completed the offer and those who did not.

The model also provides several key insights about the features that have a higher predictive power for identifying customers that will complete an offer:
- Reward: Moderate rewards increase offer completion likelihood, particularly among long-term members. No reward or high rewards decrease this likelihood.
- Membership Days: Long-term members are more inclined to complete offers.
- Social Channel: The social channel is the most effective for sharing offers, outperforming web, mobile, and email.
- Income: Middle-income customers are more likely to complete offers, especially with increased rewards. Low and high-income customers show a decreased likelihood of offer completion.
- Difficulty: Easier offers are more likely to be completed.
- Duration, Offer Type: These factors do not significantly influence offer completion.
- Gender: Non-male customers are more likely to complete offers, especially those with higher rewards. Male customers are less likely.
- Age: Customers older than 40 are more likely to complete offers, especially those with higher rewards. Younger customers are less likely.

These insights should guide marketing strategies. However, it's crucial to ensure fairness and non-discrimination based on gender or age. When tailoring offers based on these insights, ethical implications and business objectives should be taken into account.

In summary, this model is particularly efficient when the aim is to capture as many offer completions as possible, even at the risk of some false positives. The results indicate that the model could be a beneficial tool for improving marketing strategies and optimizing promotional offers.

## Next Steps
The future course of action should involve training a new LightGBM model, concentrating exclusively on the features that showed high predictive power. These features are reward, membership_days, income, social, difficulty, and duration, while intentionally omitting gender and age-related features. This strategy could potentially improve the model's interpretability, decrease noise, and enhance performance. If the performance does not improve, it would be necessary to assess whether the inclusion of gender and age aligns with the business goals.

Another approach worth considering is the creation of a two-step model. The initial model would predict whether a customer will view an order. Assuming the customer views it, a subsequent model would then predict if they will complete the order. The target population for this second model should be those who viewed the offer. Examining the features that influence a customer to both view and complete an order in this two-step process could potentially increase the accuracy and interpretability of our predictive approach. By segmenting the problem into two stages, we might be able to identify distinct patterns that are specific to each stage, potentially enhancing the overall accuracy of our predictions.
