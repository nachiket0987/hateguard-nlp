# Product Requirement Document (PRD) — HateGuard NLP

**Project Name:** HateGuard NLP  
**Project Description:** Production-Ready Hate Speech Classification System using LSTM & Deep Learning, deployed on AWS EC2 with CircleCI CI/CD.  
**Author:** Nachiket Gadilohar  

---

## 1. Executive Summary
HateGuard NLP is a production-grade NLP toxicity and hate speech detection platform. It uses deep LSTM neural networks, NLTK preprocessing pipelines, and a Flask/FastAPI backend deployed on AWS EC2 with CircleCI automated testing.

---

## 2. Core Features
1. **LSTM Hate Speech Classifier**: Binary and multi-class classification for toxic text.
2. **Automated CircleCI Pipeline**: Runs unit tests and builds Docker images upon git push.
3. **AWS EC2 Production Deployment**: High-availability cloud REST API for batch text scanning.
