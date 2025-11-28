# Mini Rapport Qualité - [Nom du Projet]

**Auteur** : Auroy Yoann
**Date** : 28 novembre 2025
**Projet analysé** : https://github.com/expressjs/express

---

## 1. Présentation du Projet

**Description** : Express est une petite bibliothèque Node structurée autour d’un noyau minimal dans lib/, complétée par des répertoires de support (test/, examples/, benchmarks/) et une configuration moderne (CI GitHub Actions, etc.).
**Langage** : JavaScript
**Nombre de lignes de code** : 15.000
**Dernière mise à jour** : 26 novembre 2025

---

## 2. Analyse Qualitative

### 2.1 Maintenabilité (Maintainability) - Note : 4/5

**Points forts** :

- ✅ Tests d'intégration complets (99.61% coverage)
- ✅ Documentation complète

**Points faibles** :

- ❌ Couplage fort (code runtime dans un seul module: `/lib`)

**Justification** : La proportion de test est exellente et atteint quasiment 100% de la code base. La documentation est très complète, chaque fonction / methode dispose d'une documentation JSDOC.

---

### 2.2 Fiabilité (Reliability) - Note : 4/5

**Points forts** :

- ✅ Mono-package simple
- ✅ CI/CD multi version et suivi des dépendences

**Points faibles** :

- ❌ Pas de logs

**Justification** : La simplicité de l'architecture et la mise en place d'une CI/CD sur plusieurs versions de node apportent une fiabilité importante. En revanche, il n'y a pas de logs et les actions passées ne sont pas consignées.

---

### 2.3 Sécurité (Security) - Note : 3/5

**Points forts** :

- ✅ Séparation des dépendences (runtime / dev dependencencies)
- ✅ Spécialisation des dépendences

**Points faibles** :

- ❌ Pas de rate limiting, de validation des données ou CORS.

**Justification** : Faible équilibre dans la sécurité, plusieurs aspects sont délégués à l'utilisateur, comme le rate limiting, la validation des données ou la protection contre les CORS. La sécurisation des dépendences est plutot forte, aucune vulnérabilité détectée lors de l'audit avec `npm`

---

### 2.4 Performance (Performance Efficiency) - Note : 4/5

**Points forts** :

- ✅ Noyau léger permet de garder une empreinte mémoire raisonnable

**Points faibles** :

- ❌ Possible empilement des middlewares, qui peut ajouter de la latence

**Justification** : La performance est excellente de part la légèreté du framework, mais le fait que les middlewares soient empilables peu nuire à cette performance.

---

## 3. Synthèse

**Note globale** : 15/20 (moyenne des 4 critères)

**Tableau récapitulatif** :

| Critère        | Note      | Commentaire                    |
| -------------- | --------- | ------------------------------ |
| Maintenabilité | 4/5       | Test et documentation complets |
| Fiabilité      | 4/5       | CI/CD multi version            |
| Sécurité       | 3/5       | Peu de protection              |
| Performance    | 4/5       | Framework léger                |
| **TOTAL**      | **15/20** |                                |

---

## 4. Recommandations

**Top 3 améliorations prioritaires** :

1. **[Maintenabilité]** : Modularisation du noyau - Reduction du couplage via des interfaces

2. **[Sécurité]** : Sécurité par défaut - Implémenter un socle de sécurité incluant headers de sécurité, CORS raisonnable, parsing et validation plus stricts, limites de taille, etc.

---

## 5. Conclusion

Le projet montre une bonne maintenabilité et fiabilité grâce à sa structure claire et sa quantité importante de tests. Cependant, la sécurité pourrait bénéficier d'améliorations significatives, qui nécessiterait un changement de version majeure pour être introduits.
