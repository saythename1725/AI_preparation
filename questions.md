Gradient Descent
What is Gradient Descent?
How does Gradient Descent work?
What are the different types of Gradient Descent?
Batch Gradient Descent
Stochastic Gradient Descent
Mini-Batch Gradient Descent
How does Gradient Descent know which direction to move?
Does Gradient Descent always reach the global minimum?
Learning Rate
What is the Learning Rate?
What happens if the Learning Rate is too high?
What happens if the Learning Rate is too low?
How does the Learning Rate affect model convergence?
How are Learning Rate and variance related?
What are Learning Rate schedules?
How do you choose an appropriate Learning Rate?
Loss Functions
What is a Loss Function?
Why is a Loss Function important during model training?
How does the choice of Loss Function affect model training?
How do Loss Functions differ between Regression and Classification?
What mathematical differences exist between Classification and Regression Loss Functions?
How does the Loss Function influence the gradients during training?
Bias-Variance Trade-off
What is the Bias-Variance Trade-off?
What is High Bias?
What is High Variance?
What is Underfitting?
What is Overfitting?
How does the Bias-Variance Trade-off manifest differently in Classification and Regression?
How can High Bias be reduced?
How can High Variance be reduced?
Regularization
What is Regularization?
What is the intuition behind Regularization?
How does Regularization prevent Overfitting?
What is L1 Regularization?
What is L2 Regularization?
What is the difference between L1 and L2 Regularization?
When would you prefer L1 over L2?
What is Elastic Net?
Cross Validation
What is Cross Validation?
Why do we use Cross Validation?
What is K-Fold Cross Validation?
What is Stratified K-Fold Cross Validation?
What is the difference between K-Fold and Stratified K-Fold?
When should Stratified K-Fold be used?
What role does Cross Validation play in model selection?
How can data leakage occur during Cross Validation?
Early Stopping
What is Early Stopping?
How does Early Stopping prevent Overfitting?
Which metrics can be monitored for Early Stopping?
What is Patience in Early Stopping?
How is Early Stopping different from Regularization?
Hyperparameter Tuning
What is Hyperparameter Tuning?
What is the difference between Parameters and Hyperparameters?
What are the common Hyperparameter Tuning techniques?
What is Grid Search?
What is Random Search?
What is Bayesian Optimization?
What is Hyperband?
What is Optuna?
How does Cross Validation help in Hyperparameter Tuning?
2. Regression
Linear Regression
What are the assumptions behind Linear Regression?
What is Linearity?
What is Independence of Errors?
What is Homoscedasticity?
What is Normality of Residuals?
What is Multicollinearity?
What happens when Linear Regression assumptions are violated?
How do assumption violations impact the model?
Which assumptions affect prediction accuracy and which primarily affect inference?
Regression Metrics
What are the common Regression metrics?
What is Mean Squared Error?
What is Mean Absolute Error?
What is Root Mean Squared Error?
When should different Regression metrics be used?
MSE vs MAE
What is the difference between MSE and MAE?
Why is MSE commonly used during model training?
When would you prefer MAE?
How do MSE and MAE handle Outliers differently?
Why does MSE penalize large errors more heavily?
R² Score
What does R² signify?
How is R² interpreted?
Where can R² be misleading?
Can a model have a high R² and still perform poorly?
What is Adjusted R²?
What is the difference between R² and Adjusted R²?
Normal Distribution
What is a Normal Distribution?
What are the properties of a Normal Distribution?
What do Mean and Standard Deviation represent?
What is the Empirical Rule?
Why is the Normal Distribution important in Machine Learning and Statistics?
3. Classification
Logistic Regression
What is Logistic Regression?
Why is it called Regression if it is used for Classification?
How does Logistic Regression create a Decision Boundary?
How are probabilities converted into class predictions?
Multiclass Logistic Regression
Can Logistic Regression be used for Multi-class Classification?
What are the approaches used for Multi-class Logistic Regression?
What is One-vs-Rest?
What is One-vs-One?
What is Multinomial Logistic Regression?
When would you use One-vs-Rest versus Multinomial Logistic Regression?
Sigmoid Function
What is the role of the Sigmoid Function in Classification models?
Why does Sigmoid output values between 0 and 1?
How is the Sigmoid output converted into a class prediction?
What are the limitations of the Sigmoid Function?
Classification vs Regression Metrics
Why can't we use Regression metrics like MSE and R² for Classification problems?
Can MSE technically be used for Classification?
Why is R² generally not meaningful for Classification?
How do the objectives of Regression and Classification differ?
What metrics are commonly used for Classification?
Confusion Matrix
What is a Confusion Matrix?
What are True Positives?
What are True Negatives?
What are False Positives?
What are False Negatives?
What does a Confusion Matrix tell you that Accuracy does not?
Accuracy, Precision, Recall, and F1 Score
What is Accuracy?
What is Precision?
What is Recall?
What is F1 Score?
Why can F1 Score be more useful than Accuracy?
When should you use F1 Score?
When would you use F1 Score over Precision or Recall?
When is Accuracy a misleading metric?
When should Precision be prioritized?
When should Recall be prioritized?
What is the difference between Precision and Recall?
ROC and AUC
What is an ROC Curve?
What is AUC?
What does AUC-ROC represent?
Why is ROC-AUC not ideal for highly imbalanced datasets?
What is Precision-Recall AUC?
When should you prefer PR-AUC over ROC-AUC?
Log Loss vs MSE
Why is Log Loss used for Classification instead of MSE?
Can MSE technically be used for Classification?
How do MSE and Log Loss produce different gradients?
Why does Log Loss heavily penalize confident wrong predictions?
What is Binary Cross-Entropy?
What is Categorical Cross-Entropy?
Multi-class F1 Averaging
What is Micro F1?
What is Macro F1?
What is Weighted F1?
What is the difference between Micro, Macro, and Weighted averaging?
When should each averaging method be used?
How does class imbalance affect these averaging methods?
Probabilistic vs Non-Probabilistic Classifiers
What are Probabilistic Classifiers?
What are Non-Probabilistic Classifiers?
What is the difference between them?
What are examples of Probabilistic Classifiers?
What are examples of Non-Probabilistic Classifiers?
4. Feature Selection and Engineering
Feature Importance
What are the different ways to find the most important features?
What are Filter Methods?
What are Wrapper Methods?
What are Embedded Methods?
What is Model-Based Feature Importance?
What is Permutation Importance?
What are SHAP Values?
What are the advantages and limitations of each method?
Correlated Features
What happens when two features are highly correlated?
How do you choose between two highly correlated variables?
What criteria can be used to decide which feature to keep?
When should you keep both correlated variables?
How can Domain Knowledge help in Feature Selection?
Multicollinearity
What is Multicollinearity?
Why is Multicollinearity a problem?
How can Multicollinearity be detected?
What is VIF?
How can Multicollinearity be handled?
Does Multicollinearity affect all Machine Learning models equally?
Correlation vs Causation
What is Correlation?
What is Causation?
What is the difference between Correlation and Causation?
Can two variables be correlated without one causing the other?
Can causation exist without a strong observed correlation?
5. Statistics and Hypothesis Testing
Hypothesis Testing
What is Hypothesis Testing?
What is the Null Hypothesis?
What is the Alternative Hypothesis?
What is a p-value?
What is a Significance Level?
What are Type I and Type II Errors?
What is Statistical Power?
Chi-Square Test
What is the Chi-Square Test?
What hypothesis testing framework is used in the Chi-Square Test?
What is the Chi-Square Test of Independence?
What is the Chi-Square Goodness-of-Fit Test?
What are the assumptions of the Chi-Square Test?
When should you use a Chi-Square Test?
What type of data is suitable for a Chi-Square Test?
Correlation vs Cohesion
What is Correlation?
What is Cohesion?
How is Correlation different from Cohesion?
In which domains is Cohesion commonly used?
6. Tree-Based Models and Gradient Boosting
Regression Trees vs Classification Trees
Why does a Regression Tree split based on Variance Reduction?
Why does a Classification Tree use Gini Impurity or Entropy?
What is the intuition behind a Decision Tree split?
How are splitting criteria different for Regression and Classification?
What is Information Gain?
What is Gini Impurity?
What is Entropy?
Pruning
What is Pruning in Decision Trees?
Why is Pruning necessary?
What is Pre-Pruning?
What is Post-Pruning?
How does Pruning help prevent Overfitting?
What is the role of Cross Validation in Pruning?
XGBoost
What Loss Function does XGBoost use?
Does XGBoost use a fixed Loss Function?
What objective functions are commonly used for Regression?
What objective functions are commonly used for Binary Classification?
What objective functions are commonly used for Multi-class Classification?
How does XGBoost use first-order derivatives?
How does XGBoost use second-order derivatives?
What is the difference between the Loss Function and the Objective Function in XGBoost?
Learning Rate in Gradient Boosting
What is the role of the Learning Rate in Gradient Boosting?
How does Learning Rate interact with the number of trees?
What happens when the Learning Rate is too high?
What happens when the Learning Rate is too low?
What is the trade-off between Learning Rate and the number of estimators?
7. SVM and Distance-Based Algorithms
SVM Decision Boundaries
How do Decision Boundaries differ in SVMs with Linear and Non-linear Kernels?
What is a Linear SVM?
What is a Non-linear SVM?
When should you use a Linear Kernel?
When should you use a Non-linear Kernel?
Kernel Trick
What is the Kernel Trick in SVM?
Why do we map data into a higher-dimensional space?
How does the Kernel Trick avoid explicitly computing the higher-dimensional transformation?
How does the Kernel Trick enable non-linear Decision Boundaries?
What are the common Kernel Functions?
Linear Kernel
Polynomial Kernel
RBF Kernel
Sigmoid Kernel
What are the limitations of Kernel-based SVMs?
Feature Scaling
Why does Feature Scaling matter?
How does Feature Scaling impact SVM?
How does Feature Scaling impact KNN?
Which algorithms are sensitive to Feature Scaling?
Which algorithms are generally insensitive to Feature Scaling?
Why are Tree-based models generally insensitive to Feature Scaling?
8. Unsupervised Learning
K-Means Clustering
How does K-Means Clustering work?
What are the steps involved in the K-Means algorithm?
What is a Centroid?
What objective does K-Means minimize?
What are the limitations of K-Means?
How is K-Means affected by Outliers?
How is K-Means affected by cluster shape?
Why is Feature Scaling important for K-Means?
How does initialization affect K-Means?
Choosing the Number of Clusters
How do you choose the optimal number of clusters?
What is the Elbow Method?
What is the Silhouette Score?
What are the limitations of the Elbow Method?
What are the limitations of the Silhouette Score?
Can Domain Knowledge influence the choice of K?
9. Deep Learning
Backpropagation
What is Backpropagation?
How does Backpropagation work?
What is the role of the Chain Rule in Backpropagation?
How are gradients calculated for each layer?
What is the difference between Forward Propagation and Backpropagation?
Optimizers vs Backpropagation
How are Optimizers different from Backpropagation?
What is the role of an Optimizer?
How does an Optimizer use gradients?
What are the common Optimizers?
SGD
Momentum
RMSProp
Adam
Does Adam replace Backpropagation?
Vanishing and Exploding Gradients
What are Vanishing Gradients?
What are Exploding Gradients?
Why do they occur?
How do they affect Deep Neural Network training?
How can Vanishing Gradients be mitigated?
How can Exploding Gradients be mitigated?
What is Gradient Clipping?
How do Activation Functions affect Gradient Flow?
How does proper Weight Initialization help?
LSTM and GRU
How do LSTMs help address Vanishing Gradients?
How do GRUs help address Vanishing Gradients?
What is the difference between LSTM and GRU?
What are the gates in LSTM?
What are the gates in GRU?
When would you prefer GRU over LSTM?
Residual Connections
What are Residual Connections?
How do Residual Connections help with Deep Neural Network training?
How do Residual Connections improve Gradient Flow?
How are Residual Connections different from LSTM and GRU mechanisms?
What is the intuition behind Skip Connections?
Dropout
What is Dropout?
How does Dropout prevent Overfitting?
What happens during training?
What happens during inference?
How is Dropout different from Early Stopping?
Transfer Learning
What is Transfer Learning?
Why is Transfer Learning useful?
What is a Pre-trained Model?
What is Fine-Tuning?
When should you freeze layers?
When should you Fine-Tune the entire model?
What are the risks of Fine-Tuning?
10. Natural Language Processing
Count Vectorization
What is Count Vectorization?
How does Count Vectorizer convert text into numerical features?
What is the Bag-of-Words approach?
What are the limitations of Count Vectorization?
What are n-grams?
How is Count Vectorizer different from TF-IDF?
What is the vocabulary in Count Vectorization?
11. Machine Learning Theory
Parametric vs Non-Parametric Models
What are Parametric Models?
What are Non-Parametric Models?
What is the difference between Parametric and Non-Parametric Models?
What are the advantages and disadvantages of each?
What are examples of Parametric Models?
What are examples of Non-Parametric Models?
Curse of Dimensionality
What is the Curse of Dimensionality?
Why does model performance suffer with increasing dimensions?
How does the Curse of Dimensionality affect Distance-Based algorithms?
How does it affect data sparsity?
How can Dimensionality Reduction help?
What techniques can be used to handle high-dimensional data?
No Free Lunch Theorem
What is the No Free Lunch Theorem in Machine Learning?
Why is there no universally best Machine Learning algorithm?
How does the choice of algorithm depend on the problem?
How does Domain Knowledge influence model selection?
12. MLOps and Deployment
YAML
What is a YAML file?
What are the basic syntax rules of YAML?
How do indentation and hierarchy work in YAML?
How do you represent Dictionaries in YAML?
How do you represent Lists in YAML?
How do you represent Strings and Boolean values?
How are YAML files commonly used in Machine Learning and MLOps?
Docker Ports
What does exposing a Port mean in Docker?
What is the difference between EXPOSE and Port Publishing?
How do you expose a Port in a Dockerfile?
How do you map a Container Port to a Host Port?
What is the difference between:
EXPOSE 8000

and:

docker run -p 8000:8000
Why is EXPOSE alone not sufficient to access a container from outside?
13. Python and DSA
Shallow Copy vs Deep Copy
What is a Shallow Copy?
What is a Deep Copy?
What is the difference between Shallow Copy and Deep Copy?
When would changes to a nested object affect both copies?
When should you use a Shallow Copy?
When should you use a Deep Copy?
__init__ Method
What does the __init__ method do in Python?
When is __init__ called?
How does __init__ initialize object attributes?
What is the difference between __new__ and __init__?
Is __init__ technically a constructor?
Second Largest Number in an Array
How do you find the second largest number in an array?
What are the different approaches?
Sorting
Two-pass approach
Single-pass approach
Heap
How would you handle duplicates?
What is the Time Complexity of each approach?
What is the Space Complexity of each approach?
How would you find the second largest distinct number?
