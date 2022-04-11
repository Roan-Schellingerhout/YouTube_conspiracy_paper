# YouTube conspiracy paper 
#### Author: Roan Schellingerhout
#### Co-authors: Davide Beraldo, Maarten Marx


# [Link to paper](**TODO once published**)

### Research question: _How does YouTube’s recommendation system treat conspiracy-classified content based on personalized watch patterns?_ 

### Sub-questions: 
 - RQ1: Do watch strategies signaling interest towards conspiracy content increase the proportion of conspiracy content being recommended? 
 - RQ2: How persistent are these effects? 
 - RQ3: How do specific users’ watch strategies, making use of more or less personalized inputs, influence these recommendation patterns?

### Method:
Using python, twenty different YouTube accounts watch videos and, after every watched video, keep track of how many conspiracy videos are recommended to them on their YouTube homepage. To label videos as conspiracy videos, there are two possibilities. Firstly, there is a dataset with nearly 2500 YouTube channels that have manually been labeled as conspiracy channels (and an additional 4000 that have been labeled as something else); a video uploaded by such a channel will count as a conspiracy video. Secondly, for videos not made by channels from within this dataset, a machine learning classifier will be used in order to determine whether or not a video can be seen as a conspiracy video. 

Videos are watched according to four different watch strategies:
  - Random non-conspiracy videos (control group);
  - Random conspiracy videos from a dataset;
  - Five similar conspiracy video from a dataset, followed by the top recommended conspiracy video that appears next to the video being watched;
  - Five similar conspiracy video from a dataset, followed by the top recommended conspiracy video that appears on the user's YouTube homepage. 

Each watch strategy will be used by five different accounts. 

In order to simulate real-world behaviour, the average watch time for videos will be normally distributed, with an average of 60% and a standard deviation of 15% [(Park et al., 2016)](https://ojs.aaai.org/index.php/ICWSM/article/view/14781/14630). 
By running the experiment like so, it will be possible to find how many conspiracy videos are recommended to a user, for each watch strategy, after each amount of watched videos. Thereby, it will be possible to find how quickly the YouTube algorithm starts preferring conspiracy content per watch strategy.

## Index:
### Notebooks  
  **data**
  - Random tests.ipynb: some random tests/descriptives about the data. 

  **Data Collections**
  - Download_videos.ipynb: Uses the YouTube API to download titles, description, and transcripts of the latest 10 videos of each channel in the dataset
  - Dataset.ipynb: Converts the original dataset (channel_review.csv) to a usable csv-file (dataset_boolean and dataset_tags)  
  - Clean_data.ipynb: Cleans the data from uploads.csv.
  - Descriptives.ipynb: Contains some descriptives about the dataset. 
  
  **Machine Learning**
  - Video_ML.ipynb: Hyperparameter tuning for five different classifiers (and an ensemble), based on the title, description, transcript, channel description, and channel keywords of each video. 
  - Predictions.ipynb: Predicting which recommendations are conspiracy videos and then analysing the videos accordingly. 

  **YouTube experiment**
  - Experiment.ipynb: The actual experiment. Automatically logs into a Google account and starts watching a certain type of videos, based on the user's assigned watch strategy. 
  
  **Results**
  - Hyperparameters.ipynb: Displays performance of optimal hyperparameters for each classifier. 
  - Results recommendations.ipynb: Downloading all needed information about the recommendations (title, description, etc.), cleaning it, and converting it to TF-IDF. 
  - Recommendation network.ipynb: Create a directed network of all videos. Nodes are videos. An edge between nodes indicates the second video was recommended to at least one user directly after watching the first video. 
  
### [CSVs](https://amsuni-my.sharepoint.com/:f:/g/personal/roan_schellingerhout_student_uva_nl/EgvhDGC6LrlInv1OpVVWvG4B_b_u3UR0ev_dKuPhQb0icw?e=uA9ogB)
- channel_review.csv: The original dataset with judge decisions.
- channels.csv: List of channels + conspiracy as a boolean. Includes: channel ID, username, country, keywords, upload-ID (playlist of uploads), conspiracy (boolean)

- uploads.csv: 10 uploads for each channel in channels.csv; includes uploader, title, description, transcript and conspiracy (True/False) 
- training_videos.csv: uploads.csv, but cleaned. Includes channel description and keywords, balanced classes, text translated to English, words stemmed, everything turned into lowercase.

- recommendations_strat.*.csv: the recommendations for a given strategy for experiment 1 or 2. Includes user, number of videos watched, video ID, views, likes, dislikes, duration, and full text of the video. 
