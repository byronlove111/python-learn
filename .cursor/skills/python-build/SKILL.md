---
name: python-build
description: Génère un mini-projet Python avec un scaffold à compléter. main.py est déjà écrit, le learner implémente les fonctions dans project.py jusqu'à ce que le programme tourne. ~1h. Utilise quand l'utilisateur dit /python-build.
---

# Python Build

Session de construction. L'agent génère un mini-programme avec un `main.py` déjà écrit et un `project.py` avec des fonctions à implémenter. Le learner complète les fonctions jusqu'à ce que `python main.py` fasse quelque chose de cool.

**Le `main.py` ne se touche pas.** Il montre ce que le programme est censé faire — les fonctions appelées, les données attendues, le résultat affiché. Le learner lit `main.py` pour comprendre, puis implémente dans `project.py`.

**Durée : ~1h.** C'est la session principale de la semaine — elle doit être dense. Générer **4 à 6 fonctions** à implémenter, avec une difficulté croissante.

---

## Workflow

### Étape 0 — Proposer 3 projets

Avant de générer quoi que ce soit, propose exactement 3 projets distincts et attends le choix.

Règles :
- Chaque projet doit produire un programme **qui fait quelque chose de visible et amusant**
- Varier les contextes : jeux en mode texte, outils, scripts utiles ou marrants
- Ne pas reproduire un projet récent (vérifier `builds/` si nécessaire)
- Calibrer la difficulté : le projet du mercredi est plus facile que celui du vendredi

Format :
```
Voici 3 projets — choisis-en un :

**A — [nom du projet]**
[2-3 lignes : ce que fait le programme une fois terminé]

**B — [nom du projet]**
[2-3 lignes]

**C — [nom du projet]**
[2-3 lignes]
```

Attends le choix avant de générer quoi que ce soit.

### Étape 1 — Générer les fichiers

Créer `builds/YYYYMMDD-build-[slug]/` avec :

```
builds/YYYYMMDD-build-[slug]/
├── BRIEF.md
├── main.py       # programme principal — déjà écrit, ne pas modifier
└── project.py    # fonctions à implémenter
```

---

### Règles de conception

**`main.py` :**
- Déjà complet et lisible — ne doit jamais être modifié par le learner
- Montre clairement ce que le programme fait : appelle les fonctions de `project.py`, affiche les résultats
- Commence par : `from project import fonction1, fonction2, ...`
- Doit être court (20-30 lignes) — lisible en 2 minutes
- Si `main.py` est lancé avec toutes les fonctions non implémentées → crash propre sur `NotImplementedError`
- Textes affichés en français, noms de variables en anglais

**`project.py` :**

Structure type :
```python
# ============================================================
# [Titre du projet]
# ============================================================
# Implémente les fonctions ci-dessous pour que main.py fonctionne.
# Lance : python main.py
# Les fonctions doivent être complétées dans l'ordre — chacune
# s'appuie sur la précédente.
# ============================================================


# ------------------------------------------------------------
# TODO 1 — [nom de la notion/action]
# ------------------------------------------------------------
# Ce que ça fait : [description en une phrase, point de vue utilisateur]
#
# Exemple :
#   Entrée  : [valeur d'entrée concrète]
#   Sortie  : [valeur de sortie concrète]
#
# Indice : [suggère le bon outil Python sans donner l'implémentation]
# ------------------------------------------------------------
def nom_fonction(parametre: type) -> type:
    raise NotImplementedError


# [répéter pour chaque TODO]
```

**Règles pour les blocs TODO :**
- L'exemple Entrée/Sortie est toujours **concret** — pas abstrait (`[3, 1, 2]` pas `une liste`)
- L'indice suggère l'outil (`sorted()`, `for...in`, `if...else`, `len()`, `.split()`) sans donner le code
- Ne jamais donner d'étapes à suivre dans l'indice — c'est donner la réponse
- Chaque fonction commence obligatoirement par `raise NotImplementedError`
- Les fonctions vont du plus simple au plus complexe — les premières donnent confiance
- **Noms de variables et fonctions en anglais** — seuls les commentaires et exemples sont en français

**Règles pour la progression dans la session :**
- La première fonction doit être implémentable en 5-10 minutes
- La dernière fonction est la plus difficile et utilise les résultats des précédentes
- Si le thème est riche, ajouter une **fonction bonus** optionnelle en fin de fichier (clairement marquée `# BONUS`)

**`BRIEF.md` :**

```markdown
# Build — [nom du projet]

## Ce que tu vas construire

[2-3 phrases : ce que le programme fait une fois terminé, du point de vue de l'utilisateur]

## Comment démarrer

1. Lis `main.py` en entier — ne le modifie pas, il te montre ce que le programme doit faire
2. Ouvre `project.py` et implémente les fonctions dans l'ordre
3. Lance `python main.py` après chaque fonction implémentée pour voir si ça avance

## Critères de réussite

- [ ] `python main.py` tourne de bout en bout sans erreur
- [ ] Chaque fonction fait ce que l'exemple Entrée/Sortie décrit
- [ ] Aucun `raise NotImplementedError` ne reste

## Indice (seulement si bloqué depuis plus de 15 min)

<details>
<summary>Indice général</summary>
[Un pointeur vers le bon concept Python — pas le code]
</details>
```

---

### Étape 2 — Lancement

Après avoir généré les fichiers, afficher :

```
🔨  BUILD — ~1h.

▶️  Lis main.py d'abord — il te montre ce que tu dois construire.
▶️  Lance : python builds/YYYYMMDD-build-[slug]/main.py
✅  Objectif : le programme tourne de bout en bout.

Dis-moi quand tu as fini ou si tu es bloqué depuis plus de 15 min.
```

### Étape 3 — Débrief (quand l'utilisateur a fini)

Demander de coller la sortie de `python main.py`.

Feedback ciblé (8-10 lignes max) :
- Quelles fonctions ont été implémentées sans hésiter
- Laquelle a demandé le plus de temps et pourquoi
- Le ou les outils Python utilisés pour la première fois
- 1 chose concrète à retenir pour la prochaine session build

---

## Banque de projets (inspiration — générer des variantes originales)

**Jeu du pendu**
Fonctions : choisir un mot, afficher le mot masqué, vérifier une lettre, mettre à jour le mot affiché, détecter victoire/défaite.

**Simulateur de combat RPG en texte**
Fonctions : créer un personnage (avec stats), calculer des dégâts, appliquer une attaque, vérifier si un personnage est mort, afficher le résumé du combat.

**Gestionnaire de contacts CLI**
Fonctions : ajouter un contact, chercher par nom, afficher la liste triée, supprimer un contact, sauvegarder dans un fichier texte.

**Calculatrice de notes**
Fonctions : ajouter une note avec coefficient, calculer la moyenne pondérée, trouver la meilleure/pire note, afficher le bulletin formaté.

**Générateur de quiz**
Fonctions : charger les questions depuis une liste, poser une question, vérifier la réponse, calculer le score final, afficher le résultat avec message personnalisé.

**Mini-jeu de blackjack en texte**
Fonctions : créer un deck, distribuer une carte, calculer la valeur d'une main, vérifier le blackjack, déterminer le gagnant.

**Analyseur de texte**
Fonctions : compter les mots, trouver les mots les plus fréquents, calculer le score de lisibilité (longueur moyenne des mots), détecter les palindromes, générer un résumé stats.

**Simulateur de banque CLI**
Fonctions : créer un compte, déposer/retirer de l'argent, vérifier le solde, appliquer des intérêts, afficher l'historique des transactions.
