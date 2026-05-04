# Programme de formation Python

## Règles générales

- **Du mardi au samedi** — 5 sessions par semaine
- Chaque session génère ses propres fichiers — tu codes dans le dossier créé par l'agent
- Pas d'enregistrement, pas de cours — tu apprends en faisant tourner du code
- Après chaque session, lis le débrief : c'est là que la progression se construit

---

## Semaine type

### Mardi — Fill

> Session d'entrée en matière. Un programme presque complet avec des trous à remplir.

1. Lance `/python-fill` — l'agent propose 3 scénarios, tu choisis
2. Lis le programme en entier avant de toucher quoi que ce soit
3. Remplace les `# ???` par le bon code, un par un
4. Lance `python main.py` après chaque trou rempli

**Objectif de progression :**

- Semaines 1-2 : comprendre la structure du programme avant de remplir
- Semaines 3+ : deviner le bon code du premier coup sans tâtonner

---

### Mercredi — Build

> Tu construis un mini-programme à partir d'un scaffold. Le `main.py` est écrit, les fonctions sont à toi.

1. Lance `/python-build` — l'agent propose 3 projets, tu choisis
2. Lis `main.py` pour comprendre ce que le programme est censé faire
3. Implémente les fonctions dans `project.py` une par une
4. Lance `python main.py` jusqu'à ce que le programme tourne de bout en bout

**Objectif de progression :**

- Semaines 1-2 : faire tourner le programme même si c'est pas élégant
- Semaines 3+ : utiliser les bons outils Python du premier coup (compréhensions, `sorted(key=)`, classes…)

---

### Jeudi — Build

> Deuxième session de construction dans la semaine. L'agent génère un projet différent, un cran plus difficile.

Même workflow que mercredi. L'agent évite automatiquement de répéter un projet récent.

---

### Vendredi — Build

> Troisième session de construction. Souvent la plus ambitieuse de la semaine.

Même workflow que mercredi et jeudi.

---

### Samedi — Debug

> Tu récupères un programme cassé. Lance-le, lis les erreurs, trouve et corrige les bugs.

1. Lance `/python-debug` — l'agent propose 3 programmes cassés, tu choisis
2. Lance `python program.py` et lis le message d'erreur
3. Trouve et corrige les bugs dans `program.py`
4. Dis "j'ai fini" pour que l'agent révèle la liste complète et fasse le débrief

**Objectif de progression :**

- Semaines 1-2 : trouver les bugs évidents (SyntaxError, NameError, TypeError)
- Semaines 3+ : identifier la cause en lisant le traceback sans tâtonner

---

## Récap hebdomadaire

| Jour     | Skill             | Durée   |
| -------- | ----------------- | ------- |
| Mardi    | `/python-fill`    | ~45 min |
| Mercredi | `/python-build`   | ~1h     |
| Jeudi    | `/python-build`   | ~1h     |
| Vendredi | `/python-build`   | ~1h     |
| Samedi   | `/python-debug`   | ~40 min |

**Total : ~4h15/semaine**

Répartition : 3× Build · 1× Fill · 1× Debug

---

## Signaux de progression

Tu es à l'aise en Python quand :

- **Fill** : tu lis un programme et tu sais exactement quoi mettre dans chaque trou sans tâtonner
- **Build** : tu lis un stub de fonction et tu sais quel outil Python utiliser sans chercher dans la doc
- **Debug** : tu lis un traceback et tu identifies le bug en moins de 2 minutes
- **Global** : tu arrives sur un programme que tu n'as pas écrit, tu comprends sa structure et tu sais où ajouter du code
