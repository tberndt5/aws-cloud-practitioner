---
tags:
  - clf-c02
  - services
  - services/machine-learning
category: "Machine Learning"
status: not-started
---
# Services: Machine Learning

> [!info] Scope
> Services below come from the CLF-C02 **in-scope** list for this category, plus any that a task statement names or implies.

## Category at a glance

AI/ML concepts and how these services fit alongside the analytics services are taught in [[3.7 AI-ML and Analytics Services]].

| Service | What it is (under ten words) | Cue in a question |
| --- | --- | --- |
| [[#Amazon Comprehend]] | NLP: sentiment, entities, key phrases in text | "Sentiment", "customer reviews", "extract insights from text", "detect PII in text" |
| [[#Amazon Kendra]] | Intelligent enterprise search with natural language | "Search internal documents", "enterprise search", "natural-language questions over company content" |
| [[#Amazon Lex]] | Chatbots and voice bots (conversational interfaces) | "Chatbot", "conversational interface", "voice or text bot", "Alexa technology" |
| [[#Amazon Polly]] | Text to lifelike speech | "Text-to-speech", "read articles aloud", "generate audio from text" |
| [[#Amazon Rekognition]] | Image and video analysis | "Facial analysis", "detect objects in images", "content moderation", "video" |
| [[#Amazon SageMaker]] | Build, train, and deploy your own ML models | "Data scientists", "build and train custom models", "deploy a model" |
| [[#Amazon Textract]] | Extract text and data from scanned documents | "Scanned forms", "extract tables and fields", "OCR", "handwriting" |
| [[#Amazon Transcribe]] | Speech to text | "Speech-to-text", "transcribe calls", "subtitles/captions" |
| [[#Amazon Translate]] | Language translation | "Translate", "multiple languages", "localize content" |

> [!tip] Direction of conversion
> Text → speech: **Polly**. Speech → text: **Transcribe**. Language A → language B: **Translate**. Document image → text/data: **Textract**. Text → meaning (sentiment, entities): **Comprehend**. Image/video → labels and faces: **Rekognition**. Conversation (chatbot): **Lex**. Search over documents: **Kendra**. Build your own model: **SageMaker**.

## Amazon Comprehend

> [!summary] Uses natural language processing (NLP) to extract insights from documents.

- **What it does:** Analyzes text to find meaning: sentiment (positive, negative, neutral, mixed), entities (people, places, organizations), key phrases, language, and topics. It can also detect and redact personally identifiable information (PII) in text. No ML expertise is needed.
- **Choose it when:** The question asks to understand or classify the content of text: review sentiment, social media analysis, support ticket categorization, PII in documents.
- **Key facts:**
  - ==Sentiment analysis== is the classic exam cue.
  - Entity recognition, key phrases, language detection, custom classification.
  - Detects PII in text.
  - Fully managed, pay per unit of text.
- **Don't confuse with:** [[#Amazon Textract]] (gets the text out of a scanned document; Comprehend interprets text you already have) and [[Services - Security, Identity, and Compliance#Amazon Macie|Amazon Macie]] (discovers sensitive data stored in Amazon S3).
- **Docs:** [What is Amazon Comprehend?](https://docs.aws.amazon.com/comprehend/latest/dg/what-is.html)

## Amazon Kendra

> [!summary] Intelligent search service that uses NLP and ML algorithms.

- **What it does:** An enterprise search service that indexes content from many repositories (S3, SharePoint, Salesforce, databases, file shares) and answers natural-language questions with precise answers, not just keyword matches.
- **Choose it when:** Employees need to search across internal documents and knowledge bases by asking questions in plain language.
- **Key facts:**
  - ==Enterprise document search== using ML.
  - Natural-language queries ("How many vacation days do I get?") return specific answers.
  - Connectors to many data sources.
- **Don't confuse with:** [[Services - Analytics#Amazon OpenSearch Service|Amazon OpenSearch Service]] (search and log analytics clusters you configure) and [[#Amazon Lex]] (chatbot conversation, not document search).
- **Docs:** [What is Amazon Kendra?](https://docs.aws.amazon.com/kendra/latest/dg/what-is-kendra.html)

Current status: Amazon Kendra entered maintenance mode on June 30, 2026 and is no longer open to new customers as of July 30, 2026; AWS recommends Amazon Bedrock Knowledge Bases instead.

## Amazon Lex

> [!summary] Build conversational interfaces for applications that use voice and text.

- **What it does:** Builds chatbots and voice bots that understand user intent through automatic speech recognition and natural language understanding. It uses the same deep learning technology that powers Amazon Alexa.
- **Choose it when:** The question describes a chatbot, virtual agent, or interactive voice response (IVR) system, for example in a contact center.
- **Key facts:**
  - ==Chatbots== in voice and text.
  - Same technology as Alexa.
  - Integrates with Lambda for business logic and with [[Services - Business Productivity#Amazon Connect|Amazon Connect]] for contact center bots.
- **Don't confuse with:** [[#Amazon Polly]] (only speaks text aloud), [[#Amazon Transcribe]] (only converts speech to text), and Amazon Connect (the contact center itself).
- **Docs:** [What is Amazon Lex V2?](https://docs.aws.amazon.com/lexv2/latest/dg/what-is.html)

## Amazon Polly

> [!summary] Convert text into lifelike speech.

- **What it does:** Turns text into natural-sounding speech in many languages and voices, so applications can talk. Output can be streamed or saved as audio files.
- **Choose it when:** The question asks to read text aloud, create audio versions of articles, or add a voice to an application.
- **Key facts:**
  - ==Text-to-speech== (TTS).
  - Many voices and languages, including neural voices.
  - SSML (Speech Synthesis Markup Language) controls pronunciation, pitch, and pauses.
- **Don't confuse with:** [[#Amazon Transcribe]], which does the opposite (speech to text). Memory aid: Polly the parrot talks.
- **Docs:** [What is Amazon Polly?](https://docs.aws.amazon.com/polly/latest/dg/what-is.html)

## Amazon Rekognition

> [!summary] Identify objects, people, text, scenes, and activities in images and videos.

- **What it does:** Analyzes images and videos with pre-trained deep learning models. It detects objects, scenes, text, and inappropriate content, and performs face detection, analysis, and comparison.
- **Choose it when:** The question involves images or video: facial recognition or verification, content moderation, labeling photos, identifying celebrities, or tracking people in video.
- **Key facts:**
  - ==Images and video== (the only service in this list that analyzes visual media).
  - Face comparison and search, celebrity recognition, unsafe content detection.
  - Custom Labels lets you train it on your own objects.
- **Don't confuse with:** [[#Amazon Textract]] (extracts text and structured data from documents; Rekognition can find text in an image but is not the document-processing answer).
- **Docs:** [What is Amazon Rekognition?](https://docs.aws.amazon.com/rekognition/latest/dg/what-is.html)

## Amazon SageMaker

> [!summary] Build and train ML models, then deploy the models in a production-ready hosted environment.

- **What it does:** A fully managed platform for the whole machine learning lifecycle: prepare data, build, train, and tune models, then deploy them to hosted endpoints. It removes the need to manage the underlying infrastructure.
- **Choose it when:** Data scientists or developers need to create their own custom ML models rather than use a pre-trained AI service.
- **Key facts:**
  - Covers the ==full ML lifecycle==: build, train, deploy.
  - SageMaker Studio is the web-based IDE for ML; Autopilot automates model building.
  - Built-in algorithms, or bring your own framework (TensorFlow, PyTorch, and others).
  - Pay for the compute and storage you use.
- **Don't confuse with:** The pre-trained AI services in this note (Comprehend, Rekognition, Polly, and so on), which need no ML expertise. Custom models point to SageMaker; a ready-made capability points to the specific AI service.
- **Docs:** [What is Amazon SageMaker AI?](https://docs.aws.amazon.com/sagemaker/latest/dg/whatis.html)

Current status: On December 3, 2024 this service was renamed Amazon SageMaker AI; the name "Amazon SageMaker" now refers to a broader unified data, analytics, and AI platform that includes SageMaker AI.

## Amazon Textract

> [!summary] Automatically extract text, handwriting, and data from scanned documents.

- **What it does:** Goes beyond simple optical character recognition (OCR) to extract printed text, handwriting, form fields (key-value pairs), and tables from scanned documents, PDFs, and images.
- **Choose it when:** The question involves processing scanned forms, invoices, receipts, tax documents, or IDs and pulling out the data automatically.
- **Key facts:**
  - ==Forms and tables==, not just raw text.
  - Handles handwriting.
  - Specialized APIs for invoices, receipts, and identity documents.
- **Don't confuse with:** [[#Amazon Comprehend]] (analyzes the meaning of text) and [[#Amazon Rekognition]] (images and video in general).
- **Docs:** [What is Amazon Textract?](https://docs.aws.amazon.com/textract/latest/dg/what-is.html)

## Amazon Transcribe

> [!summary] Automatic speech recognition that converts audio to text.

- **What it does:** Converts speech in audio or video files, or live audio streams, into text. It can identify different speakers, add timestamps, and redact sensitive information from transcripts.
- **Choose it when:** The question asks to transcribe calls or meetings, generate subtitles or captions, or make audio searchable.
- **Key facts:**
  - ==Speech-to-text== (automatic speech recognition, ASR).
  - Batch files and real-time streaming.
  - Speaker identification and PII redaction.
  - Specialized versions for medical dictation and call analytics.
- **Don't confuse with:** [[#Amazon Polly]] (text to speech, the opposite) and [[#Amazon Translate]] (changes language, not medium).
- **Docs:** [What is Amazon Transcribe?](https://docs.aws.amazon.com/transcribe/latest/dg/what-is.html)

## Amazon Translate

> [!summary] Translate unstructured text documents or build applications that work in multiple languages.

- **What it does:** Neural machine translation that converts text from one language to another, in real time or in batches. Used to localize websites, apps, and user-generated content.
- **Choose it when:** The question asks to translate text or documents, or support customers in multiple languages.
- **Key facts:**
  - ==Language-to-language== text translation.
  - Real-time and batch translation.
  - Custom terminology keeps brand and product names consistent.
- **Don't confuse with:** [[#Amazon Transcribe]] (audio to text). For spoken-language translation, chain Transcribe → Translate → Polly.
- **Docs:** [What is Amazon Translate?](https://docs.aws.amazon.com/translate/latest/dg/what-is.html)

---
Index: [[Services Index]] · Home: [[00 - Start Here]]
