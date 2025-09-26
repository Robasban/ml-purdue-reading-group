# Byte Latent Transformer
- Presenter: Arnav Grover 
- Date: 9/25/25

## Summary
The Byte Latent Transformer (BLT) is a transformer that instead of tokenizing text, it converts it to UTF-8 bytes. It groups the bytes into "patches" based on entropy, which is a measure of the uncertainty of a prediction. With higher entropy, the prediciton is more unpredictable, and so higher compute is used in those regions. The low entropy regions, on the other hand, take much less compute, improving efficiency. The benefit of using a BLT instead of a standard tokenizer is that it is more robust across different languages, can more easily understand orthographic languages (those without spaces), and can understand more domain-specific or new words.

## Notes
- Tokenization: splitting text up into smaller units to make it easier to process
  - This is valuable for a few reasons
    - Many languages do not have orthographic words (spaces between words)
    - The number of words in a language grows endlessly, so it is hard for a model to know a word after it has been trained
      - By using tokenization, the model can predict what a new word means
  - Tokenization has many failures
    - There was a difficutly in counting the number of letters in a word
    - Domain and modality sensitivity
    - Multilingual inequity
- Byte Latent Transformer (BLT) Architecture
  - Self attention: each token in the text gets weighed against all other words in the text to understand context
  - Entropy Based Patching: the transform allocates the same compute to every token
    - It is generally easier to predict tokens at the end of specific things, like titles
      - This would mean low entropy, which is the uncertainty about the next token
      - High entropy would show that a phrase is more dynamic and could branch off into many other tokens
  - Lanugage Encoder: takes byte embeddings (with UTF-8 ID) and determines if the next token's uncertainty
  - Latent Global Transformer: takes each patch, and predicts the next most likely patch
  - Decoder: changes the patches back into bytes to be able to convert back into language
- Results
  - The BLT was far more efficient than previous transformer models
  - It was better able to understand orthographic language

## Questions
- Why not tokenize every character?
  - It would likely cause the text to lose meaning as singular characters do not really convey meaning
  - Inefficient as every character would need to be tokenized
