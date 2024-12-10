# CBHI-prediction-RF
Predicting Community Based Health Insurance Uptake Using Random Forest
## Data Loading and Preprocessing
We began our project by loading the dataset into our environment, ensuring that all necessary libraries and tools were in place for further analysis. An initial examination was conducted to check for missing values and correlation between variables which are critical as they can significantly affect model. We ensured that the data was clean and after ruling out multicollinearity, the data was ready for model training. The dataset was split into training and testing sets with a 70/30 ratio, stratifying the split by the target variable to maintain the class distribution in both sets. This ensured that the training and testing sets were representative of the overall class imbalance in the dataset.

## Handling Class Imbalance
One of the significant challenges we encountered was class imbalance, where certain classes were underrepresented in the dataset. To handle the class imbalance, we combined ADASYN (Adaptive Synthetic Sampling) with RandomUnderSampler using a pipeline. This approach allowed us to generate synthetic samples for the minority class while under sampling the majority class, resulting in a balanced dataset. The resampled dataset had an equal distribution of both classes:
•	Resampled dataset shape: Counter({0.0: 8371, 1.0: 8371}).
Model Training and Selection
We trained a Random Forest classifier on the resampled data. The Random Forest algorithm was chosen based on literature and for its robustness and ability to handle large datasets with many features.

## Feature importance
 
The features importance derived from the model highlight the relative significance of various factors in predicting the target variable. "Region" emerges as the most influential feature, indicating that regional location plays a crucial role in the model's predictions. Following this, "Educational level" and "Wealth index combined" are also substantial contributors, suggesting that socioeconomic factors significantly impact the outcome. "Total children ever born" and "Occupation (grouped)" further add to the model's predictive power, emphasizing the relevance of demographic and occupational characteristics. Other factors, such as "Type of place of residence," "Number of wives/partners," and "Currently working," exhibit moderate importance, while "Usual resident or visitor" is the least influential. This distribution of features importance provides valuable insights into the key drivers of the model, aiding in the understanding of which variables most affect the predictions. 

## Model Evaluation
To evaluate the models, we used multiple metrics including accuracy, F1-score, precision, recall, and AUC-ROC. Despite achieving high accuracy scores, the model's performance on the minority class was suboptimal. 

Despite the high accuracy of 90%, the detailed performance metrics reveal significant issues: for class 0, we achieved a precision of 0.96, recall of 0.93, and F1-score of 0.95 on a support of 3588 samples. In contrast, for class 1, the precision was only 0.24, recall was 0.34, and F1-score was 0.28 on a support of 219 samples. This disparity highlights that while the model performs well overall, it struggles with the minority class. The macro average scores of 0.60 (precision), 0.64 (recall), and 0.61 (F1-score), along with the weighted averages, further emphasize the imbalance in performance.
 
The ROC curve for our Random Forest classification model, with an AUC of 0.81, indicated good discriminatory power. The ROC curve's orange line, significantly above the blue dashed diagonal, shows the model performs much better than random guessing. However, the curve is not perfect, indicating room for improvement.
This suggests the need for further optimization or alternative methods to enhance performance. Strategies to consider include fine-tuning model parameters, exploring ensemble methods, implementing cost-sensitive learning, and further data augmentation. By integrating these insights with the ROC curve analysis and detailed evaluation metrics, we have a comprehensive understanding of our Random Forest model's performance and the next steps for improving results, particularly for the minority class. 


## Conclusion
While our models achieved high accuracy, we observed that the performance on the minority class was still suboptimal. Combining ADASYN with RandomUnderSampler slightly improved the recall of the minority class, still precision and F1-score for the minority class remain areas for improvement. Future work could involve further hyperparameter tuning, exploring additional resampling techniques, or using advanced algorithms specifically designed to handle imbalanced datasets.
By leveraging these techniques, we aim to develop a more robust model capable of accurately identifying instances of the minority class, thereby improving overall classification performance in the presence of class imbalance. The other metrics, despite providing a more detailed evaluation, also indicated low performance for the minority class. This suggests that our models struggle to correctly classify the minority class instances, highlighting the inherent difficulty of dealing with imbalanced datasets and the need for further refinement in o
