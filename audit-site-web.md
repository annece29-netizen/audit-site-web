---
name: audit-site-web
description: Audite un site web (vitrine, blog, e-commerce, SaaS) sur plusieurs volets — sécurité/technique, UX, copywriting, SEO, design/responsive, RGPD/juridique, stratégie/branding/confiance — via des agents lancés en parallèle. Déclencher quand l'utilisateur veut "auditer mon site", "vérifier si mon site a des failles", "checker mon site avant de le publier", "revue complète de mon site", ou colle un prompt d'audit de site trouvé ailleurs. Produit un rapport daté classé par priorité et un fichier de suivi des actions. Propose un mode rapide (survol de tous les volets, points clés seulement) et un mode complet (agents dédiés par volet, analyse approfondie).
---

# /audit-site-web — Audit complet d'un site web par agents en parallèle

Audite un site (code source et/ou site en ligne) sur autant de volets que nécessaire, en confiant chaque volet à un agent dédié dont le prompt est adapté au contexte réel du site plutôt que rejoué mot pour mot d'une fois sur l'autre. Le but : un diagnostic aussi utile pour un site vitrine artisanal que pour une boutique e-commerce ou une appli SaaS, sans jamais recopier bêtement une checklist pensée pour un autre type de site.

## 1. Cadrer l'audit avant de lancer quoi que ce soit

Ne jamais foncer directement sur une liste de volets standard. Poser d'abord ces questions (via AskUserQuestion si plusieurs choix, en une seule salve si possible) :

- **Quel site ?** URL en ligne, et/ou chemin du code source local si disponible. Les deux sont utiles : le code source révèle ce qu'un audit "boîte noire" du site en ligne ne voit pas (secrets exposés, logique de validation, etc.), et le site en ligne révèle ce que le code seul ne montre pas (rendu réel, en-têtes HTTP serveur, performance perçue).
- **Quel type de site et quelle activité ?** Site vitrine B2B, e-commerce, blog/média, SaaS, association, portfolio... Cette réponse conditionne complètement quels volets sont pertinents (un e-commerce a besoin d'un audit de tunnel d'achat et de fiches produit ; un blog a besoin d'un audit de maillage éditorial ; un SaaS a besoin d'un audit d'onboarding). Ne jamais appliquer un prompt d'audit générique trouvé ailleurs sans l'adapter à cette réponse — un prompt écrit pour un site de financement participatif avec mineurs, par exemple, contient des points hors sujet pour un site vitrine B2B (et inversement, un site e-commerce a des angles morts qu'un prompt générique ne couvre pas).
- **Qui est la cible du site ?** Utile pour calibrer les volets UX/copywriting/confiance : les attentes ne sont pas les mêmes pour un site destiné à des particuliers pressés que pour un site destiné à des acheteurs B2B qui comparent plusieurs prestataires.
- **Quels volets couvrir ?** Présenter la liste des volets disponibles (voir section 3) et demander lesquels sont pertinents pour ce site — ne jamais tous les lancer par défaut sans demander, certains volets sont hors sujet selon le type de site (ex : pas de "tunnel d'achat" pour un site vitrine sans panier).
- **Mode rapide ou complet ?**
  - **Rapide** : un seul passage qui survole tous les volets choisis et ne remonte que les 2-3 points les plus importants de chacun. Utile en premier passage, pour savoir où creuser ensuite, ou quand le temps manque.
  - **Complet** : un agent dédié par volet, lancé en parallèle, qui analyse en profondeur et produit un rapport détaillé (Important / Mineur / points positifs) pour son volet. Plus long mais beaucoup plus actionnable.

## 2. Si l'utilisateur fournit un prompt d'audit tout fait

Il arrive qu'on colle un prompt d'audit trouvé ailleurs (un article, un autre projet, une checklist générique). Ne jamais l'appliquer tel quel : le lire, identifier les points qui sont réellement pertinents pour CE site (compte tenu du type de site et de l'activité clarifiés à l'étape 1), écarter explicitement ceux qui ne le sont pas en le disant à l'utilisateur (par exemple : un point sur la protection des mineurs n'a pas de sens sur un site B2B sans public mineur), et ne garder que ce qui s'applique vraiment. Le dire clairement dans le rapport final ("ce point du prompt d'origine n'a pas été traité car non applicable à ce site, voir raison").

## 3. Volets disponibles

Cette liste n'est pas figée : l'ajuster selon le type de site identifié à l'étape 1 (retirer ce qui ne s'applique pas, ajouter un volet spécifique si le site en a besoin — ex. tunnel d'achat pour un e-commerce, onboarding pour un SaaS).

| Volet | Ce qu'il couvre | Bon agent à utiliser si disponible |
|---|---|---|
| Sécurité & technique | Secrets exposés dans le code, failles XSS, tabnabbing, contenu HTTP mixte, intégrité des scripts tiers (SRI), en-têtes de sécurité HTTP (CSP, X-Content-Type-Options, HSTS...), validation des données côté serveur | agent généraliste sur le code source + agent technique SEO sur le site en ligne |
| UX (parcours, formulaires, CTA) | Clarté du parcours visiteur, friction dans les formulaires, cohérence et priorisation des appels à l'action, navigation, accessibilité de base | agent orienté expérience de recherche/UX si disponible |
| Copywriting (ton, accroche, FAQ) | Clarté de l'accroche, cohérence du ton avec la voix de la marque, qualité de la FAQ, preuves concrètes vs discours abstrait | agent orienté contenu |
| SEO contenu | Qualité (pas seulement présence) des title/meta/H1-H2, maillage interne, structure de titres, opportunités de contenu manquées | agent orienté contenu/SEO |
| Design & responsive | Cohérence visuelle, rendu mobile, éléments cassés ou qui débordent, cohérence des composants d'une page à l'autre | agent avec accès navigateur (captures d'écran desktop + mobile) |
| RGPD & juridique | Mentions légales, politique de confidentialité (sous-traitants réels nommés), bandeau de consentement cookies AVANT chargement des outils de tracking, CGU/CGV si vente en ligne | agent généraliste, lit directement le code |
| Stratégie produit / branding / confiance | Clarté du positionnement, cohérence de l'identité visuelle, crédibilité des preuves sociales (témoignages, avis), signaux de réassurance, cohérence avec les canaux d'acquisition externes | agent généraliste |
| (Spécifique au type de site) | Ex. tunnel d'achat et fiches produit pour un e-commerce, onboarding et pricing pour un SaaS, fraîcheur et maillage éditorial pour un blog/média | à définir selon le contexte, ne pas hésiter à improviser un prompt sur mesure |

## 4. Rédiger les prompts d'agents à la volée, pas depuis un modèle figé

C'est le cœur de la méthode : ne jamais réutiliser un prompt d'agent mot pour mot d'un audit à l'autre. Chaque prompt doit être réécrit à partir des réponses de l'étape 1, avec :

- Le contexte réel du site (type d'activité, cible, ce qui le différencie) pour que l'agent juge avec les bons repères (ex : un site B2B avec peu de clients établis ne doit jamais laisser un agent recommander de "mettre en avant le volume de clients")
- Les chemins exacts (URL en ligne, chemin du code source local)
- Un périmètre clair et volontairement resserré à un seul volet — ne jamais demander à un agent de couvrir plusieurs volets à la fois, la qualité en pâtit
- Une consigne de vulgarisation si l'utilisateur n'est pas technique : classer chaque problème en Important/Mineur, expliquer l'impact concret plutôt que le jargon
- Pour les agents avec accès navigateur (design, RGPD en conditions réelles) : une consigne explicite de rester efficace et de rendre un rapport dans un temps raisonnable plutôt que d'explorer indéfiniment — les agents avec captures d'écran ont tendance à s'enliser sur un détail (ex. tester un formulaire multi-étapes en entier) si on ne les cadre pas

## 5. Lancer les agents en parallèle (mode complet) ou un seul passage (mode rapide)

En mode complet, lancer tous les agents choisis dans le même tour de réponse (plusieurs appels d'outil dans le même message), pas les uns après les autres — c'est ce qui fait gagner le temps par rapport à un audit manuel séquentiel.

Créer le fichier de rapport (voir structure section 6) avant même que les agents aient terminé, avec un tableau de statut par volet ("En cours"), pour pouvoir intégrer chaque résultat au fur et à mesure qu'il arrive plutôt que d'attendre que tout soit fini.

**Si un agent semble bloqué ou anormalement lent** (aucune activité depuis plusieurs minutes alors que les autres volets similaires ont pris 5-10 minutes) : vérifier son état réel plutôt que de supposer qu'il travaille encore. Un agent avec accès navigateur peut planter silencieusement sans le signaler. Si un doute existe, le relancer plutôt que d'attendre indéfiniment — un audit vaut mieux tard mais fini qu'une attente sans fin sur un agent mort.

## 6. Structure des 2 fichiers produits

### Fichier 1 : rapport d'audit daté

Nommer `AAAA-MM-JJ_audit-[nom-court-du-site].md` (ou selon la convention de nommage du projet si elle existe). Structure :

```markdown
# Audit [nom du site] — [date]

Contexte en 1-2 phrases : quel site, quel périmètre (code source / site en ligne / les deux), méthode (agents en parallèle, mode rapide/complet).

## Statut (uniquement en mode complet, pendant que les agents tournent)
Tableau volet / agent utilisé / statut

## Synthèse — les N actions prioritaires
Liste numérotée des points les plus importants tous volets confondus, avec ✅ et note "publié" dès qu'une correction est appliquée et déployée.

## 1. [Nom du volet]
Résumé en 2-4 lignes.
### Important
Liste numérotée, un problème par point : quoi, où (fichier/page), pourquoi c'est important, correction concrète suggérée.
### Mineur
Même format, priorité plus faible.
### Points positifs à conserver
Ce qui est déjà bien fait — ne pas seulement chercher des problèmes.

[Répéter par volet]
```

### Fichier 2 : suivi des actions restantes

Nommer `a-faire-sur-site.md` (ou équivalent existant dans le projet). Liste à cocher, classée par priorité, qui pointe vers le rapport détaillé pour chaque point. Cocher au fur et à mesure que les corrections sont appliquées et publiées, avec la date et si possible la référence du commit ou de la publication.

## 7. Appliquer les corrections (si demandé)

Ne jamais appliquer de correction sans validation explicite de l'utilisateur sur le principe (même si un point individuel semble évident) — un audit reste un diagnostic, pas un mandat pour modifier le site. Une fois l'accord donné :

- Pour chaque correction, vérifier son impact avant de la publier si elle touche un point d'entrée sensible (formulaire, paiement, tracking) : tester en local si possible avant de mettre en ligne.
- Si le site a une architecture "source locale + clone de déploiement séparé" (fréquent avec des sites statiques publiés via un service tiers), toujours vérifier que les deux restent synchronisés après une correction — une désynchronisation silencieuse peut faire disparaître une correction précédente ou en écraser une autre.
- Cocher la case correspondante dans le fichier de suivi (section 6, fichier 2) dès que la correction est publiée, pas seulement codée.

## Ton

Vulgariser systématiquement les notions techniques si l'utilisateur n'est pas développeur — expliquer l'impact concret ("un visiteur qui ne comprend pas l'offre en 5 secondes part sans convertir") plutôt que le jargon seul. Être honnête sur ce qui est déjà bien fait, pas seulement sur les problèmes. Si un point d'un prompt d'audit fourni par l'utilisateur ne s'applique pas au site, le dire explicitement plutôt que de l'ignorer silencieusement.
