# Text-Summarization
What is ROUGE?
ROUGE stands for Recall Oriented Understudy For Gisting Evaluation. It is essentially of a set of metrics for evaluating automatic summarization of texts as well as machine translation.It works by comparing an **automatically produced summary** or **translation** against a set of **reference summaries**(typically human produced).
Let us say, we have the following system and reference summaries:

**System Summary(what the machine produced)**
>the cat was found under the bed

**Reference Summary(gold standard -ususlly by humans)**
>the cat was under the bed

If we consider just the individual words, the number of overlapping words between the system summary and refrence summary is 6.This however, does not tell you much as metric . To get a good quantitative value, we can actuall compute the *precision* and *recall* using the overlap.

##Precision and Recall in the Context of ROUGE

Simply put. *Recall* in the context of ROUGE means how much of the *reference summary* is the *system summary* recovering or capturing?If we are just considering the individual words, it can be computed as:
>(number_of_overlapping_words)/(total_words_in_reference_summary)

In this example , the recall would be thus be:
>Recall=6/6=1.0

This means that all the words in the *reference summary* has been captured by the *system summary*. This looks good for a text summarization system. However, it does not tellyou the other side of the story. A machine generated summary(system summary) can be extremely long, capturing all words in the reference summary. But, much of the words in the system summary may be useless, making the summary unnecessarily verbose. This is where precision comes into play. In terms of precision, what are you essentially measuring is, how much of the system summary was in fact relevant or needed?
Precision is measured as:
>(number_of_overlapping_words)/(total_words_in_system_summary)

In this example,Precision would thus be:
Precision=6/7=0.86

This means that 6 out of 7 words in the system summary were in fact relevant or needed.

**System Summary2**
>the tiny little cat was found under the big funny bed

Precision will now be-6/11=0.55

The *Precision* aspect becomes really crucial when you are trying to generate summaries that are concise in nature. Therefore, it is always best to compute both the *Precision* and *Recall* and then report the *F-Measure*. 

##So What is ROUGE-N,ROUGE-S & ROUGE-L?
They can be thought of as the granularity of texts being compared between the system summaries and reference summaries.For example, **ROUGE-1** refers to overlap of unigrams between the system summary and reference summary.**ROUGE-2** refers to the overlap of bigrams between the system and reference summaries. 
Let's say we want to compute the **ROUGE-2 precision and recall** scores.
**System Summary-**
>the cat was found under the bed

**Reference Summary-**
>the cat was under the bed

**System Summary Bigrams-**
'''
the cat,
cat was,
was found,
found under,
under the,
the bed
'''
**Reference Summary Bigrams**
'''
the cat,
cat was,
was under,
under the,
the bed
'''

Based on the bigrams above, the *ROUGE-2* Rrecall is as follows-
>ROUGE-2 RECALL=4/5=0.8

>ROUGE-2 precision=4/6=0.67

The precision here tells us that out of all the system summary bigrams, there is a 67% overlap with the reference summary. This is not too bad either.Note that as the summaries (both system and reference summaries) get longer and longer, there will be fewer overlapping bigrams especially in the case of abstractive summarization where you are not directly re-using sentences for summarization.
-**ROUGE-N-Measures unigram,bigram,trigram and higher order n-gram overlap.**
-**ROUGE-L-Measures longest matching sequence of words using LCS. An advantage of using LCS is that it does not require consecutive matches but in-sequence matches that reflect sentence level word order. Since it automatically includes longest in-sequence common
n-grams, you don't need a predefined n-gram length.**
-**ROUGE-S-Is any pair of word in a sentence in order,allowing for arbitary gaps. THis can also be called skip-gram coocurrence.for example, skip-bigram measures the overlap of word pairs that can have a maximum of two gaps in between words.As an example, for the phrase "cat in the hat" the skip-bigrams would be" cat in,cat the,cat hat,in the,in hat,the hat"**

*If you are working on extractive summarization with fairly verbose system and reference summaries, then it may make sense to use ROUGE-1 and ROOUGE-L. For very concise summaries, ROUGE-1 alone may suffice especiall if you are also applying stemming and stop word removal.*













 
