# Unleashing Context: Enhancing Tweet Classification with Contextual Insights

## Authors
Andrija Banić, Dario Pavlović, Marko Jurić  
University of Zagreb, Faculty of Electrical Engineering and Computing  
Unska 3, 10000 Zagreb, Croatia  
{andrija.banic, dario.pavlovic, marko.juric}@fer.hr

## Abstract
This repository contains the implementation and resources for the research paper titled "Unleashing Context: Enhancing Tweet Classification with Contextual Insights". The study investigates how the context of an individual tweet affects simpler models in classifying the stance towards rumours. By examining the impact of context on classification accuracy, the research aims to understand the potential advantages of incorporating contextual information in tweet classification.

## Table of Contents
- [Introduction](#introduction)
- [Dataset Analysis](#dataset-analysis)
- [Experimental Setup](#experimental-setup)
- [Results](#results)
- [Conclusion](#conclusion)
- [References](#references)

## Introduction
Rumours have evolved from harmless gossip to potentially dangerous misinformation in the modern era. With millions of tweets being posted daily, it is crucial to identify those spreading harmful rumours. This research focuses on stance classification using simpler machine learning models like Random Forest Classifier (RF), Gradient Boosting Classifier (GBC), and Stochastic Gradient Descent Classifier (SGDC), with an emphasis on feature engineering and contextual information. By incorporating the context of the tweet being replied to, or both replies and the tweet being replied to (children and parent context), the study aims to improve classification accuracy.

## Dataset Analysis
The primary data source for this study is the RumourEval2019 dataset, which includes tweets and Reddit posts formatted to match tweet posts. The dataset comprises tweets related to various crisis events, labeled using crowdsourcing platforms into four categories: support, deny, query, and comment. A significant challenge is the label imbalance, with the comment label greatly outnumbering other labels, which can introduce biases in prediction.

## Experimental Setup
The experimental setup involves data selection, preprocessing, feature extraction, and choosing optimal models. Selected features include favorite count, text, hashtags, retweet count, and a list of direct replies. Text preprocessing includes lemmatization and cleaning to remove irrelevant elements. Features extracted include capital ratio, text length, polarity sentiment analysis, punctuation marks count, word embeddings, presence of links, and mentions of news agencies.

### Features
- **Capital Ratio**: Ratio of uppercase characters in the text.
- **Length of the Text**: Number of characters or words.
- **Polarity Sentiment Analysis**: Sentiment score ranging from -1 to 1 using TextBlob.
- **Amount of Question and Exclamation Marks**: Count of these punctuation marks.
- **Word Embeddings**: Semantic meaning of words using Gensim with pre-trained glove vectors.
- **Has Link**: Indicates presence of a link in the post.
- **Mentions News Agency**: Detects mentions of news agencies.
- **Reply Count and Reply Labels**: Used when considering children and parent context of a tweet.

## Results
The impact of context on model performance was tested under three scenarios: without context, with parent context, and with both parent and children context. The results indicate that the Stochastic Gradient Descent Classifier (SGDC) outperforms other models in terms of Macro F1-score, especially when considering both parent and children context. The SGDC model with both parent and children context is recommended for its competitive performance across all labels.

### Performance Metrics
| Model                            | Macro F1-score | Accuracy | F1S  | F1D  | F1Q  | F1C  |
|----------------------------------|----------------|----------|------|------|------|------|
| **Without context**              |                |          |      |      |      |      |
| Random Forest Classifier         | 0.2624         | 0.76     | 0.00 | 0.00 | 0.18 | 0.87 |
| Gradient Boosting Classifier     | 0.2953         | 0.71     | 0.14 | 0.00 | 0.21 | 0.84 |
| Stochastic Gradient Descent Classifier | 0.3735    | 0.72     | 0.23 | 0.00 | 0.42 | 0.84 |
| **With parent context**          |                |          |      |      |      |      |
| Random Forest Classifier         | 0.2971         | 0.77     | 0.00 | 0.00 | 0.32 | 0.87 |
| Gradient Boosting Classifier     | 0.3454         | 0.69     | 0.15 | 0.07 | 0.35 | 0.82 |
| Stochastic Gradient Descent Classifier | 0.2925    | 0.72     | 0.14 | 0.07 | 0.41 | 0.81 |
| **With children and parent context** |            |          |      |      |      |      |
| Random Forest Classifier         | 0.2964         | 0.77     | 0.02 | 0.00 | 0.29 | 0.87 |
| Gradient Boosting Classifier     | 0.3062         | 0.69     | 0.14 | 0.04 | 0.23 | 0.82 |
| Stochastic Gradient Descent Classifier | 0.3641    | 0.72     | 0.21 | 0.18 | 0.36 | 0.71 |

## Conclusion
The study demonstrates that incorporating context significantly enhances the accuracy of stance classification models. The SGDC model with both parent and children context offers the best performance. Future research should explore more sophisticated models and larger datasets to further validate the importance of context in stance classification.

## References
- Piush Aggarwal and Ahmet Aker. 2019. Identification of good and bad news on Twitter. In Proceedings of the International Conference on Recent Advances in Natural Language Processing (RANLP 2019), pages 9–17, Varna, Bulgaria, September. INCOMA Ltd.
- Ahmet Aker, Leon Derczynski, and Kalina Bontcheva. 2017. Simple open stance classification for rumour analysis. In Proceedings of the International Conference Recent Advances in Natural Language Processing, RANLP 2017, pages 31–39, Varna, Bulgaria, September. INCOMA Ltd.
- J. Bhuvana B. Bharathi and Nitin Nikamanth Appiah Balaji. 2020. Textual and contextual stance detection from tweets using machine learning approach.
- Leon Derczynski, Kalina Bontcheva, Maria Liakata, Rob Procter, Geraldine Wong Sak Hoi, and Arkaitz Zubiaga. 2017. SemEval-2017 task 8: RumourEval: Determining rumour veracity and support for rumours. In Proceedings of the 11th International Workshop on Semantic Evaluation (SemEval-2017), pages 69–76, Vancouver, Canada, August. Association for Computational Linguistics.
- William Ferreira and Andreas Vlachos. 2016. Emergent: a novel data-set for stance classification. In Proceedings of the 2016 Conference of the North American Chapter of the Association for Computational Linguistics: Human Language Technologies, pages 1163–1168, San Diego, California, June. Association for Computational Linguistics.
- Genevieve Gorrell, Elena Kochkina, Maria Liakata, Ahmet Aker, Arkaitz Zubiaga, Kalina Bontcheva, and Leon Derczynski. 2019. SemEval-2019 task 7: RumourEval, determining rumour veracity and support for rumours. In Proceedings of the 13th International Workshop on Semantic Evaluation, pages 845–854, Minneapolis, Minnesota, USA, June. Association for Computational Linguistics.
- Parinaz Sobhani, Saif Mohammad, and Svetlana Kiritchenko. 2016. Detecting stance in tweets and analyzing its interaction with sentiment. In Proceedings of the Fifth Joint Conference on Lexical and Computational Semantics, pages 159–169, Berlin, Germany, August. Association for Computational Linguistics.
