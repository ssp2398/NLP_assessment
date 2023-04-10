# NLP_project
Objective :
            Objective 1: 
                         Get the most frequent entities from the tweets.
            Objective 2:  
                        Find out the sentiment/polarity of each author towards each of the entities.
About dataset:
             Given a JSON file (tweets.json) that contains tweets (sentences)  along with the name of the author.
Downloading and reading the JSON file:
Get the JSON file here:   http://bit.ly/akaiketech_cll_tweets_json 
Python code for reading the JSON file:
import json
with open('tweets.json') as jfile:
d = json.load(jfile)
d would be a dictionary with tweet_id as key and another dictionary as a value. The inner
dictionary contains the information tweet_text and tweet_author. See the sample below.

{"1374140386071961602":
● {tweet_author:"Hematopoiesis News"
● tweet_text:"⚕️ Scientists conducted a Phase II study of acalabrutinib in
patients with relapsed/refractory #CLL who were ibrutinib-intolerant,
and found an overall response rate of 73%. https://t.co/eJ6m4QpC5P
https://t.co/kuZz6ZO47r"}
techniques/methods/libraries use:
                                  pandas dataframe, regular expression, translator, nltk-stopward, nltk-tokenize, FreqDist, pos_tags, SentimentIntensityAnalyzer, etc

Approaches to solve the problem:
                                               For the any NLP problems first thing important understand the objective/aim of statement and understand the data. As I start working on this dataset its little time consuming  process to understand the data. Most of the time is invested in what is exact objective of the assessment. 
-	Importing dataset :
                The given dataset is available in json file format. For the language preprocessing techniques  important step is import the dataset and convert them into pandas DataFrame . for this following  method I used.

with open('tweets.json') as jfile:
    d = json.load(jfile) 

df=pd.DataFrame(d)
df=df.transpose()  #transpose() convert the columns into row and rows in columns 
df=df[['tweet_author','tweet_text']]

after importing and converting dataset into DataFrame , by observation we can see there is lots emojis , special characters (‘’.,><?/!$#&%),unsual numbers in tweet_text columns . for the removing those thing I use ‘regular expression’  method . 

for removing digits/numbers from tweet_text I used following method 

re.sub(r'\d+','',col) 

for removing special characters, emojis I used 

re.sub(r'[^\w\s]','',word)

after removing above things I observed there is various languages used for tweet so we need to translate all the tweet_text into english language.
for translating I used  python inbuild translator method 

from translate import Translator
translator=Translator(to_lang="en")  
translated_tweet=translator.translate(tweet)

for removing stopwords I used nltk.corpus , using  this method we can remove/extract the stopwords from tweet.
Stopwords=this,is,who,were,where,those……
After all of the above preprocessing dataset is ready for building solution on every problem statement.

For extracting entities from tweet I used ne_chunk , pos_tag , 
And for the sentiments/polarity analysis used SentimentIntensityAnalyzer 


The challenges faced while Solving  problem statement:
-	Converting json formatted dataset into DataFrame and labelling them correct 
-	Removing numbers , special characters , stopwords and translating the tweets into any one understanding language .
-	Finding the correct/required entities from the tweet. 
-	Sentiment analysis is little challenging part for me .  
My Handles:




             

Thus with this, we are done with the solutions of both of the objectives.
Thank you for going through this solution and presentations
I will add  more approaches that came to my mind in the later in  this notebook. I found this approach more Profound, thus it is part of the solution

Thanks and regards 
SURAJ PAGADE
                                    
              
