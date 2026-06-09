# Math Foundations of AI: Recommend Me a Movie

This repo contains a single beginner-friendly Jupyter/Colab notebook that builds a movie
recommendation system from scratch to show the math behind AI in practice. The guiding
idea: **an AI recommendation = turn things into vectors, then measure which ones are
closest / most similar.**

Each step follows the same template: **what we do -> why (a real-life analogy) ->
the formula -> the link to the theory.**

## Sources

- **Vectors** - Gilbert Strang, *Linear Algebra and Its Applications*, Chapter 2 (Vector Spaces):
  describing things with numbers and treating them as points in a space.
  [PDF](https://rksmvv.ac.in/wp-content/uploads/2021/04/Gilbert_Strang_Linear_Algebra_and_Its_Applicatio_230928_225121.pdf)
- **Similarity / distance** - *Introduction to Analysis*, Chapter 7 (Metric Spaces):
  how to measure how close two points are.
  [PDF](https://www.math.ucdavis.edu/~hunter/m125a/intro_analysis_ch7.pdf)

## The Notebook

**`ai_movie_recommender.ipynb`** — a step-by-step movie recommender for someone seeing AI
for the first time. It uses only `numpy`, `pandas`, and `matplotlib`, plus a small hand-made
table of ~10 movies described by 5 features (action, romance, comedy, pace, seriousness).

What it demonstrates, step by step:

- **A movie is a vector** — a row of numbers is a point in a feature space; similar movies
  are nearby points (Strang 2.1, 2.3).
- **Euclidean distance** — how "far apart" two movies are; smaller distance = more similar
  (Analysis ch. 7, definition 7.1, exercise 7.4/7.5).
- **Cosine similarity** — comparing the *angle* (taste) instead of the magnitude (rating
  strength), bounded to [-1, 1] via Cauchy-Schwarz (inner product and norm, exercise 7.15;
  Cauchy-Schwarz, theorem 7.54).
- **Normalization** — fair comparison of "taste" regardless of how high/low someone rates
  (Analysis ch. 7, norms).
- **Making a recommendation** — combining the pieces into a `recommend(movie, n)` function,
  using a similarity threshold as an open ball around a movie (definition 7.18).
- **A taste "recipe"** — solving `Ax = b` to find how much of each movie to mix to reach a
  desired taste profile `b` (Strang 2.2).
- **Movie map** — a 2D visualization of the movies with lines drawn to their recommendations,
  plus a recap of where the math showed up.

## Running in Google Colab

1. Open [Google Colab](https://colab.research.google.com/).
2. Open `ai_movie_recommender.ipynb` from this repo (upload it, or use the "Open in Colab"
   badge at the top of the notebook).
3. Run the cells in order (`Runtime -> Run all`).

## Dependencies

The first cell installs everything needed: `numpy`, `pandas`, and `matplotlib`. No other
setup is required.
