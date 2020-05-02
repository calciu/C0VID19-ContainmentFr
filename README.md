# ContainmentDay (#ConfinementJour) COVID-19-TweetIDs

The repository contains an ongoing collection of tweets IDs associated with the Containment period due to the coronavirus COVID-19 (SARS-CoV-2), that started in France on March 18, 2020. 

We used the Twitter’s search API to gather on a daily basis Tweets defined by  hashtags #confinementJour1 to #confinementJour_n (that is ContainmentDay1 to n).

To comply with Twitter’s [Terms of Service](https://developer.twitter.com/en/developer-terms/agreement-and-policy), we are only publicly releasing the Tweet IDs of the collected Tweets. The data is released for non-commercial research use. 

Additionally we release annotations of this corpus using sentiment and emotions mesurement instruments. This allows researchers to evaluate the capability of these tools to capture variations of émotions expressed by people on a daily basis.

The associated paper to this repository can be found here: [#COVID-19: The First Public COVID19 Containment Twitter Dataset](under development)

## Data Organization
The Tweet-IDs that help recover (hydrate) all datasets are organized as follows:
* Tweet-ID files are stored in two folders ContainmentDays and ContainmentOther. The first has tweets collected with the containment day hashtag #ConfinementJourX, the second one contains tweets collected using a larger set of hashtags indicating the containment period.
* Individual Tweet-ID files contain a collection of Tweet IDs, and the file names all follow the same structure, with a prefix “df_ids” followed by either "jX" indicating the day (jour) for the first folder and by "confX" meaning containement (confinement) for the second.

Sentiment and Emotion Annotations are also available in a folder called ContainmentAnnot and the csv files have the following pattern dff_method_nublerOfDays_chunk.csv (dff meaning data frame free and the method is nrc or lds)

### dff\_nrc\_41\_1.csv 
nrc files contain ten columns the first eight represent emotions frequencies and the last two sentiments frequencies per tweet

| anger | anticipation | disgust | fear | joy | sadness | surprise | trust | negative | positive |
| ----: | -----------: | ------: | ---: | --: | ------: | -------: | ----: | -------: | -------: |
|     0 |            0 |       0 |    0 |   0 |       0 |        0 |     0 |        0 |        0 |
|     0 |            0 |       0 |    1 |   0 |       0 |        1 |     0 |        3 |        0 |
|     1 |            1 |       0 |    2 |   1 |       1 |        1 |     4 |        2 |        2 |
|     0 |            1 |       0 |    2 |   0 |       1 |        0 |     0 |        1 |        0 |

### dff\_lds\_41\_1.csv 
lds files contain four columns negative and positive sentiment frequencie, number of words and identification number of the tweets
    
| Neg\_lsdfr | Pos\_lsdfr | nb | id |
| ---------: | ---------: | -: | -: |
|          0 |          0 |  1 |  1 |
|          0 |          0 | 20 |  2 |
|          0 |          1 | 38 |  3 |
|          1 |          1 | 26 |  4 |


### dff\_emos\_41\_1.csv
emos files contain five columns. The first is a list of emojis separated by ";", the second indicates the number of emojis per tweet. The other three indicate the minimum, average and maximum sentiment score (on a scale from -1 to 1) 


|     | emoji  | nemoji | min\_sentsc | mean\_sentsc | max\_sentsc |
| --- | :----- | -----: | ----------: | -----------: | ----------: |
| 193 | ;      |      0 |          NA |           NA |          NA |
| 194 | 😂;😂;😂; |      3 |       0.221 |       0.2210 |       0.221 |
| 195 | 📷;     |      1 |       0.430 |       0.4300 |       0.430 |
| 196 | 😆;😅;🤣; |      3 |       0.178 |       0.2935 |       0.409 |

## Notes About the Data
A few notes about this data: 
* We will be continuously maintaining this database for the foreseeable future, and will be uploading new data on a weekly basis.  
* We will keep a running summary of basic statistics as we upload data in each new release. 
* Consider using tools such as the [Hydrator](https://github.com/DocNow/hydrator) and [Twarc](https://github.com/DocNow/twarc) to rehydrate the Tweet IDs. Instructions for both are in the next section. 
* Hydrating may take a while, and Tweets may have been deleted since our initial collection. If that is the case, unfortunately you will not be able to get the deleted Tweets from querying Twitter's API.

## How to Hydrate

### Hydrating using [Hydrator](https://github.com/DocNow/hydrator) (GUI)
Navigate to the [Hydrator github repository](https://github.com/DocNow/hydrator) and follow the instructions for installation in their README. As there are a lot of separate Tweet ID files in this repository, it might be advisable to first merge files from timeframes of interest into a larger file before hydrating the Tweets through the GUI. 

### Hydrating using [Twarc](https://github.com/DocNow/twarc) (CLI)
Many thanks to Ed Summers ([edsu](https://github.com/edsu)) for writing this script that uses [Twarc](https://github.com/DocNow/twarc) to hydrate all Tweet-IDs stored (in their corresponding folders). 

First install Twarc and tqdm
```
pip3 install twarc
pip3 install tqdm
```

Configure Twarc with your Twitter API tokens (note you must [apply](https://developer.twitter.com/en/apply-for-access) for a Twitter developer account first in order to obtain the needed tokens). You can also configure the API tokens in the script, if unable to configure through CLI. 
```
twarc configure
```

Run the script. The hydrated Tweets will be stored in the same folder as the Tweet-ID file, and is saved as a compressed jsonl file
```
python3 hydrate.py
```

# Data Usage Agreement
This dataset is licensed under the Creative Commons Attribution-NonCommercial-ShareAlike 4.0 International Public License ([CC BY-NC-SA 4.0](https://creativecommons.org/licenses/by-nc-sa/4.0/)). By using this dataset, you agree to abide by the stipulations in the license, remain in compliance with Twitter’s [Terms of Service](https://developer.twitter.com/en/developer-terms/agreement-and-policy), and cite the following manuscript: 

Sophie Balech, Christophe Benavent, and Mihai Calciu. 2020. #COVID-19: The First Public COVID19 Containment Twitter Dataset.  arXiv:(under development)

# Statistics Summary (v0.1)
Number of Tweets : ** to come**

# Inquiries
If you have technical questions about the data collection, please contact Mihai Calciu at **mihai.calciu[at]univ-lille[dot]fr**.

If you have any further questions about this dataset please contact Christophe Benavent at **christophe.benavent[at]gmail[dot]com**.
