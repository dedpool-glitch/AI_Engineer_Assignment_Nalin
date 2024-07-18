# AI_Engineer_Assignment_Nalin
This repository contains code for the NLP tasks as stated in the assignment for Predixion AI

## Code Functionality
I will explain what the code in the Jupyter Notebook does. Hugging Faces' transformers library is put to use in the Notebook

1) Going sequentially, the first objective is to translate the Hindi conversation into an English one, to sentiment analysis and summarization in English. That is what we do in the first cell, which takes in the conversation and translates it line by line from Hindi to English. We get the combined translation as the output.
2) Next, we summarize the translated text by specifying minimum and maximum token lengths and set the do_sample parameter to False to ensure reproducibility.
3) We pass the text to a summarizer pipeline, using the default summarization model provided by Hugging Face (distilbart-cnn-12-6)
4) Now for the sentiment analysis, we use the default model (distilbert-base-uncased-finetuned-sst-2-english) provided by Hugging Face in its sentiment analysis pipeline.


## Results
1) Translation:
Recovery Agent (RA): Hello Mr. Kumar, I'm talking to X Y Z Finance. I had to talk about your loan.
Borrower: Yes, speak. What's the matter?
RA: Sir, your last month's EMI hasn' t arrived yet. Is there a problem?
B: Yeah, I'm having a little trouble. My job' s gone and I'm looking for a new job.
RA: Oh, that's bad. But sir, you have to understand that it' s very important to pay the loan on time.
B: I understand, but I don 't have the money yet. Can I have some time?
RA: We understand your situation. Can you make some payments by next week?
B: I 'll try, but I can' t give the full EMI. Will half the payment go?
RA: Okay, make half the payment by next week. What's your plan for the rest?
B: I hope to get a new job by next month. Then I 'll pay the rest.
RA: All right. So we 'll do that - you deposit half of the EMI up to the next week, and pay the rest up to the 15th of next month. Do you accept that?
B: Yeah, it 'll be fine. I' ll do my best to follow this plan.
RA: Very good. I'm sending you an SMS with payment details. Please follow this and pay on time.
B: Well, thank you for understanding.
RA: Welcome. If you have any other questions, please let me know. Bye.
B: By the way.

2) Summarization:


## Result Explanation

### Translation
As you observed in the output for translation, the Hindi-to-English conversion didn't capture all nuances of the conversation and it also changed some phrases which sounded polite in Hindi, but changed slightly when converted to English. For example, "Borrower (B): हां, बोलिए। क्या बात है?" which is considered to be polite in Hindi, changed to "Borrower: Yes, speak. What's the matter?" which sounds slightly impolite and firm. "B: अलविदा।" was mistranslated to "B: By the way.". But other parts of the conversation seemed to be translated properly, and we can move forward to the next analysis task.

### Summarization
The summarization output of the model was extremely direct, but it led to a few grammatical inaccuracies in the text. "Borrower's last month's EMI hasn't arrived yet, says XYZ Finance." failed to mention that an individual from the XYZ finance company had contacted the borrower. Also, there is a sequential mismatch between the translated output that was given to the summarizer and the output of the summarizer. The absence of a job is something that was mentioned at the starting point in the conversation but in the summary, it has been mentioned near the end. But overall, the conversation manages to capture the problems, as well as the solution provided, which is important information that needs to be covered.

### Sentiment Analysis
For this task, I have again used the default hugging-face model for sentiment analysis. The outputs are limited to 3 sentiments, Negative, Positive and Neutral. Each line was passed separately to the sentiment analyzer instance, and in the output we can see each sentence appended with the sentiment score as well as the classified sentiment. Out of 16 sentences passed to the pipeline, 10 were classified as negative, and the remaining 6 were positive. From the output, we can observe that on the whole, the sentiment changed from negative at the start of the conversation to positive in the middle and at the end. This can be justified by the shift in tone of the Recovery Agent who acted politely and in a considerate and supportive manner and suggested a solution to the Borrower. The borrower also felt relived that they were supported and a logical solution was given to them which they accepted without any hesitation. 
