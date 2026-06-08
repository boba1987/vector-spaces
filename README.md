# Vector & Metric Spaces u AI (Colab Projekat)

Ovaj repo sadrzi Jupyter/Colab notebook-e koji pokazuju prakticnu primenu matematike iz dve knjige u jednom AI pipeline-u (semantic retrieval + kNN klasifikacija). Vodeci princip: **definicija/teorema iz knjige -> numericki dokaz da vazi -> upotreba u prakticnom AI zadatku.**

## Izvori

- Gilbert Strang, *Linear Algebra and Its Applications*, **Chapter 2: Vector Spaces**
  - 2.1 Vector Spaces and Subspaces
  - 2.2 Solving Ax=0 and Ax=b
  - 2.3 Linear Independence, Basis, and Dimension
  - 2.4 The Four Fundamental Subspaces
  - PDF: `Gilbert_Strang_Linear_Algebra_and_Its_Applications.pdf` (Ch2 ~ str. 87-130)
- *Introduction to Analysis*, **Chapter 7: Metric Spaces**
  - Def 7.1 (aksiomi metrike), Ex 7.2-7.8 (L1/L2/Linf/discrete metrike)
  - Def 7.11 / Prop 7.12 (norma -> metrika), Ex 7.15 (Lp-norma, inner product)
  - Fig 1 / Ex 7.20 (jedinicne lopte), str. 98 (ekvivalencija normi)
  - Def 7.18 (otvorene lopte), Def 7.31/7.38/7.39 (nizovi, Cauchy, kompletnost)
  - Thm 7.54 (Cauchy-Schwarz), Cor 7.55 (Minkowski)
  - PDF: `intro_analysis_ch7.pdf`

## Notebook-i

- **`simple_recommender_ai_colab.ipynb`** (pocetnicki) - jednostavan sistem za preporuku filmova, objasnjen korak-po-korak za nekoga ko prvi put vidi AI; intuicija i analogije pre formula.
- **`vector_metric_spaces_ai_colab.ipynb`** (math-heavy) - objedinjuje obe teorije kroz retrieval + kNN.
- **`neural_network_math_colab.ipynb`** (math-heavy) - mala neuralna mreza od nule u NumPy; obe teorije primenjene samo onoliko koliko je potrebno da se objasni kako mreza radi.
- `vector_spaces_ai_colab.ipynb` (raniji, samo Strang Ch2) - ostaje kao referenca.

### Sta `simple_recommender_ai_colab.ipynb` demonstrira

Pocetnicki uvod u AI preporuke ("posto ti se svideo ovaj film, probaj ove"). Svaki korak ima isti sablon: **sta radimo -> zasto (analogija) -> mala formula -> veza sa knjigom**. Koristi samo numpy/pandas/matplotlib i rucno napravljenu tabelu od ~10 filmova.
- film kao vektor / tacka u prostoru osobina (Strang 2.1, 2.3) + 2D scatter
- Euklidsko rastojanje kao mera slicnosti (Ch7 Def 7.1, Ex 7.4)
- cosine slicnost i zasto je u [-1, 1] preko Cauchy-Schwarz (Ch7 Thm 7.54)
- norma i normalizacija za posteno poredjenje "ukusa" (Ch7 Def 7.11)
- funkcija `preporuci(film, n)` + prag slicnosti kao lopta oko filma (Ch7 Def 7.18)
- "recept" mesavine filmova za zeljeni ukus resavanjem `Ax=b` (Strang 2.2)
- vizualizacija mape filmova sa linijama ka preporukama + rekapitulacija korak -> matematika -> zasto

### Sta `vector_metric_spaces_ai_colab.ipynb` demonstrira

Vector Spaces (Ch2):
- numericku proveru aksioma vektorskog prostora (2.1)
- rank i eksplicitnu bazu prostora kolona preko RREF (2.3)
- resavanje `Ax=0` (baza nullspace-a) i `Ax=b` (least squares) (2.2)
- cetiri fundamentalna podprostora, rank-nullity i ortogonalnost (2.4)
- SVD bazu `V_k`, projekcionu matricu `P=V_k V_k^T` (`P^2=P`, `P=P^T`), residual (2.1/2.3/2.4)

Metric Spaces (Ch7):
- verifikaciju aksioma metrike za L1/L2/Linf/Lp/discrete (Def 7.1)
- norme, indukovanu metriku, translacionu invarijantnost i homogenost (Def 7.11, Prop 7.12)
- Cauchy-Schwarz i izvodjenje cosine slicnosti (Thm 7.54, Ex 7.15)
- Minkowski / nejednakost trougla (Cor 7.55)
- ekvivalenciju normi (str. 98) i jedinicne lopte (Fig 1)
- otvorene lopte za radius retrieval (Def 7.18)
- gradient descent kao Cauchy niz + kompletnost (Def 7.31/7.38/7.39)

AI primena:
- semantic retrieval sa poredjenjem metrika (cosine/L2/L1/Linf/Mahalanobis), full vs subspace, Recall@k i radius retrieval
- kNN klasifikaciju po metrikama + decision boundary vizualizaciju u 2D

### Sta `neural_network_math_colab.ipynb` demonstrira

Mala MLP (`2 -> 8 -> 1`) na 2D two-moons datasetu, implementirana od nule (rucni forward/backprop). Svaki korak vezan za poglavlje:
- linearni sloj `z=Wx+b` kao afino preslikavanje izmedju vektorskih prostora (Strang 2.1, 2.2)
- `rank(W)` kao kapacitet sloja (2.3); `C(W)` i `N(W)` = sta sloj propusta/ignorise, sa proverom `W@n~0` (2.4)
- aktivacije kao neprekidne, Lipschitz funkcije (Ch7 Def 7.44, Cor 7.55)
- loss kao kvadrat L2 norme + L2 regularizacija (Ch7 Def 7.11)
- backprop + gradient-check; inner product i Cauchy-Schwarz za smer najbrzeg pada (Ch7 Ex 7.15, Thm 7.54)
- trening kao Cauchy niz koji konvergira zbog kompletnosti `R^P` (Ch7 Def 7.31/7.38/7.39)
- evaluacija + vizualizacija zakrivljene granice odluke

## Pokretanje u Google Colab-u

1. Otvori [Google Colab](https://colab.research.google.com/).
2. Uploaduj zeljeni notebook iz ovog repoa (`simple_recommender_ai_colab.ipynb`, `vector_metric_spaces_ai_colab.ipynb` ili `neural_network_math_colab.ipynb`), ili koristi Open In Colab badge u notebook-u.
3. Pokreni celije redom (`Runtime -> Run all`).
4. Po potrebi promeni:
   - `USE_SENTENCE_TRANSFORMERS = False/True`
   - dimenziju podprostora `k`

## Napomena o zavisnostima

Notebook po default-u koristi lagani TF-IDF backend (stabilan za Colab). Zavisnosti: `numpy`, `pandas`, `matplotlib`, `scikit-learn`, `scipy`, `sympy` (instaliraju se u prvoj celiji). Opcioni `sentence-transformers` backend moze se ukljuciti jednim flag-om za semanticki bogatije embeddinge.
