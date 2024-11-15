# Mitigating-socio-demographic-bias

## Mitigating socio-demographic bias in language-based machine learning models of depression
Patients with depression depict differences in language use compared to their healthy counter-
parts, such as an increased use of first-person singular pronoun use, increased use of negative
emotion words, and decreased use of positive emotion words [7]. Yet, the use of language also
carries evidence on the speaker’s socio-demographic characteristics, such as gender, race, and
ethnicity. For example, in a study that analyzed English text, women used more words related
to psychological and social processes, while men referred more to object properties and imper-
sonal topics [6]. A meta-review further found that women were more likely to use more tentative
language than men [4]. This study explores the effectiveness of language-based ML models for
automatically estimating the degree of depression severity, as well as gender and race/ethnicity
bias in these models.


The data for this study comes from the Extended Distress Analysis Interview Corpus (E-DAIC)
dataset [2], which contains clinical interviews designed to support the diagnosis of psycho-
logical distress conditions such as depression. More details about the dataset, including the
experimental setup and type of data, can be found here: https://dcapswoz.ict.usc.edu/.
The data uploaded on CANVAS includes interview transcripts from 190 participants. The
‘DAIC demographic data.xlsx’ file contains three tabs with information on participants’ gen-
der, race/ethnicity, and depression severity (PHQ Score). The folder ‘E-DAIC Transcripts’
includes csv files (one per participant) with the transcript data. Each filename, named as
‘x Transcript.csv’, where x is the participant ID, includes the transcripts from the responses
provided by participant x during the clinical interview. In the following analysis, participants
will be grouped by gender, including female and male participants, and by race/ethnicity, includ-
ing African American, Hispanic, and White American participants, along with the intersections
of these categories. Due to the small sample size of the other groups, the remaining
participants will be excluded from this analysis.

# Questions

Randomly split the participants into 5 folds and report results accordingly in the following
experiments.
## (a) (2 points) Extracting language features. 
Extract several language features from
the data. Include at least two of the following types of features, spanning different levels of
complexity:
• Syntactic vectorizers: count vectorizer (e.g., CountVectorizer from sklearn) transforming
a collection of text documents into a numerical matrix of word or token counts; TF-
IDF vectorizer (e.g., TfidfVectorizer from sklearn) incorporating document-level weighting,
which emphasizes words significant to specific documents’ part-of-speech features counting
the distribution of part of speech tags over a document
• Semantic features: sentiment scores (e.g., Vader, https://github.com/cjhutto/vaderSentiment),
topic distribution (using topic modeling), or named entities
• Advanced features: word embeddings, such as Word2Vec or BERT (e.g., pytorch-pretrained-
bert)) for capturing contextual meaning
Below are some additional resources that could be useful for feature extraction: NLTK toolkit
(https://www.nltk.org/); Google word2vec (https://code.google.com/archive/p/word2vec/);
2
Hugging Face (https://huggingface.co/); Jurafski & Martin, Speech & Language Process-
ing, Chapter 6: Vector Semantics and Embeddings (https://web.stanford.edu/~jurafsky/
slp3/6.pdf).


## (b) (2 points) Classifying for gender. 
Use one tree-based ML model of your choice and
one deep learning ML model of your choice to classify participants in terms of gender. Explore
a filter feature selection method of your choice to identify the n features that are the most in-
formative of gender based on the provided data. Experiment with different values of n. Please
report the simple classification accuracy A and balanced classification accuracy BA.
Note: The simple classification accuracy A and balanced classification accuracy BA are defined
as follows:
A = #correctly classified samples
total # samples
BA = 0.5 · #correctly classified samples for depression
total # samples for depression + 0.5 · #correctly classified samples for no depression
total # samples for no depression


## (c) (2 points) Classifying for race/ethnicity. 
Use one tree-based ML model of your choice
and one deep learning ML model of your choice to classify participants in terms of race/ethnicity.
Explore a filter feature selection method of your choice to identify the m features that are the
most informative of race/ethnicity based on the provided data. Experiment with different values
of m. Please report the simple classification accuracy A and balanced classification accuracy BA.


## (d) (2 points) Estimating depression severity. 
Use one tree-based ML and one deep
learning ML algorithm of your choice to estimate the degree of depression for each participant.
Explore a filter feature selection method of your choice to identify the k features that are the
most informative of depression based on the data. Please report the Pearson’s correlation r and
absolute relative error (RE) between the estimated and actual PHQ-8 scores for all participants
included, as well as separately by gender (i.e., female, male), race/ethnicity (African American,
White American, Hispanic), and their intersection (African American female, White American
female, etc.). Experiment with different values of k. Please discuss your findings (e.g., Is there
any overlap between the features that are the most informative of demographic characteristics
and the ones that are the most informative of depression severity? Are there differences in per-
formance among the different demographic groups based on gender, race/ethnicity, and their
intersection? For which demographic groups (gender×race/ethnicity combination) does the ML
model depict the worst performance?).
Note: The absolute relative error, RE, is defined as follows:
RE = |estimated PHQ-8−actual PHQ-8|
max(PHQ-8)


## (e) (2 points) Mitigating bias via reducing socio-demographic dependencies in fea-
tures. Remove the n most informative features of gender and the m most informative features
of race/ethnicity from the original feature set. Use the updated feature set and the same ML
models as in the previous questions to conduct depression classification. In addition to the
aforementioned feature selection, please use one more in-processing method to mitigate poten-
tial bias. Please report the results similar to (d) and discuss your findings.
Note: You can use the following toolbox for in-processing methods for de-biasing:
https://github.com/ahxt/fair_fairness_benchmark
Please discuss the results of the revised ML models grounded in your findings from question
3
### (d), after identifying the demographic group for which the ML model performed the worst.
Depending on the value of n and m, you can use the combination of features that are most
informative to gender and most informative to race/ethnicity, or the features that are common
between the two.


## (f ) (Bonus, 2 points) Experimenting with transformers. 
Use a pre-trained transformer- based model (e.g., quantized Llama, minGPT) to conduct depression severity estimation based
on the provided transcripts. Experiment with prompt engineering or task-specific prompts to
guide the model in adapting to each classification objective, including incorporating a few la-
beled example transcripts within the prompt. Please use the same evaluation metrics as in (d).
How does the performance of this model compare to the previous models? Please provide a
discussion for all participants and for different participant groups.
Note: You can find a useful github repo here: https://github.com/karpathy/minGPT


## (g) (2 points) Presentation. 
Create a presentation of your work. The presentation will
provide the main gist of your work, including the problem statement, your methodology, and
the main results from your experiments. Add visuals so that people understand the main
concepts. Each team will have 4 minutes to present, followed by 4 minutes of questions.
Note: Each team will present in class on December 2, 4, and 6 during class time (10.10-11pm
MT). The assigned time slot for your team has been announced on CANVAS. Participation
in the presentation for all three days (December 2, 4, 6) is mandatory will count
toward the in-class participation grade. Members from other teams will be called
on by name to ask questions during the presentations.


## (h) (2 points) Teamwork. 
Please follow the survey link below, in which you will need to discuss the level of engagement of your team members. The feedback that your team members
will provide for one another will be used as an indication of each member’s contribution to this
group assignment.
Survey Link: https://forms.gle/P2GuKRVmoUqfZ