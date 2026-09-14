# System Architecture Document — HateGuard NLP

**Project Name:** HateGuard NLP  
**Author:** Nachiket Gadilohar  

---

## 1. Architecture Flow
- User Input -> FastAPI / Flask Gateway -> Tokenizer & NLTK Preprocessor -> Keras/TensorFlow LSTM Model -> AWS EC2 / CircleCI CD.
