# Natural Language Processing (NLP)

- [Natural Language Processing (NLP)](#natural-language-processing-nlp)
  - [Chapter 1: Introduction to NLP](#chapter-1-introduction-to-nlp)
    - [Definition ⭐](#definition-)
    - [Roles of NLP ⭐](#roles-of-nlp-)
    - [NLP Components ⭐](#nlp-components-)
    - [Applications ⭐](#applications-)
    - [Techniques in NLP](#techniques-in-nlp)
    - [Ambiguity in NLP (NLU \& NLG)](#ambiguity-in-nlp-nlu--nlg)
    - [NLU Steps](#nlu-steps)
    - [Real World Examples of NLP](#real-world-examples-of-nlp)
  - [Chapter 2: Text Preprocessing](#chapter-2-text-preprocessing)
    - [Text Cleaning/Noise Removal ⭐](#text-cleaningnoise-removal-)
      - [1. Emoji Handling ⭐](#1-emoji-handling-)
      - [2. Punctuation Handling ⭐](#2-punctuation-handling-)
      - [3. Numbers ⭐](#3-numbers-)
    - [Stop Word Removal ⭐](#stop-word-removal-)
    - [Tokenisation ⭐](#tokenisation-)
    - [Normalisation ⭐](#normalisation-)
    - [Abbreviations ⭐](#abbreviations-)
    - [Importance of Preprocessing ⭐](#importance-of-preprocessing-)
    - [Concepts of Morphology ⭐](#concepts-of-morphology-)
  - [Chapter 3: Phonetics and Phonology](#chapter-3-phonetics-and-phonology)
    - [Concept of Phonetics ⭐](#concept-of-phonetics-)
    - [Concept of Phonology ⭐](#concept-of-phonology-)
    - [Articulary Phonetics ⭐](#articulary-phonetics-)
    - [Acoustic Phonetics](#acoustic-phonetics)
    - [Syllable Structure ⭐](#syllable-structure-)
  - [Chapter 4 Syntactic Analysis](#chapter-4-syntactic-analysis)
    - [Concept of Syntactic Analysis ⭐](#concept-of-syntactic-analysis-)
    - [Grammar Rules ⭐](#grammar-rules-)
    - [Context-Free Grammar (CFG) ⭐](#context-free-grammar-cfg-)
    - [Parser ⭐](#parser-)
    - [Derivation ⭐](#derivation-)
    - [Phrase Structure ⭐](#phrase-structure-)

> [!Note]
> Starred sections (⭐) indicate topics mentioned by lecturer

## Chapter 1: Introduction to NLP

### Definition ⭐

- Study of interaction between computers and human language, involving either text or speech

### Roles of NLP ⭐

- Enable computers to understand, interpret, and generate human language in a way that is valuable

### NLP Components ⭐

- **Natural Language Understanding (NLU)**
  - Input component
  - Convert unstructured human language into structured data that machines can logically process
  - Analysing different aspects of language, such as syntax, semantics, and pragmatics
  - Examples: Intent Recognition, Named Entity Recognition (NER), Sentiment Analysis
- **Natural Language Generation (NLG)**
  - Output component
  - Convert structured data into natural language that is human-readable
  - How to phrase information, choosing right tone, so human can easily understand
  - Examples: Content Planning (Selecting relevant information for final response), Sentence Structuring, Text Summarisation

### Applications ⭐

- Document Recommendation
- Natural Language Search
- Sentiment Analysis
- Text Summarisation
- Topic Modelling
- Machine Translation
- Image Captioning
- Question Answering

### Techniques in NLP

- **Computer Science and Programming**
  - Python, NLP frameworks and Machine Learning libraries
- **Mathematics and Data Science**
  - Linear Algebra, Probability and Statistics, Calculus
- **Computational Linguistics**
  - Syntax & Grammars, Semantics & Pragmatics, Text Preprocessing
- **Machine Learning and Deep Learning**
  - Vector Embeddings, Sequence Models, Transformers

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

## Chapter 2: Text Preprocessing

### Text Cleaning/Noise Removal ⭐

- Remove unwanted characters and text that do not contribute to the analysis, such as HTML tags, special characters, and extra whitespace

#### 1. Emoji Handling ⭐

- Remove
- Replace with text (e.g., 🙂 → "smiley face")
- Keep as is (if the model can handle emojis)

#### 2. Punctuation Handling ⭐

- Remove standard punctuation marks (e.g., ., !, ?, etc.)
- Preserve punctuation marks that are important for meaning (e.g., apostrophes in contractions, hyphens in compound words)

#### 3. Numbers ⭐

- Remove numbers if they are not relevant to the analysis
- Token replacement (e.g., "123" → "\<NUM>")
- Normalize numbers (e.g., "1,000" → "1000", "twenty-one" → "21")
- NER recognition for numbers (e.g., dates, times, monetary values) to preserve their meaning in context

### Stop Word Removal ⭐

- Stopword are commonly used words in a language
- **Why remove?** Has low information, causing ambiguity, server load problem, help to deliver results faster

### Tokenisation ⭐

- Process of splitting text into smaller units called tokens
- Paragraph → Sentence → Word → Subword → Character

### Normalisation ⭐

- Process of converting text into a standard format
- Reduce vocabulary size (reduce noise and map similar words to a single representation)
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

### Abbreviations ⭐

- Expand abbreviations (e.g., "Dr." → "Doctor", "St." → "Street")
- Keep abbreviations as is if they are commonly understood in the context of the text

### Importance of Preprocessing ⭐

- Improves model performance by reducing noise and irrelevant information
- Enhances the quality of features extracted from the text

### Concepts of Morphology ⭐

- Study of the composition of words and their structure
- **Morphemes**: The smallest meaningful units in a language
  - E.g., "unhappiness" → "un-" (prefix) + "happy" (root) + "-ness" (suffix)
- **Root Words**: A morpheme which is the basic part of a word, carrying the primary meaning.
  - E.g., "happy" in "unhappiness"
  - Can join with other roots or affixes to form new words
- Type of affixes:
  - **Prefix**: Added to the beginning of a root word (e.g., "un-" in "unhappy")
  - **Suffix**: Added to the end of a root word (e.g., "-ness" in "happiness")
  - **Infix**: Inserted within a root word (e.g., "nowadays" → "now-a-days")
  - **Circumfix**: Surrounds a root word (e.g., "enlighten" → "en- + light + -en")

## Chapter 3: Phonetics and Phonology

### Concept of Phonetics ⭐

- Study of the physical sounds of human speech, how they are produced, transmitted, and perceived
- **International Phonetic Alphabet (IPA)**: A standardized system of symbols used to represent the sounds of spoken language
- **Phonemes**: The smallest units of sound in a language that can distinguish meaning
  - E.g., /p/ and /b/ in "pat" and "bat"
- **Importance**
  - Increase accuracy of Automatic Speech Recognition (ASR) and Text-to-Speech (TTS) systems

### Concept of Phonology ⭐

- Study of the abstract, cognitive aspects of sounds in a language, how they function and interact with each other
- **Segmental phonology**: Study of individual sounds and their patterns
- **Suprasegmental phonology**: Study of features that extend over multiple sounds, such as stress, intonation, and rhythm

### Articulary Phonetics ⭐

- How sounds are produced
- **Place of articulation**: Where the airflow is constricted (to produce different sounds)

  | Place        | Description                                   | Example                      |
  | ------------ | --------------------------------------------- | ---------------------------- |
  | Bilabial     | Both lips                                     | "p", "b", "m"                |
  | Labiodental  | Lower lip against upper teeth                 | "f", "v"                     |
  | Alveolar     | Tongue against alveolar ridge                 | "t", "d", "s", "z", "n", "l" |
  | Postalveolar | Tongue just behind alveolar ridge             | "sh", "zh"                   |
  | Palatal      | Tongue against hard palate                    | /j/ in "yes"                 |
  | Dental       | Tongue against upper teeth                    | "th" in "think", "this"      |
  | Velar        | Back of tongue against soft palate            | "k", "g", "ng"               |
  | Glottal      | Using the glottis (space between vocal cords) | "h", glottal stop            |
  
- **Manners of articulation**: How the airflow is constricted (to produce different sounds)

  | Manner           | Description                                                                             | Example                                    |
  | ---------------- | --------------------------------------------------------------------------------------- | ------------------------------------------ |
  | Nasal            | Produced with airflow through the nose                                                  | "m", "n", "ng"                             |
  | Plosive          | Produced by stopping the airflow and then releasing it                                  | "p", "b", "t", "d", "k", "g"               |
  | Fricative        | Produced by forcing air through a narrow constriction                                   | "f", "v", "s", "z", "sh", "zh", "th", "dh" |
  | Affricate        | Plosives followed by fricatives                                                         | "ch", "j"                                  |
  | Laterals/Liquids | Produced with the tongue against the alveolar ridge                                     | "l", "r"                                   |
  | Taps/Flaps       | Quick, single contact of the tongue against the alveolar ridge                          | "tt" in "butter" in American English       |
  | Approximants     | Produced with a narrowing of the vocal tract, but not enough to cause turbulent airflow | Glides: "w", /j/ (y); Liquids: "l", "r"    |
  
### Acoustic Phonetics

- Study of the physical properties of speech sounds, such as frequency, amplitude (intensity), oscillation, and duration

### Syllable Structure ⭐

- **Syllable**: A unit of spoken language consisting of a single uninterrupted sound, typically containing a vowel sound and optionally surrounded by consonants
- Structured in (C)V(C) format, where C = consonant and V = vowel
  - **Onset**: The initial consonant(s) of a syllable (optional)
  - **Nucleus**: The core of the syllable, usually a vowel (mandatory)
  - **Coda**: The final consonant(s) of a syllable (optional)
- Syllable theories
  - **Prominence Theory**: Syllables are organized around a prominent vowel sound, which serves as the nucleus of the syllable
  - **Chest Pulse Theory**: Syllables are produced based on the muscular activity
  - **Sonority Theory**: Syllables are organized based on the sonority hierarchy, which ranks speech sounds according to their relative loudness and resonance

## Chapter 4 Syntactic Analysis

### Concept of Syntactic Analysis ⭐

- Process of analyzing the structure of sentences in a language, identifying the relationships between words and phrases, and determining their grammatical roles

### Grammar Rules ⭐

- Describe how words and phrases can be combined to form valid sentences in a language

### Context-Free Grammar (CFG) ⭐

- Finite set of grammar rules of 4 components
  - V: Variables, set of non-terminal symbols (e.g., S, NP, VP)
  - T: Tokens, set of terminal symbols (e.g., words in the language, tokens)
  - P: Productions, set of production rules on how to combine terminal and non-terminal symbols (e.g., S → NP VP)
  - S: Start symbol (e.g., S)

### Parser ⭐

- Algorithm that implement CFG to analyze the structure of sentences
- **Parse Tree**: Graphical depiction of a derivation of a sentence, in-order traversal of the tree gives the original sentence
- Roles
  - Create parse trees
  - Create symbol table
  - Report syntax errors
  - Recover from common syntax errors
  - Produce intermediate representation (IR) of the input text for further processing
    > In computer architecture, IR is an internal data structure/code used by compilers and interpreters to bridge high-level source code and low-level machine code. Example: Abstract Syntax Tree (AST), Three-Address Code (TAC), Control Flow Graph (CFG)

### Derivation ⭐

- Sequence of production rules applied to generate a sentence from the start symbol
- **Leftmost Derivation**: Always expand the leftmost non-terminal symbol first (In common practice, leftmost derivation is used to generate parse trees)
- **Rightmost Derivation**: Always expand the rightmost non-terminal symbol first

### Phrase Structure ⭐

- Sentence (S)
  - Declarative: NP + VP
    - E.g., "(NP) The cat (VP) sat on the mat."
  - Imperative: VP
    - E.g., "(VP) Sit down."
  - Interrogative: (Wh-NP) + Aux + NP + VP
    - E.g., "(Wh-NP) What (Aux) is (NP) the cat (VP) doing?"
    - E.g., "(Aux) Is (NP) the cat (VP) sitting on the mat?"
- Noun Phrase (NP)
- Verb Phrase (VP)
- Determiner (Det)
  - E.g., "the", "a", "some"
- Nominals
  - Pre and post modifiers of nouns
  - Quantifiers, adjectives, ordering, prepositions, relative clauses, etc.
- Verb (V)
- Noun (N)
