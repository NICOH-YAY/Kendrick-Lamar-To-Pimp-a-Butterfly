📖 Project Overview


This project uses Machine Learning to explore a peronsal question regarding my favorite rap album. Where does Kendrick Lamar's album To Pimp a Butterfly (TPAB) thematically fit within universe of rap music?

   To answer this, I built machine learning models. First, I used k-means clustering to discover the natural, underlying thematic groups within a large dataset of 16,992 rap songs (non TPAB songs). Using said classification, I then used K-Nearest Neighbors (KNN) to place each of TPAB's 16 tracks into this newly mapped landscape. 
The result is a visual and analytical breakdown of the album's thematic structure which highlights which of its songs resonate with broader rap themes and which stand uniquely apart.

🎧 Why This Album?


TPAB has redfined what hip-hop can be, using unorthodox beats as well as talking about current-day events. Beyond it's Grammy-winning work, it weaves in complex, novel-like story about materialism, systemic oppression, black identity, and the painful journey toward self-love and redemption.

The simple workflow was as follows:
I first compiled datasets from Kaggle using python, I wrangled them into CSV files and then imported them into R studio where I used the latest version of R (2026) to clean the data with tidyverse, dpylr and created visualizations with ggplot2 and t-SNE. Struggles with KNN-code were consulted using DeepSeekR1.

⚙️ How It Works:



   To compare songs, I first had to translate lyrical content into quantifiable features.
Thematic Features: I created custom dictionaries for eight themes (e.g., social_justice, personal_identity, material_ambition) and calculated how densely these words appear in each song's lyrics.
Sentiment & Audio Features: I analyzed the emotional sentiment of the lyrics and combined it with standard audio features like danceability, tempo, and energy, which describe the musical properties of a track.

With all songs quantified, I needed to find the natural groupings in the broad rap dataset. This is an unsupervised task the algorithm looks for patterns without any pre-existing labels.
I used k-means clustering which is an algorithm groups similar data points together by finding central points ("centroids") that minimize the distance to all points in a cluster.
Using the "elbow method" on a plot of clustering compactness, I determined that k=4 clusters was optimal for this dataset. The algorithm grouped the 16,992 rap songs into four distinct thematic clusters that form the foundational map of this project.
Finally, I treated each TPAB song as a new, unlabeled data point and asked: "Based on the map we just created, which neighborhood does this song belong in?"
I used KNN classification, a supervised method. For a given TPAB song, the algorithm finds its k=5 closest neighbors from the rap song dataset. It then assigns the TPAB song to the most common cluster among those five neighbors
Each TPAB song received a thematic classification (e.g., "Social Justice Focus") and a confidence score (e.g., 0.8), which reflects how unanimous the vote from its five nearest rap song neighbors was.

 🧠 What I Learned: k-Means vs. KNN


 
   A fundamental insight from this work is understanding how k-means clustering and K-Nearest Neighbors (KNN), though similarly named, serve distinct and complementary purposes. k-means is an unsupervised learning algorithm; its core task is discovery, as it analyzed my dataset of 16,992 unlabeled rap songs to find and define four natural, hidden groupings, effectively drawing a "thematic map" of the genre. In contrast, KNN is a supervised classification method; it required those pre-defined cluster labels to perform its task, which was to take each new TPAB song and predict its thematic group by finding the five most similar rap songs from my existing map. You can think of k-means as the cartographer that draws the constellations in the night sky, while KNN is the navigator that looks at a new star and determines which constellation it belongs to based on its closest neighbors. 

 ⚠️ Limitations & Challenges


 
   While insightful, this project has some important limitations, primarily due to data constraints.
he most significant limitation is that the rap song dataset was pre-existing and static. At the time of development, the Spotify Web API was down. A pre-configured dataset means the analysis is a snapshot and not easily replicable or expandable with newer music.
The thematic dictionaries, while thoughtful, are ultimately simplified. Human language and symbolism (like the "caterpillar/butterfly" metaphor central to TPAB) are nuanced, and a bag-of-words model cannot capture that context

🚀 Future Iterations & Practical Improvements



   Integrate the Spotify API: The most impactful upgrade would be to rebuild the data pipeline using the official Spotify Web API
Implementing NLP techniques like topic modeling (LDA) or sentiment analysis on full lyric transcripts could capture more complex thematic and emotional content.
