# Iterative Semantic with Cross Embedding (ISCE)

This repository contains a research notebook exploring a **novel method for multi-hop question answering**.  
The method works entirely in **embedding space**: after each retrieval step, we algebraically update the query vector to remove already-covered information. We stop retrieving once the information gain plateaus, then pass the collected passages to a generative model to produce the final answer.

---

## Key Idea

- Embed the question with a sentence embedding model.  
- Retrieve passages from a dense index (hnswlib).  
- Update the query embedding after each hop:  
  - Subtract or adjust with the passage embedding to represent “remaining information.”  
- Check if retrieval scores have plateaued (“semantic exhaustion”).  
- Stop when exhausted, and generate the final answer from the gathered passages.

This avoids the need for a learned controller and makes multi-hop retrieval lightweight and unsupervised. Instead of relying on supervision for when to “hop,” ISCE shows that **simple algebra in embedding space** can control multi-hop retrieval effectively.

---

## Repository Contents

- `isce.ipynb` — the main notebook with method, experiments, and results.  
- Dataset used: HotpotQA (subset).  

---

## Results (HotpotQA, dev subset)

- Baseline RAG: **F1 ~0.45, EM ~0.38**  
- ISCE variants: **F1 up to ~0.48, EM up to ~0.41**

---

## How to Use

1. Open the notebook `isce.ipynb`.  
2. Run cells in order to reproduce the method and experiments.  
3. The dataset (HotpotQA subset) needs to be available locally.  
