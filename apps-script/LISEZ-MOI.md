# P12 — Exercices n°1 et n°2 : report automatique des notes

Quand le professeur clique sur **Enregistrer la note** dans le modal d'une copie « P12 — Exercice n°1 » ou
« P12 — Exercice n°2 » du site Technologie (ou valide la copie avec ✅), les points de chaque partie, la note
sur 20 et l'appréciation sont reportés dans le classeur de l'exercice, sur la ligne de l'élève (identité de son
compte du site), dans l'onglet de sa classe.

| Script | Classeur | Colonnes de points |
|---|---|---|
| [`Ex1-Report.gs`](Ex1-Report.gs) | P12 — Exercice n°1 — Distributeur de croquettes | A 5 · B 3 · C 4 · D 4 · E 4 (sur 20) |
| [`Ex2-Report.gs`](Ex2-Report.gs) | P12 — Exercice n°2 — Bac à sable connecté | Q1 3 · Q2 3 · Q3 3 · Q4 9 · bonus Q5 6 (somme plafonnée à 20) |

## Installation (une seule fois par classeur)

1. Ouvrir le classeur → **Extensions → Apps Script** → remplacer `Code.gs` par le script de l'exercice, enregistrer.
2. Choisir la fonction **`installer`** → **Exécuter** (autoriser l'accès). Onglets 4A à 4G, Journal, Mode d'emploi.
3. Coller la liste des élèves (NOM Prénom, export Ecole Directe) en colonne A de chaque onglet, à partir de la ligne 4.
4. **Déployer → Nouveau déploiement → Application web** · Exécuter en tant que **Moi** · Accès **Tout le monde**.
5. Transmettre l'URL `/exec` à Claude, qui la branche dans `index.html` du site (`P11_REPORT["p12-ex1"].url`,
   `P11_REPORT["p12-ex2"].url`). Tant que l'URL est vide, le site n'envoie rien.

## Règles

- La note proposée par le site est **ajustable** dans le modal (boutons − / +, par demi-point) ; c'est la note
  enregistrée qui part au classeur.
- Revalider une copie met la ligne à jour (c'est la dernière validation qui compte).
- **Protection :** une ligne dont les points ont été saisis à la main n'est jamais écrasée : le site affiche
  « report refusé » et le Journal garde la trace.
- Élève introuvable ou homonyme : ajouté en bas de l'onglet, fond orangé, remarque « vérifier le nom ».
- Bouton **Reporter toutes les copies validées** (modal d'une copie) : envoie celles qui ne l'ont pas encore été.
- Rien n'est envoyé depuis une page du site ouverte en local.
- Après toute modification du script : **Déployer → Gérer les déploiements → Modifier → Nouvelle version**.
