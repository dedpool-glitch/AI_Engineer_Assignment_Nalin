# AI_Engineer_Assignment_Nalin
This repository contains code for the NLP tasks as stated in the assignment for Predixion AI

## Code Functionality
I will explain what the code in the Jupyter Notebook does. Hugging Faces' transformers library is put to use in the Notebook. The notebook has 2 sections of analysis, one does the summarization and sentiment analysis from the English-translated version of the Hindi conversation, and the other showcases sentiment analysis output for XLM-Roberta-Base multilingual model.

### SECTION ONE
1) Going sequentially, first we translate the Hindi conversation into an English one, for sentiment analysis and summarization in English. 
2) Next, we summarize the translated text by specifying minimum and maximum token lengths and set the do_sample parameter to False to ensure reproducibility.
3) We pass the text to a summarizer pipeline, using the default summarization model provided by Hugging Face (distilbart-cnn-12-6)
4) Now for the sentiment analysis, we use the default model (distilbert-base-uncased-finetuned-sst-2-english) provided by Hugging Face in its sentiment analysis pipeline.

### SECTION TWO
1) Here, we perform Sentiment Analysis for the XLM-Roberta-Base model.


   
## SECTION ONE

### Results

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
Borrower's last month's EMI hasn't arrived yet, says X Y Z Finance . Recovery Agent (RA) asks borrower to make payments by next week . He says he hopes to get a new job by next month, then pay the rest of the money . The borrower says he is 'having a little trouble' because he can't give the full EMI . The debt collector says it is important to pay the loan on time and deposit half of the EMI up to the next week, and pay rest of next month .


3) Sentiment Analysis:
Text: Recovery Agent (RA): Hello Mr. Kumar, I'm talking to X Y Z Finance. I had to talk about your loan.
Sentiment: [{'label': 'NEGATIVE', 'score': 0.8278596997261047}]

Text: Borrower: Yes, speak. What's the matter?
Sentiment: [{'label': 'NEGATIVE', 'score': 0.9892157316207886}]

Text: RA: Sir, your last month's EMI hasn' t arrived yet. Is there a problem?
Sentiment: [{'label': 'NEGATIVE', 'score': 0.9990589022636414}]

Text: B: Yeah, I'm having a little trouble. My job' s gone and I'm looking for a new job.
Sentiment: [{'label': 'NEGATIVE', 'score': 0.9995023012161255}]

Text: RA: Oh, that's bad. But sir, you have to understand that it' s very important to pay the loan on time.
Sentiment: [{'label': 'NEGATIVE', 'score': 0.6003400683403015}]

Text: B: I understand, but I don 't have the money yet. Can I have some time?
Sentiment: [{'label': 'NEGATIVE', 'score': 0.9988842606544495}]

Text: RA: We understand your situation. Can you make some payments by next week?
Sentiment: [{'label': 'NEGATIVE', 'score': 0.9534904956817627}]

Text: B: I 'll try, but I can' t give the full EMI. Will half the payment go?
Sentiment: [{'label': 'NEGATIVE', 'score': 0.9981967806816101}]

Text: RA: Okay, make half the payment by next week. What's your plan for the rest?
Sentiment: [{'label': 'NEGATIVE', 'score': 0.9965583682060242}]

Text: B: I hope to get a new job by next month. Then I 'll pay the rest.
Sentiment: [{'label': 'NEGATIVE', 'score': 0.9934502840042114}]

Text: RA: All right. So we 'll do that - you deposit half of the EMI up to the next week, and pay the rest up to the 15th of next month. Do you accept that?
Sentiment: [{'label': 'POSITIVE', 'score': 0.9802226424217224}]

Text: B: Yeah, it 'll be fine. I' ll do my best to follow this plan.
Sentiment: [{'label': 'POSITIVE', 'score': 0.9990525841712952}]

Text: RA: Very good. I'm sending you an SMS with payment details. Please follow this and pay on time.
Sentiment: [{'label': 'POSITIVE', 'score': 0.9997013211250305}]

Text: B: Well, thank you for understanding.
Sentiment: [{'label': 'POSITIVE', 'score': 0.9998034834861755}]

Text: RA: Welcome. If you have any other questions, please let me know. Bye.
Sentiment: [{'label': 'POSITIVE', 'score': 0.9995200634002686}]

Text: B: By the way.
Sentiment: [{'label': 'POSITIVE', 'score': 0.9887120723724365}]


### Result Interpretation 

#### Translation
As you observed in the output for translation, the Hindi-to-English conversion didn't capture all nuances of the conversation and it also changed some phrases which sounded polite in Hindi, but changed slightly when converted to English. For example, "Borrower (B): हां, बोलिए। क्या बात है?" which is considered to be polite in Hindi, changed to "Borrower: Yes, speak. What's the matter?" which sounds slightly impolite and firm. "B: अलविदा।" was mistranslated to "B: By the way.". But other parts of the conversation seemed to be translated properly, and we can move forward to the next analysis task.

#### Summarization
The summarization output of the model was extremely direct, but it led to a few grammatical inaccuracies in the text. "Borrower's last month's EMI hasn't arrived yet, says XYZ Finance." failed to mention that an individual from the XYZ finance company had contacted the borrower. Also, there is a sequential mismatch between the translated output that was given to the summarizer and the output of the summarizer. The absence of a job is something that was mentioned at the starting point in the conversation but in the summary, it has been mentioned near the end. But overall, the conversation manages to capture the problems, as well as the solution provided, which is important information that needs to be covered.

#### Sentiment Analysis
For this task, I have again used the default hugging-face model for sentiment analysis. The outputs are limited to 3 sentiments, Negative, Positive and Neutral. Each line was passed separately to the sentiment analyzer instance, and in the output we can see each sentence appended with the sentiment score as well as the classified sentiment. Out of 16 sentences passed to the pipeline, 10 were classified as negative, and the remaining 6 were positive. From the output, we can observe that on the whole, the sentiment changed from negative at the start of the conversation to positive in the middle and at the end. This can be justified by the shift in tone of the Recovery Agent who acted politely and in a considerate and supportive manner and suggested a solution to the Borrower. The borrower also felt relived that they were supported and a logical solution was given to them which they accepted without any hesitation. 


## SECTION TWO

### Results

1) Sentiment Analysis:
   
Text: Recovery Agent (RA): नमस्ते श्री कुमार, मैं एक्स वाई जेड फाइनेंस से बोल रहा हूं। आपके लोन के बारे में बात करनी थी।
Sentiment: positive (Score: 0.2646923065185547)

Text: Borrower (B): हां, बोलिए। क्या बात है?
Sentiment: very negative (Score: 0.38013380765914917)

Text: RA: सर, आपका पिछले महीने का EMI अभी तक नहीं आया है। क्या कोई समस्या है?
Sentiment: very negative (Score: 0.48783984780311584)

Text: B: हां, थोड़ी दिक्कत है। मेरी नौकरी चली गई है और मैं नया काम ढूंढ रहा हूं।
Sentiment: negative (Score: 0.3589804470539093)

Text: RA: ओह, यह तो बुरा हुआ। लेकिन सर, आपको समझना होगा कि लोन का भुगतान समय पर करना बहुत जरूरी है।
Sentiment: neutral (Score: 0.4536367952823639)

Text: B: मैं समझता हूं, लेकिन अभी मेरे पास पैसे नहीं हैं। क्या कुछ समय मिल सकता है?
Sentiment: negative (Score: 0.4188579320907593)

Text: RA: हम समझते हैं आपकी स्थिति। क्या आप अगले हफ्ते तक कुछ भुगतान कर सकते हैं?
Sentiment: neutral (Score: 0.3204396963119507)

Text: B: मैं कोशिश करूंगा, लेकिन पूरा EMI नहीं दे पाऊंगा। क्या आधा भुगतान चलेगा?
Sentiment: negative (Score: 0.47138145565986633)

Text: RA: ठीक है, आधा भुगतान अगले हफ्ते तक कर दीजिए। बाकी का क्या प्लान है आपका?
Sentiment: very negative (Score: 0.4194673001766205)

Text: B: मुझे उम्मीद है कि अगले महीने तक मुझे नया काम मिल जाएगा। तब मैं बाकी बकाया चुका दूंगा।
Sentiment: negative (Score: 0.409562349319458)

Text: RA: ठीक है। तो हम ऐसा करते हैं - आप अगले हफ्ते तक आधा EMI जमा कर दीजिए, और अगले महीने के 15 तारीख तक बाकी का भुगतान कर दीजिए। क्या यह आपको स्वीकार है?
Sentiment: very negative (Score: 0.4215473234653473)

Text: B: हां, यह ठीक रहेगा। मैं इस प्लान का पालन करने की पूरी कोशिश करूंगा।
Sentiment: neutral (Score: 0.2783663868904114)

Text: RA: बहुत अच्छा। मैं आपको एक SMS भेज रहा हूं जिसमें भुगतान की डिटेल्स होंगी। कृपया इसका पालन करें और समय पर भुगतान करें।
Sentiment: very positive (Score: 0.4573466181755066)

Text: B: ठीक है, धन्यवाद आपके समझने के लिए।
Sentiment: neutral (Score: 0.39061108231544495)

Text: RA: आपका स्वागत है। अगर कोई और सवाल हो तो मुझे बताइएगा। अलविदा।
Sentiment: positive (Score: 0.37999919056892395)

Text: B: अलविदा।
Sentiment: negative (Score: 0.32469531893730164)

### Result Interpretation

#### Sentiment Analysis:
As observed from the results, we see that the model is identifying the sentiments but every sentiment is paired with a fairly low confidence. This indicates that the model might not be good enough to understand these types of RA-Borrower conversations and could perform better with some fine-tuning. The highest confidence given was around 0.48. 


