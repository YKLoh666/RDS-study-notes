# Natural Language Processing (NLP)

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

### Stop Word Removal ⭐

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
