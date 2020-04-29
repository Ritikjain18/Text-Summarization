# Text-Summarization
What is ROUGE?
ROUGE stands for Recall Oriented Understudy For Gisting Evaluation. It is essentially of a set of metrics for evaluating automatic summarization of texts as well as machine translation.It works by comparing an **automatically produced summary** or **translation** against a set of **reference summaries**(typically human produced).
Let us say, we have the following system and reference summaries:

**System Summary(what the machine produced)**
-the cat was found under the bed

**Reference Summary(gold standard -ususlly by humans)**
-the cat was under the bed

If we consider just the individual words, the number of overlapping words between the system summary and refrence summary is 6.This however, does not tell you much as metric . To get a good quantitative value, we can actuall compute the *precision* and *recall* using the overlap.




 
