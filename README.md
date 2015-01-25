Machine-Learning-Newspaper
======================

##**Step1. Data Wrangling**
- Run "data_wrangling.py"
- Get API Key from NYTimes.
- Get articles from NYTimes and convert json to csv format to save.
- They don't provide full article.
- Challenges:
 * simplejson library errors occurs and fixed it with upgrade 3.6.5.
 * Sometimes server timeout.
 * Article have utf-8 and unicode both of them.
 * Sometimes JSON Data contains journalist name but does not have article.
  
 
##**Step2. Data Exploratory**
- Run "data_exploratory.py"
- Clean stemmer with SnowballStemmer.
- Change encoding utf-8 to unicode.
- step2_data_exploratory.py generates pkl file with all article from 2010 to 2014.
 * It is to expensive to my MAC.
- step2_data_exploratory(2_people).py generates pkl file with two journalist's articles from 2010 to 2014.
 * It is not that expensive.
 * I choose two journalist, NEIL GENZLINGER and STEPHEN HOLDEN because they have written so many articles.
 * During 2010~2014, NEIL GENZLINGER wrote 1211 articles and STEPHEN HOLDEN wrote 1317 articles.
 

##**Step3. Feature Engineering**
- Feature Extraction
 * Applied TfidfVectorizer and deleted stopwords.
- Feature Selection
 * SelectKBest, chi2 are faster than SelectPercentile in my case.
 * f_classif for classification problem.
 * f_regression for regression problems.
 * chi2 for classification problems with sparse non-negative data (typically text data).
 * My prefer : SelectPercentile(score_func=chi2), SelectKBest(k=100), SelectPercentile(f_classif, percentile=30).
- preprocess_4 method is for supervised learning.
- preprocess_2 method is for unsupervised learning.


##**Step4. Apply Different Algorithm**
- I applied various Supervised and Unsupervised Algorithm with Dimension Reduction.
- Supervised Learning
 * Classification : GaussianNB, BernoulliNB, AdaBoostClassifier, DecisionTreeClassifier, KNeighborsClassifier, RandomForestClassifier, SVC
 * Regression : LinearRegression, ElasticNet, Lasso, Ridge
- Unsupervised Learning
 * KMeans, SpectralClustering, AgglomerativeClustering
- Dimension Reduction
 * Linear Dimensionality Reduction : PCA, RandomizedPCA, LDA
 * Non Linear Dimensionality Reduction : Isomap, LocallyLinearEmbedding
 
 
 Algorithm | Feature Selection | Accuracy | Time |
 ----------|--------------------|----------|----------|
 GaussianNB |  SelectPercentile | 0.93 | 0.3s|
 GaussianNB | chi2 | 0.93 | 0.12s|
 BernoulliNB | SelectPercentile | 0.92 | 0.2s|
 BernoulliNB | chi2 | 0.90 | 0.06s|
 AdaBoostClassifier | SelectPercentile | 0.72 | 14s|
 AdaBoostClassifier | chi2 | 0.71 | 4.6s|
 DecisionTreeClassifier | SelectPercentile | 0.79 | 9s|
 DecisionTreeClassifier | chi2 | 0.80 | 2.2s|
 KNeighborsClassifier | SelectPercentile | 0.75 | 3s|
 KNeighborsClassifier | chi2 | 0.55 | 1.0s|
 RandomForestClassifier | SelectPercentile | 0.84 | 2s|
 RandomForestClassifier | chi2 | 0.85 | 0.8s|
 RandomForestClassifier | SelectPercentile | 0.88 | 30s|
 RandomForestClassifier | chi2 | 0.87 | 10s|




