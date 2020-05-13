# fake_news_detection using ML/NLP. 

The main purpose of this project is to use Machine Learning and Deep learning technology to make a way to automatically identify authenticity of news. 


<h4> Material and Tools Required  </h4> 
•	Jupyter Notebook / Google Colab: It will be the IDE required to build the system and run python script.<br>
•	Machine Learning algorithms (SVM, KNN, Logistic Regression) : This are the Machine learning algorithm that will be consumed in our model. We will be using this algorithm via sklearn python package.<br>
•	Python Natural Language Toolkit (NLTK) : This is the python package used to perform the pre-processing and feature extraction on the dataset. <br>
•	Selenium / Newspaper: This is the python package that we used for extracting news article from the internet.<br>
•	Dataset: This is our proprietary dataset that we have built for this project.<br>


<h4> Modules in the System  </h4> 

•	Dataset: As there is no readily available dataset for fake news specifically for Indian scenario, we decided to create our own for this project.
The below table summarize the content of dataset:


|               |               | Sports News   | Political News| Entertainment News |
| ------------- | ------------- | ------------- | ------------- |------------- |
|   FakeNews    |http://www.fakingnews.com/|105  |205| 149|
|               |http://www.theunrealtimes.com/|461|943|231|
|   RealNews    |https://timesofindia.indiatimes.com/ |-|510| 450|
|               |https://epaper.hindustantimes.com/|481| 146|-|


<br>
    
We have collected fake and real news article relating to only most popular topics like Sports, Politics and Entertainment industry. 

To extract news article, we first extracted web links to the articles from respective websites. For this purpose, web scraping on the respective websites and used selenium for the same. After that we feed this links to Newspaper library in python. This library is will provide the news article while avoiding unnecessary texts and advertisements on the webpage. If required it can also extract Title, Date, Author, etc from the giving link to a news article.
•	Pre-processing: Before apply the collected dataset to machine learning algorithms it must be processed to ensure consistency and improve accuracy. 
<br><br>
For Pre-processing we followed following steps:
▪	Remove stop words- we removed unnecessary word like 'I', 'me', 'my’, ‘myself', 'we', 'our', etc.
▪	Remove Punctuation- we removed all the punctuation marks from every news articles.
▪	Remove white-spaces and line feeds.
<br><br>
After the this step the dataset is ready for feature extraction as the machine learning algorithms understands only number and not text.

We extracted following features from the text in dataset:
<br>▪	Count vectors: Count vectors represent each of the news article by same length vector. The values in those vectors represent the frequency of occurrence of a particular word in the news article. 
<br>▪	N-grams: N-grams are extension to count vectors as it also represents each news article with equal length vector while the values of the vector are occurrence of any phrase of length n (2,3,4,5, 6….). Due to limitation of computing power we had we could extract on bi-grams.
<br>▪	TF-IDF: TF-IDF stands for term frequency–inverse document frequency. The vectors values here is determined by following formula,

          IDF(t) = log_e(Total number of documents / Number of documents with term t in it)

<br>•	Processing: The Features extracted in previous stage are now ready to be used for machine learning. Because of computation limitation we could not use bi-gram feature here.

Result obtained from different algorithm and feature set are mentioned below:

|               | KNN  |  Logistic Regression| SVM(Kernel=’Lenear’) |
| ------------- | ------------- | ------------- |------------- |
|Count vector	 | 0.5634  |0.9686|  0.9727|
|TF-IDF	|0.5361	 | 0.9658|0.9502|

<h4>Data Dictionary</h4>  
 
Column 1: URL <br>
Column 2: Date <br>
Column 3: Source <br>
Column 4: Text  <br>
Column 5: Title <br>
Column 6: Label: Fake(0), Real(1) 

