# laughbot-transformer
Extending laughbot project (https://github.com/katepark/laughbot) and paper (https://cs.stanford.edu/~katepark/Laughbot.pdf) to transformer model finetuned with same dataset of the Switchboard Corpora (3000 transcripts from phone conversations between two speakers)

Dataset: Any line of a transcript preceding indication of laughter (often transcribed as "[laughter]") classified as a positive "punchline." Else, "unfunny". Example
|Transcript|Class|
|--|---|
|A:  Uh-huh. Well, you must have a relatively clean conscience then.|Punchline|
|B: [Laughter]|-|

Num Examples
* Train: 23658 (38.7% "punchline")
* Val: 2966
* Test: 2893

|Model|Model Description|Accuracy|Precision|Recall|F1-score|
|-----|----|--------|---------|------|--------|
|Positive Baseline|Always predict positive class ("punchline")|37.2|37.2|100.0|54.2|
|Random Weighted Baseline|Predict positive class 37.2% of the time matching overall dataset distribution|37.2|37.2|37.2|37.2|
|Logistic regression (language only)|Logistic Regression trained on language features(ngrams, parts of speech, sentiment, line length)|70.6|62.7|51.4|56.5|
|RNN (audio only)|RNN trained on acoustic features (MFCC vectors, Energy level)|71.7|63.5|55.9|59.4|
|Paper Final Model (RNN+LogReg)|Extract final hidden state vector from RNN trained on acoustic features. Concatenate with language features. Train logistic regression model on combined feature vector|73.9|66.5|60.3|63.2|
|Finetuned Transformer (this repo)|distilbert-base-uncased finetuned on tokenized transcripts, no audio features|**74.1**|**73.3**|73.6|**73.7**|

<br>Transformers rock!

Overfitting...
|Dataset|Accuracy|Precision|Recall|F1-score|
|-----|----|--------|---------|------|
|Train|89.9|89.9|89.9|89.9|
|Val|72.2|71.7|72.1|71.8|

<br>You can play with the model here https://huggingface.co/goldenk/distilbert-base-uncased-finetuned-switchboard-2

This was inspired by the following (install.py and utils.py):
```
  @book{tunstall2022natural,
    title={Natural Language Processing with Transformers: Building Language Applications with Hugging Face},
    author={Tunstall, Lewis and von Werra, Leandro and Wolf, Thomas},
    isbn={1098103246},
    url={https://books.google.ch/books?id=7hhyzgEACAAJ},
    year={2022},
    publisher={O'Reilly Media, Incorporated}
  }
```
