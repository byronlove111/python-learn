---
name: python-fill
description: Génère un programme Python presque complet avec des trous à remplir. Session d'entrée en matière, idéale pour démarrer la semaine. Utilise quand l'utilisateur dit /python-fill.
---

# Python Fill

Un programme court et amusant, presque complet — mais avec des `# ???` à des endroits clés. Le learner lit, comprend, remplit les trous un par un jusqu'à ce que le programme tourne.

**Pas de fonctions entières à écrire.** Juste des expressions, des conditions, des valeurs — jamais plus d'une ligne par trou.

**Durée : ~45 minutes.**

---

## Workflow

### Étape 0 — Proposer 3 scénarios

Avant de générer quoi que ce soit, propose exactement 3 scénarios distincts et attends le choix.

Règles :
- Chaque scénario doit produire un programme **amusant et exécutable** — quelque chose qu'un ado de 16 ans a envie de faire tourner
- Varier les contextes : jeux, outils du quotidien, scripts marrants
- Ne pas reproduire un scénario récent (vérifier `fills/` si nécessaire)
- Chaque scénario doit avoir 6 à 9 trous — ni trop peu (trop facile) ni trop (décourageant)

Format :
```
Voici 3 scénarios — choisis-en un :

**A — [nom]**
[2 lignes : ce que fait le programme + ce que le learner va remplir]

**B — [nom]**
[2 lignes]

**C — [nom]**
[2 lignes]
```

Attends le choix avant de générer quoi que ce soit.

### Étape 1 — Générer les fichiers

Créer `fills/YYYYMMDD-fill-[slug]/` avec :

```
fills/YYYYMMDD-fill-[slug]/
├── BRIEF.md
└── main.py     # programme à trous — le seul fichier à modifier
```

---

### Règles de conception de `main.py`

**Le programme doit :**
- Être court : **40 à 60 lignes maximum**
- Tourner de bout en bout quand tous les trous sont remplis
- Être amusant — le learner doit avoir envie de le voir fonctionner
- Utiliser uniquement les bases Python : variables, conditions, boucles, fonctions, listes, strings, input/print
- Pas d'imports complexes — `random` et `math` sont OK, rien d'autre

**Les trous (`# ???`) :**
- Toujours **1 ligne ou moins** par trou — jamais une fonction entière
- Marqués avec `# ???` suivi d'un indice entre parenthèses : `# ??? (indice : utilisez len())`
- Les indices suggèrent l'outil, jamais la réponse
- Les trous sont **progressifs** : les premiers sont évidents, les derniers demandent à réfléchir
- Jamais deux trous consécutifs — toujours du code déjà écrit entre deux trous

**Types de trous à utiliser :**
- Expression simple : `score = # ??? (indice : score actuel + points gagnés)`
- Condition : `if # ???: (indice : vérifier si la réponse est correcte)`
- Ce sur quoi itérer : `for lettre in # ???: (indice : la liste des lettres du mot)`
- Valeur de retour : `return # ??? (indice : True si le score est supérieur à 10)`
- Argument d'une fonction : `print(# ???) (indice : le message de victoire)`
- Valeur dans une liste : `choix = ["pierre", # ???, "ciseaux"]`

**Structure de `main.py` :**

```python
# ============================================================
# [Titre du programme]
# ============================================================
# Lance : python main.py
# Remplis les # ??? pour que le programme fonctionne.
# Chaque indice entre parenthèses te guide — mais ne donne pas la réponse.
# ============================================================

import random  # si nécessaire


# [code déjà écrit]

def nom_fonction(parametre):
    # [quelques lignes déjà écrites]
    resultat = # ??? (indice : [outil ou concept suggéré])
    # [suite déjà écrite]
    return resultat


def autre_fonction():
    for element in # ???: (indice : [ce sur quoi itérer])
        if # ???: (indice : [la condition à vérifier])
            # [code déjà écrit]


# --- Programme principal ---
if __name__ == "__main__":
    # [code déjà écrit qui appelle les fonctions]
```

**Règles de style :**
- Noms de variables et fonctions en anglais
- Textes affichés (print, input) en français
- Commentaires `# ???` et indices en français
- Pas de commentaires qui expliquent le code évident — seulement les indices

---

### Étape 2 — Lancement

Après avoir généré les fichiers, afficher :

```
🧩  FILL — ~45 minutes.

▶️  Lis main.py en entier avant de toucher quoi que ce soit.
▶️  Lance : python fills/YYYYMMDD-fill-[slug]/main.py après chaque trou rempli.
✅  Objectif : le programme tourne de bout en bout.

Dis-moi quand tu as fini ou si tu es bloqué.
```

### Étape 3 — Débrief (quand l'utilisateur a fini)

Feedback court (5 lignes max) :
- Quels trous ont été remplis du premier coup
- Lequel a demandé le plus de temps et pourquoi
- 1 réflexe à retenir pour la prochaine session

---

## Banque de scénarios (inspiration — générer des variantes originales)

**Jeu de devinette de nombre**
Le programme choisit un nombre aléatoire, l'utilisateur devine. Les trous : génération du nombre, comparaison, comptage des essais, message de victoire.

**Quiz culture générale**
Liste de questions/réponses hardcodées. Les trous : vérification de la réponse, calcul du score, affichage du résultat final, message selon le score.

**Générateur de mot de passe**
L'utilisateur choisit une longueur, le programme génère un mot de passe. Les trous : construction de l'alphabet, sélection aléatoire, assemblage du mot de passe, affichage.

**Jeu du 421 simplifié**
Le programme simule des lancers de dés et calcule les points. Les trous : simulation d'un lancer, calcul du score, condition de victoire.

**Calculatrice interactive**
L'utilisateur entre deux nombres et une opération. Les trous : lecture des inputs, conversion en nombre, sélection de l'opération, affichage du résultat.

**Compteur de mots**
L'utilisateur entre une phrase, le programme l'analyse. Les trous : découpage en mots, comptage des occurrences, tri, affichage du mot le plus fréquent.
