---
name: python-debug
description: Génère un programme Python cassé avec des bugs intentionnels. Le learner lance le programme, lit les messages d'erreur et corrige les bugs. ~40 min. Utilise quand l'utilisateur dit /python-debug.
---

# Python Debug

Un programme qui était censé fonctionner. Il ne fonctionne plus. Le learner le lance, lit les erreurs Python, trouve les bugs, corrige — jusqu'à ce que tout tourne.

**Règle absolue : ne modifier que `program.py`.** Le programme est correct dans son intention — seuls les bugs introduits intentionnellement l'empêchent de tourner.

**Durée : ~40 min.**

---

## Workflow

### Étape 0 — Proposer 3 scénarios

Avant de générer quoi que ce soit, propose exactement 3 scénarios distincts et attends le choix.

Règles :
- Chaque scénario cible un **type de bug différent**
- Varier la difficulté : 1 facile, 1 moyen, 1 difficile
- Les programmes doivent être **amusants** — jeux, outils, scripts
- Ne pas reproduire un scénario récent (vérifier `debugs/` si nécessaire)
- Nommer clairement le type de bugs dans la proposition

Format :
```
Voici 3 programmes cassés — choisis-en un :

**A — [nom] (Facile)**
[2 lignes : ce que fait le programme + type de bugs]

**B — [nom] (Moyen)**
[2 lignes]

**C — [nom] (Difficile)**
[2 lignes]
```

Attends le choix avant de générer quoi que ce soit.

### Étape 1 — Générer les fichiers

Créer `debugs/YYYYMMDD-debug-[slug]/` avec :

```
debugs/YYYYMMDD-debug-[slug]/
├── BRIEF.md
├── BUGS.md       # liste complète des bugs — spoiler sous <details>
└── program.py    # programme à débugger
```

---

### Règles de conception de `program.py`

**Le programme :**
- Court : **40 à 70 lignes maximum**
- Clair dans son intention — le learner comprend ce qu'il est censé faire
- Contient **4 à 6 bugs** au total
- **2 à 3 parties du programme fonctionnent déjà** — pour donner un point de repère
- Uniquement les bases Python : variables, conditions, boucles, fonctions, listes, strings
- Pas d'imports complexes — `random` et `math` sont OK

**Les bugs :**
- **1 bug par endroit au maximum** — jamais deux bugs dans la même fonction
- Les bugs **ressemblent à de vraies erreurs de débutant** — pas des typos évidentes
- Le traceback Python doit pointer vers la cause sans la révéler entièrement
- Les bugs sont variés — pas 4 fois le même type

**Types de bugs à utiliser :**

*Bugs de syntaxe (débutant niveau 1) :*
- `if condition` sans `:` en fin de ligne
- `def fonction()` sans `:` en fin de ligne
- String ouverte mais non fermée
- Indentation incorrecte (un bloc mal décalé)

*Bugs de type (débutant niveau 2) :*
- Concaténation string + int sans `str()` : `"Score : " + score`
- Appel de `.upper()` sur un int
- `len()` sur un int au lieu d'une liste
- Division entière là où on voulait une division float

*Bugs de logique (débutant niveau 3) :*
- Condition inversée : `if score < 10` au lieu de `> 10`
- Boucle `range(len(liste))` avec un off-by-one : `range(len(liste) + 1)`
- Variable non initialisée avant d'être incrémentée
- Retourner `False` là où le programme devrait retourner `True`

*Bugs de référence (débutant niveau 2-3) :*
- Appel d'une fonction avec le mauvais nom (typo légère : `calcul_score` vs `calculate_score`)
- Variable locale utilisée avant assignation
- Paramètre de fonction utilisé avec un nom différent dans le corps

**Règles de distribution :**
- Session facile : 2 bugs de syntaxe, 2 bugs de type
- Session moyenne : 1 bug de syntaxe, 2 bugs de type, 1 bug de logique
- Session difficile : 1 bug de type, 2 bugs de logique, 2 bugs de référence

**En-tête de `program.py` :**
```python
# ============================================================
# [Titre du programme]
# ============================================================
# Ce programme était censé [description courte].
# Lance : python program.py
# Quelque chose ne va pas. À toi de trouver quoi.
# ============================================================
```

---

### Format `BUGS.md`

```markdown
# Liste des bugs

<details>
<summary>⚠️ Spoiler — à lire seulement après avoir fini</summary>

## Bug 1 — ligne [N]
**Ce que Python affiche :** [message d'erreur exact ou comportement incorrect]
**Cause :** [explication simple]
**Correction :** [la ligne correcte]

## Bug 2 — ligne [N]
**Ce que Python affiche :** ...
**Cause :** ...
**Correction :** ...

[répéter pour chaque bug]
</details>
```

### Format `BRIEF.md`

```markdown
# Debug — [nom du programme]

## Contexte

[2 phrases : ce que le programme est censé faire]
Quelque chose s'est cassé. Le code n'a pas changé dans son intention — seulement des erreurs se sont glissées dedans.

## Ta mission

1. Lance `python program.py` et lis le message d'erreur
2. Trouve le bug, corrige-le
3. Relance jusqu'à ce que le programme tourne
4. Dis "j'ai fini" quand tout est vert

## Règles

- Tu ne modifies que `program.py`
- Chaque endroit cassé a exactement 1 bug
- Les parties qui fonctionnent déjà sont correctes — ne les touche pas

## Indices (seulement si bloqué depuis plus de 10 min)

<details>
<summary>Nombre de bugs</summary>
Il y a [N] bugs au total.
</details>

<details>
<summary>Types de bugs</summary>
[Ex : "deux erreurs de type, un bug de logique, un bug de syntaxe" — sans les localiser]
</details>
```

---

### Étape 2 — Lancement

Après avoir généré les fichiers, afficher :

```
🐛  DEBUG — ~40 minutes.

📋  Brief dans BRIEF.md
▶️  Lance : python debugs/YYYYMMDD-debug-[slug]/program.py
🎯  Objectif : le programme tourne sans erreur

⚠️  Ne regarde pas BUGS.md avant d'avoir fini.

Dis-moi quand tu as terminé ou si tu es bloqué depuis plus de 10 min.
```

### Étape 3 — Débrief (quand l'utilisateur a fini)

1. Demander de coller la sortie finale de `python program.py`
2. Dire à l'utilisateur d'ouvrir `BUGS.md`
3. Évaluer :
   - Bugs trouvés vs bugs manqués
   - Est-ce que le traceback a été lu ou ignoré ?
   - Combien de temps par bug

**Format du débrief (dans le chat) :**
```
## Débrief — [nom du programme]

**Résultat :** [X] bugs trouvés sur [Y]

**Ce que tu maîtrises :**
- [type de bug identifié rapidement]

**Ce qui t'a coûté du temps :**
- [bug difficile + pourquoi]

**Règle à retenir :**
[Une heuristique concrète — ex: "quand Python dit TypeError: can only concatenate str, cherche une concaténation str + int"]
```

---

## Banque de scénarios (inspiration — générer des variantes originales)

**Jeu de devinette cassé**
Programme qui génère un nombre et demande de deviner. Bugs : condition de victoire inversée, concaténation str+int, boucle infinie par off-by-one.

**Calculatrice interactive cassée**
Programme qui lit deux nombres et une opération. Bugs : inputs non convertis en float, opérateur mal orthographié dans une condition, division par zéro non gérée.

**Quiz de culture générale cassé**
Liste de questions/réponses. Bugs : index hors liste, comparaison casse incorrecte (pas de `.lower()`), score jamais incrémenté (mauvais nom de variable).

**Générateur de mot de passe cassé**
Construit un mot de passe aléatoire. Bugs : `random.choice` appelé sur un int, concaténation str+int, `range` avec mauvais paramètre.

**Classement de scores cassé**
Trie et affiche une liste de scores. Bugs : `sorted()` avec `reverse` mal utilisé, accès à une clé inexistante dans un dict, fonction appelée avec le mauvais nom.
