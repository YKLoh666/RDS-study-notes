- [Chapter 1 (The Nature of AI)](#chapter-1-the-nature-of-ai)
  - [Glossary](#glossary)
  - [Timeline of AI](#timeline-of-ai)
  - [AI Approaches](#ai-approaches)
  - [Turing Test](#turing-test)
  - [The Chinese Room](#the-chinese-room)
- [Chapter 2 (Problem Definition and Problem Solving)](#chapter-2-problem-definition-and-problem-solving)
  - [Problem Solving Concept](#problem-solving-concept)
  - [Goal Formulation](#goal-formulation)
  - [Problem Formulation](#problem-formulation)
  - [Search-Solution-Execution](#search-solution-execution)
  - [Problem Solving Metrics](#problem-solving-metrics)
- [Chapter 3 (Uninformed Search)](#chapter-3-uninformed-search)
  - [Algorithms](#algorithms)
  - [Goal Test](#goal-test)
  - [Closed/Open Lists](#closedopen-lists)
  - [Performance](#performance)
  - [Cautions](#cautions)
  - [More algorithms](#more-algorithms)
- [Chapter 4 (Informed Search)](#chapter-4-informed-search)
  - [Heuristic](#heuristic)
  - [Hill Climbing](#hill-climbing)
  - [Issues in Hill Climbing](#issues-in-hill-climbing)
  - [Best First Search](#best-first-search)
  - [A\* Search](#a-search)
  - [Performance](#performance-1)
- [Chapter 5 (Knowledge Representation)](#chapter-5-knowledge-representation)
  - [Introduction](#introduction)
  - [Semantic Networks](#semantic-networks)
  - [Conceptual Graphs](#conceptual-graphs)
  - [And/Or Graphs](#andor-graphs)
  - [Frames](#frames)
- [Chapter 6 (Natural Language Understanding)](#chapter-6-natural-language-understanding)
  - [NLP](#nlp)
  - [NLU Challenges](#nlu-challenges)
    - [Ambiguity](#ambiguity)
    - [Sarcasm (Extra)](#sarcasm-extra)
  - [Stages of Language Analysis](#stages-of-language-analysis)
  - [Symbolic Analysis](#symbolic-analysis)
  - [Statistical Analysis](#statistical-analysis)

# Chapter 1 (The Nature of AI)

### Glossary

- Artificial Intelligence (AI): The simulation of human intelligence processes by machines, especially computer systems.

### Timeline of AI

> Not all from the lecture notes are included

- **1950**: Alan Turing proposes the **Turing Test**
- **1964**: The first chatbot, **ELIZA**, is created by Joseph Weizenbaum
- **1997**: IBM's **Deep Blue** defeats world chess champion Garry Kasparov
- **2011**: **Siri**, Apple's virtual assistant, is launched
- **2014**: **Amazon Alexa** is launched
- **2020**: OpenAI releases **ChatGPT** with GPT-3, a state-of-the-art language processing AI

### AI Approaches

- **Think Humanly**: Cognitive Modelling Approach
  - Design to solve problem by thinking, reasoning and remembering, mimic how human brain works
- **Think Rationally**: Law of Thought Approach
  - Codify rationality using logics, process inferences and derive new representation to deduce conclusions.
- **Act Humanly**: Turing Test Approach
  - Reflects human behavior and emotions
- **Act Rationally**: Agent Approach
  - Act autonomously, sensitive to environment, adaptable to changes, goal-oriented.

### Turing Test

- By Alan Turing
- "Imitation Game"
- One human, one machine, one human interrogator
- The interrogator gives questions to both the human and the machine, without knowing which is which.
- Through the answers by the respondents, the interrogator guess who is the machine
- If the interrogator is unable to distinguish between the human and the machine, the machine is considered to have passed the test.
- **Application**
  - CAPTCHA (Completely Automated Public Turing test to tell Computers and Humans Apart)

### The Chinese Room

- Thought experiment by John Searle
- Given a room containing a respondent and a rule book dictating how to respond to questions in Chinese
- The respondent does not understand Chinese but is able to follow the rules to produce appropriate responses.
- When the interrogator receives responses from the room, they cannot tell whether the respondent understands Chinese or is simply following the rules.
- This thought experiment raises questions about the difference in semantic understanding and syntactic processing.

# Chapter 2 (Problem Definition and Problem Solving)

### Problem Solving Concept

1. Goal Formulation
2. Problem Formulation
3. Search Solution Execution

### Goal Formulation

- **Goal**
  - Define what is considered a successful outcome
- **Optimal Solution**
  - The best possible solution among all feasible solutions
- **Abstraction**
  - Simplify the scope of the problem by focusing on the most relevant aspects
- **Example (Maze Problem)**
  - The goal is to reach the exit.
  - The optimal solution is the shortest path to the exit.
  - Abstract away the steepness of the path to the exit, solely focusing on the distance to the exit.

### Problem Formulation

- **Initial State**
  - Starting configuration of the problem
- **Successor Function**
  - All possible actions that can be taken from a given state to reach the next state
- **State Space**
  - All possible configurations of the problem
- **Path**
  - A sequence of states connected by actions
- **Goal Test**
  - A test to determine if the current state is the goal state
- **Step Cost**
  - Cost of taking a specific action
- **Path Cost**
  - The total cost of a path from the initial state to a given state

### Search-Solution-Execution

- **Search** for the best path from the initial state to the goal state
- **Solution** discovering using search algorithms
- **Execution** of the solution discovered

### Problem Solving Metrics

- **Completeness**: Does the solution cover all possible scenarios?
- **Optimality**: Is the solution the best among all possible solutions?
- **Space Complexity**: How much memory does the solution require?
- **Time Complexity**: How much time does the solution take to execute?

# Chapter 3 (Uninformed Search)

### Algorithms

- **Breadth-First Search (BFS)**
  - Examine all nodes in the same level (depth) before proceed to next level
  - Repeat until solution is found or all nodes are explored
  - Skip nodes existed in either closed or open lists when generating new nodes
- **Depth-First Search (DFS)**
  - Explore as far as possible along a branch before backtracking
  - Repeat until solution is found or all nodes are explored
  - Skip nodes existed in closed list when generating new nodes

### Goal Test

- **Early Goal Test**: Test the state/node as soon as it is generated
- **Late Goal Test**: Test the state/node only when it is expanded

### Closed/Open Lists

- **Closed List**: A list of all explored nodes
- **Open List**: A list of all generated but not yet explored nodes

### Performance

| BFS         | DFS                    |
| ----------- | ---------------------- |
| Complete    | Complete               |
| Optimal     | Not guaranteed optimal |
| O(V+E)      | O(V+E)                 |
| More memory | Less memory            |

> V: Number of vertices (nodes)
>
> E: Number of edges (connections)

### Cautions

- Must follow the successor function to generate/expand the states in consistent order

### More algorithms

- Iterative Deepening Search (IDS)
  - Combining BFS and DFS
  - The tree starts with a depth limit of 1
  - Perform DFS with the current depth limit
  - If the solution is not found, increase the depth limit and repeat
- Bidirectional Search
  - Search from both the initial state and the goal state simultaneously
  - Stop when the two searches meet

# Chapter 4 (Informed Search)

### Heuristic

- Function used to identify how close a state is to the goal state
- Design using domain knowledge and experience
- Can lead to suboptimal solutions if it is not admissible
- **Local Heuristic**: A heuristic that is only applicable to a specific region of the search space
- **Global Heuristic**: A heuristic that is applicable to the entire search space

### Hill Climbing

- Simple Hill Climbing
  - Find all neighboring states
  - Select the **FIRST** neighbor that is better than the current state
    - Eg. Current State = `4`, Neighbors = `[3, 2, 5]`
    - Choose `3`, because it is the first one that is better than `4`, despite the fact that `2` is better.
  - Continue this process until no better neighbors are found.
- Steepest Ascent Hill Climbing
  - Find all neighboring states
  - Select the neighbor with the **BEST** score
    - Eg. Current State = `4`, Neighbors = `[3, 2, 5]`
    - Choose `2`, because it is the best one among `3`, `2`, and `5`.
  - Continue this process until no better neighbors are found.

### Issues in Hill Climbing

- **Foothill**: Local Maximum
- **Plateau**: Flat areas in the search space (All neighbors have the same score)
- **Ridge**: States where multiple paths lead to the same state, but only one path is the best, which can be easily missed.

### Best First Search

- Steepest Ascent Hill Climbing with backtracking
- f(n) = h(n)
- Expand the best node in the open list
- Don't re-expand nodes in the closed list
- Expand until the goal is found or all nodes are explored

### A\* Search

- Best First Search with a path cost
- f(n) = g(n) + h(n)
- Expand the node with the lowest f(n) value
- Don't re-expand nodes in the closed list
- Expand until the goal is found or all nodes are explored

### Performance

| SHC              | SAHC             | Best FS           | A\*               |
| ---------------- | ---------------- | ----------------- | ----------------- |
| Incomplete       | Incomplete       | Complete          | Complete          |
| Not optimal      | Not optimal      | Not optimal       | Optimal           |
| Time inefficient | Time inefficient | Time inefficient  | Time efficient    |
| Space efficient  | Space efficient  | Space inefficient | Space inefficient |

> The performance above is relative to one another

# Chapter 5 (Knowledge Representation)

### Introduction

- Knowledge representation is a key aspect of AI, enabling machines to understand and reason about the world.

### Semantic Networks

- Node and edge
- Nodes represent concepts or entities.
- Edges represent relationships between nodes.
- Inheritance: `isa`, `instance`
- Binary/Non-Binary Predicate
  - Binary: `team(Ronaldo, Portuguese)`
  - Non-Binary: `score(Portuguese, Morocco, 0-1)`
- Advantages
  - Easy to visualize and understand
  - Related knowledge is easily categorized
- Disadvantages
  - No standardized representation
  - Cannot describe attribute

### Conceptual Graphs

- Nodes represent concepts or conceptual relationship.
- No labeled arcs
- Conceptual Relationship is a pill shape
- Reduce the statements into binary predicates
  - Sidnee is a small dog
    - `instance(Sidnee, dog)`
    - `size(Sidnee, small)`
  - Sidnee bites a postman very hard
    - `bite(Sidnee, postman)` = `agent(Sidnee, bite), victim(postman, bite)`
    - `strength(bite, hard)`

### And/Or Graphs

- Hypergraphs
- Suitable for rule based systems
- Can represent complex relationships
- If-Then rules can be easily represented
- Use a link between arrows to show `and`
- Example:
  - If A then B: `A -> B`
  - If A or B then C: `A -> C <- B`
  - If A and B then D:
    ```
          A -> D
            |  ^
     (Link) ---|
               B
    ```

### Frames

- Frames are data structures for representing stereotypical situations.
- Each frame consists of:
  - **Slots**: Attributes or properties of the frame.
  - **Values**: Specific values for each slot.
- Inheritance: Frames can inherit properties from other frames.
- Example:

  ```
  Dog
  isa: Class
  color:
  size:
  breed:
  ```

  ```
  Labrador
  instance: Dog
  color: Brown
  size: Medium
  breed: Labrador
  ```

- Advantages
  - Represent stereotype objects
  - Flexible to add new slots in child frames.
  - Show constraints (one instance for a class must have a unique set of attribute values as in the class inherited).
  - Show inheritance relationships clearly.
- Disadvantages
  - Difficult to program and make inferences
  - Limited events/actions representation.
  - Cannot be quantified using all and some

# Chapter 6 (Natural Language Understanding)

### NLP

- Subfield of AI focused on the interaction between computers and humans through natural language.
- **Natural Language Understanding (NLU)**
  - The ability of a computer program to understand human language as it is spoken or written.
  - Involves tasks such as sentiment analysis, entity recognition, and intent detection.
- **Natural Language Generation (NLG)**
  - The ability of a computer program to generate human-like text based on input data.
  - Involves tasks such as text summarization, report generation, and dialogue systems.
- Examples
  - Word Sense Disambiguation
  - Named Entity Recognition
  - Information Retrieval (Search Engines)
  - Text Summarization
  - Machine Translation

### NLU Challenges

#### Ambiguity

- **Syntactic Ambiguity**
  - The same sentence structure can be interpreted in multiple different syntactic structures.
    - "I saw the man with the telescope."
    - Either the man had the telescope, or I used the telescope to see the man.
  - Use parse trees to represent the different interpretations.
- **Semantic Ambiguity**
  - The same word or phrase can have multiple meanings.
  - "Bank" can refer to a financial institution or the side of a river.

#### Sarcasm (Extra)

- Context and tone are crucial for understanding sarcasm.
- Example:
  - "Oh great! Another rainy day."
  - The literal meaning is positive, but the speaker likely feels negative about the rain.

### Stages of Language Analysis

1. Parsing
   - Use parse trees to represent the syntactic structure of sentences.
2. Semantic Representation
   - Using semantic networks, conceptual graphs, or frames to represent meaning.
   - Able to solve **canonicity** issues.
     - "I was given a book by the teacher."
     - "The teacher gave me a book."
3. World Knowledge Representation
   - Incorporating general world knowledge and context into the understanding process.
   - Expand the existing network of knowledge by adding new information and relationships.
   - Reasoning

### Symbolic Analysis

- **Morphology**
  - Prefixes
  - Suffixes
  - Target: Detect changes in meaning of root words based on context.
- **Prosody**
  - Rhythm
  - Intonation
  - Target: Emotion recognition
- **Phonology**
  - Sound patterns
  - Relate sounds to the words they represent.
  - Target: Recognize and generate speech sounds.
- **Pragmatics**
  - Contextual meaning
  - Target: Understand the intended meaning behind words based on context.
- **World Knowledge**
  - Ontology: A formal representation of knowledge as a set of concepts within a domain, and the relationships between those concepts.

### Statistical Analysis

- **Bag of Words / Term Frequency**
  - Count the frequency of each word in a document.
  - Ignore grammar and word order.
  - Understand a document's main topics using the intensity of word occurrences.
- **TF-IDF (Term Frequency-Inverse Document Frequency)**
  - Term Frequency \* ln(Total Documents / Document Frequency)
  - Penalizes common words and rewards rare words.
- **Word Embeddings**
  - Represent words in N-dimensional space.
  - Each dimension captures a different aspect of word meaning
- **N-Grams**
  - Can capture word orders
  - Eg. `"I love AI"`
    - Unigrams: `["I", "love", "AI"]`
    - Bigrams: `["I love", "love AI"]`
- **Recurrent Neural Networks (RNNs/LSTMs etc.)**
  - Can capture sequential dependencies
- **Transformers (BERT, GPT, etc.)**
  - Use self-attention mechanisms
  - Can capture long-range dependencies and figure out important contextual relationships.
