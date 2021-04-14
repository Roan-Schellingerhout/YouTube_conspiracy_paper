# Bachelor_scriptie 
#### Roan Schellingerhout

### Research question: _What is the impact of different watch strategies on the number of conspiracy videos that have to be watched until a user's YouTube-recommendations start preferring conspiracy content?_ 

(Preferring: the amount of conspiracy videos present in the recommendations is significantly higher than that of the baseline.)

### Sub-questions: 
  - With which watch strategy do YouTube recommendations start preferring conspiracy videos the quickest?
  - How long does it take for a YouTube user to get out of a filter bubble, once they find themselves in one?
  - What type of classifier performs the best when it comes to labeling conspiracy videos on YouTube?

### Methode:
Using python, twenty different YouTube accounts will watch videos and, after every watched video, keep track of how many conspiracy videos are recommended to them on their YouTube homepage. To label videos as conspiracy videos, there are two possibilities. Firstly, there is a dataset with nearly 2500 YouTube channels that have manually been labeled as conspiracy channels (and an additional 4000 that have been labeled as something else); a video uploaded by such a channel will count as a conspiracy video. Secondly, for videos not made by channels from within this dataset, a machine learning classifier will be used in order to determine whether or not a video can be seen as a conspiracy video. 

Videos will be watched according to four different watch strategies:
  - Random non-conspiracy videos (control group);
  - Random conspiracy videos from a dataset;
  - One random conspiracy video, followed by recommended videos that appear next to the video being watched;
  - One random conspiracy video, followed by recommended videos that appear on the user's YouTube homepage. 

Each watch strategy will be used by five different accounts. 

In order to simulate real-world behaviour, the average watch time for videos will be normally distributed, with an average of 60% and a standard deviation of 15% [(Park et al., 2016)](https://ojs.aaai.org/index.php/ICWSM/article/view/14781/14630). 
By running the experiment like so, it will be possible to find how many conspiracy videos are recommended to a user, for each watch strategy, after each amount of watched videos. Thereby, it will be possible to find how quickly the YouTube algorithm starts preferring conspiracy content per watch strategy. By applying a statistical analysis (ANOVA), this result can be tested for statistical significance. 

## Index:
### Notebooks  
  **Data Collections**
  - Download_videos.ipynb: Uses the YouTube API to download titles, description, and transcripts of the latest 10 videos of each channel in the dataset
  - Dataset.ipynb: Converts the original dataset (channel_review.csv) to a usable csv-file (dataset_boolean and dataset_tags)  
  
  **Machine Learning**
  - Video_ML.ipynb: Hyperparameter tuning for five different classifiers (and an ensemble), based on the title, description, transcript, channel description, and channel keywords of each video. 

  **YouTube experiment**
  - Experiment.ipynb: The actual experiment. Automatically logs into a Google account and starts watching a certain type of videos, based on the user's assigned watch strategy. 
  
  
### [CSVs](https://amsuni-my.sharepoint.com/:f:/g/personal/roan_schellingerhout_student_uva_nl/EgvhDGC6LrlInv1OpVVWvG4B_b_u3UR0ev_dKuPhQb0icw?e=uA9ogB)
- channel_review.csv: The original dataset with judge decisions  
- channels.csv: ID, username, country, keywords, upload-ID, conspiracy (boolean)  

- uploads.csv: 10 uploads for each channel in channels.csv; includes uploader, title, description, transcript and conspiracy (True/False) 
- training_videos.csv: uploads.csv, but cleaned. Includes channel description and keywords, balanced classes, text translated to English, words stemmed, everything turned into lowercase