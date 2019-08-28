# we-rate-dogs

# Overview
This is a data wrangling report that uses data from Twitter's WeRateDog's trend. 
The project deals with gathering, assessing, cleaning, and visualizing the data. 
The analyis for this project was done using python and it's libraries.

# Software
- Jupyter Notebook
- Need consumer_key, consumer_secret, access_token, access_secret to query from Twitter API.
- Python: Numpy, Pandas, Requests, JSON, Matplotlib, Seaborn, Tweepy

# Data Gathering
- twitter_archive. This file was provided by Udacity as part of the Nanodegree program, 
it is the WeRateDog's archive from Twitter. 
The file is a csv and was imported using pd.read_csv().
- image_predictions. This file contains image predictions gathered from using a neural network. 
It was provided by the website
https://d17h27t6h515a5.cloudfront.net/topher/2017/August/599fd2ad_image-predictions/image-predictions.tsv. 
This item was read in using the requests library and the given url. 
The file was a tsv and was imported into the dataframe using pd.read_csv().
- tweet_data. This file contains the Tweet data. Using the Tweet ID's in the Twitter Archive I accessed 
information for every Tweet in the Twitter API using Tweepy and stored all the JSON data in a .txt file 
named tweet_json.txt.

# Data Assessing
## Data Quality Issues
- Timestamp was stored in string format. This needed to be changed to datetime.
- There are instances where the rating_demoninator has errors in the values. The standard rating_denominator is 10. 
Demoninator values needed to all be 10.
- Columns that contained information on retweet and reply data have large amounts of missing values. 
Retweets and reply data was not be used and therefore these columns were be deleted.
- The source column was a html string. This was replaced to be readable.
- The p1_dog values contained False values. These are images are not dogs are not need. All False values were removed.
- The p1 and p1_confidence columns are not descriptive names. These columns were changed to dog_breed and breed_confidence.
- The dog_breed column contained underscores and was improperly capitalized. The underscores were replaced with spaces and 
breed names were properly capitalized.
- All p2 and p3 columns were removed from the dataset because for analysis I was only concerned with the highest confidence.
- The jpeg_url column was removed because url's are included in the Archive Data Frame.
- Drop the old dog rank columns.
## Data Tidiness Issues
- Dog ranking columns (doggo, floofer, etc.) was merged to one column.
- Removed 181 retweets and 78 replies.

# Data Cleaning
## Data Quality Issues
- Changed to datetime using pd.to_datetime
- All rating demoninators were changed to 10 using a lambda function
- Drop columns that deal with retweets and replies using .drop
- Source was made readable using .replace
- Removed false values using .drop
- Renamed dog_breed and breed_confidence using .rename
- Cleaned up names using .replace and .str.title
- All p2 and p3 columns were removed and p1_dog was removed using .drop
- Removed jpeg_url using .drop
- Drop the old dog rank columns using .drop
## Data Tidiness Issues
- Defined a new column called rank and filled in the values from the 4 old columns.
- Removed 181 retweets and 78 replies using the .drop

# Analysis
- What is the most popular year for WeRateDogs?
- What is the breakdown of Dog Rankings?
- What is the most popular dog breed?
- What platform provided the most Tweets?
- Is there a correlation between favorites and retweets? 
