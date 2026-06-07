# Vector Spaces u AI (Colab Projekat)

Ovaj repo sadrzi Jupyter/Colab notebook koji pokazuje prakticnu primenu teorije iz:

- Gilbert Strang, *Linear Algebra and Its Applications*
- Chapter 2: Vector Spaces
  - 2.1 Vector Spaces and Subspaces
  - 2.2 Solving Ax=0 and Ax=b
  - 2.3 Linear Independence, Basis, and Dimension
  - 2.4 The Four Fundamental Subspaces

Mapirani deo u preuzetom PDF-u:
- `Gilbert_Strang_Linear_Algebra_and_Its_Applications.pdf`
- Chapter 2 se pojavljuje na PDF stranama otprilike 87-130 (book pagination ~77-120).

## Notebook

- `vector_spaces_ai_colab.ipynb`

Notebook demonstrira:
- embedding matricu `X` kao vektorski prostor podataka
- podprostor dimenzije `k` preko SVD baze
- projekciju `x_proj` i residual/nullspace-like komponentu
- baseline retrieval vs subspace-aware retrieval
- evaluaciju preko Recall@3 i grafikon trade-off-a po `k`

## Pokretanje u Google Colab-u

1. Otvori [Google Colab](https://colab.research.google.com/).
2. Uploaduj fajl `vector_spaces_ai_colab.ipynb` iz ovog repoa.
3. Pokreni celije redom (`Runtime -> Run all`).
4. Po potrebi promeni:
   - `USE_SENTENCE_TRANSFORMERS = False/True`
   - dimenziju podprostora `k`

## Napomena o zavisnostima

Notebook po default-u koristi lagani TF-IDF backend (stabilan za Colab).
Opcioni `sentence-transformers` backend moze se ukljuciti jednim flag-om ako zelis semanticki bogatije embeddinge.
