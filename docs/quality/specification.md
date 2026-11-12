# Cahier des charges — TrocarLab V1

Bac à sable open source pour apprendre la robotique chirurgicale

Nov 3, 2026 · @itsdocafro

## Suivi des versions

Statut : figé (v1.15), le 4 novembre 2026, à ma décision de démarrer le projet. Toute modification ultérieure sera notée dans le suivi des versions ; les nouvelles décisions vont dans des ADR (docs/adr/).

| Version | Date | Auteur | Nature des modifications |
| --- | --- | --- | --- |
| 1.10 à 1.15 | Novembre 2026 | Maxime JOBERT | v1.15 (figée le 4 novembre 2026, au démarrage du projet) : statut « en cours de rédaction » jusqu'à ma décision de démarrer, puis gel ; liens ES-003 → RP-019 et ES-018 → RP-014 ajoutés ; module d'icônes (sprite SVG, type IconName, composant Icon) et design system en composants, avec les mêmes noms dans Figma et dans le code ; SVGO et jeu d'icônes ajoutés aux licences. v1.14 : dossier docs/design/ pour les exports Figma ; wireframe rapide possible dès le J1, maquettes détaillées au J6. v1.13 : contrôle tige/sphère et machine d'états écrits par moi (section 9.5) ; RJ-008 passé en « Élevée » ; abonnement Claude Pro mentionné comme seule exception au budget de 0 €. v1.12 : réarmement corrigé (retrait en ligne droite avant tout mouvement de MoveIt), position d'entrée (EF-104), EF-107 et RP-021 ; preuves nocturnes lues par la matrice ; cas de test rédigés à chaque jalon contenant une exigence de sécurité ; ES-008 au J5 ; point ouvert sur la langue fermé. v1.11 : section 9.5 sur l'usage de l'IA agentique (l'IA écrit l'essentiel du code ; cinématique du Panda et cas de test de sécurité écrits par moi ; vérification indépendante, traçabilité, sécurité de l'agent, CLAUDE.md et AI\_POLICY.md) ; RJ-008 (apprentissage superficiel). v1.10 : brief des maquettes de la console ajouté en section 5.6 (zones de l'écran, états à dessiner, règles d'ergonomie inspirées de l'IEC 62366-1) ; EF-506 (progression de la séquence de démarrage) ; maquettage dans Figma. v1.10.1 : paroi abdominale stylisée dans la vue 3D (Should) ; anatomie réaliste reportée en V2. |
| 1.9.1 | Novembre 2026 | Maxime JOBERT | Licences de toutes les dépendances vérifiées dans leurs dépôts officiels le 4 novembre 2026 (noVNC compris) ; rosbridge\_suite, RViz, GoogleTest, pytest, Vitest, Vite, MkDocs et l'image Docker de base ajoutés au tableau ; option EIGEN\_MPL2\_ONLY ; point ouvert sur noVNC fermé |
| 1.9 | Novembre 2026 | Maxime JOBERT | Jalon bloquant pour chaque exigence Must (tableau de la section 11, lu par le script de traçabilité ; fichier current-milestone) : la CI reste verte dès le J1 ; colonne priorité ajoutée aux ENF ; ES-019 et son test ramenés à ce qu'une plage peut détecter ; code, identifiants et noms de fichiers en anglais (ENF-012 passée en Must) |
| 1.8 | Novembre 2026 | Maxime JOBERT | Analyse de risques complétée : RP-017 à RP-020 (défaillance du code de sécurité, erreur d'unité, confusion des commandes, anomalie d'un composant tiers), ES-019 à ES-021, RJ-007 (sur-ingénierie), évaluation du risque résiduel global, méthode de revue des risques, tableau des risques produit unique, probabilités après mesure présentées comme des cibles. Relecture complète de cohérence : preuves de vérification au lieu de « tests » partout, ES-008 reliée à RP-003, exception ES-010 dans ENF-010, outils de test dans les choix techniques, anomalies connues dans la liste SOUP, rosbags rejoués chaque nuit, légende de la feuille de route, IEC 62366-1 ajoutée |
| 1.7 | Novembre 2026 | Maxime JOBERT | Conventions Git et CI complétées : rulesets sans exception pour l'administrateur, job obligatoire unique ci-ok, CI à deux niveaux avec couverture et sanitizers, cache, release-please, publication sur GitHub Container Registry avec attestation de provenance, limites de Dependabot, taille des rosbags |
| 1.6 | Novembre 2026 | Maxime JOBERT | Matrice de traçabilité fondée sur des preuves selon la méthode (tests qui passent, fiches d'inspection, rapports de mesure), lecture des rapports JUnit XML, contrôle des identifiants orphelins, chaîne risque → exigence de sécurité → preuve, photo par version, ENF-014 corrigée |
| 1.5 | Novembre 2026 | Maxime JOBERT | Jalons redécoupés : l'ancien J3 coupé en J3 (C++ et calculs) et J4 (nœud RCM et sécurité de démarrage), sept jalons au lieu de six ; J1 rallongé ; marge d'environ 15 % ; estimation portée à 30 à 40 semaines (publication entre juin et août 2027) ; règle en cas de dépassement ; feuille de route redessinée et références aux jalons mises à jour |
| 1.4.2 | Novembre 2026 | Maxime JOBERT | Réarmement (ES-013) qui relance la séquence de démarrage, écart de démarrage fixé à 1 mm (ES-012), exception ES-010 dans rcm\_core, ES-009 rattachée au J2, planning annoncé à recaler après le J1 |
| 1.4.1 | Novembre 2026 | Maxime JOBERT | RP-014 ajouté aux risques résiduels à 4 ; rattachement de toutes les exigences de sécurité aux jalons |
| 1.4 | Novembre 2026 | Maxime JOBERT | Exigences de sécurité complétées avant et après le mouvement : ES-012 à ES-018 (démarrage à l'arrêt, sortie de faute par réarmement, état du bras périmé, paramètres de sécurité figés, enfoncement maximal, affichage de l'état de sécurité, journal des événements) ; risques RP-011 à RP-016 ; tests d'injection de fautes associés ; surveillant indépendant prévu en V2 |
| 1.3 | Novembre 2026 | Maxime JOBERT | Propriété de test corrigée (écart sous 1 mm, refus ou faute) ; seuils définis strictement (ES-002, EF-402) et testés à ± ε ; horloge simulée pour ES-005 ; titres de PR vérifiés au lieu de commitlint ; tout le code de sécurité dans trocarlab\_safety ; sanitizers limités aux bibliothèques sans ROS ; ENF-002 et ENF-004 en analyse ; outils de test ajoutés aux licences et à la liste SOUP ; renvois corrigés |
| 1.2 | Novembre 2026 | Maxime JOBERT | Stratégie de tests renforcée : tests aux limites, tests de propriétés, injection de fautes, sanitizers, 100 % des branches pour le code de sécurité, différences finies, Playwright, scénarios rosbag, mesures de temps hors CI ; ENF-016 ; mise en place par jalon ; mutation et validation prévues en V2 |
| 1.1 | Novembre 2026 | Maxime JOBERT | Organisation du dépôt au niveau professionnel : paquet d'interfaces, dépendances figées, ADR, documentation qualité séparée avec liste SOUP, outils dans tools/, matrice de traçabilité générée par la CI, pratiques Git renforcées (commits signés, commitlint, historique linéaire, CodeQL, SBOM), ENF-013 à ENF-015, mise en place progressive par jalon |
| 1.0.1 | Novembre 2026 | Maxime JOBERT | Licence de franka\_description vérifiée dans le dépôt (Apache 2.0, maillages compris) ; Panda nommé fer ; maillages UR non open source ; point de vigilance sur la compilation sous Jazzy ; RJ-004 clos ; justifications du C++ et de KDL corrigées |
| 1.0 | Novembre 2026 | Maxime JOBERT | Validation : ES-008 passée en Must (ES-003, qui maîtrise RP-003, en dépend), retouches de forme, nom TrocarLab confirmé disponible |
| 0.3 | Novembre 2026 | Maxime JOBERT | Cinématique testée contre des données de référence figées, clavier du terminal en pas à pas, sortie de zone toujours autorisée, marge de sécurité supérieure au pas maximal, noVNC et bascule sur le schéma, Jazzy définitivement retenue, licences et convention DH précisées |
| 0.2 | Novembre 2026 | Maxime JOBERT | Relecture : zone vérifiée sur toute la tige, refus plutôt que projection, RViz via noVNC, RCM en bibliothèque puis nœud, bascule MoveIt → RCM, choix de la cinématique, risques singularité et butées, CI ARM64 native, v0.1.0 au J2 |
| 0.1 | Novembre 2026 | Maxime JOBERT | Première rédaction : objectifs, périmètre V1, exigences numérotées, première analyse de risques |

Ces numéros sont ceux du **document**. Les versions du **logiciel** TrocarLab (v0.1.0 au J2, v1.0.0 au J7) suivent leur propre numérotation, décrite en section 9.3.

Le nom « TrocarLab » est définitif : sa disponibilité a été vérifiée sur GitHub, PyPI, npm, l'index ROS, l'INPI et l'EUIPO.

## 1. Résumé

### 1.1 Le projet en une phrase

TrocarLab est un bac à sable open source qui simule un robot de chirurgie laparoscopique (contrôle RCM, zones de sécurité, téléopération, console web). Il se lance en une commande Docker sur n'importe quel ordinateur, sans carte graphique, et s'accompagne de tutoriels pas à pas.

### 1.2 Avertissement obligatoire

> **Projet éducatif, non destiné à un usage clinique.** TrocarLab n'est pas un dispositif médical. Il ne doit jamais piloter un robot réel au contact d'un patient.

Cet avertissement figure en tête du README, de la documentation et de la console web (voir ES-001).

### 1.3 Objectifs de la V1

1. **Pédagogique** : qu'un débutant lance la simulation et pilote l'instrument autour du trocart en moins de 30 minutes, en suivant le README.
2. **Technique** : démontrer un contrôle RCM en C++ dont l'écart au point d'incision reste inférieur à 1 mm en simulation, et une zone interdite jamais franchie.
3. **Professionnel** : disposer d'un projet public, documenté et testé, que je peux présenter et défendre en entretien pour un poste en robotique chirurgicale.
4. **Apprentissage** : acquérir les bases de Python, C++17, ROS 2 et MoveIt, chaque étape devenant un tutoriel.

### 1.4 Indicateurs de succès de la V1

| Indicateur | Cible V1 |
| --- | --- |
| Temps entre `git clone` et robot qui bouge | ≤ 30 min (téléchargement des images compris) |
| Plateformes testées | macOS ARM64 (M3 Pro) et Linux x86\_64 (via la CI) |
| Écart maximal au RCM pendant la téléopération | < 1 mm |
| Franchissements de la zone interdite lors des tests | 0 |
| Tutoriels publiés | ≥ 7 (un par jalon) |
| Exigences « Must » dotées d'une preuve de vérification (test, inspection ou mesure) | 100 % |

### 1.5 Contraintes assumées

- **Budget : 0 €.** Outils gratuits ou open source uniquement ; aucun serveur payant. Seule exception : l'abonnement Claude Pro déjà souscrit (assistant et Claude Code). Le projet n'en dépend pas : sans IA, tout reste réalisable, plus lentement.
- **Temps : 1 à 2 h par jour**, la recherche d'emploi restant prioritaire (environ 70 % du temps).
- **Développeur seul, débutant** en C++, Python, ROS 2 et robotique.
- **Pas de simulateur physique** : le *mock hardware* de ros2\_control recopie les commandes comme si le robot les exécutait parfaitement : ni physique, ni contact, ni gravité.
- **Machine de développement** : MacBook M3 Pro (ARM64), 18 Go de RAM, macOS 15 ; ROS 2 tourne dans Docker.

## 2. Contexte et positionnement

TrocarLab n'invente pas le contrôle RCM. Il rend la robotique chirurgicale accessible à quelqu'un qui n'a ni robot, ni carte graphique NVIDIA, ni laboratoire.

### 2.1 La contrainte au cœur du projet

En chirurgie laparoscopique, l'instrument entre dans l'abdomen par un trocart posé dans une petite incision. L'instrument doit pivoter autour de ce point sans jamais le déplacer, sinon il déchire la paroi. Ce point fixe s'appelle le **RCM** (*Remote Center of Motion*). Autour du RCM, l'instrument ne garde que 4 mouvements : deux inclinaisons, l'enfoncement et la rotation sur lui-même.

### 2.2 État de l'art

| Outil | Ce qu'il apporte | Ce qui le rend difficile d'accès |
| --- | --- | --- |
| Plateforme de recherche pour la chirurgie laparoscopique autonome (arXiv:2603.08490, 2026) | Contrôle RCM open source, proche de notre périmètre | Vise des laboratoires équipés de vrais robots |
| dVRK | Standard de la recherche sur le da Vinci | Nécessite le robot réel |
| SurRoL | Environnements d'apprentissage par renforcement | Python 3.7, dépendances anciennes |
| AMBF | Simulation multi-corps riche | Installation complexe |
| ORBIT-Surgical | Simulation photoréaliste | Exige un GPU NVIDIA |
| PolygonMeshVirtualFixture (IROS 2020) | Zones de sécurité sur maillage | ROS 1 ; **aucune licence indiquée : lecture seule, aucun code copié** |

Tous ces travaux seront cités dans le README (voir section 13.5).

### 2.3 Le manque comblé

Aucun outil connu ne réunit ces trois points : **une commande** pour tout lancer, **n'importe quel ordinateur** (ARM ou x86, sans GPU), et des **tutoriels progressifs** pour débutants. TrocarLab ne rivalise pas avec la recherche ; il sert de marchepied vers elle.

### 2.4 Hypothèses à vérifier avec la V1

- **H1** : un MacBook ARM sans GPU fait tourner ROS 2, MoveIt et ros2\_control dans Docker avec une fluidité suffisante.
- **H2** : le *mock hardware* suffit pour démontrer le RCM et les zones de sécurité de façon convaincante.
- **H3** : un débutant peut suivre les tutoriels sans aide extérieure.
- **H4** : le projet suscite de l'intérêt (étoiles GitHub, retours, questions en entretien).

## 3. Périmètre de la V1

La V1 est minimale mais complète : un parcours de bout en bout, du lancement Docker jusqu'au pilotage de l'instrument dans le navigateur, avec une seule zone de sécurité.

### 3.1 Inclus dans la V1

| Bloc | Contenu V1 | Langage |
| --- | --- | --- |
| Socle | Image Docker ROS 2 (ARM64 et x86\_64), lancement en une commande, dépôt structuré en paquets ROS | Docker, YAML |
| Bras simulé | Modèle open source (Franka Panda, licence vérifiée) affiché dans RViz, piloté par ros2\_control avec le *mock hardware* et par MoveIt | Python, URDF |
| Instrument et trocart | Instrument rigide droit fixé au bras ; position du trocart définie dans un fichier de configuration | URDF, YAML |
| Contrôle RCM | Bibliothèque puis nœud ROS 2 qui convertissent une consigne (2 inclinaisons, enfoncement, rotation) en mouvements articulaires tout en gardant l'instrument sur le trocart | C++17 |
| Téléopération | Pilotage au clavier dans un terminal et dans la console web | Python, TypeScript |
| Zone de sécurité | **Une** zone interdite de forme simple (sphère) représentant un organe ; aucune partie de l'instrument, de la pointe à la tige, ne peut y entrer | C++17 |
| Console web réduite | Vue 3D du bras (Three.js), commandes clavier, affichage de l'état (écart au RCM, distance à la zone), arrêt d'urgence logiciel | TypeScript |
| Qualité | Tests unitaires, CI GitHub Actions, matrice de traçabilité | — |
| Documentation | README, avertissement, tutoriels MkDocs | Markdown |

### 3.2 Exclu de la V1 (reporté en V2 ou plus tard)

- Enregistrement des sessions et relecture dans le navigateur (V2)
- Démo en ligne sur GitHub Pages (V2, dépend de l'enregistrement)
- Journal infalsifiable (entrées chaînées par hash et signées) (V3)
- Plusieurs zones de sécurité, zones sur maillage, zones de guidage, glissement le long de la frontière (V2) ; anatomie réaliste, avec des modèles 3D gratuits sous licence libre compatible, en lien avec les zones sur maillage (V2)
- Pilotage à la manette (V2, optionnel)
- Simulateur physique (Gazebo, MuJoCo) : contacts, forces, tissus mous
- Instruments articulés (poignet, pince) et plusieurs bras
- Retour d'effort (haptique), vision endoscopique, autonomie
- Pilotage d'un robot réel (exclu définitivement, voir ES-001)
- Réécriture en Rust

### 3.3 Livrables

- [ ] Dépôt GitHub public sous licence Apache 2.0
- [ ] Image et fichier Docker Compose fonctionnant sur ARM64 et x86\_64
- [ ] Paquets ROS 2 : description du robot, configuration MoveIt, bibliothèque et nœud RCM, zone de sécurité, téléopération, pont vers la console
- [ ] Console web (TypeScript + Three.js)
- [ ] Ce cahier des charges, l'analyse de risques, la matrice de traçabilité générée automatiquement et la liste SOUP (docs/quality/), ainsi que les ADR (docs/adr/)
- [ ] Maquettes de la console dans Figma (formule gratuite), conformes au brief de la section 5.6
- [ ] Site de tutoriels MkDocs
- [ ] Tickets et tableau de suivi publics (GitHub Issues + Projects)

## 4. Personas et user stories

### 4.1 Personas

| Persona | Profil | Ce qu'il attend | Ce qui le fait abandonner |
| --- | --- | --- | --- |
| **Léa, étudiante en robotique** (primaire) | Master ou école d'ingénieurs, connaît un peu ROS 2, n'a pas accès à un robot chirurgical | Comprendre le RCM et les zones de sécurité en modifiant du vrai code | Une installation qui échoue ou demande un GPU |
| **Karim, développeur en reconversion** (secondaire) | Développeur web, débutant en robotique, ordinateur portable ordinaire | Un parcours pas à pas, du lancement au premier contrôleur | Du jargon non expliqué, des étapes sautées |
| **Dr Martin, interne en chirurgie** (tertiaire) | Pratique la cœlioscopie, curieux de la technique | Voir et piloter le robot sans rien installer de compliqué | Une interface en ligne de commande uniquement |
| **Recruteur ou ingénieur medtech** (lecteur) | Évalue un candidat | Un dépôt propre : exigences, tests, CI, décisions justifiées | Un projet sans tests ni documentation |

### 4.2 User stories prioritaires

- **US-001 — Lancer en une commande.** En tant que Léa, je veux lancer toute la simulation avec une seule commande Docker, pour commencer à apprendre sans passer une soirée à installer. *Critère : robot visible dans le navigateur (RViz via noVNC au début, puis la console web) en ≤ 30 min après le `git clone`.*
- **US-002 — Piloter autour du trocart.** En tant que Karim, je veux déplacer l'instrument au clavier et voir qu'il pivote autour du trocart, pour comprendre le RCM. *Critère : écart au RCM affiché en permanence et < 1 mm.*
- **US-003 — Être bloqué par la zone interdite.** En tant que Léa, je veux voir l'instrument s'arrêter au bord de la zone interdite, pour comprendre les *virtual fixtures*. *Critère : aucune partie de l'instrument, tige comprise, ne pénètre la sphère, une alerte s'affiche.*
- **US-004 — Piloter depuis le navigateur.** En tant que Dr Martin, je veux piloter le robot depuis une page web, pour ne pas toucher au terminal. *Critère : console accessible sur `localhost` après le lancement.*
- **US-005 — Suivre un tutoriel.** En tant que Karim, je veux suivre un tutoriel par étape, pour reproduire et comprendre chaque brique. *Critère : chaque tutoriel se termine par un résultat vérifiable.*
- **US-006 — Évaluer la rigueur.** En tant que recruteur, je veux retrouver pour chaque exigence sa preuve de vérification et les pull requests qui la couvrent, pour juger la démarche qualité. *Critère : matrice de traçabilité à jour dans le dépôt.*

## 5. Exigences fonctionnelles

Chaque exigence a un identifiant unique, une priorité MoSCoW (Must, Should, Could) et une méthode de vérification : **T** = test automatisé, **I** = inspection (relecture, démonstration), **A** = analyse. Les centaines regroupent les blocs : 0xx socle, 1xx bras, 2xx RCM, 3xx téléopération, 4xx zone de sécurité, 5xx console web, 6xx documentation.

### 5.1 Socle (EF-0xx)

| ID | Exigence | Priorité | Vérif. |
| --- | --- | --- | --- |
| EF-001 | Une seule commande (`docker compose up`) démarre la simulation, le pont rosbridge et la console web. | Must | T |
| EF-002 | Les images Docker sont construites pour ARM64 et x86\_64, chacune sur une machine native de la CI (sans émulation). | Must | T |
| EF-003 | La simulation fonctionne sans carte graphique dédiée. | Must | I |
| EF-004 | La position du trocart, la zone interdite et les vitesses maximales se règlent dans un fichier YAML, sans recompiler. | Should | T |
| EF-005 | RViz est accessible dans un onglet du navigateur grâce à un conteneur noVNC, sans serveur d'affichage à installer sur l'ordinateur hôte. | Must | T |

### 5.2 Bras simulé (EF-1xx)

| ID | Exigence | Priorité | Vérif. |
| --- | --- | --- | --- |
| EF-101 | Le système charge un modèle de bras open source dont la licence autorise la redistribution. | Must | I |
| EF-102 | Le bras est piloté par ros2\_control avec le *mock hardware*. | Must | T |
| EF-103 | Un instrument rigide droit est monté au bout du bras ; sa longueur est paramétrable. | Must | T |
| EF-104 | MoveIt amène le bras en position d'entrée : l'instrument hors du corps, aligné sur l'axe du trocart. MoveIt ne bouge jamais le bras quand l'instrument est inséré : l'insertion et le retrait se font en ligne droite le long de l'axe, par le nœud RCM, avec la zone interdite vérifiée. | Must | T |
| EF-105 | L'état du bras (positions articulaires, pose de la pointe) est publié sur des topics ROS 2. | Must | T |
| EF-106 | Une fois le bras en position d'entrée, le controller manager désactive le contrôleur de trajectoire utilisé par MoveIt et active celui que pilote le nœud RCM ; deux contrôleurs ne commandent jamais les mêmes articulations en même temps. | Must | T |
| EF-107 | La zone interdite est aussi déclarée comme obstacle dans la scène de MoveIt, pour que ses trajets ne la traversent jamais. | Must | T |

### 5.3 Contrôle RCM (EF-2xx)

Le RCM se construit en trois étapes : une bibliothèque C++ sans ROS, puis un nœud ROS 2 simple qui l'utilise, puis (en option) un plugin ros2\_control. L'étape 1 valide le J3, l'étape 2 valide le J4. Toutes les vérifications de sécurité (zone, seuil d'écart, butées, validation des consignes, enfoncements minimal et maximal, pas maximal par rapport à la marge, fraîcheur de l'état du bras, états de démarrage et de faute) sont regroupées dans trocarlab\_safety ; rcm\_core ne contient que les calculs. Seule exception : la jacobienne amortie (ES-010), indissociable du calcul de cinématique inverse, reste dans rcm\_core ; elle est couverte par les tests aux singularités et par les différences finies.

| ID | Exigence | Priorité | Vérif. |
| --- | --- | --- | --- |
| EF-201 | Les calculs du RCM sont regroupés dans une bibliothèque C++17 sans dépendance à ROS (`trocarlab_rcm_core`), testée avec gtest. | Must | T |
| EF-202 | Elle accepte une consigne en 4 degrés de liberté : inclinaison gauche-droite, inclinaison haut-bas, enfoncement, rotation. | Must | T |
| EF-203 | Elle calcule les mouvements articulaires qui réalisent la consigne en gardant l'axe de l'instrument sur le trocart. | Must | T |
| EF-204 | Le nœud RCM publie en continu l'écart entre l'axe de l'instrument et le trocart (en mm). | Must | T |
| EF-205 | En téléopération, le nœud RCM refuse une consigne qui ferait sortir l'instrument du trocart (enfoncement minimal). Seul le retrait du réarmement (ES-013) fait sortir l'instrument, en ligne droite le long de son axe. | Must | T |
| EF-206 | Avec un bras à 7 axes, le calcul utilise l'axe en réserve pour s'éloigner des butées articulaires. | Could | T |
| EF-207 | Un nœud ROS 2 (`trocarlab_rcm_node`) utilise la bibliothèque et envoie des positions articulaires à un contrôleur standard de ros2\_control. | Must | T |
| EF-208 | Le nœud RCM est transformé en plugin contrôleur ros2\_control. | Should | I |
| EF-209 | La cinématique du bras (pose de l'outil, jacobienne) est calculée par la bibliothèque et vérifiée par gtest contre des données de référence générées une fois avec MoveIt (1 000 configurations et leurs poses, dans un fichier versionné avec les tests). Un script de tools/ régénère ce fichier ; la bibliothèque reste sans ROS. | Must | T |

### 5.4 Téléopération (EF-3xx)

| ID | Exigence | Priorité | Vérif. |
| --- | --- | --- | --- |
| EF-301 | Un nœud de téléopération traduit les touches du clavier en consignes RCM. | Must | T |
| EF-302 | Dans le terminal, chaque appui produit un pas fixe (par défaut 1 mm ou 1°), puis le bras s'arrête : il n'y a pas de mouvement continu. Dans la console web, le mouvement est continu avec homme mort : il s'arrête sur l'événement `keyup` ou quand l'onglet perd le focus (`blur`). | Must | T |
| EF-303 | Un facteur d'échelle réduit les mouvements (par défaut 1/3), comme sur une console chirurgicale. | Should | T |
| EF-304 | Une touche dédiée déclenche l'arrêt d'urgence logiciel. | Must | T |

Un terminal ne signale pas le relâchement d'une touche, et la répétition automatique du clavier varie selon le système. Le pas à pas supprime le problème au lieu de le régler : sans mouvement continu, il n'y a rien à arrêter. Le mouvement continu est réservé à la console, où `keyup` existe vraiment.

### 5.5 Zone de sécurité (EF-4xx)

| ID | Exigence | Priorité | Vérif. |
| --- | --- | --- | --- |
| EF-401 | Une zone interdite sphérique (centre, rayon) est définie dans la configuration, avec une marge de sécurité ajoutée au rayon (paramètre YAML). | Must | T |
| EF-402 | Toute consigne qui amènerait une partie de l'instrument dans la zone est refusée : le bras reste à sa dernière position sûre. Le contrôle porte sur tout le segment trocart → pointe (distance d'un point à un segment), pas seulement sur la pointe. Une consigne n'est acceptée que si la distance entre la tige et le centre de la sphère est strictement supérieure au rayon augmenté de la marge : une tige exactement sur la marge est refusée. Les consignes qui éloignent l'instrument de la zone restent toujours acceptées, pour ne jamais coincer le robot contre la frontière. | Must | T |
| EF-403 | La distance entre l'instrument (segment trocart → pointe) et la zone est publiée en continu (en mm). | Must | T |
| EF-404 | Une alerte est publiée quand l'instrument passe sous une distance d'approche (par défaut 10 mm). | Should | T |

Le glissement le long de la frontière (projection de la consigne sur la sphère) est reporté en V2 : c'est un comportement différent, qui se teste différemment.

### 5.6 Console web (EF-5xx)

| ID | Exigence | Priorité | Vérif. |
| --- | --- | --- | --- |
| EF-501 | La console affiche le bras, le trocart et la zone interdite en 3D (Three.js), à partir des topics reçus via rosbridge. | Must | T |
| EF-502 | La console envoie les commandes clavier au nœud de téléopération. | Must | T |
| EF-503 | La console affiche l'écart au RCM, la distance à la zone et l'état de connexion. | Must | T |
| EF-504 | Un bouton d'arrêt d'urgence est visible en permanence. | Must | T |
| EF-505 | La console affiche l'avertissement « usage non clinique ». | Must | I |
| EF-506 | La console affiche la progression de la séquence de démarrage (vérification de la configuration, placement par MoveIt, bascule, vérification de l'écart). | Should | T |

**Brief des maquettes de la console.** Ce brief décrit le contenu attendu de l'écran, pas son design. Les maquettes sont réalisées dans Figma (formule gratuite), de la basse vers la haute fidélité : un wireframe rapide (une à deux heures au plus) peut être fait dès le J1 pour vérifier ce brief et illustrer le README ; les maquettes détaillées attendent le début du J6, et sont relues point par point avec ce brief avant d'écrire la console. Le fichier source reste dans Figma ; le dépôt ne contient que des exports légers (PNG ou SVG), dans docs/design/wireframes/ puis docs/design/mockups/. Dans Figma, les écrans sont construits uniquement à partir de composants : variables pour les tokens, composants avec leurs variantes, auto layout, convention de nommage et page « bibliothèque ». Leurs noms sont repris à l'identique dans le code (section 8.1, ligne « Design system »).

*Un seul écran, organisé en zones :*

| Zone | Contenu | Exigences |
| --- | --- | --- |
| Vue 3D (centre) | Le bras, le trocart, la zone interdite et l'axe de l'instrument ; une paroi abdominale stylisée (dôme transparent dessiné dans le code, sans modèle extérieur) sur laquelle est posé le trocart, et la zone interdite étiquetée « organ » (Should) | EF-501 |
| Bandeau d'état de sécurité (haut) | État courant (prêt, consigne refusée, faute, arrêt d'urgence) et sa cause | ES-017 |
| Indicateurs | Écart au trocart en mm, avec la cible de 1 mm et le seuil de 2 mm visibles ; distance à la zone en mm, avec l'alerte sous 10 mm ; état de la connexion | EF-503, EF-404, ENF-001, ES-002 |
| Légende des commandes | Quelle touche fait quoi, exprimée du point de vue de la pointe, avec les axes dessinés ; facteur d'échelle en cours | ES-020, EF-303 |
| Arrêt d'urgence | Bouton toujours visible, à une place fixe, jamais recouvert | EF-504, ES-007 |
| Avertissement | « Educational project, not for clinical use », permanent | EF-505, ES-001 |

*États à dessiner, une maquette pour chacun :* séquence de démarrage en cours, avec ses étapes (ES-012, EF-506) ; prêt ; en mouvement ; approche de la zone (EF-404) ; consigne refusée (EF-402) ; faute, avec le bouton de réarmement et l'explication qu'il relance la séquence de démarrage (ES-013) ; arrêt d'urgence (ES-007) ; connexion perdue (ES-005) ; focus de l'onglet perdu, mouvement arrêté (EF-302).

*Règles d'ergonomie, inspirées de l'IEC 62366-1 :*

- ne jamais transmettre une information par la couleur seule : toujours un texte ou une icône en plus ;
- l'arrêt d'urgence est utilisable au clavier comme à la souris ;
- interface en anglais (ENF-012), pensée pour un écran d'ordinateur, pas pour un mobile.

### 5.7 Documentation (EF-6xx)

| ID | Exigence | Priorité | Vérif. |
| --- | --- | --- | --- |
| EF-601 | Le README explique en moins d'une page comment lancer le projet. | Must | I |
| EF-602 | Chaque brique a un tutoriel MkDocs avec un résultat vérifiable en fin d'étape. | Should | I |
| EF-603 | Le README cite les travaux de référence de la section 2.2. | Must | I |

## 6. Exigences non fonctionnelles

Ces valeurs sont des cibles de départ. Elles seront confirmées ou ajustées après les premières mesures sur le MacBook (hypothèse H1), et chaque changement sera noté dans le suivi des versions.

| ID | Catégorie | Exigence | Cible | Priorité | Vérif. |
| --- | --- | --- | --- | --- | --- |
| ENF-001 | Précision | Écart maximal entre l'axe de l'instrument et le trocart pendant la téléopération (cible de performance) | < 1 mm | Must | T |
| ENF-002 | Fréquence | Fréquence de la boucle du nœud RCM, visée mais non garantie (Docker sur Mac n'est pas un système temps réel), mesurée sur la machine de référence, hors CI | ≥ 100 Hz | Must | A |
| ENF-003 | Réactivité | Délai entre l'appui sur une touche de la console et le mouvement visible, en local | < 200 ms | Should | A |
| ENF-004 | Réactivité | Délai entre l'arrêt d'urgence et l'arrêt complet du bras, mesuré sur la machine de référence et consigné dans le rapport de version | < 100 ms | Must | A |
| ENF-005 | Ressources | Mémoire utilisée par l'ensemble des conteneurs | < 6 Go | Must | A |
| ENF-006 | Ressources | Machine minimale supportée | 4 cœurs, 8 Go de RAM, sans GPU | Should | I |
| ENF-007 | Installation | Temps entre `git clone` et robot visible dans le navigateur, connexion de 50 Mbit/s | ≤ 30 min | Must | I |
| ENF-008 | Portabilité | Plateformes supportées | macOS ARM64, Linux x86\_64 ; Windows via WSL2 « au mieux » | Must | T |
| ENF-009 | Versions | Distribution de ROS 2 et version de MoveIt figées et notées dans le README | ROS 2 Jazzy (LTS) | Must | I |
| ENF-010 | Maintenabilité | Couverture de tests : 100 % des branches pour trocarlab\_safety, qui regroupe tout le code de sécurité (sauf la jacobienne amortie d'ES-010, voir 5.3), 80 % des lignes pour le reste du C++ | 100 % des branches (sécurité) ; ≥ 80 % des lignes (reste) | Must | T |
| ENF-011 | Maintenabilité | Code formaté et analysé automatiquement (clang-format, clang-tidy, ruff, prettier), par pre-commit avant chaque commit et par la CI | 0 erreur | Must | T |
| ENF-012 | Langue | Code, identifiants, noms de fichiers, messages de commit et documentation en anglais (projet open source lu à l'international) ; tutoriels aussi en français si le temps le permet ; ce cahier des charges reste en français | Tout le code en anglais | Must | I |

Quatre exigences portent sur la tenue du projet dans la durée :

| ID | Catégorie | Exigence | Cible | Priorité | Vérif. |
| --- | --- | --- | --- | --- | --- |
| ENF-013 | Reproductibilité | Toutes les dépendances sont figées : image Docker de base par empreinte, dépôts sources par commit (`dependencies.repos`), verrous npm et Python, actions GitHub par empreinte de commit | 0 dépendance non figée | Must | I |
| ENF-014 | Traçabilité | La matrice exigence → preuve est générée automatiquement à partir des résultats des tests, des fiches d'inspection et des rapports de mesure ; la CI échoue si une exigence Must dont le jalon bloquant est atteint n'a aucune preuve valide, ou si une preuve cite un identifiant inexistant | 100 % des Must des jalons atteints | Must | T |
| ENF-015 | Sécurité de la chaîne | Commits et versions signés, analyse CodeQL, détection des secrets, SBOM et attestation de provenance publiés à chaque version, workflows aux permissions minimales | Actif dès la v1.0.0 | Must | I |
| ENF-016 | Robustesse du C++ | Les tests C++ de trocarlab\_rcm\_core et trocarlab\_safety (sans ROS) s'exécutent aussi avec AddressSanitizer et UndefinedBehaviorSanitizer dans la CI ; ils ne sont pas appliqués aux nœuds ROS, où ils remontent du bruit venant des bibliothèques ROS elles-mêmes | 0 erreur | Must | T |

**ENF-001 et ES-002 ne se contredisent pas.** Moins de 1 mm est la cible de performance ; 2 mm est le seuil de sécurité au-delà duquel le bras s'arrête. Entre les deux, le système fonctionne mais s'écarte de sa cible.

**Ce que mesure l'écart au RCM.** Avec le *mock hardware*, le bras exécute parfaitement chaque commande. L'écart mesure donc la justesse du calcul, pas la qualité du suivi d'un vrai robot. Piste pour la V2 : un faux matériel qui ajoute un retard et du bruit, pour rendre cette mesure significative.

**Distribution ROS 2.** Humble est écartée : sa fin de support (mai 2027) tombe au moment de la publication de la V1. Jazzy, maintenue jusqu'en mai 2029, est retenue : plus de tutoriels, un MoveIt mature.

## 7. Exigences de sécurité

Chaque exigence de sécurité (ES-xxx) est une mesure qui maîtrise un risque de la section 10 (RP-xxx). C'est le lien que l'ISO 14971 impose entre un danger et sa mesure de maîtrise. Ici, « sécurité » veut dire : le comportement simulé serait sûr s'il était transposé à un vrai robot.

| ID | Exigence | Risque maîtrisé | Priorité | Vérif. |
| --- | --- | --- | --- | --- |
| ES-001 | L'avertissement « Projet éducatif, non destiné à un usage clinique » figure dans le README, la documentation et la console ; le code ne fournit aucun pilote pour un robot réel. | RP-001 | Must | I |
| ES-002 | Si l'écart au RCM est strictement supérieur à 2 mm (seuil de sécurité), le nœud RCM arrête le bras et passe en état « faute ». | RP-002 | Must | T |
| ES-003 | La zone interdite est vérifiée sur la consigne **avant** qu'elle soit envoyée au bras, pour toute la tige de l'instrument (segment trocart → pointe). Comme le pas maximal par cycle reste inférieur à la marge (ES-008), l'instrument ne peut pas sauter par-dessus la frontière entre deux cycles. | RP-003, RP-019 | Must | T |
| ES-004 | Les vitesses articulaires et la vitesse de la pointe sont limitées par des valeurs de configuration. | RP-004, RP-009 | Must | T |
| ES-005 | Si aucune consigne ou aucun signal de vie de la console n'arrive pendant 500 ms, le bras s'arrête, et pas avant. Le délai est mesuré avec l'horloge du nœud, qui peut être simulée pour les tests. | RP-005 | Must | T |
| ES-006 | Le nœud RCM refuse toute consigne invalide (valeur non numérique, hors bornes) et le signale. | RP-006 | Must | T |
| ES-007 | L'arrêt d'urgence est prioritaire sur toute autre commande et ne se lève que par une action explicite. | RP-005 | Must | T |
| ES-008 | Au démarrage, le système vérifie la configuration (trocart atteignable, zone hors du trocart, déplacement maximal de l'instrument en un cycle (vitesse maximale × période) inférieur à la marge de la zone) et refuse de démarrer si elle est incohérente. | RP-007, RP-003 | Must | T |
| ES-009 | Le pont rosbridge n'écoute que sur `localhost` par défaut. | RP-008 | Must | T |
| ES-010 | Le calcul des mouvements articulaires utilise une inversion amortie de la jacobienne (moindres carrés amortis, *damped least squares*) pour rester stable près des singularités. | RP-009 | Must | T |
| ES-011 | Si une articulation atteint sa butée et que le RCM ne peut plus être respecté, le nœud RCM arrête le bras et passe en état « faute ». | RP-010 | Must | T |

**Avant et après le mouvement.** Les exigences suivantes couvrent le démarrage, la sortie de faute, les informations périmées, les réglages, les unités, les commandes, les composants tiers et l'information de l'utilisateur.

| ID | Exigence | Risque maîtrisé | Priorité | Vérif. |
| --- | --- | --- | --- | --- |
| ES-012 | Au démarrage, le système est à l'arrêt. La téléopération n'est activée qu'après la vérification de la configuration (ES-008, ES-019), le placement par MoveIt en position d'entrée (instrument hors du corps), la bascule vers le nœud RCM (EF-106), l'insertion en ligne droite le long de l'axe du trocart avec la zone vérifiée, et un écart au trocart vérifié sous la cible de 1 mm (ENF-001), et non sous le seuil de sécurité de 2 mm : on ne démarre pas déjà en dehors de la cible. | RP-011, RP-021 | Must | T |
| ES-013 | On ne sort de l'état « faute » que par une action explicite de réarmement. Le réarmement ne relance pas la téléopération. Il commence par retirer l'instrument en ligne droite le long de son axe jusqu'à la sortie du trocart, avec la zone interdite toujours vérifiée. Si ce retrait est impossible (butée, état du bras périmé, zone sur le trajet), le système reste en faute. Une fois l'instrument sorti, il relance la séquence de démarrage d'ES-012 : position d'entrée par MoveIt, bascule, insertion en ligne droite, vérifications. Raison : bras arrêté, la cause d'une faute ne peut pas disparaître d'elle-même ; et MoveIt, qui ne connaît ni le RCM ni la zone, ne doit jamais bouger le bras quand l'instrument est inséré. Autoriser seulement les mouvements qui réduisent la cause est envisagé pour la V2. | RP-012, RP-021 | Must | T |
| ES-014 | Si l'état du bras (`/joint_states`) n'a pas été mis à jour depuis un délai configurable (par défaut 100 ms, mesuré avec l'horloge du nœud), le nœud RCM arrête le bras et passe en faute. | RP-013 | Must | T |
| ES-015 | Les paramètres de sécurité (marge, vitesses, seuils, enfoncements minimal et maximal) sont lus et vérifiés au démarrage, puis ne peuvent plus être modifiés pendant le fonctionnement. Toute tentative est refusée et journalisée. | RP-014 | Must | T |
| ES-016 | Un enfoncement maximal configurable est défini ; toute consigne qui le dépasserait est refusée. | RP-015 | Must | T |
| ES-017 | L'état de sécurité (prêt, consigne refusée, faute, arrêt d'urgence) et sa cause sont affichés en permanence dans la console et dans le terminal. | RP-012 | Should | T |
| ES-018 | Chaque événement de sécurité (refus, faute, arrêt d'urgence, réarmement, tentative de modification d'un paramètre) est enregistré avec sa date, sa cause et l'état du bras. Ce journal prépare le futur journal infalsifiable. | RP-016, RP-014 | Should | T |
| ES-019 | Chaque paramètre de configuration porte son unité dans son nom (par exemple `zone_radius_m`, `max_speed_m_s`). Au démarrage, chaque valeur est comparée à une plage autorisée, et le système refuse de démarrer si une valeur en sort. Ces plages attrapent les erreurs d'unité grossières (un facteur 10 ou plus), pas celles qui restent dans la plage autorisée. | RP-018 | Must | T |
| ES-020 | Les commandes de téléopération sont exprimées du point de vue de la pointe (ce que verrait le chirurgien à l'écran), et non du bras ; la console affiche les axes de commande. | RP-019 | Must | T |
| ES-021 | Les anomalies connues de chaque composant de la liste SOUP sont revues à chaque mise à jour de version ; leur effet possible sur la sécurité est évalué et noté dans la liste SOUP. | RP-020 | Must | I |

**Prévu pour la V2 : un surveillant indépendant.** Aujourd'hui, les vérifications de sécurité tournent dans le même programme que les calculs : un bug de ce programme peut emporter la vérification avec lui. Un surveillant indépendant, un nœud séparé, observera la position réelle du bras et arrêtera tout s'il voit la tige dans la zone, quoi qu'ait décidé le nœud RCM. Avec le *mock hardware*, la position réelle est toujours égale à la commande ; ce surveillant prendra son sens avec le faux matériel bruité prévu en V2.

## 8. Architecture et choix techniques

Tout tourne dans un conteneur Docker. Le navigateur ne parle au robot qu'à travers rosbridge, et chaque consigne passe par le nœud RCM, qui applique la zone de sécurité avant d'envoyer quoi que ce soit au bras.

&#91;embedded content: architecture V1 · 7 composants dans un conteneur Docker\]

La console envoie des touches ; la téléopération en fait une consigne RCM ; seul le nœud RCM commande le bras simulé, à travers un contrôleur standard de ros2\_control. MoveIt n'intervient qu'au démarrage, pour placer l'instrument dans le trocart ; le controller manager bascule ensuite d'un contrôleur à l'autre (EF-106).

### 8.1 Choix techniques

| Domaine | Choix | Pourquoi | Alternative écartée |
| --- | --- | --- | --- |
| Middleware | ROS 2 Jazzy (LTS, maintenue jusqu'en mai 2029) | Standard de l'industrie ; reste maintenue après la V1 | Humble (fin de support en mai 2027) ; ROS 1 (fin de vie en mai 2025) |
| Planification | MoveIt 2 | Position initiale et vérification des collisions, sans réinventer | Planificateur maison |
| Contrôle | ros2\_control + *mock hardware* | Même interface qu'un vrai robot, très léger | Gazebo (lourd, GPU conseillé) |
| Bras | Franka Panda (nommé fer dans franka\_description, licence Apache 2.0 vérifiée) | 7 axes : il reste un axe de réserve une fois le RCM imposé | UR à 6 axes (aucune réserve ; maillages sous conditions propres au fabricant) |
| RCM et zone de sécurité | Bibliothèques C++17 sans ROS (CMake, Eigen), puis nœud ROS 2 | Testables seules avec gtest ; on n'affronte pas le plugin ros2\_control en débutant | Contrôleur ros2\_control dès le départ (trop de notions à la fois) ; Python (non utilisé pour le contrôle dans l'industrie, pauses imprévisibles, incompatible avec un plugin ros2\_control) |
| Cinématique | Écrite à la main à partir des paramètres publics du Panda (convention de Denavit-Hartenberg modifiée, dite de Craig ; décalage de la bride et longueur de l'instrument inclus), vérifiée contre des données de référence MoveIt | Très formateur, aucune dépendance de plus | KDL (bibliothèque vieillissante, aucun gain pédagogique ; LGPL compatible en usage séparé) ; Pinocchio (BSD, disproportionné pour le besoin) gardé en repli |
| Téléopération, outils | Python (rclpy) | Rapide à écrire, idéal pour débuter ROS 2 | — |
| Console | TypeScript, Three.js, roslibjs, Vite | Mon point fort ; rendu 3D léger dans le navigateur | Foxglove (outil externe, moins pédagogique) |
| Affichage RViz | Conteneur noVNC : RViz dans un onglet du navigateur | Aucun serveur d'affichage à configurer sur le Mac | XQuartz (configuration pénible) |
| Conteneurs | Docker, Docker Compose, images ARM64 et x86\_64, image de base figée par empreinte, Dockerfile multi-étapes, utilisateur non root | Une commande, même environnement partout | Installation native (impossible sur macOS) |
| Tests | gtest, pytest, launch\_testing, RapidCheck, Hypothesis, Vitest, Playwright, `colcon test` | Outils standard de chaque langage | — |
| Documentation | MkDocs Material sur GitHub Pages | Gratuit, Markdown, versionné avec le code | Wiki GitHub (non versionné avec le code) |
| Icônes | Sprite SVG unique (symbols.svg) généré par un script : normalisation par SVGO, un symbole icon-\<nom> par icône, couleur héritée (currentColor), icônes multicolores exclues ; type TypeScript IconName généré ; composant Icon accessible (décorative masquée aux lecteurs d'écran, ou libellée). Fichiers générés à la construction, non commités | Un seul fichier téléchargé et mis en cache ; icônes qui suivent le thème ; une faute de frappe dans un nom fait échouer la compilation | Script maison sans SVGO (casse les icônes à contours, perd les formes qui ne sont pas des tracés) ; police d'icônes (moins accessible) |
| Design system | Découpage en composants (atomic design) : tokens, atomes (icône, bouton, badge, valeur), molécules (indicateur, ligne de légende), organismes (bandeau d'état, panneau d'indicateurs, légende, arrêt d'urgence, vue 3D), gabarit, pages (les 9 états). Mêmes noms de composants, de variantes et de tokens dans Figma et dans le code ; tokens versionnés dans le dépôt comme source unique | Maquette et code ne divergent pas ; un changement se répercute sans ambiguïté ; chaque écran n'est qu'un assemblage de composants | Une maquette ou un artefact par écran, sans composants partagés (les artefacts Claude ne servent qu'à explorer en basse fidélité) |

### 8.2 Organisation du dépôt

Le dépôt est un monodépôt : une même pull request peut modifier une exigence, son code et son test. Il sépare le code exécuté par le robot, les outils de développement, la documentation pour les utilisateurs et la documentation qualité.

```
trocarlab/
├── .github/
│   ├── workflows/                 # ci.yml, nightly.yml, docs.yml, release.yml, codeql.yml
│   ├── ISSUE_TEMPLATE/            # bogue, fonctionnalité, exigence
│   ├── PULL_REQUEST_TEMPLATE.md   # exigences couvertes, tests ajoutés, risques touchés, usage de l'IA
│   └── dependabot.yml             # mises à jour de dépendances proposées automatiquement
├── .devcontainer/                 # environnement de développement reproductible
├── docker/
│   ├── Dockerfile                 # multi-étapes : base, dev, runtime ; utilisateur non root
│   ├── compose.yaml
│   └── novnc/
├── src/
│   ├── trocarlab_interfaces/      # messages et services propres au projet
│   ├── trocarlab_description/     # URDF : bras, instrument, trocart
│   ├── trocarlab_moveit_config/
│   ├── trocarlab_rcm_core/        # C++ sans ROS : include/, src/, test/
│   ├── trocarlab_safety/          # C++ sans ROS : include/, src/, test/
│   ├── trocarlab_rcm_node/        # nœud ROS 2 qui utilise rcm_core et safety
│   ├── trocarlab_teleop/          # téléopération (Python)
│   ├── trocarlab_bringup/         # launch/, config/
│   └── trocarlab_integration_tests/
├── console/                       # package.json, package-lock.json, src/, tests/
│   ├── icons/                     # sources SVG, une icône par fichier, noms en anglais
│   ├── icons.statics.json         # icônes multicolores, exclues de la normalisation
│   ├── scripts/build-icons.ts     # SVGO, sprite symbols.svg, type IconName, option --list
│   └── src/styles/tokens          # tokens du design system, source unique partagée avec Figma
├── docs/
│   ├── tutorials/                 # site MkDocs public
│   ├── design/                    # exports des wireframes (wireframes/) et des maquettes (mockups/), lien vers Figma
│   ├── quality/                   # CDC exporté, risques, cas de test, matrice, inspections, mesures, SOUP, rapports
│   └── adr/                       # décisions d'architecture numérotées
├── tools/                         # données de référence, génération de la matrice
├── dependencies.repos             # dépendances sources figées sur un commit
├── .pre-commit-config.yaml        # formatage et vérifications avant chaque commit
├── .clang-format  .clang-tidy  .editorconfig
├── .gitignore  .gitattributes  .dockerignore
├── pyproject.toml                 # configuration ruff et pytest
├── mkdocs.yml
├── README.md  LICENSE  NOTICE  CHANGELOG.md
├── CONTRIBUTING.md  CODE_OF_CONDUCT.md  SECURITY.md  CITATION.cff
└── CLAUDE.md  AI_POLICY.md         # contexte pour l'agent IA ; politique d'usage de l'IA
```

**Pourquoi ces éléments :**

- **`trocarlab_interfaces`** regroupe les messages propres au projet (consigne en 4 degrés de liberté, écart au trocart, état « faute »). Tous les autres paquets en dépendent, ce qui évite les dépendances circulaires.
- **`docs/adr/`** contient un court fichier par décision d'architecture : contexte, options, choix, conséquences. Sur plusieurs années, c'est la mémoire des « pourquoi ». Premiers ADR : choix du Panda, de Jazzy, de la cinématique maison, du C++, du mock hardware.
- **`docs/quality/`** sépare la documentation qualité des tutoriels publics. Elle contient notamment la liste **SOUP** (*Software Of Unknown Provenance*, terme de l'IEC 62304) : chaque composant tiers avec sa version, sa licence, son rôle et ses anomalies connues (ES-021).
- **`tools/`** contient les outils de développement, dont le script qui régénère les données de référence de la cinématique (EF-209). Ce n'est pas du code exécuté par le robot.
- **`dependencies.repos`** fige sur un commit précis les dépôts compilés depuis les sources, comme `franka_description`.

**Mise en place progressive.** Chaque élément arrive au moment où il sert :

| Jalon | Éléments mis en place |
| --- | --- |
| J1 | README, LICENSE, NOTICE, `.gitignore`, `.editorconfig`, pre-commit, CI minimale, modèle de pull request, protection de `main`, commits signés, `docs/adr/` et `docs/quality/` |
| J2 | `trocarlab_interfaces`, `dependencies.repos`, image Docker figée par empreinte, Dependabot |
| J3 | clang-tidy, mesure de la couverture, matrice de traçabilité générée automatiquement |
| J7 (v1.0.0) | SECURITY.md, CITATION.cff, CodeQL, SBOM, versions signées |

## 9. Qualité, tests et traçabilité

Toute exigence « Must » doit pouvoir être suivie jusqu'à sa preuve de vérification : un test qui passe dans la CI, une fiche d'inspection ou un rapport de mesure (section 9.2). C'est la version simplifiée de la traçabilité demandée par l'IEC 62304.

### 9.1 Stratégie de tests

| Niveau | Ce qu'on teste | Outil | Exemple |
| --- | --- | --- | --- |
| Unitaire C++ | Calculs du RCM, cinématique et zone de sécurité, sans ROS | gtest | Une consigne qui ferait traverser la sphère par la tige est refusée, même si la pointe reste dehors ; au bord de la zone, une consigne qui s'en éloigne est acceptée (EF-402) |
| Limites | Chaque seuil chiffré, de part et d'autre de la limite (à ± ε) | gtest, pytest | Tige à marge + ε (acceptée) et à marge − ε (refusée) (EF-402) ; écart de 2,0 mm − ε (le bras continue) et 2,0 mm + ε (arrêt) (ES-002), avec ε très supérieur à la précision des calculs en virgule flottante |
| Propriétés | Une règle qui doit toujours être vraie, vérifiée sur des milliers de cas générés ; en cas d'échec, l'outil réduit au cas le plus simple | RapidCheck (C++), Hypothesis (Python) | Quelle que soit la consigne, la tige n'entre jamais dans la zone (ES-003). Et pour chaque consigne, soit l'écart reste sous 1 mm, soit la consigne est refusée, soit le système passe en faute : jamais d'écart supérieur à 1 mm pendant que le bras bouge (ENF-001, ES-002, ES-011) |
| Cinématique | Cinématique maison contre deux références indépendantes | gtest | Même pose que les données MoveIt sur 1 000 configurations (EF-209) ; jacobienne égale aux différences finies |
| Injection de fautes | Chaque mesure de sécurité face au danger qu'elle maîtrise | gtest, launch\_testing | Console coupée en plein mouvement, avec une horloge simulée : bras encore en mouvement au tick qui précède 500 ms, arrêté au tick de 500 ms (ES-005) ; `NaN` ou infini refusé (ES-006) ; configuration incohérente refusée (ES-008) ; butée → état « faute » (ES-011) ; vitesses bornées près d'une singularité (ES-010) ; téléopération bloquée tant que la bascule n'est pas terminée (ES-012) ; réarmement → retrait en ligne droite avec la zone vérifiée, puis séquence de démarrage ; système maintenu en faute si le retrait est impossible (ES-013) ; aucun ordre envoyé à MoveIt tant que l'instrument est inséré (EF-104) ; topic de l'état du bras coupé → faute (ES-014) ; modification d'un paramètre de sécurité refusée et journalisée (ES-015, ES-018) ; valeur hors plage → refus de démarrer (ES-019) |
| Sanitizers | Erreurs mémoire et comportements indéfinis du C++ | ASan, UBSan | Tests gtest de trocarlab\_rcm\_core et trocarlab\_safety (sans ROS) recompilés avec les sanitizers dans la CI : 0 erreur (ENF-016) |
| Unitaire Python | Traduction touches → consigne | pytest | Un appui → un pas de 1 mm ; aucun mouvement sans appui (EF-302) ; touche « gauche » → pointe vers la gauche dans le repère de la pointe (ES-020) |
| Intégration ROS 2 | Nœuds lancés ensemble, topics réels | launch\_testing | Bascule MoveIt → RCM sans conflit (EF-106) ; publication de l'écart (EF-204) |
| Non-régression | Scénarios enregistrés, rejoués chaque nuit et avant chaque version | rosbag, launch\_testing | Une séance de pilotage type et une approche de la zone donnent le même comportement qu'à l'enregistrement |
| Front unitaire | Composants et connexion à rosbridge | Vitest | Le bouton d'arrêt d'urgence publie sur le bon topic (EF-504) |
| Front de bout en bout | La console dans un vrai navigateur, branchée au système complet | Playwright | Perte du focus de l'onglet → arrêt (EF-302) ; arrêt d'urgence depuis l'interface (EF-504) |
| Système de bout en bout | Lancement complet par Docker Compose | Script CI | La console répond et le robot bouge (EF-001) |
| Mesures de temps | Fréquence et délais, sur la machine de référence, hors CI | Script de mesure | Boucle à 100 Hz (ENF-002) ; arrêt d'urgence en moins de 100 ms (ENF-004) |
| Manuel | Démonstration, relecture | Liste de contrôle | Avertissement visible partout (ES-001) |

Les tests de sécurité (ES-xxx) sont écrits **avant** le code qu'ils vérifient, pour s'assurer qu'ils échouent d'abord.

**Règles de conception des tests**

- Chaque seuil chiffré est défini sans ambiguïté (« strictement supérieur » ou « supérieur ou égal »), puis testé de part et d'autre, à la limite − ε et à la limite + ε. On ne teste jamais l'égalité exacte en virgule flottante.
- Chaque exigence de sécurité (ES-xxx) a au moins un test d'injection de faute, qui provoque volontairement le danger qu'elle maîtrise.
- Les tests aléatoires et les tests de propriétés enregistrent leur graine, pour pouvoir rejouer exactement un échec.
- Les mesures de temps ne bloquent pas la CI, dont les machines ont des performances variables : elles sont faites sur la machine de référence (le MacBook) et consignées dans le rapport de vérification de chaque version. À l'inverse, la logique temporelle (délais de surveillance comme ES-005) est testée dans la CI avec une horloge simulée (paramètre use\_sim\_time de ROS 2, ou horloge passée en paramètre) : le test vérifie la logique sans dépendre de la vitesse de la machine.

**Mise en place par jalon**

| Jalon | Tests mis en place |
| --- | --- |
| J1 | pytest, CI minimale |
| J2 | launch\_testing, test système de bout en bout |
| J3 | gtest, tests aux limites, tests de propriétés, sanitizers, couverture des branches, différences finies, données de référence MoveIt |
| J4 | Injection de fautes sur le nœud RCM : démarrage, bascule, état du bras périmé, paramètres figés, butées |
| J5 | Injection de fautes sur la téléopération et la zone, scénarios rosbag |
| J6 | Vitest, Playwright |
| J7 | Mesures de temps, rapport de vérification de la v1.0.0 |

**Prévu pour la V2**

- **Tests de mutation** (Mull) : l'outil modifie volontairement le code de sécurité (par exemple `<` devient `<=`) et vérifie qu'au moins un test échoue. C'est la mesure la plus honnête de la qualité des tests.
- **Validation formalisée** : la vérification prouve que les exigences sont remplies (« a-t-on bien construit le produit ? ») ; la validation prouve que le produit sert vraiment son public (« a-t-on construit le bon produit ? »). Des personnes correspondant aux personas réalisent des tâches précises (installer, piloter, suivre un tutoriel), et les résultats sont notés. Le test d'installation par un tiers au J7 en est une première forme.

### 9.2 Matrice de traçabilité

La matrice n'est pas tenue à la main : elle est **générée automatiquement** par la CI (ENF-014), car une matrice manuelle finit toujours par diverger du code. Elle relie chaque exigence à sa **preuve de vérification**, qui dépend de sa méthode :

| Méthode | Preuve acceptée | Où elle se trouve |
| --- | --- | --- |
| T (test) | Au moins un test automatique qui **passe** | Rapports de résultats JUnit XML produits par la CI |
| I (inspection) | Une fiche d'inspection : identifiant, date, ce qui a été vérifié, résultat | `docs/quality/inspections/` |
| A (analyse) | Un rapport de mesure : valeur obtenue, machine, date | `docs/quality/measurements/` |

**Fonctionnement**

1. La liste des exigences vient de l'export Markdown du cahier des charges (`docs/quality/specification.md`) : le script y extrait les identifiants, les priorités, les méthodes, les risques liés et les jalons bloquants.
2. Chaque test déclare l'exigence qu'il vérifie dans son rapport de résultats : `RecordProperty("requirement", "EF-402")` en gtest, `record_property("requirement", "EF-402")` en pytest, une annotation équivalente dans Vitest et Playwright.
3. Un script de `tools/` croise ces trois sources et produit `docs/quality/traceability.md`.
4. Une exigence est « vérifiée » seulement si sa preuve existe et, pour un test, si ce test a passé.

**La CI échoue si :**

- une exigence Must dont le jalon bloquant est atteint n'a aucune preuve de vérification valide ;
- un test, une fiche ou un rapport cite un identifiant absent du cahier des charges (faute de frappe, exigence supprimée) ;
- une exigence de sécurité (ES-xxx) dont le jalon bloquant est atteint n'est pas vérifiée, ce qui laisserait un risque (RP-xxx) sans preuve d'efficacité de sa mesure.

**Jalon bloquant.** Chaque exigence Must a un jalon bloquant : le jalon à la fin duquel elle doit être vérifiée (tableau de la section 11). Le jalon en cours est indiqué dans le fichier `docs/quality/current-milestone`, mis à jour par la pull request qui clôt chaque jalon. Avant son jalon bloquant, une exigence sans preuve apparaît dans la matrice comme « prévue au Jx », sans bloquer la CI. La CI reste donc verte dès le J1, et chaque clôture de jalon rend bloquantes les exigences de ce jalon.

**Preuves nocturnes.** Certains tests ne tournent que la nuit (images Docker, test système, Playwright, scénarios rosbag). Le script de la pull request lit donc aussi les résultats conservés de la dernière exécution nocturne sur `main` : une exigence prouvée par un test nocturne est vérifiée si ce test a passé lors de cette exécution. Sans résultat nocturne récent (plus de 48 heures), la matrice le signale, et l'exécution nocturne en échec est traitée en priorité.

Les exigences Should et Could figurent dans la matrice, mais leur absence de preuve ne bloque pas la CI.

**Une photo par version.** À chaque version publiée (v0.1.0, v1.0.0...), la matrice est figée dans le rapport de vérification de `docs/quality/`. On peut ainsi prouver ce qui était vérifié à cette date.

Exemple de lignes produites (valeurs fictives, pour illustrer) :

| Exigence | Priorité | Méthode | Risques | Preuves | Statut |
| --- | --- | --- | --- | --- | --- |
| EF-402 | Must | T | RP-003 | 4 tests passés (gtest, propriétés) | Vérifiée |
| ES-005 | Must | T | RP-005 | 2 tests passés (horloge simulée) | Vérifiée |
| ES-001 | Must | I | RP-001 | Fiche d'inspection | Vérifiée |
| ENF-004 | Must | A | RP-005 | Rapport de mesure sur le MacBook M3 Pro | Vérifiée |
| EF-206 | Could | T | — | Aucune | Non vérifiée (non bloquant) |

Les tickets restent hors de la matrice générée, car ce lien serait fragile à automatiser. Chaque ticket et chaque pull request citent les identifiants couverts (par exemple « Couvre EF-202, ES-002 »), grâce au modèle de pull request, sans bloquer la CI.

### 9.3 Conventions Git et CI

**Protection de `main`.** Elle passe par les *rulesets* de GitHub, **sans exception pour l'administrateur** : seul sur le dépôt, j'en suis propriétaire, et sans cette précaution je pourrais contourner mes propres règles. Règles actives :

- fusion uniquement par pull request ;
- vérification `ci-ok` obligatoire (voir ci-dessous) ;
- branche à jour avec `main` avant la fusion ;
- historique linéaire ;
- commits signés ;
- interdiction de réécrire l'historique de `main` (*force push*) et de la supprimer.

Tant que je suis seul, la CI obligatoire tient lieu de relecture (GitHub ne permet pas d'approuver sa propre pull request) ; les relectures obligatoires et `CODEOWNERS` arriveront avec le premier contributeur.

**Branches, pull requests et commits.**

- **Une branche par ticket**, préfixée par son type : `feat/12-rcm-command`, `fix/20-zone-radius`, `docs/`, `test/`, `chore/`.
- **Pull request même en travaillant seul**, avec le modèle : description, exigences couvertes, risques touchés, tests ajoutés.
- **Titres de pull request au format Conventional Commits** (`feat(rcm): ...`, `test(safety): ...`, `docs(tutorial): ...`), vérifiés par la CI (action semantic-pull-request) : avec la fusion par squash, c'est ce titre qui devient le commit dans `main`.
- **Historique linéaire** : fusion par squash ; une pull request égale un commit lisible dans `main`.
- **Commits signés** (clé SSH ou GPG) sur les branches. Avec la fusion par squash depuis GitHub, le commit final dans `main` est signé par GitHub, pas par moi : c'est attendu.
- **pre-commit** : formatage et vérifications lancés avant chaque commit, sur ma machine.

**La CI à deux niveaux.** Une compilation complète de ROS 2 avec tous les tests est longue ; tout ne tourne donc pas à chaque pull request.

| Quand | Ce qui est vérifié |
| --- | --- |
| À chaque pull request (`ci.yml`) | Titre de la PR ; formatage et analyse statique ; `colcon build` ; tests unitaires et d'intégration (gtest, pytest, launch\_testing) ; tests du front (Vitest) ; sanitizers sur les bibliothèques sans ROS (ENF-016) ; seuils de couverture (ENF-010) ; matrice de traçabilité (ENF-014) |
| Chaque nuit et avant chaque version (`nightly.yml`) | Construction des images Docker sur des machines ARM64 natives (gratuites pour les dépôts publics) et x86\_64, sans émulation ; test système avec Docker Compose ; tests Playwright ; scénarios rosbag ; résultats conservés et lus par la matrice des pull requests |

- **Un seul job obligatoire, `ci-ok`**, qui attend tous les autres. C'est le seul déclaré dans le ruleset : renommer ou ajouter un job ne casse pas la protection, et un job lancé seulement quand certains fichiers changent ne bloque pas la fusion.
- **Cache** : `ccache` pour le C++ et cache des couches Docker, pour ne pas tout recompiler à chaque PR.
- **Workflows sécurisés** : actions figées par empreinte de commit, permissions minimales déclarées dans chaque workflow.

**Publication d'une version.**

- **release-please** lit les titres de PR fusionnées, prépare le CHANGELOG et propose le numéro de version suivant (SemVer : `v0.1.0`, ...).
- La création de l'étiquette signée déclenche `release.yml` : construction des images, publication sur GitHub Container Registry, génération du SBOM, **attestation de provenance** (preuve signée que l'image vient de la CI), rapport de vérification et photo de la matrice dans `docs/quality/`.
- `docs.yml` publie le site de tutoriels à chaque fusion dans `main`.

**Sécurité et dépendances.**

- Dependabot, détection des secrets et CodeQL (`codeql.yml`), gratuits pour un dépôt public.
- Dependabot met à jour les actions GitHub, l'image Docker de base, npm et Python, mais pas `dependencies.repos` : ce fichier est vérifié à la main à chaque jalon (ou avec Renovate plus tard).
- Les scénarios rosbag restent courts (quelques mégaoctets) : ce sont des fichiers binaires, et la formule gratuite de Git LFS est limitée en volume.

### 9.4 Définition de « terminé » pour un ticket

- [ ] Le code est fusionné dans `main` par une pull request dont la CI passe
- [ ] Les exigences couvertes ont une preuve de vérification (test, fiche d'inspection ou rapport de mesure)
- [ ] Les tests portent l'identifiant de leur exigence et la matrice générée ne signale aucun manque
- [ ] Le tutoriel ou la documentation de l'étape est écrit ; un ADR est rédigé si une décision d'architecture a été prise
- [ ] Je sais expliquer le choix technique en deux minutes

### 9.5 Usage de l'IA agentique

L'IA (Claude, y compris Claude Code en mode agent) sert d'accélérateur et de tuteur. Ses règles d'usage préservent deux choses : la vérification indépendante du code de sécurité, et mon apprentissage.

| Partie | Qui écrit | Mon rôle |
| --- | --- | --- |
| Outillage : CI, Dockerfile, configuration, mise en forme de la documentation | L'IA | Relire, comprendre, laisser la CI valider |
| Nœuds ROS 2, console web, scripts, `trocarlab_safety` (sauf les deux modules écrits par moi, ci-dessous), reste de `trocarlab_rcm_core` | L'IA, à partir des exigences et de mes cas de test | Relire, comprendre, puis expliquer chaque module dans son tutoriel sans regarder le code |
| Cinématique du Panda (pose de la pointe, jacobienne) | Moi, avec l'IA comme tuteur (explications, relecture) | Écrire le code et dériver les formules à la main |
| Spécification des cas de test de sécurité (`docs/quality/test-cases.md`) | Moi, avec l'IA comme tuteur | Rédiger les cas avant le code, au début de chaque jalon qui contient une exigence de sécurité vérifiée par test (du J2 au J6) ; vérifier que le code des tests leur correspond |
| Dans trocarlab\_safety : le contrôle tige/sphère (EF-402) et la machine d'états prêt / faute / arrêt d'urgence (ES-007, ES-012, ES-013) | Moi, avec l'IA comme tuteur (explications, relecture) | Écrire le code : ce sont les modules de sécurité les plus intéressants à défendre en entretien, et ils me font pratiquer le C++ au-delà de la cinématique |

**Règles**

- **Vérification indépendante** : pour une exigence de sécurité, c'est moi qui définis ce qui est correct, par mes cas de test (situation de départ, action, résultat attendu, identifiant relié à l'exigence). L'IA ne définit jamais seule à la fois le code et ce qui le valide.
- **Aucune confiance aveugle** : tout code produit avec l'IA passe par une pull request, la CI et ma relecture, comme n'importe quel code.
- **Compréhension obligatoire** : un module n'est terminé que si je sais l'expliquer (section 9.4) et si son tutoriel est écrit sans regarder le code.
- **Traçabilité** : le modèle de pull request indique si l'IA a été utilisée et pour quoi faire ; les commits concernés portent une mention Co-Authored-By.
- **Provenance** : aucun passage dont je ne comprends pas l'origine n'est repris ; même règle que pour PolygonMeshVirtualFixture (RJ-005).
- **Sécurité de l'agent** : l'agent travaille sur une branche, jamais sur `main` (protégée par les rulesets) ; il n'a accès à aucun secret ; aucune action irréversible (publication d'une version, étiquette, suppression) sans ma validation.
- **`CLAUDE.md`** à la racine du dépôt donne à l'agent le contexte du projet, ses conventions et ces règles. **`AI_POLICY.md`** publie cette politique pour les lecteurs et les contributeurs.

## 10. Analyse de risques

Aucun risque produit ne reste élevé après ses mesures. Le risque projet principal est le manque de temps : il est maîtrisé par une V1 réduite et des jalons courts.

La méthode s'inspire de l'ISO 14971 : on identifie le danger, on cote sa **gravité** (G) et sa **probabilité** (P) avant mesure, on définit une mesure de maîtrise, puis on recote le risque résiduel. Comme rien ne touche un patient, la gravité est évaluée « comme si » le comportement était transposé à un vrai robot : c'est là que se trouve la valeur pédagogique.

### 10.1 Échelles

| Note | Gravité (si transposé à un vrai robot) | Probabilité |
| --- | --- | --- |
| 1 | Négligeable : gêne, aucune lésion | Rare |
| 2 | Mineure : lésion superficielle réversible | Possible |
| 3 | Grave : lésion d'un organe, reprise chirurgicale | Probable |
| 4 | Critique : hémorragie majeure, menace vitale | Très probable |

Criticité = G × P. **1 à 3** acceptable ; **4 à 6** à réduire si possible ; **8 à 16** inacceptable sans mesure.

### 10.2 Risques produit (RP-xxx)

| ID | Danger | Situation dangereuse | G | P | Avant | Mesure | P après (cible) | Résiduel |
| --- | --- | --- | --- | --- | --- | --- | --- | --- |
| RP-001 | Usage hors du cadre pédagogique | Quelqu'un adapte le code pour piloter un robot réel au contact d'un patient | 4 | 2 | 8 | ES-001 : avertissement partout, aucun pilote matériel réel, licence sans garantie | 1 | 4 |
| RP-002 | Dérive du point de pivot | L'instrument s'écarte du trocart et déchire la paroi abdominale | 3 | 3 | 9 | ES-002 : arrêt si écart strictement supérieur à 2 mm ; tests sur des milliers de consignes (ENF-001) | 1 | 3 |
| RP-003 | Franchissement de la zone interdite | La pointe entre dans un organe ou un vaisseau, ou la tige le traverse alors que la pointe reste dehors | 4 | 3 | 12 | ES-003 : contrôle de toute la tige sur la consigne, avant envoi ; ES-008 : marge supérieure au pas maximal ; tests aux limites | 1 | 4 |
| RP-004 | Mouvement trop rapide | Un geste brusque lèse un tissu | 3 | 2 | 6 | ES-004 : vitesses limitées ; EF-303 : réduction d'échelle | 1 | 3 |
| RP-005 | Perte de liaison avec la console | Le bras continue sur sa dernière consigne | 3 | 3 | 9 | ES-005 : arrêt après 500 ms sans signal ; ES-007 : arrêt d'urgence prioritaire ; EF-302 : arrêt à la perte du focus | 1 | 3 |
| RP-006 | Consigne invalide | Une valeur aberrante provoque un saut articulaire | 3 | 2 | 6 | ES-006 : validation des entrées | 1 | 3 |
| RP-007 | Configuration incohérente | Trocart inatteignable ou zone posée sur le trocart | 2 | 2 | 4 | ES-008 : vérification au démarrage | 1 | 2 |
| RP-008 | Accès non autorisé | Une autre machine du réseau envoie des commandes | 2 | 2 | 4 | ES-009 : rosbridge limité à `localhost` | 1 | 2 |
| RP-009 | Singularité du bras | Près d'une position où le bras perd un degré de liberté (bras tendu), un petit geste demande des vitesses articulaires énormes : mouvement brusque | 3 | 3 | 9 | ES-010 : jacobienne amortie ; ES-004 : vitesses limitées | 1 | 3 |
| RP-010 | Butée articulaire | Le bras ne peut plus suivre la consigne sans quitter le trocart | 3 | 2 | 6 | ES-011 : arrêt et état « faute » ; EF-206 (Could) : axe de réserve pour s'éloigner des butées | 1 | 3 |
| RP-011 | Mouvement avant que le système soit prêt | La téléopération agit pendant le placement par MoveIt ou avant les vérifications : l'instrument bouge hors du trocart | 3 | 3 | 9 | ES-012 : démarrage à l'arrêt, téléopération activée en dernier | 1 | 3 |
| RP-012 | Reprise après une faute alors que le danger est toujours là | L'utilisateur relance le mouvement sans que la cause de la faute ait disparu | 3 | 3 | 9 | ES-013 : réarmement explicite : retrait en ligne droite, puis séquence de démarrage complète ; ES-017 : cause affichée | 1 | 3 |
| RP-013 | Calcul sur une position périmée | L'état du bras n'est plus mis à jour ; les commandes sont calculées à partir d'une position fausse | 3 | 2 | 6 | ES-014 : arrêt et faute si l'état n'est plus mis à jour | 1 | 3 |
| RP-014 | Réglage de sécurité modifié en fonctionnement | La marge est réduite ou la vitesse maximale augmentée sans nouvelle vérification | 4 | 2 | 8 | ES-015 : paramètres de sécurité figés après le démarrage ; ES-018 : tentative journalisée | 1 | 4 |
| RP-015 | Enfoncement excessif | La pointe va trop profond et touche un organe situé hors de la zone interdite | 3 | 3 | 9 | ES-016 : enfoncement maximal ; tests aux limites | 1 | 3 |
| RP-016 | Événement de sécurité non tracé | Un incident ne peut être ni analysé ni reproduit | 2 | 3 | 6 | ES-018 : journal horodaté des événements de sécurité | 1 | 2 |
| RP-017 | Défaillance du code de sécurité lui-même | Un bug dans `trocarlab_safety` désactive plusieurs protections à la fois | 4 | 2 | 8 | 100 % des branches couvertes (ENF-010), tests de propriétés, sanitizers (ENF-016), injection de fautes ; surveillant indépendant en V2 | 1 | 4 |
| RP-018 | Erreur d'unité dans la configuration | Une valeur plausible dans la mauvaise unité (3 m au lieu de 3 cm) place la zone ou la marge au mauvais endroit | 4 | 2 | 8 | ES-019 : unité dans le nom de chaque paramètre, plages de valeurs vérifiées au démarrage | 1 | 4 |
| RP-019 | Confusion des commandes | Par l'effet de levier, l'utilisateur envoie la pointe dans la mauvaise direction, éventuellement vers la zone | 3 | 3 | 9 | ES-020 : commandes exprimées du point de vue de la pointe, axes affichés ; ES-003 : la zone reste protégée | 1 | 3 |
| RP-020 | Anomalie d'un composant tiers | Un bug connu de ROS 2, de MoveIt ou d'Eigen fausse un calcul ou un échange | 3 | 2 | 6 | ES-021 : revue des anomalies connues de la liste SOUP ; versions figées (ENF-013) ; tests | 1 | 3 |
| RP-021 | Mouvement non contraint avec l'instrument inséré | MoveIt, qui ne connaît ni le RCM ni la zone, déplace le bras alors que l'instrument est dans l'abdomen : il arrache le trocart ou fait traverser la zone par la tige | 4 | 3 | 12 | EF-104 : MoveIt ne bouge le bras qu'instrument sorti ; ES-012 et ES-013 : insertion et retrait en ligne droite par le nœud RCM, zone vérifiée ; EF-107 : zone déclarée dans la scène de MoveIt | 1 | 4 |

La probabilité après mesure est une **cible** : elle n'est acquise qu'une fois la mesure vérifiée (tests passés, preuve dans la matrice de traçabilité, section 9.2). Tant que ce n'est pas le cas, le risque garde sa valeur d'avant mesure.

### 10.3 Évaluation du risque résiduel global

Six risques restent à 4, dans la zone « à réduire si possible » : RP-001, RP-003, RP-014, RP-017, RP-018 et RP-021. Leur gravité ne peut pas baisser, car elle tient à la nature du danger (une lésion grave si le comportement était transposé à un vrai robot). Seule la probabilité diminue, et elle est déjà au plus bas de l'échelle.

Le risque résiduel global est jugé acceptable, pour trois raisons :

- TrocarLab ne pilote aucun robot réel et n'a aucun contact avec un patient : les gravités sont évaluées « comme si », pour leur valeur pédagogique ;
- chaque risque à 4 est maîtrisé par des mesures de conception vérifiées par des tests, et pas seulement par un avertissement. Pour RP-001, la mesure de conception est l'absence de tout pilote pour un robot réel, complétée par l'avertissement ;
- le bénéfice est réel : un outil gratuit et accessible pour apprendre la robotique chirurgicale.

Cette évaluation est revue à chaque version publiée.

### 10.4 Risques projet (RJ-xxx)

| ID | Risque | Conséquence | Probabilité | Mesure |
| --- | --- | --- | --- | --- |
| RJ-001 | Manque de temps (recherche d'emploi prioritaire) | V1 jamais terminée | Élevée | V1 réduite ; jalons courts, chacun montrable seul ; règle de réduction du contenu en cas de dépassement (section 11) |
| RJ-002 | Courbe d'apprentissage C++, ROS 2 et cinématique | Blocage long sur le RCM | Élevée | Commencer en Python ; prototyper le calcul RCM en Python ; RCM réparti sur deux jalons (J3 calculs, J4 nœud) ; bibliothèque C++ sans ROS, puis nœud simple, plugin ros2\_control en dernier (EF-208, Should) ; IA comme tuteur (section 9.5) ; s'appuyer sur *Modern Robotics* |
| RJ-003 | Performances de Docker sur Mac ARM | Simulation saccadée, H1 invalidée | Moyenne | Mesurer dès le J1 ; images ARM64 natives ; RViz servi dans le navigateur par noVNC dès le départ (EF-005) |
| RJ-004 | Licence du modèle de bras incompatible | Redistribution impossible | Clos | Licence vérifiée le 3 novembre 2026 : Apache 2.0, maillages compris. Version de franka\_description figée par commit dans `dependencies.repos` |
| RJ-005 | Copie involontaire de code sans licence | Problème juridique, perte de crédibilité | Faible | Règle : PolygonMeshVirtualFixture est lu, jamais copié ; aucun code proposé par l'IA n'est repris sans en comprendre l'origine ; citer toutes les sources |
| RJ-006 | Projet trop ambitieux perçu comme inachevé | Effet négatif en entretien | Moyenne | Dépôt public dès le J1, version v0.1.0 à la fin du J2 ; chaque jalon produit une démo et un tutoriel montrables |
| RJ-007 | Sur-ingénierie : plus de temps passé sur la documentation et l'outillage que sur le code | Retard, perte de motivation | Élevée | Mise en place progressive par jalon (sections 8.2 et 9.1) ; cahier des charges figé dès ma décision de démarrer, nouvelles décisions ensuite dans des ADR ; règle de réduction du contenu |
| RJ-008 | Apprentissage superficiel dû à l'IA : un projet qui fonctionne, mais que je ne sais pas expliquer ni réécrire | Échec en entretien technique | Élevée | Cinématique, contrôle tige/sphère, machine d'états et cas de test de sécurité écrits par moi ; tutoriel de chaque module rédigé sans regarder le code ; critère « je sais expliquer le choix en deux minutes » (sections 9.4 et 9.5) |

### 10.5 Méthode de revue des risques

Le registre est revu :

- à la fin de chaque jalon ;
- à chaque ajout ou modification d'une exigence de sécurité ;
- dès qu'une pull request touche un risque (le modèle de pull request le demande) ;
- à chaque version publiée, avec l'évaluation du risque résiduel global (10.3).

## 11. Planning et jalons

À raison de 1 à 2 h par jour (environ 10 h par semaine), la V1 demande 26 à 35 semaines de travail, soit environ 30 à 40 semaines avec la marge, et une publication entre juin et août 2027 si le travail commence en novembre 2026.

&#91;embedded content: feuille de route V1 · 7 jalons\]

Chaque jalon se termine par une démo et un tutoriel : même si le projet s'arrête en cours de route, ce qui est fait reste montrable (RJ-006). Le RCM, la partie la plus risquée, est réparti sur deux jalons : le J3 pour les calculs en C++ (après un prototype Python), le J4 pour le nœud ROS 2 et la sécurité de démarrage (RJ-002).

**Montrer tôt.** Le dépôt est public dès le J1, et une version v0.1.0 est publiée à la fin du J2, quand le bras amène l'instrument à l'entrée du trocart. Il y aura ainsi quelque chose à présenter en entretien d'ici 2 à 3 mois, pas dans 7.

**Jalon bloquant de chaque exigence Must.** Ce tableau indique le jalon à la fin duquel chaque exigence Must doit être vérifiée ; le script de traçabilité le lit (section 9.2). Une exigence construite sur plusieurs jalons (par exemple côté terminal puis côté console) est rattachée au jalon où elle est complète. Les exigences Should et Could n'ont pas de jalon bloquant.

| Jalon | Exigences Must qui deviennent bloquantes |
| --- | --- |
| J1 | EF-601, EF-603, ENF-009, ENF-011, ENF-012, ES-021 |
| J2 | EF-002, EF-003, EF-005, EF-101 à EF-105, ENF-008, ENF-013, ES-009 |
| J3 | EF-201 à EF-203, EF-209, ENF-010, ENF-014, ENF-016, ES-010 |
| J4 | EF-106, EF-204, EF-205, EF-207, ENF-001, ENF-002, ES-002, ES-011, ES-012, ES-014 à ES-016, ES-019 |
| J5 | EF-107, EF-301, EF-304, EF-401 à EF-403, ENF-004, ES-003 à ES-008 (ES-008 vérifie la marge de la zone, qui n'existe qu'au J5), ES-013 |
| J6 | EF-001, EF-302, EF-501 à EF-505, ES-001 (avertissement dans le README dès le J1, complet avec la console), ES-020 |
| J7 | ENF-005, ENF-007, ENF-015 |

Un écart par rapport à l'ordre prévu dans le contexte : une **CI minimale dès le J1** (formatage et `colcon build`) plutôt qu'en fin de projet. Elle coûte une soirée, protège `main` dès le début et montre la démarche aux recruteurs.

Depuis la v1.5, cette estimation intègre les ajouts des versions 1.1 à 1.4 : l'ancien J3, trop chargé, est coupé en deux jalons, le J1 est rallongé, et une marge d'environ 15 % s'ajoute aux durées par jalon. Elle sera recalée à la fin du J1.

**Règle en cas de dépassement.** Si un jalon dépasse nettement son estimation, on réduit son contenu plutôt que d'allonger le délai : les exigences Should et Could passent au jalon suivant ou en V2, les exigences Must restent. Ces durées sont des estimations de départ ; elles seront recalées à la fin de chaque jalon, en notant l'écart entre l'estimé et le réel.

## 12. Licences et propriété intellectuelle

TrocarLab est publié sous licence **Apache 2.0**, sans dépôt de brevet. Toute dépendance doit avoir une licence compatible, vérifiée avant son ajout.

### 12.1 Pourquoi Apache 2.0

- Licence permissive : entreprises, laboratoires et étudiants peuvent réutiliser le code, ce qui maximise sa diffusion.
- Clause de non-garantie explicite, qui renforce l'avertissement d'usage non clinique (RP-001).
- Licence la plus courante dans l'écosystème ROS 2, ce qui simplifie les contributions.

### 12.2 Dépendances et licences

Toutes les licences retenues sont compatibles avec la publication de TrocarLab sous Apache 2.0, à condition de garder leurs mentions dans le fichier `NOTICE`. Sauf mention contraire, chaque licence a été lue le 4 novembre 2026 dans le fichier de licence du dépôt officiel, sur sa version la plus récente. Elle sera revérifiée pour la version exacte qui sera figée, lors de la revue de la liste SOUP (ES-021).

| Composant | Rôle | Licence | Remarque |
| --- | --- | --- | --- |
| ROS 2 (bibliothèques de base, vérifié sur rclcpp) | Middleware | Apache 2.0 | — |
| ros2\_control | Contrôle du bras | Apache 2.0 | — |
| MoveIt 2 | Placement initial | BSD 3 clauses | — |
| RViz | Visualisation | BSD 3 clauses (variante « Clear BSD ») | — |
| rosbridge\_suite | Pont vers le navigateur | BSD 3 clauses | Absent de la version précédente du tableau |
| Eigen | Calcul matriciel | MPL 2.0 pour l'essentiel ; quelques fichiers tiers sous BSD ou LGPL | Lue sur le miroir officiel de Google (le dépôt GitLab était inaccessible). Compiler avec l'option `EIGEN_MPL2_ONLY`, qui fait échouer la compilation si du code LGPL est inclus |
| Description du Franka Panda (URDF et maillages) | Modèle du bras | Apache 2.0 | Vérifiée le 3 novembre 2026 (LICENSE, NOTICE, package.xml, README), maillages compris ; le Panda y figure sous le nom fer |
| noVNC | RViz dans le navigateur | MPL 2.0 (code JavaScript), BSD 2 clauses (HTML et CSS), SIL OFL 1.1 (police), CC BY-SA 3.0 (images) | Utilisé sans modification ; si un fichier est modifié, sa modification est publiée sous la même licence |
| Three.js | Vue 3D de la console | MIT | — |
| roslibjs | Client ROS de la console | BSD 3 clauses | — |
| Vite | Outillage de la console | MIT | — |
| GoogleTest (gtest) | Tests C++ | BSD 3 clauses | — |
| RapidCheck | Tests de propriétés C++ | BSD 2 clauses | Sans paquet Ubuntu : figé par commit dans `dependencies.repos` |
| pytest | Tests Python | MIT | — |
| Hypothesis | Tests de propriétés Python | MPL 2.0 | Figé dans le verrou Python |
| Vitest | Tests unitaires de la console | MIT | — |
| Playwright | Tests de bout en bout de la console | Apache 2.0 | Figé dans `package-lock.json` |
| MkDocs | Site de tutoriels | BSD 2 clauses | — |
| Material for MkDocs | Thème du site | MIT | — |
| Pinocchio | Cinématique, solution de repli | BSD 2 clauses | Seulement si la cinématique maison ne suffit pas |
| KDL | Cinématique | LGPL 2.1 | Non retenu : objectif pédagogique, bibliothèque vieillissante ; LGPL compatible en usage séparé |
| Modèle Universal Robots | Bras alternatif | BSD 3 clauses pour le code ; maillages (UR20 au moins) sous les conditions d'utilisation d'Universal Robots, non open source | Écarté : maillages non redistribuables librement |
| Image Docker de base (Ubuntu et paquets ROS) | Système des conteneurs | Licences multiples | Inventoriées automatiquement par le SBOM à chaque version (ENF-015) |
| SVGO | Normalisation des icônes | MIT (à confirmer) | Outil de construction, non livré dans l'image |
| Jeu d'icônes de départ (Lucide, Tabler ou autre) | Icônes de la console | À choisir | Licence à vérifier avant usage ; icônes ajoutées une à une dans console/icons/, avec leur mention dans NOTICE |

Les outils de test font partie de la liste SOUP au même titre que les bibliothèques : ils ne sont pas livrés avec le robot, mais ils servent à prouver sa sécurité.

Le fichier `NOTICE` du dépôt listera chaque dépendance et sa licence ; la liste SOUP (docs/quality/) précise en plus sa version figée et son rôle.

### 12.3 Règles

- **PolygonMeshVirtualFixture** n'a pas de licence : son code peut être lu pour comprendre l'approche, jamais copié ni adapté ligne à ligne. L'article est cité.
- Les travaux de la section 2.2 sont cités dans le README, avec liens et références.
- Aucun nom ni logo de robot chirurgical commercial n'est utilisé dans le projet.
- Le nom TrocarLab a été vérifié disponible, notamment sur l'INPI et l'EUIPO.

## 13. Annexes

### 13.1 Points ouverts

- [ ] franka\_description, publié seulement pour Humble dans l'index ROS, se compile-t-il depuis les sources sous Jazzy ? À vérifier au J2.
- [ ] Les cibles chiffrées des ENF (fréquence, latence, mémoire) tiennent-elles sur le MacBook ? À mesurer au J1.
- [ ] La console web reste-t-elle en TypeScript « pur » (Vite) ou utilise-t-elle un framework (Qwik, React) ?
- [ ] Quel jeu d'icônes de départ (Lucide, Tabler ou autre), et sa licence est-elle compatible ? À trancher au plus tard au J6.

### 13.2 Glossaire

| Terme | Définition |
| --- | --- |
| Laparoscopie (cœlioscopie) | Chirurgie de l'abdomen par de petites incisions, avec une caméra et des instruments longs |
| Trocart | Tube posé dans l'incision, par lequel passe l'instrument |
| RCM (*Remote Center of Motion*) | Point fixe autour duquel l'instrument pivote : le trocart |
| DDL | Degré de liberté : une façon indépendante de bouger |
| *Virtual fixture* | Contrainte logicielle qui interdit ou guide un mouvement (ici : zone interdite) |
| Téléopération | Pilotage à distance d'un robot par un opérateur humain |
| Homme mort | Dispositif qui arrête le mouvement dès que l'opérateur relâche la commande |
| ROS 2 | *Robot Operating System* : ensemble de bibliothèques pour faire communiquer les programmes d'un robot |
| Nœud, topic | Un nœud est un programme ROS ; un topic est un canal nommé sur lequel les nœuds publient et lisent des messages |
| ros2\_control | Cadre ROS 2 qui relie les contrôleurs au matériel (réel ou simulé) |
| *Mock hardware* | Faux matériel de ros2\_control qui recopie les commandes comme si le robot les exécutait parfaitement |
| MoveIt | Bibliothèque de planification de mouvements pour bras robotiques |
| URDF | Fichier XML qui décrit la géométrie et les articulations d'un robot |
| rosbridge | Pont qui expose les topics ROS au navigateur par WebSocket |
| Cinématique inverse | Calcul des angles articulaires qui amènent l'outil à une position voulue |
| MoSCoW | Priorisation : Must (indispensable), Should (important), Could (souhaitable), Won't (pas maintenant) |

### 13.3 Références normatives (version simplifiée, sans prétention de conformité)

- **ISO 14971** — Dispositifs médicaux, application de la gestion des risques : inspire la section 10.
- **IEC 62304** — Logiciels de dispositifs médicaux, processus du cycle de vie : inspire la traçabilité de la section 9 et la liste SOUP des composants tiers.
- **IEC 80601-2-77** — Exigences de sécurité pour les équipements chirurgicaux assistés par robot : lecture recommandée pour enrichir les exigences de sécurité en V2.

* **IEC 62366-1** — Ingénierie de l'aptitude à l'utilisation des dispositifs médicaux : inspire le traitement des erreurs d'utilisation (RP-019, ES-020).

### 13.4 Ressources d'apprentissage

- *Modern Robotics*, K. Lynch et F. Park (PDF gratuit) : cinématique, jacobienne, RCM
- learncpp.com : C++ moderne
- Tutoriel officiel de Python
- Tutoriels officiels de ROS 2, ros2\_control et MoveIt 2

### 13.5 Travaux cités

- Plateforme de recherche open source pour la chirurgie laparoscopique autonome, arXiv:2603.08490 (2026), surgical-robot-testbed.github.io
- dVRK (da Vinci Research Kit)
- SurRoL
- AMBF (Asynchronous Multi-Body Framework)
- ORBIT-Surgical
- PolygonMeshVirtualFixture, IROS 2020

Les références complètes (auteurs, liens) seront ajoutées dans le README lors de la publication.
