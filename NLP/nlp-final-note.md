# Natural Language Processing (NLP)

- [Natural Language Processing (NLP)](#natural-language-processing-nlp)
  - [Chapter 1: Introduction to NLP](#chapter-1-introduction-to-nlp)
    - [NLP Components](#nlp-components)
    - [Ambiguity in NLP (NLU \& NLG)](#ambiguity-in-nlp-nlu--nlg)
    - [NLU Steps](#nlu-steps)
    - [Real World Examples of NLP](#real-world-examples-of-nlp)
  - [Chapter 2: Text Preprocessing \& Morphology Analysis](#chapter-2-text-preprocessing--morphology-analysis)
    - [Normalisation](#normalisation)
    - [Stop Word Removal](#stop-word-removal)
    - [Concepts of Morphology](#concepts-of-morphology)
  - [Chapter 4: Synthetic Analysis](#chapter-4-synthetic-analysis)
    - [Part-of-Speech (POS) Tagging](#part-of-speech-pos-tagging)
    - [Hidden Markov Model](#hidden-markov-model)
  - [Chapter 5: Semantic Analysis](#chapter-5-semantic-analysis)
    - [Lexical Semantics](#lexical-semantics)
    - [Semantic Roles Labeling](#semantic-roles-labeling)
    - [Levenshtein Distance](#levenshtein-distance)
    - [Word Sense Disambiguation (WSD)](#word-sense-disambiguation-wsd)
    - [Similarity Measures](#similarity-measures)
  - [Chapter 7 Sentiment Analysis](#chapter-7-sentiment-analysis)
    - [Lexical vs Machine Learning Approaches](#lexical-vs-machine-learning-approaches)
    - [Sentiment Analysis Techniques](#sentiment-analysis-techniques)
    - [Sentiment Analysis Limitation/Challenges](#sentiment-analysis-limitationchallenges)
  - [Chapter 8 Topic Modeling](#chapter-8-topic-modeling)
    - [Topic Modeling Techniques](#topic-modeling-techniques)
    - [Topic Distribution](#topic-distribution)
  - [Chapter 9 Text Mining \& Named Entity Recognition (NER)](#chapter-9-text-mining--named-entity-recognition-ner)
    - [Text Mining](#text-mining)
    - [Named Entity Recognition (NER)](#named-entity-recognition-ner)

## Chapter 1: Introduction to NLP

### NLP Components

| Aspect               | Natural Language Understanding (NLU)                                                         | Natural Language Generation (NLG)                                                                                 |
| -------------------- | -------------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------------------------- |
| **Component of NLP** | Input Component                                                                              | Output Component                                                                                                  |
| **What it does**     | Convert unstructured human language into structured data that machines can logically process | Convert structured data into natural language that is human-readable                                              |
| **Function**         | Analysing different aspects of language, such as syntax, semantics, and pragmatics           | Phrase information, choosing right tone, and generating text that is contextually relevant and easy to understand |
| **Examples**         | Intent Recognition, Named Entity Recognition (NER), Sentiment Analysis                       | Text Summarization, Chatbots, Question Answering Systems                                                          |

### Ambiguity in NLP (NLU & NLG)

- **Lexical Ambiguity**: A word has multiple meanings (e.g., "bank" can mean a financial institution or the side of a river)
- **Syntax Level Ambiguity**: A sentence can be parsed in multiple ways (Different parse trees)
- **Referential Ambiguity**: Ambiguity in pronoun reference (e.g., "John told Mike that he was tired." Who is "he"? John or Mike?)

### NLU Steps

- **Lexical Analysis**: or Morphology Analysis, divides text into tokens of paragraph, sentence and word.
- **Syntactic Analysis**: analyse the structure of sentences and the correctness of grammar. It rejects sentence like "The school goes to the student."
- **Semantic Analysis**: draw meaning from the text. It rejects sentence like "hot ice-cream"
- **Discourse Integration**: understand the sentence with the context of the previous sentence.
- **Pragmatic Analysis**: understand the sentence with the context of the real world.

### Real World Examples of NLP

- **Healthcare**
  - Unstructured text data from EHR (Electronic Health Records), physician notes, and patient intake forms
  - NLP can extract relevant information, identify patterns, track patient history, support clinical decision-making, ensure insurance billing and legal compliance
- **Retail & E-commerce**
  - Unstructured text data from customer reviews, chatbot interactions, email enquiries
  - Sentiment analysis, identify product trends and defects, optimise chatbot, and support inventory management decision-making
- **Banking & Securities**
  - Unstructured text data from conversational text and transaction logs
  - Identify fraudulent activities such as behavioural manipulation and phishing
  - Regulatory compliance by analysing compliance documents, contracts, and financial reports. Avoid regulatory penalties and legal issues

## Chapter 2: Text Preprocessing & Morphology Analysis

### Normalisation

- Process of converting text into a standard format
- Reduce vocabulary size (reduce noise and map similar words to a single representation), reduce dimensionality, improve generalisation
- **Stemming**
  - Eliminating suffixes, prefixes, infix, circumfix, etc. to get the stem of a word
  - Example: "running" → "run", "happily" → "happi"
  - Faster, simple rule based, ignore context, may not always produce a valid word
    > Stem is not necessarily a root word, but a part of a word that can form other words by adding affixes. Root is always a valid word, but stem may not be a valid word.
- **Lemmatization**
  - Canonical form of a word, considering the context and meaning of the word
  - Example: "running" → "run", "better" → "good"
  - Slower, require knowledge of the context, backed up by part-of-speech tagging, always produces a valid word
- **Case Folding**
  - Convert all characters to lowercase
  - Example: "Hello" → "hello"
- **Unicode Canonicalization**
  - Convert characters to a standard Unicode representation
  - Example: "é" → "e"

### Stop Word Removal

- Stopword are commonly used words in a language
- **Why remove?** Has low information, causing ambiguity, server load problem, help to deliver results faster, reduce dimensionality, and improve model performance

### Concepts of Morphology

- Study of the composition of words and their structure
- **Morphemes**: The smallest meaningful units in a language
  - E.g., "unhappiness" → "un-" (prefix) + "happy" (root) + "-ness" (suffix)
- **Root Words**: A morpheme which is the basic part of a word, carrying the primary meaning.
  - E.g., "happy" in "unhappiness"
  - Can join with other roots or affixes to form new words
- Type of **affixes**:
  - **Prefix**: Added to the beginning of a root word (e.g., "un-" in "unhappy")
  - **Suffix**: Added to the end of a root word (e.g., "-ness" in "happiness")
  - **Infix**: Inserted within a root word (e.g., "nowadays" → "now-a-days")
  - **Circumfix**: Surrounds a root word (e.g., "enlighten" → "en- + light + -en")

## Chapter 4: Synthetic Analysis

### Part-of-Speech (POS) Tagging

- Some common tags
  - **Noun**
  - **Verb**
  - **Adjective**
  - **Adverb** (to describe verbs, adjectives, or other adverbs, like unfortunately, slowly)
  - **Preposition** (of, by, to etc.)
  - **Pronoun** (I, me, mine, etc.)
  - **Determiner** (the, a, those, that etc.)

### Hidden Markov Model

"computers process programs accurately"

| (part of) lexicon      |       |
| ---------------------- | ----- |
| $P(computers \| N)$    | 0.123 |
| $P(process \| N)$      | 0.1   |
| $P(process \| V)$      | 0.2   |
| $P(programs \| N)$     | 0.11  |
| $P(programs \| V)$     | 0.15  |
| $P(accurately \| Adv)$ | 0.789 |

| (part of) transitions |      |
| --------------------- | ---- |
| $P(N \| V)$           | 0.5  |
| $P(V \| N)$           | 0.4  |
| $P(N \| N)$           | 0.6  |
| $P(N \| Adv)$         | 0.12 |
| $P(Adv \| N)$         | 0.01 |
| $P(V \| V)$           | 0.05 |
| $P(V \| Adv)$         | 0.05 |
| $P(Adv \| V)$         | 0.13 |

- Path (N -> N -> N -> Adv)
  - Emission: $0.123 * 0.1 * 0.11 * 0.789 = 0.001067517$
  - Transition: $0.6 * 0.6 * 0.01 = 0.0036$
  - Total: $0.001067517 * 0.0036 = 3.84306e^{-6}$
- Path (N -> V -> N -> Adv)
  - Emission: $0.123 * 0.2 * 0.11 * 0.789 = 0.002135034$
  - Transition: $0.4 * 0.5 * 0.01 = 0.002$
  - Total: $0.002135034 * 0.002 = 4.27006e^{-6}$
- Path (N -> N -> V -> Adv)
  - Emission: $0.123 * 0.1 * 0.15 * 0.789 = 0.001455705$
  - Transition: $0.6 * 0.4 * 0.13 = 0.0312$
  - Total: $0.001455705 * 0.0312 = 4.541799e^{-5}$
- Path (N -> V -> V -> Adv)
  - Emission: $0.123 * 0.2 * 0.15 * 0.789 = 0.00291141$
  - Transition: $0.4 * 0.05 * 0.13 = 0.0026$
  - Total: $0.00291141 * 0.0026 = 7.56966e^{-6}$
- Path (N -> N -> V -> Adv) has the highest probability, so the most likely POS tagging is "computers/N process/N programs/V accurately/Adv".

## Chapter 5: Semantic Analysis

### Lexical Semantics

- **Homonymy**: Words that pronounced and possibly spelled the same but have different meanings (e.g., "bat" as an animal and "bat" as a sports equipment)
  
  |           | Pronunciation | Spelling  | Meaning   | Example                                |
  | --------- | ------------- | --------- | --------- | -------------------------------------- |
  | Homonym   | Same          | Same      | Different | Bat (animal) vs Bat (sports equipment) |
  | Homophone | Same          | Different | Different | "to" vs "two"                          |
  | Homograph | Different     | Same      | Different | "lead" (to guide) vs "lead" (a metal)  |

- **Polysemy**: A word that has multiple related meanings (e.g., "wood" can refer to the material or a forested area)
- **Synonymy**: Words that have the same or similar meanings (e.g., "big" and "large")
- **Antonymy**: Words that have opposite meanings (e.g., "hot" and "cold")
- **Hyponymy**: A word that is more specific than another word (e.g., "rose" is a hyponym of "flower"), like subclass

### Semantic Roles Labeling

| Role        | Description                                                | Example                        |
| ----------- | ---------------------------------------------------------- | ------------------------------ |
| Agent       | The entity that performs the action                        | The investor                   |
| Predicate   | The action or event being described                        | deposited                      |
| Theme       | The entity that is affected by the action                  | the funds                      |
| Goal        | The entity that is the target or destination of the action | into the high-interest account |
| Source      | The entity from which the action originates                | from the bank                  |
| Instrument  | The entity that is used to perform the action              | with a pen                     |
| Patient     | The entity that undergoes a change of state or condition   | The vase (was broken)          |
| Location    | The place where the action occurs                          | at the office                  |
| Stimulus    | The entity that triggers the action                        | The takeoff                    |
| Experiencer | The entity that experiences the action or event            | The passenger                  |
| Beneficiary | The entity that benefits from the action                   | for the charity                |

### Levenshtein Distance

- A measure of the difference between two strings, defined as the minimum number of single-character edits (**insertions, deletions, or substitutions**) required to change one string into the other.
- Each operation has a cost of 1
- Steps to calculate Levenshtein Distance between two strings:
  1. Create a matrix with dimensions (len(str1)+1) x (len(str2)+1), there is an extra epsilon row and column to account for the empty string
  2. Initialize the first row and column with index values
  3. Go through each empty cell in right and down direction (right first or down first, doesn't matter), and fill the cell based on the case:
      - If the characters are the same, copy the value from the top-left diagonal cell
      - If the characters are different, take the minimum of the three neighboring cells (top, left, top-left diagonal) and add 1
  4. The final answer is the value in the bottom-right cell of the matrix, which represents the Levenshtein Distance between the two strings.
- Example: Calculate the Levenshtein Distance between "kitten" and "sitting"

|                | $\epsilon$ | s   | i   | t          | t   | i          | n   | g   |
| -------------- | ---------- | --- | --- | ---------- | --- | ---------- | --- | --- |
| **$\epsilon$** | 0          | 1   | 2   | 3          | 4   | 5          | 6   | 7   |
| **k**          | 1          | 1   | 2   | 3          | 4   | 5 `(5, 1)` | 6   | 7   |
| **i**          | 2          | 2   | 1   | 2          | 3   | 4          | 5   | 6   |
| **t**          | 3          | 3   | 2   | 1          | 2   | 3          | 4   | 5   |
| **t**          | 4          | 4   | 3   | 2 `(3, 4)` | 1   | 2          | 3   | 4   |
| **e**          | 5          | 5   | 4   | 3          | 2   | 2          | 3   | 4   |
| **n**          | 6          | 6   | 5   | 4          | 3   | 3          | 2   | 3   |

- For example, at the cell `(3, 4)`, the characters are 't' and 't', which are the same, so we copy the value from the top-left diagonal cell (which is 2).
- At the cell `(5, 1)`, the characters are 'i' and 'k', which are different, so we take the minimum of the three neighboring cells (top: 5, left: 4, top-left diagonal: 4) and add 1, resulting in 5.
- Final answer is **3** (bottom-right cell), which means it takes 3 edits to change "kitten" into "sitting" (substitute 'k' with 's', substitute 'e' with 'i', and insert 'g' at the end).

### Word Sense Disambiguation (WSD)

- Process of identifying the specific meaning of a word (sense) in a given context, especially when the word has multiple meanings (polysemy)
- NLP model use surrounding words as context to resolve ambiguity
- E.g.
  - "I went to the bank to deposit money.", context of "deposit money" indicates that "bank" refers to a financial institution
  - "I sat on the river bank and watched the sunset.", context of "river" indicates that "bank" refers to the side of a river
- Methods:
  - **Knowledge-based methods**: Use dictionaries, thesauri, or semantic networks to determine the correct sense of a word based on its context, e.g. Lesk algorithm
  - **Supervised machine learning methods**: Train a model on a labeled dataset where the correct sense of words is annotated, and use features from the context to predict the sense of a word in new sentences

### Similarity Measures

- **Cosine Similarity**, embed the documents into vectors using algorithms such as TF-IDF, Word2Vec, or BERT, and then calculate the cosine of the angle between the vectors to determine similarity
- **Jaccard Similarity**, measure the similarity between two sets by dividing the size of their intersection by the size of their union

## Chapter 7 Sentiment Analysis

### Lexical vs Machine Learning Approaches

| Lexical Approach                                                                                                                          | Machine Learning Approach                                                              |
| ----------------------------------------------------------------------------------------------------------------------------------------- | -------------------------------------------------------------------------------------- |
| Rule-based, uses a predefined dictionary with sentiment scores for words                                                                  | Data-driven, uses labeled datasets to train models                                     |
| Word order matters, linguistic modifiers can control intensity and polarity of sentiment (e.g., "not good" vs "good")                     | Varies based on the model, transformers can capture context and word order             |
| Struggles with sarcasm, irony, double negation, out of vocabulary words, and context-dependent sentiment (e.g., "I love waiting in line") | Handles context better, especially with advanced models like BERT and GPT              |
| Explainable, as the sentiment score can be traced back to specific words in the dictionary                                                | Not always explainable, as the model's decision-making process can be opaque/black box |
| Suitable for social media text, short reviews                                                                                             | Suitable for longer reviews, articles, and complex text                                |

### Sentiment Analysis Techniques

- **VADER**
  - Lexicon and rule-based sentiment analysis tool specifically designed for social media text (short, informal, and emotive)
- **Transformers & BERT-based models**
  - Pre-trained language models that can be fine-tuned for sentiment analysis tasks, capturing context and nuances in text

### Sentiment Analysis Limitation/Challenges

- **Context-Dependent Words and Sarcasm**: Words can have different sentiment based on context, and sarcasm can invert the intended sentiment. E.g. "The singer was so sick!!!" means the singer was amazing, but the word "sick" is usually negative.
- **Polyglot Mixing, Slang, Dialects**: Social media text often contains a mix of languages, slang, and dialects, making it challenging for models to accurately interpret sentiment. E.g. "Bruh, dis is hella lit!"
- **Subjectivity and Data Labeling Noise**: Emotional expressions can be subjective, and different annotators may label the same text differently, leading to noisy training data. A strict and consistent labeling guideline is necessary to reduce subjectivity of the data labeling process.

## Chapter 8 Topic Modeling

- Statistical Model used to discover abstract topics that occur in a collection of documents
- Concern about the word frequency, word relationship, and word co-occurrence in the documents

### Topic Modeling Techniques

- Bag-of-Words (BoW) Model
  - Represents documents as a collection of words, ignoring grammar and word order
  - Each document is represented as a vector of word counts or frequencies
  - Cosine similarity can be used to measure the similarity between documents based on their word vectors
- Latent Features
  - Using the result of BoW, we can use dimensionality reduction techniques such as Latent Semantic Analysis (LSA) to identify clusters in the latent space, which can represent topics in the documents
  - E.g., words like "height", "weight", and "BMI" may cluster together in the latent space, indicating a topic related to health and fitness

### Topic Distribution

- Probabilistic topic modeling techniques, documents may contain multiple topics, and each topic may be represented by a distribution of words
- **Latent Dirichlet Allocation (LDA)**
  - The algorithm ***assumes*** all documents are generated by:
    - A defined number of topics and their respective distributions (like "politics 60%", "economics 30%", "sports 10%")
    - A defined number of words and their respective distributions for each topic (like "politics: government, election, policy", "economics: market, trade, inflation", "sports: football, basketball, tennis")
    - Randomly selecting a topic for each word in the document based on the topic distribution, and then randomly selecting a word from the selected topic's word distribution, until all words in the document are generated
  - It attempts to reverse this process, going through iterations to improve its guess of the topic distribution for each document and the word distribution for each topic, unsupervisedly
  - In each iteration, for each document, for each word
    - check how popular is the topic in the document (document-topic balance) and how popular is the word belongs to the topic across all documents (topic-word balance), this is called Gibbs Sampling
    - The probability of the word belonging to a topic is the product of the two balances. After all topics are considered, then the topic of the word is updated by the weighted random selection of the topic based on the probability of the word belonging to each topic
  - This will slowly converge to a stable state

## Chapter 9 Text Mining & Named Entity Recognition (NER)

### Text Mining

- Text Mining is more challenging compared to traditional data mining, as the data is unstructured and requires more preprocessing and feature extraction to convert it into a structured format suitable for analysis

### Named Entity Recognition (NER)

- Identifying and classifying named entities in text into predefined categories such as person names, organizations, locations, dates, and more
- Applications
  - **Information Extraction**: Extracting relevant entities from unstructured text for further analysis
  - **Question Answering Systems**: Identifying entities in questions to provide accurate answers
  - **Content Classification**: Categorizing documents based on the entities they contain
  - **Sentiment Analysis**: Understanding the sentiment associated with specific entities in text
- Approaches

    | Knowledge Engineering Approach                                                                     | Learning Approach                                                                                             |
    | -------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------- |
    | Rule-based, uses handcrafted rules and patterns to identify entities                               | Statistical and machine learning-based, data-driven, uses labeled datasets to train models                    |
    | Developed by linguists and domain experts, requires extensive knowledge of the language and domain | No need for extensive knowledge of the language or domain                                                     |
    | Requires small amount of training data, as the rules are manually created                          | Requires large amounts of quality labeled training data                                                       |
    | Very time-consuming and labor-intensive to create and maintain rules                               | Depends on the quality and quantity of training data, and may require retraining for new domains or languages |
    | Hard to accomodate new entities or adapt to new domains, as rules may not generalize well          | Some changes may require re-annotating the training data and retraining the model                             |

- Steps
  1. Preprocessing: Tokenization, POS tagging, and other preprocessing steps to prepare the text for NER
  2. Entity Extraction: Identify potential named entities in the text using rules, patterns, or machine learning models
  3. Coreference Resolution: Resolve references to the same entity in the text (e.g., "Barack Obama" and "he" may refer to the same person)
  4. Output Generation: Classify the identified entities into predefined categories and generate structured output (e.g. export to database) for further analysis or applications
