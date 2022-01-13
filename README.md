# CompLit
Complexity Analysis of Literary texts using BERT AND RoBERTa
 
## About
Complexity analysis of literary text is the process of evaluating the reading difficulty of a given passage of literature. To overcome the shortcomings of commercially available models, we propose the use of the pretrained BERT and ROBERTa models and use transfer learning as a technique to generate an accurate numerical prediction representing the reading complexity of the text while considering the relationships between the words of a sentence irrespective of their respective positions. The text was first encoded into a BERT and RoBERTa Input friendly format. Exploratory data analysis, data cleaning, data preprocessing techniques such as tokenization was performed on the training set before performing inference on it. We found that using these embeddings gives us a much lower root mean square loss than other language models. 

##  Data
The dataset used in this Project is CommonLit Readability Prize (from [Kaggle](https://www.kaggle.com/c/commonlitreadabilityprize/data))
This dataset consists of approximately 3000 entries of literary passages that have been accumulated from several different time periods and a wide range of reading ease scores. The test set contains a larger proportion of modern texts than the training set. Each row contains all of the above mentioned attributes. However, the url_legal and license attributes for approximately 71% of the training dataset have not been provided. However, this does not concern us greatly as the attributes that we are concerned with are the literary excerpts, the reading ease and the standard_error.

The literary excerpts that have been provided consist of a variety of passages of varying levels of reading complexity varying from that of the level of a third grader to that of a twelfth grader. The target variable is used to indicate the complexity of any given passage. The target variable ranges from the values of -3.6 to +1.7. The more positive values indicate an easier level of complexity while the more negative values indicate a harder complexity. The standard error shows the spread of the scores among multiple raters provided for each passage.

## Architecture
![BERT Arch](img/1.png?raw=true "BERT Arch" )

BERT Architecture
![RoBERTa Arch](img/2.png?raw=true "RoBERTa Arch" )

RoBERTa Architecture
## Flow Diagram

![Flow](img/3.png?raw=true "Flow" )

1. Each excerpt is first tokenized and converted to a vector representation using the appropriate pretrained tokenizers of BERT and RoBERTa.
2. A base pretrained model for BERT and RoBERTa has been imported as a local variable and additional layers according to our problem statement are being added and compiled(transfer learning).
3. The vectors are then sent as input to the model (BERT and RoBERTa respectively). 
4. The output of the BERT model is trained further using the tensorflow Dense layers and the output of the RoBERTa models is trained using PyTorch.
5. The models are trained based on this data and used to predict the target value of reading ease as output for the specified test set.
6. We get the output from these models in the form of the complexity scores of the corresponding excerpts.
7. These complexity scores are then standardized to correspond to the appropriate grade levels using a scaling function which provides the output in the form of the grade whose students have the ability to understand an excerpt of that particular complexity.

## Results

![Results](img/4.png?raw=true "Results")

Ranking prediction made for a random sample data, gives 10th standard as  the result which is similar to score obtained by the Flesch-Kincaid Grade Level. 

## Future Work
Further training and fine-tuning both the BERT and roBERTa models to achieve greater levels of accuracy on the same data to have better results, working on a web interface for our project would be one of our objectives. We also wish to train these models to be multilingual and hence wish to work on better datasets.

## Contributors 
<a href="https://github.com/avats101/CompLit/graphs/contributors">
  <img src="https://contrib.rocks/image?repo=avats101/CompLit" />
</a>
