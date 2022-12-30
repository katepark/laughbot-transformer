# laughbot-transformer
Extending laughbot project (https://github.com/katepark/laughbot) to transformer model finetuned on same dataset of the Switchboard Corpora (3000 transcripts from phone conversations between two speakers)
<br>* Original paper (https://cs.stanford.edu/~katepark/Laughbot.pdf) achieved accuracy of 73.9 and F1-score of 63.2 via a combined RNN and logistic regression model that used both acoustic and language features.
<br>* Finetuning distilbert-base-uncased on the same exact dataset outperforms this model with an accuracy of 74.1 and F1 score of 73.7. 
<br>* Note: A random baseline that follows the class distribution has an F1 score of 37. An always positive baseline has an F1 score of 54.

<br>Transformers rock!

<br>You can play with the model here https://huggingface.co/goldenk/distilbert-base-uncased-finetuned-switchboard
