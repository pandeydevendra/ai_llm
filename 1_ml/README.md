# Machine Learning

[← Back to main README](../README.md)

## 📖 Book Index — Part 1: Machine Learning

**Chapters:** [1. Python for ML](#chapter-1-python-for-ml) · [2. Data preprocessing & feature engineering](#chapter-2-data-preprocessing--feature-engineering) · [3. Linear & logistic regression](#chapter-3-linear--logistic-regression) · [4. Decision trees & random forests](#chapter-4-decision-trees--random-forests) · [5. Gradient boosting](#chapter-5-gradient-boosting) · [6. SVM, KNN & Naive Bayes](#chapter-6-svm-knn--naive-bayes) · [7. Unsupervised learning](#chapter-7-unsupervised-learning) · [8. Model evaluation & tuning](#chapter-8-model-evaluation--tuning) · [9. Project: end-to-end ML pipeline](#chapter-9-project-end-to-end-ml-pipeline)

### Chapter 1: Python for ML

🟢 Core · 📝 Notes coming

- **1.1** NumPy: arrays, vectorization, broadcasting
- **1.2** Pandas: Series, DataFrames, indexing, groupby, merge
- **1.3** Visualization: Matplotlib & Seaborn
- **1.4** Exploratory Data Analysis (EDA) workflow

**🔑 Key terms:** array, shape, broadcasting, DataFrame, Series, groupby, distribution, correlation, outlier  
**🎯 You'll learn:** Load, clean, summarize and plot a dataset; replace Python loops with vectorized maths  
**🛠️ You can build:** An EDA notebook on a real dataset (e.g. Titanic or a Kaggle dataset)

### Chapter 2: Data preprocessing & feature engineering

🟢 Core · 📝 Notes coming

- **2.1** Handling missing values
- **2.2** Encoding categories: one-hot, ordinal
- **2.3** Scaling: standardization, normalization
- **2.4** Creating & selecting features
- **2.5** Train / validation / test split and data leakage
- **2.6** scikit-learn Pipelines

**🔑 Key terms:** feature, label / target, imputation, one-hot encoding, scaling, data leakage, pipeline  
**🎯 You'll learn:** Turn messy raw data into clean model-ready features without leaking test information  
**🛠️ You can build:** A reusable preprocessing pipeline you can drop in front of any model

### Chapter 3: Linear & logistic regression

🟢 Core · 📝 Notes coming

- **3.1** ML basics: supervised vs. unsupervised, regression vs. classification
- **3.2** Linear regression & least squares
- **3.3** Loss functions: MSE, cross-entropy
- **3.4** Gradient descent
- **3.5** Logistic regression & the sigmoid
- **3.6** Regularization: L1 (Lasso), L2 (Ridge)

**🔑 Key terms:** model, parameter, loss, gradient, learning rate, overfitting, sigmoid, decision boundary, regularization  
**🎯 You'll learn:** How a model learns by minimizing a loss; implement it from scratch, then with scikit-learn  
**🛠️ You can build:** A house-price predictor and a spam / not-spam classifier

### Chapter 4: Decision trees & random forests

🟢 Core · 📝 Notes coming

- **4.1** Decision trees: splits, Gini impurity, entropy
- **4.2** Overfitting, depth & pruning
- **4.3** Ensembles & bagging
- **4.4** Random forests & feature importance

**🔑 Key terms:** node, leaf, impurity, depth, ensemble, bagging, feature importance  
**🎯 You'll learn:** How trees make decisions, and why many trees beat one  
**🛠️ You can build:** A customer-churn or loan-approval classifier that explains its most important features

### Chapter 5: Gradient boosting

⚪ Later · 📝 Notes coming

- **5.1** The boosting idea: fix the previous model's mistakes
- **5.2** XGBoost, LightGBM, CatBoost
- **5.3** Key hyperparameters
- **5.4** Early stopping

**🔑 Key terms:** weak learner, boosting, residual, learning rate, n_estimators, early stopping  
**🎯 You'll learn:** The go-to method for tabular data and how to tune it  
**🛠️ You can build:** A Kaggle tabular-competition submission

### Chapter 6: SVM, KNN & Naive Bayes

⚪ Later · 📝 Notes coming

- **6.1** K-Nearest Neighbours & distance metrics
- **6.2** Support Vector Machines: margin & kernels
- **6.3** Naive Bayes & Bayes' theorem
- **6.4** When to use which

**🔑 Key terms:** distance metric, k, margin, support vector, kernel trick, prior, likelihood  
**🎯 You'll learn:** Classic algorithms and the intuition behind each  
**🛠️ You can build:** A Naive Bayes text classifier and a model-comparison notebook

### Chapter 7: Unsupervised learning

⚪ Later · 📝 Notes coming

- **7.1** K-Means clustering
- **7.2** DBSCAN
- **7.3** Hierarchical clustering
- **7.4** PCA (dimensionality reduction)
- **7.5** t-SNE / UMAP for visualization

**🔑 Key terms:** cluster, centroid, inertia, density, principal component, explained variance  
**🎯 You'll learn:** Find structure in data that has no labels  
**🛠️ You can build:** A customer-segmentation analysis

### Chapter 8: Model evaluation & tuning

🟢 Core · 📝 Notes coming

- **8.1** Regression metrics: MAE, RMSE, R²
- **8.2** Classification metrics: accuracy, precision, recall, F1, ROC-AUC, confusion matrix
- **8.3** Cross-validation
- **8.4** Bias–variance trade-off, under- & overfitting
- **8.5** Hyperparameter tuning: grid, random, Optuna

**🔑 Key terms:** confusion matrix, precision, recall, F1, ROC curve, k-fold, bias, variance, hyperparameter  
**🎯 You'll learn:** Measure a model honestly and pick the best one  
**🛠️ You can build:** An evaluation report comparing several models on one dataset

### Chapter 9: Project: end-to-end ML pipeline

⚪ Later · 📝 Notes coming

- **9.1** Data → features → model → evaluation
- **9.2** Experiment tracking
- **9.3** Serving predictions through an API

**🔑 Key terms:** experiment tracking, model registry, inference, endpoint  
**🎯 You'll learn:** Connect every step into one working system  
**🛠️ You can build:** A prediction API with FastAPI and MLflow tracking

Legend: 🟢 Core = study now · ⚪ Later = after the core ([Core Path](../README.md#core-path))
