# audit-site-web

Un skill Claude Code qui audite un site web (vitrine, blog, e-commerce, SaaS) sur plusieurs volets : sécurité/technique, UX, copywriting, SEO, design/responsive, RGPD/juridique, stratégie/branding/confiance.

Chaque volet est confié à un agent dédié en parallèle, avec un prompt adapté au contexte réel du site plutôt qu'une checklist générique rejouée à l'identique. Produit un rapport daté classé par priorité et un fichier de suivi des actions restantes.

Deux modes disponibles :
- **Rapide** : survol de tous les volets, points clés seulement
- **Complet** : un agent dédié par volet, analyse approfondie

## Installer avec Claude Code

Colle ce message dans une conversation Claude Code :

> Récupère le contenu de https://raw.githubusercontent.com/annece29-netizen/audit-site-web/master/audit-site-web.md et crée le fichier `audit-site-web.md` avec ce contenu dans mon dossier `~/.claude/commands/` (le créer s'il n'existe pas).

Une fois fait, tape `/audit-site-web` dans une conversation pour l'utiliser.

## Utiliser sans Claude Code (Claude.ai, app, Cowork)

Pas d'installation possible de la même façon. Colle plutôt ce message dans la conversation :

> Suis les instructions de ce fichier pour auditer mon site : [colle le contenu de audit-site-web.md]

## Licence

Fourni tel quel, sans garantie. Libre à réutiliser et adapter.
