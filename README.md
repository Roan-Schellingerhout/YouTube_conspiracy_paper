# bachelor_scriptie  
  
  
### Notebooks  
**Data Collections**
  - Download_videos.ipynb: roept youtube API aan om titels, beschrijvingen en transcripts te downloaden van de kanalen uit de dataset.  
  - Dataset.ipynb: Zet de originele (channel_review.csv) om in een bruikbare csv (dataset_boolean en dataset_tags)  
  
**Machine Learning**
  - Channel_ML.ipynb: Machine learning met informatie beschikbaar op het kanaal zelf --> description, keywords, etc.  
  - Video_ML.ipynb: Machine learning met informatie over video's --> titel, beschrijving, transcript, etc.  

**YouTube experiment**
  - Experiment.ipynb: Een notebook die inlogt op een google account en vervolgens YouTube videos gaat kijken
  
  
### [CSVs](https://amsuni-my.sharepoint.com/:f:/r/personal/roan_schellingerhout_student_uva_nl/Documents/scriptie?csf=1&web=1&e=Z06rpn)
- channel_review.csv: originele dataset, met judge-beslissingen e.d.  
- channels.csv: ID, username, country, keywords, upload-ID, conspiracy (boolean)  

- uploads.csv: 10 uploads per kanaal uit channels.csv, met uploader, titel, description, transcript en conspiracy ja/nee  
- training_videos.csv: uploads.csv, maar dan opgeschoond. Klassen gebalanceerd, alle tekst vertaald naar het Engels, worden gestemd, alles lowercase.
