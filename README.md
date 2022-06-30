# Topic-modeling-Billboard-Hot-100
Topic modeling the Billboard Hot 100 throughout the ages (1950-2021) using LDA and insights from songfacts.com to define distinct topics within the chart.

The paper performs a topic modeling comparison based on two different sources of
corpa: song lyrics and the about section from Genius (user generated content). We assign titles 
for each defined topic with the aid of Songfacts data, before showing a word cloud distribution among each topic. At last, we
display pyLDAvis in order to comment on the closeness of the identified topics.

**t-sne plot of the identified groups for both lyrics and user generated content**
<img align="center" img width="500" height="600" alt="image" src="https://user-images.githubusercontent.com/64472833/176750167-e09f1a65-0529-4adf-8add-eb2b76ab22f8.png">

The main trait of this tool is its ability to neatly present high-dimensional data
in two- or three-dimensional space. The method lying behind that is a state-of-art non-linear
algorithm, that is controlled by the perplexity parameter, setting the importance between local
clusters and overall data. One important thing to bear in mind when analyzing t-SNE output is
the fact that the distances between outlined clusters do not represent any specific value.

**The following section uses the lyrics data only**

Inspired by Choi et al. (2016), we resorted to Songfacts.com to support our topic modeling
decision-making. In total, 3.172 songs were both part of the Billboard Top 100 (1950-2021) and
of the labeled about section in Songfacts.
These 3.172 labels will aid us in interpreting the different topic allocations performed by our
LDA model. Tables 2 and 3 display the most informative labels assigned by Songfacts per topic
cluster defined by the model, alongside the topic title we assigned:

<img align="center", img width="350", height="400", alt="image" src="https://user-images.githubusercontent.com/64472833/176750954-beae0e3d-8f21-44da-b5c9-ae6e6028c318.png">

<<img align="center", img width="500", height="600", alt="image" src="https://user-images.githubusercontent.com/64472833/176750994-e6f6c07f-f12e-4fc5-8ecb-21e228f8a4b0.png">

Analyzing the table above, we can see that the label with the most tags was Topic 1. We
found it to contain songs that mainly revolved around romantic relationships, under a negative
perspective ("love triangle", "regret", "unhealthy relationship"). Topic 6 also seemed to be
related to romantic relationships, but on a positive angle ("Finding Love", "Flirting", "Desire").
Looking at the most informative Songfact labels, Topic 1 hints towards overlapping with
Topic 0. Although the latter is a smaller group, it conveys a sentiment similar to Topic 1, but
on a broader interpretation (not restricted to romance). We see that the most informative tags
here were "Getting out of a bad relationship", "Suicide", "alcohol" and "Depression", which
characterizes struggles in general. Topic 3, the second most populous, contained the majority
of songs about "Dancing" and "Night out", which led us to classifying under the "Nightlife"
category.
A similar analysis was implemented across all 8 topics, leading to clearly defined labels. An
exception, however, is Topic 5, which failed to provide insightful labels.
A caveat to these findings are the fact that we do not have labels for all the data. The
assigned labels should therefore be interpreted as what some songs found in these topics are
about, not what the whole cluster is about. Nevertheless, it provides some useful insights as to
what the topics try to convey.

<img align="center", img width="500", height="600", alt="image" src="https://user-images.githubusercontent.com/64472833/176751151-73e2fe4b-59e1-4b57-8af3-7608c21fd503.png">

To further substantiate the classification of the topics we provide a distribution of the most
frequent words in each group. The word cloud allows for appealing visualizing and was therefore
used. The cloud validated most insights obtained from the Songfacts mapping. Topic 3, for
instance, displays high frequency of words associated with nightlife, such as "Live", "Night", and
"Play". Topic 5, which we failed to assign a label by using the data from Songfacts, looks from
the distribution to be centred around physical attraction, with words as "Love" and "body" being
prominent. We can also see that topic 7 is related to "Fame and success" also seems reasonable,
taking into account the high frequency of words such as "Rock", "Sign" and "Young".

Proposed in Sievert and Shirley (2014), the LDAvis is a R and Python built-in interface that
allow researchers to understand topic-term relationships in LDA models. Figure 8 displays our
model through the LDAvis visualisation.
<img align="center", img width="300", height="400", alt="image" src="https://user-images.githubusercontent.com/64472833/176751290-42be361e-5938-437f-a6b3-dcfd64245997.png">

The size of each circle is proportional to the marginal distribution of the respective topic
on the corpus. We can also visualize the inter-topic distances and validate the assumptions we
reached with the graphs so far. It is worth noting that this graph displays topics from 1-8, where
we have dealt with topics from 0-7. This section will use the same notation as previous, referring
to Topic 1 in the figure as Topic 0.
The main insight that can be drawn from the LDAvis displayed above is that topics 0, 1
and 5 are closely related, which corroborates the analysis based on Songfacts and the word
cloud. Topic 1, related to a negative aspect on romantic relationships, seems to be the common
ground for topics 5 and 0. Although, by using the word cloud, we found Topic 5 to be centred
around physical attraction, examining the LDAvis shows a different story. The plot hints towards
Topic 5 as dealing more with negative thematics. The likelihood is that the true distribution
is somewhere in between the two approaches, which further emphasises the importance of using
multiple tools for conveying topic information.
The LDAvis also points towards an overlapping between Topics 2 and 3. This goes against
what was spotted by analyzing the word cloud and the Songfacts data, since the categories "Deep
Topics" and "Nightlife" seem to be contrasting.

In this paper we have used NLP techniques to provide a deep dive into the Billboard Hot 100
list across the ages. We have shown that by leveraging LDA on pre-processed lyrics we were able
to separate the songs into 8 distinct topics. By investigating the most frequent words in each
category and by using externally labeled data from songfacts we were able to convey interesting
findings about the composition of the topics. We have shown that song thematics mainly address
various aspects of romantic relations, as well as life-style topics, such as Nigthlife and Fame and
Success.
We also show that the lyrics is a better foundation for performing the topic modelling than
the user generated about section from Genius. This is contrasting to previous findings, Choi
et al. (2014) Choi et al. (2016), which tend to favour user generated content over lyrics for topic
modelling. We found the user generated content to carry less descriptive information than the
lyrics, and than initially hypothesised. It was also shown in this paper that the lyrics allowed
for better separation into fewer groups. This must be caveated with the fact that by extracting
the user generated content from Genius, we have obtained this aspect from a different source
than most previous work. It is also worth noting that the better performance of lyrics might
be partially explained by the number of data instances retrieved. In our study we managed to
obtain 40% more lyrics than about sections.
The groupings provided by this paper can be useful for machine learning models that have
the task of predicting the topic of a given song. The work here will allow for easier labelling of
the data, but first and foremost it outlines knowledge about what the different topics encompass,
something that is crucial for understanding and improving models on the topic. We encourage
others to build on this work by producing models for prediction, where a natural step would be
comparing the predictive powers of models such as Support Vector Machine (SVM), BiLSTM,
Nonnegative matrix, and k-nearest neighbour. An important step here would be how to address
the class imbalance between our groups, which will pose a challenge. Different techniques such
as under sampling, specifying a custom loss function, and synthetically generating new instances
using the SMOTE algorithm can be employed. The likelihood is that a combination of these are
needed.
Regarding the limitations of this paper, we emphasise the fact that the model is not trained
on all the songs of Billboard Hot 100 in the time range. This was partially due to exclusion
of songs in the pre-processing, for instance non-English songs, and the fact that the site used
for scraping, Genius, did not have the content for several of the songs. The last point was
particularly true for the about sections, where the data was available for less than half of the
songs of the Hot 100’s list. Although to a lesser degree, this problem also troubled the lyrics,
in particular the earlier years of our scope. With the benefit of hindsight we should have used
another source for the lyrics data as there are several sources that are easy to access.
The fact that the scraping returned merged words hampered the performance of the NER. It
would have performed better if we had the initial capitilazied letters in place, this was not the
case on our data since the word tokenizer used lowercased all text. To address this problem we
could have included a function that re-capitalizes the words, based on the entries in the scraped
corpus.

