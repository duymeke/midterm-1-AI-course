# Midterm 1: answers

GitHub username: duymeke  
Session code: maple-66  
Fingerprint: 809a7923

## AI-use declaration

I used ChatGPT to understand the assignment, generate my dataset in Google Colab, check formulas, calculate results, and write simple explanations. I used Google Colab to run the provided Python code and read my CSV files. My dataset was generated using my own username and session code. I checked the results and used AI to help me understand them. I am responsible for my answers and will explain the main calculations during the oral check.

## Part 1: Retrieval and cost decision

### 1a. Metrics (all 60 questions)

| config | recall@1 | recall@3 | recall@5 | MRR@10 |
|---|---:|---:|---:|---:|
| A | 0.4667 | 0.6333 | 0.7167 | 0.5615 |
| B | 0.3667 | 0.6500 | 0.7167 | 0.5087 |

### 1b. Recall and 95 % Wilson interval of each candidate (recall at its own k)

| candidate | recall@k | lower | upper |
|---|---:|---:|---:|
| A, k=3 | 0.6333 | 0.5068 | 0.7438 |
| A, k=5 | 0.7167 | 0.5923 | 0.8149 |
| B, k=3 | 0.6500 | 0.5236 | 0.7583 |
| B, k=5 | 0.7167 | 0.5923 | 0.8149 |

### 1c. Annual model cost in USD

| candidate | annual cost |
|---|---:|
| A, k=3 | 31084.20 |
| A, k=5 | 40724.80 |
| B, k=3 | 20153.37 |
| B, k=5 | 22506.74 |

### 1d. Decision (at most 150 words)

Chosen candidate: B, k=3

I choose B, k=3 because it costs 20153.37 per year and stays within the 26800 budget. Both A options are too expensive. B, k=5 also fits the budget, but it costs more and its confidence interval overlaps with B, k=3. More tests are needed to know if the extra cost is worth it. For B, k=3, recall is 75% for English, 60% for Russian, and 60% for Kazakh. This means the system works better for English than for Russian and Kazakh. I would choose B, k=3 to save money and test more questions before spending more.

### 1e. Next measurement (at most 60 words)

Test more questions in English, Russian, and Kazakh. Pay special attention to Russian and Kazakh because their results are weaker. Compare B, k=3 with B, k=5 using the same questions. Measure accuracy, response time, and cost to see if retrieving five chunks is worth the extra money.

## Part 2: A document pipeline you can defend

### 2a. Numbers

| pipeline | overall accuracy | weakest cell (language, condition) | accuracy there | lower | upper | annual cost |
|---|---:|---|---:|---:|---:|---:|
| H | 0.8889 | KK, degraded | 0.7000 | 0.5212 | 0.8334 | 35341.13 |
| L | 0.8111 | KK, degraded | 0.6333 | 0.4551 | 0.7813 | 10800.00 |

Personal-data pages per year sent abroad under H: 410625

### 2b. Memo (at most 300 words)

**To: Head of Operations**

**Subject: Choosing a document-processing system**

Pipeline H has 88.89% accuracy, while Pipeline L has 81.11%. H gives more correct results, but it costs 35341.13 per year. L costs only 10800.00 per year.

Both systems have the most problems with degraded Kazakh documents. H gets 70% correct, while L gets 63.33% correct. The confidence intervals overlap, so we need more tests to understand the real difference.

Pipeline H sends 410625 pages containing names and ИИН abroad each year. This creates privacy risks. We must check where the data is stored, who can access it, how long it is kept, and whether the provider uses it for training.

Pipeline L can keep data in Kazakhstan if the server, backups, and access are also managed locally. We must still protect the data with encryption, access controls, and deletion rules.

I recommend Pipeline L because it is much cheaper and can reduce the risk of sending personal data abroad. However, we should test more degraded Kazakh documents and ask a person to check difficult results. We should choose H only if its higher accuracy is worth the extra cost and its privacy risks can be managed.

## Part 3: Explain your own numbers

### Q1

Number: 1.06

Why (at most 40 words): Most of the difference comes from encoding bytes. The tokenizer adds a smaller extra cost for Kazakh. This means encoding is the main reason for the larger token count.

### Q2

Number: 44.4%

Why (at most 40 words): English chunks exceed the 512-token limit, but Russian and Kazakh chunks do not. The extra English text is cut off and is not included in the embedding.

### Q3

Number: 39.7%

Why (at most 40 words): Higher temperature makes the probabilities more equal but does not change the ranking. All five tokens can still be selected.

### Q4

Number: +30

Why (at most 40 words): The public leaderboard prefers X because X has more correct answers. However, the penalty score prefers Y because Y gives fewer wrong answers and can say “I don't know.”

### Q5

Number: 11.55

Why (at most 40 words): This model uses more tokens per parameter than the Chinchilla ratio, so it is over-trained by that criterion. Chinchilla argued that models such as GPT-3 needed more training tokens.
