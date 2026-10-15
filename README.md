# Week 05 Lab: Text Embeddings, Semantic Retrieval and CLIP

**Name:**
**Student ID:**

## What this project does

This lab uses pretrained models (no training) for two prototypes:

1. **Semantic text matching** with `sentence-transformers/all-MiniLM-L6-v2`
2. **Zero-shot image classification** with `openai/clip-vit-base-patch32`

## What was done

**Task 1: Sentence similarity**
- Encoded 7 classroom commands into 384-dimensional vectors.
- Built a cosine similarity matrix and ranked sentences against "Turn on the classroom fan".
- Wrote `top_matches(query, texts, k)` and tested it on new paraphrases and a negative command.
- Finding: "Turn on" and "Turn off" score as similar because they share the same topic. Similarity does not capture opposite intent.

**Task 2: FAQ retriever**
- Encoded 5 FAQ titles and matched student questions to the closest one.
- Added an empty-input check and a threshold that returns `no_match` for low scores.
- Compared thresholds 0.30, 0.45 and 0.60, and measured top-1 accuracy on in-scope questions.
- Finding: a low threshold accepts unrelated questions, and a high threshold rejects valid paraphrases. Cosine similarity is not a probability.

**Task 3: CLIP image-text matching**
- Classified 4 or more images using text labels, with no classifier training.
- Reworded prompts and added a fifth label to see how scores and ranking change.
- Wrote `decide_folder()` that returns a folder or `Review` for low-confidence results.
- Finding: CLIP scores are relative to the label set, and ambiguous images give uncertain results. CLIP alone cannot count objects or give bounding boxes (use YOLO for that).

**Task 4: Testing and reflection**
- Ran test cases for empty input, paraphrases, out-of-domain questions and CLIP prompt changes.
- Answered the short reflection questions and wrote a conclusion.

## Results

Fill in after running the notebook:

| Item | Result |
| --- | --- |
| FAQ top-1 accuracy (in-scope) | |
| Best threshold found | |
| Out-of-scope questions rejected | |
| CLIP images correct (top label) | |
| Ambiguous image outcome | |

## How to run

1. Open `Week05_StudentID.ipynb` in Google Colab.
2. Run all cells in order. The first cell installs the libraries.
3. Upload 4 or more non-sensitive images when the Task 3 upload cell asks.

## Limitations

- Small test sets and few images.
- Thresholds are experimental values, not universal defaults.
- Semantic similarity alone is not safe for control actions.

## Possible improvements

- Richer FAQ text with synonyms and example questions.
- More test queries for threshold tuning.
- A human `Review` step for low-confidence cases.
