# Bachelor_scriptie 
#### Roan Schellingerhout

### Research question: _What is the impact of different watch strategies on the number of conspiracy videos that have to be watched until a user's YouTube-recommendations start preferring conspiracy content?_ (Preferring: the amount of conspiracy videos present in the recommendations is significantly higher than that of the baseline.)
### Sub-questions: 
  - With which watch strategy do YouTube recommendations start preferring conspiracy videos the quickest?
  - How long does it take for a YouTube user to get out of a filter bubble, once they find themselves in one?
  - What type of classifier performs the best when it comes to labeling conspiracy videos on YouTube?

### Methode:
Met behulp van Python zullen twintig YouTube accounts video’s gaan kijken en na elke video bijhouden voor welk deel hun ‘aanbevolen’-pagina uit complotvideo’s bestaat. Om video’s als complotvideo’s te kunnen bestempelen, zijn er twee mogelijkheden. Als eerst is er is een dataset met daarin 3000 YouTube-kanalen die door mensen zijn bestempeld als complotkanalen, dus een video die geüpload is door een dergelijk kanaal, zal tellen als complotvideo. Daarnaast, voor video’s die buiten deze kanalen vallen, zal een ensemble van machine learning classifiers gebruikt worden, om zo te bepalen welke video’s wel en niet als complotvideo’s gezien kunnen worden. 

Er zullen vier kijkstrategieën zijn:
  - Willekeurige niet-complotvideo’s (controlegroep);
  - Willekeurige complotvideo’s uit een dataset;
  - Eerst een willekeurige complotvideo en vervolgens telkens een aanbevolen video naast die video (gekozen o.b.v. propensity weighting);
  - Eerst een willekeurige complotvideo en vervolgens telkens een aanbevolen video op de YouTube-homepage van het account (gekozen o.b.v. propensity weighting).
 
Elke kijkstrategie zal door vijf verschillende accounts worden uitgeprobeerd.  

Om het gedrag van echte gebruikers zo realistisch mogelijk te simuleren, zal de gemiddelde kijkduur van video’s normaal verdeeld worden, met een gemiddelde van 60% en een standaardafwijking van 15% [(Park et al., 2016)](https://ojs.aaai.org/index.php/ICWSM/article/view/14781/14630). 
Door deze opzet kan er, voor elke kijkstrategie, na elk aantal bekeken video’s, worden berekend welk deel van de aanbevolen video’s bestaat uit complotvideo’s, om zo te zien hoe snel complot-filterbubbels ontstaan voor elke strategie. Daarna kan er met behulp van statistische analyse gecontroleerd worden of één of meerdere van de kijkstrategieën significant sneller zorgt voor een filterbubbel. 

## Index:
### Notebooks  
  **Data Collections**
  - Download_videos.ipynb: roept YouTube API aan om titels, beschrijvingen en transcripts te downloaden van de kanalen uit de dataset.  
  - Dataset.ipynb: Zet de originele (channel_review.csv) om in een bruikbare csv (dataset_boolean en dataset_tags)  
  
  **Machine Learning**
  - Channel_ML.ipynb: Machine learning met informatie beschikbaar op het kanaal zelf --> description, keywords, etc.  
  - Video_ML.ipynb: Machine learning met informatie over video's --> titel, beschrijving, transcript, etc.  

  **YouTube experiment**
  - Experiment.ipynb: Het daadwerkelijke experiment. Eerst wordt er ingelogd op een google account, vervolgens wordt er, afhankelijk van de usertype, een bepaald type video's gekeken. 
  
  
### [CSVs](https://amsuni-my.sharepoint.com/:f:/g/personal/roan_schellingerhout_student_uva_nl/EgvhDGC6LrlInv1OpVVWvG4B_b_u3UR0ev_dKuPhQb0icw?e=uA9ogB)
- channel_review.csv: originele dataset, met judge-beslissingen e.d.  
- channels.csv: ID, username, country, keywords, upload-ID, conspiracy (boolean)  

- uploads.csv: 10 uploads per kanaal uit channels.csv, met uploader, titel, description, transcript en conspiracy ja/nee  
- training_videos.csv: uploads.csv, maar dan opgeschoond. Klassen gebalanceerd, alle tekst vertaald naar het Engels, woorden gestemd, alles lowercase.
