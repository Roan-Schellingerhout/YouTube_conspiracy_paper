# bachelor_scriptie  
  
  
### Notebooks  
- Download_videos.ipynb: roept youtube API aan om titels, beschrijvingen en transcripts te downloaden van de kanalen uit de dataset.  
- Dataset.ipynb: Zet de originele (channel_review.csv) om in een bruikbare csv (dataset_boolean en dataset_tags)  
  
- Channel_ML.ipynb: Machine learning met informatie beschikbaar op het kanaal zelf --> description, keywords, etc.  
- Video_ML.ipynb: Machine learning met informatie over video's --> titel, beschrijving, transcript, etc.  
  
  
### CSVs  
- channel_review.csv: originele dataset, met judge-beslissingen e.d.  
- channels.csv: ID, username, country, keywords, upload-ID, conspiracy (boolean)  
- dataset_boolean.csv: kanalen uit channel_review, maar dan gecleaned met booleans voor conspiracy ja/nee  
- dataset_tags.csv: kanalen uit channel_review, maar dan gecleaned met individuele tags ipv lijst   
- uploads.csv: 10 uploads per kanaal uit channels.csv, met uploader, titel, description, transcript en conspiracy ja/nee  
