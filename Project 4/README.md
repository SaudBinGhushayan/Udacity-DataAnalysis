# Report on wrangling-act.ipynb
most of data in the real world comes messy and dirty so in this project I completed the whole wrangling process for Gathering to cleaning and storing 
so here I'm going to describe briefly about my wrangling process 

### First (Gathering) :
I downloaded the `twitter_archive_enhanced.csv` manually this file contains the data that I'm going to assess and clean after that I downloaded `image_predictions.tsv` programmatically by the given url that is in udacity project page , after that I coudn't query Twitter API to get the `json-data.txt` the issue was I had some problems with setting the developer account for twitter so instead I put the code in udacity project page and used the `json-data.txt` that udacity provided as well .

The `json-data.txt` file was in json format but the problem is that it's a text file so in order to use the functionality of the json file I loaded it as json file again .

The only two information that I needed it is `retweet_count` and `favorite_count` so I took it from the json file and appended it with it's `tweet_id` into a temporary list after that a created pandas dataframe `additional_data` that holds only `tweet_id` , `retweet_count` and `favorite_count` .

### Second (Assessing) :
in this part of the wrangling process and assessed all the datasets visually and programmaticaly starting with the  `twitter_archive` to `additional_data`.
####  `twitter_archive`  Quality issues:
I found that there a lot of quality issues in this dataset , the name column holds invalid name , the datatypes of `tweet_id` and `timestamp` column isn't right , the source column comes with a long url instead it should be only the source of the tweet , no null entries for (name doggo floofer  pupper puppo) columns , row 313 comes with wrong rating the denominater is 0 which is invalid after searching the `json-data.txt` manually using sublime text I found that the true rating should be 13/10 , expanded_url column have missing values which isn't right ,I noticed that their some rows with two styles of dogs and after searching manually I found that it came by mistake 
and also row 531 and 889 have two dogs so the name column should hold their name .

####  `twitter_archive`  Tidiness  issues:
the structure of this dataset is not right because dogs should hold only one column that tells their style instead in this dataset their are 4 columns each type of dog has it's own column so to make this right we must megre the columns together to be only one column and delete the previous 4 columns .

there are a lot of unnecessary columns ('in_reply_to_status_id' , 'in_reply_to_user_id' , 'retweeted_status_id' 'retweeted_status_user_id' , 'retweeted_status_timestamp') that hold a lot of missing values and I don't need them for analysis so I dropped them

`additional_data` should be merged with this dataset since they are related to each other .

####  `image_predictions`  Quality issues:
this dataset came clean there only few changes to make , I found that the `tweet_id` column is int instead of object and after searching the rows and columns I found that there two rows in `jpg_url` column that ins't a jpg url .

####  `image_prediction`  Tidiness  issues:
because we only need the tweets that comes with pictures so we need to merge `twitter_archive` with this dataset to make that happen.

####  `additional_data`  Quality  issues:
in this dataset there is only one problem which is the `tweet_id` is int instead of object.

### Third (Cleaning and Storing) :
I noted all the necessary cleaning effort that I needed and started with `twitter_archive` table that has 8 quality issues , `image_predictions` that has 2 quality issues and `additional_data` that has only one quality issue.

after cleaning the quality issues now it's turn to fix the tidiness of our dataset starting with`twitter_archive` and ending with `additional_data`

After finishing cleaning now it's time to store out dataset so I stored the merged and cleaned datasets into a SQLite database file `twitter_archive_master.db`.


# Report on the insights and visualization

After cleaning our dataset I came up with three answers that realy intrests me :
- The number of tweets with rating equals or more that one 
- What's the relation between `retweet_count` and `favorite_count` 
- What's the accuracy for the algorthim in it's first , second and last predictions


### The number of tweets with rating equals or more that one
To know what's the number of the tweets that have more than or equal to one is by filtering the rows that the `rating_numerator` is great or equal to the `rating_denominator` , and looks like we have `1659` rows that have "Good Rating" and `416` have "Bad Rating" , as shown below I plotted these values in a Horizonatal bar chat to get a better visual on them
![image](https://user-images.githubusercontent.com/82407781/129191469-bfdde317-2934-4d0e-b19d-73a4258a2632.png)

### What's the relation between retweet_count and favorite_count

To know the relation between two variables your best choice is to plot a `Scatter PLot` and in this case I plotted a scatter plot to know the relationship between `retweet_count` and `favorite_count` , as shown below the Scatter Plot seems to be strongly positve which mean that the relationship between `retweet_count` and `favorite_count` is strong (whenever a tweet have high retweets it will have high likes)

![image](https://user-images.githubusercontent.com/82407781/129191522-e65a8e88-f2fa-4a58-8de5-dba4b756c28a.png)

### What's the accuracy for the algorthim in it's first , second and last predictions
To know the algorthim confident accuracy in each predection I'm going to show you a Line Chart to help with the visualization and understanding for the confident accuracy in each prediction

- Here is the Confident Accuracy in each Predection (using moving average in each 50 value)

![image](https://user-images.githubusercontent.com/82407781/129191546-7cd4fd94-dcd3-4f6c-8490-de11d2db7e45.png)

In the above line chart it looks like the algorithm in it's first prediction is very high but in the second and last is very low .

the first time the algorithm predicts have more chance to predict right than the second and third time 

- Here is the Confident Accuracy in each Predection (without the moving average)

![image](https://user-images.githubusercontent.com/82407781/129191564-f3750230-32f5-46c4-a15e-d607b8739aa2.png)

