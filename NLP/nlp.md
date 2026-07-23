# Natural Language Processing (NLP)

- [Natural Language Processing (NLP)](#natural-language-processing-nlp)
  - [Chapter 1: Introduction to NLP](#chapter-1-introduction-to-nlp)
    - [Definition](#definition)
    - [Roles of NLP](#roles-of-nlp)
    - [NLP Components](#nlp-components)
    - [Applications](#applications)
  - [Chapter 2: Text Preprocessing](#chapter-2-text-preprocessing)
    - [Stop Word Removal](#stop-word-removal)
    - [Tokenisation](#tokenisation)
    - [Normalisation](#normalisation)
    - [Emoji Handling](#emoji-handling)
    - [Punctuation Handling](#punctuation-handling)
    - [Numbers](#numbers)
    - [Abbreviations](#abbreviations)
    - [Importance of Preprocessing](#importance-of-preprocessing)
    - [Concepts of Morphology](#concepts-of-morphology)
  - [Chapter 3: Phonetics and Phonology](#chapter-3-phonetics-and-phonology)
    - [Concept of Phonetics](#concept-of-phonetics)
    - [Articulary Phonetics](#articulary-phonetics)
    - [Acoustic Phonetics](#acoustic-phonetics)
    - [Syllable Structure](#syllable-structure)
  - [Chapter 4 Syntactic Analysis](#chapter-4-syntactic-analysis)
    - [Concept of Syntactic Analysis](#concept-of-syntactic-analysis)
    - [Grammar Rules](#grammar-rules)
    - [Context-Free Grammar (CFG)](#context-free-grammar-cfg)
    - [Parser](#parser)
    - [Derivation](#derivation)
    - [Phrase Structure](#phrase-structure)

## Chapter 1: Introduction to NLP

### Definition

- Study of interaction between computers and human language

### Roles of NLP

- Enable computers to understand, interpret, and generate human language in a way that is valuable

### NLP Components

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

### Applications

- Document Recommendation
- Natural Language Search
- Sentiment Analysis
- Text Summarisation
- Topic Modelling
- Machine Translation
- Image Captioning
- Question Answering

## Chapter 2: Text Preprocessing

### Stop Word Removal

- Stopword are commonly used words in a language
- **Why remove?** Has low information, causing ambiguity, server load problem, help to deliver results faster

### Tokenisation

- Process of splitting text into smaller units called tokens
- Paragraph → Sentence → Word → Subword → Character

### Normalisation

- Process of converting text into a standard format
- **Stemming**
  - Eliminating suffixes, prefixes, infix, circumfix, etc. to get the root word
  - Example: "running" → "run", "happily" → "happi"
  - Faster, but may not always produce a valid word
- **Lemmatization**
  - Canonical form of a word, considering the context and meaning of the word
  - Example: "running" → "run", "better" → "good"
  - Slower, but always produces a valid word

### Emoji Handling

- Remove
- Replace with text (e.g., 🙂 → "smiley face")
- Keep as is (if the model can handle emojis)

### Punctuation Handling

- Remove standard punctuation marks (e.g., ., !, ?, etc.)
- Preserve punctuation marks that are important for meaning (e.g., apostrophes in contractions, hyphens in compound words)

### Numbers

- Token replacement (e.g., "123" → "\<NUM>")
- Remove numbers if they are not relevant to the analysis
- Normalize numbers (e.g., "1,000" → "1000", "twenty-one" → "21")
- NER recognition for numbers (e.g., dates, times, monetary values) to preserve their meaning in context

### Abbreviations

- Expand abbreviations (e.g., "Dr." → "Doctor", "St." → "Street")
- Keep abbreviations as is if they are commonly understood in the context of the text

### Importance of Preprocessing

- Improves model performance by reducing noise and irrelevant information
- Enhances the quality of features extracted from the text

### Concepts of Morphology

- Study of the composition of words and their structure
- **Morphemes**: The smallest units of meaning in a language
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

### Concept of Phonetics

- Study of the physical sounds of human speech, how they are produced, transmitted, and perceived
- **Phonemes**: The smallest units of sound in a language that can distinguish meaning
  - E.g., /p/ and /b/ in "pat" and "bat"

### Articulary Phonetics

- How sounds are produced
- **Place of articulation**: Where the airflow is constricted (to produce different sounds)

  | Place        | Description                                   | Example                      |
  | ------------ | --------------------------------------------- | ---------------------------- |
  | Bilabial     | Both lips                                     | "p", "b", "m"                |
  | Labiodental  | Lower lip against upper teeth                 | "f", "v"                     |
  | Alveolar     | Tongue against alveolar ridge                 | "t", "d", "s", "z", "n", "l" |
  | Postalveolar | Tongue just behind alveolar ridge             | "sh", "zh"                   |
  | Palatal      | Tongue against hard palate                    | "j" in "yes"                 |
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
  | Approximants     | Produced with a narrowing of the vocal tract, but not enough to cause turbulent airflow | Glides: "w", "j"; Liquids: "l", "r"        |
  
### Acoustic Phonetics

- Study of the physical properties of speech sounds, such as frequency, amplitude (intensity), oscillation, and duration

### Syllable Structure

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

### Concept of Syntactic Analysis

- Process of analyzing the structure of sentences in a language, identifying the relationships between words and phrases, and determining their grammatical roles

### Grammar Rules

- Describe how words and phrases can be combined to form valid sentences in a language

### Context-Free Grammar (CFG)

- Finite set of grammar rules of 4 components
  - V: Set of non-terminal symbols (e.g., S, NP, VP)
  - T: Set of terminal symbols (e.g., words in the language, tokens)
  - P: Set of production rules (e.g., S → NP VP)
  - S: Start symbol (e.g., S)

### Parser

- Algorithm that implement CFG to analyze the structure of sentences
- **Parse Tree**: Graphical depiction of a derivation of a sentence, in-order traversal of the tree gives the original sentence
- Roles
  - Create parse trees
  - Create symbol table
  - Report syntax errors
  - Recover from common syntax errors
  - Produce intermediate representation (IR) of the input text for further processing
    > In computer architecture, IR is an internal data structure/code used by compilers and interpreters to bridge high-level source code and low-level machine code. Example: Abstract Syntax Tree (AST), Three-Address Code (TAC), Control Flow Graph (CFG)

### Derivation

- Sequence of production rules applied to generate a sentence from the start symbol
- **Leftmost Derivation**: Always expand the leftmost non-terminal symbol first (In common practice, leftmost derivation is used to generate parse trees)
- **Rightmost Derivation**: Always expand the rightmost non-terminal symbol first

### Phrase Structure

- Noun Phrase (NP)
- Sentence (S)
- Verb Phrase (VP)
- Determiner (Det)
- Verb (V)
- Noun (N)
