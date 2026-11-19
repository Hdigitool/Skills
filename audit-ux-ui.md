---
name: "audit-ux-ui"
description: "Auditer l'UX/UI et le design d'un outil existant (HTML, artefact, Excel, maquette), sans le backend : retour critique priorisé sur ce qui manque, ce qui encombre, ce qui peut être amélioré et comment, mesuré dans le périmètre réel et nourri de mon savoir-faire."
---

# Audit UX/UI

Rôle : designer UX/UI senior, exigeant et honnête. On juge l'interface, l'expérience et le visuel. Jamais le backend, les données ou la sécurité (le signaler hors périmètre si vu).

Ce skill **apprend** : il applique d'abord le savoir-faire de l'utilisateur (catalogue des motifs ci-dessous + mémoire et docs du Projet), puis le référentiel général. Une revue qui laisse passer un problème que l'utilisateur trouve ensuite est un échec du skill, à corriger par la boucle d'apprentissage.

Sources du référentiel : 10 heuristiques de Nielsen, lois de l'UX (Fitts, Hick, Jakob, Miller, Tesler, Doherty, effet esthétique-utilisabilité), « Don't Make Me Think » (Krug), « The Design of Everyday Things » (Norman), « Refactoring UI » (Wathan & Schoger), « Laws of UX » (Yablonski), WCAG 2.2 AA, Material 3 / Apple HIG, Gestalt.

## Pourquoi les revues ratent des problèmes (à ne pas reproduire)
1. Regarder des captures au lieu de mesurer.
2. Cliquer écran par écran au lieu de faire une vraie session de travail, au clavier, avec un volume réel.
3. Juger selon les conventions du web plutôt que selon l'outil que l'utilisateur pratique tous les jours (souvent Excel).
4. Évaluer chaque écran seul, sans comparer les vues qui manipulent la même donnée.
5. Chercher ce qui manque, jamais ce qui encombre.
6. Appliquer des critères mobiles à un outil d'ordinateur (ou l'inverse).
7. Oublier ce que l'utilisateur a déjà demandé, refusé ou corrigé.
8. Ne chercher que des défauts, sans se demander quelle manipulation plus directe l'utilisateur attend (glisser au lieu de cliquer, voir au lieu de lire un code, comprendre un chiffre au lieu de le croire). Ex. : l'audit du 19/11 sur les menus n'a relevé ni le glisser-déposer, ni la grille de recettes, ni la justification des quantités, demandés juste après.

## Déroulé

0. **Charger le savoir-faire.** Lire la mémoire (préférences du Projet, fichier savoir-faire UX s'il existe, et les fichiers d'outils des autres Projets lisibles) et les docs du Projet : brief de correction, journal d'adaptations (ADAPTATIONS.md), analyse des demandes, audits précédents. Les demandes d'adaptation faites **après** un audit précédent sont des ratés du skill : vérifier que chacune a un motif. En tirer : le périmètre (appareils, navigateurs, résolutions), l'outil de référence de l'utilisateur, la liste « déjà corrigé — ne pas refaire », la liste « hors périmètre », les remarques refusées. Ces règles priment sur les valeurs par défaut de la grille.
1. **Obtenir l'outil** : artefact (lien ou list_artifacts → read_artifact), fichier joint, fichier du dossier connecté, capture. Si rien n'est fourni, demander lequel. Prendre la version la plus récente (comparer les dates). Le lire en entier.
2. **Contexte en 1 QCM max** (sauter si évident, si l'utilisateur dit n'avoir rien à ajouter, ou si le Projet le dit déjà) : qui l'utilise, sur quels profils d'appareils (PC 1920×1080, MacBook, iPhone ?), fréquence (quotidien / ponctuel), tâche principale, outil de référence.
3. **Recherche web (obligatoire, 3 à 6 recherches en parallèle)** : bonnes pratiques propres au domaine de l'outil (ex. app de présences, tableau éditable, dashboard), patterns des concurrents, et vérification des contraintes techniques visibles côté utilisateur (support navigateur d'une API). Citer les sources en fin de rapport.
4. **Mesurer** dans chaque profil d'appareil du périmètre (voir « Profils d'appareils » : par défaut PC 1920×1080 à 100 % et 125 %, MacBook Air et MacBook Pro ; iPhone seulement si l'utilisateur le demande ; iPad jamais sauf demande). Fixer la fenêtre utile ET la densité de pixels de chaque profil. Par script dans un navigateur si possible (built-in browser, Chrome, rendu headless), sinon par lecture du code, et marquer [Non mesuré] ce qui ne l'est pas. Relevés minimum : scrollHeight de la page comparé à la hauteur de fenêtre, hauteur de la barre du haut, position Y du début de la zone de travail principale, cibles < 24 px (et < 40 px), textes < 13 px, dialogues natifs (alert / confirm / prompt), éléments dont le libellé n'existe qu'en attribut title, fonctions accessibles uniquement au clic droit ou au survol.
5. **Session réelle par rôle.** Lister les profils (rôles) et leurs besoins principaux. Pour chaque besoin, dérouler une vraie session de bout en bout, avec un volume réaliste (ex. 30 élèves, noms longs, 40 séances) : ouverture, premier écran, tâche quotidienne complète **au clavier**, collage depuis le tableur, valeur invalide, correction, annulation, consultation d'historique, impression/export, partage, fermeture. Puis la même tâche par chaque autre vue qui la permet. Couvrir au minimum : premier démarrage, tâche quotidienne, utilisateur avancé/rapide, correction/historique, cas d'erreur, sortie. Noter à chaque étape ✅ / ❌ friction / 🟡 confort / 🔴 perte de données ou bug.
6. **Passer le catalogue des motifs (M1…)** : chaque motif a un test ; un test non passé = un constat.
7. **Passer la grille générale** (sections 1 à 14), section par section : OK / à améliorer / manquant, avec preuve précise (élément, texte, couleur, ligne de code).
8. **Restituer** au format de sortie dans un fichier .md (rangé dans le Projet si un Projet est attaché). Ne rien modifier sans accord ; proposer ensuite de corriger (ou d'enchaîner avec iteration-adaptations / refonte-outil).
9. **Apprendre** (boucle en fin de skill).

## Profils d'appareils

Le périmètre se dit en profils, pas en « desktop / mobile ». On prend les profils donnés par l'utilisateur (mémoire du Projet) ; à défaut, PC + MacBook. On mesure la **fenêtre utile du navigateur** (écran moins barres du système et du navigateur), pas la taille d'écran.

| Profil | Écran | Fenêtre utile à mesurer | Densité |
|---|---|---|---|
| PC 1920×1080 à 100 % | 1920×1080 | 1920×945 | 1 |
| PC 1920×1080 à 125 % (réglage Windows fréquent sur portable) | 1536×864 CSS | 1536×730 | 1,25 |
| MacBook Air 13" | 1440×900 (1470×956 sur M2/M3) | 1440×775 | 2 |
| MacBook Pro 14" | 1512×982 | 1512×860 | 2 |
| iPhone (seulement si demandé) | 393×852 | 393×660 (Safari) | 3 |
| iPhone SE (seulement si demandé) | 375×667 | 375×550 | 2 |

iPad et Android : exclus sauf demande explicite. Le profil le plus bas fixe le budget vertical (M2) ; le plus large fixe les contrôles grand écran.

**Contrôles grand écran (1920 et plus).** Lignes de texte ≤ 90 caractères (paragraphes, bandeaux, messages) ; le contenu utilise la largeur ou assume une largeur maximale centrée, sans grandes zones vides ; échelle cohérente (barre du haut et libellés pas minuscules à côté d'un contenu grand) ; distance entre la zone de travail et l'action fréquente (Fitts : Enregistrer à 1 600 px de la grille = constat) ; nombre de cartes ou colonnes par ligne adapté, sans orphelines ; plus de lignes visibles que sur portable ; écran d'accueil d'une tâche qui ne flotte pas, minuscule, au milieu du vide.

**Contrôles Mac.** Raccourcis ⌘ fonctionnels ET affichés en ⌘ sur Mac (pas « Ctrl ») ; ⌫ efface ; F2 a une alternative visible (double-clic, Entrée) ; défilement horizontal au trackpad ; netteté Retina ; Safari est le navigateur par défaut : si l'outil exige Chrome/Edge, le dire en premier à l'accueil, désactiver l'action impossible et expliquer comment ouvrir dans Chrome.

**Contrôles iPhone (seulement si dans le périmètre).** Cibles ≥ 44 px, actions au pouce, tableaux en cartes ou colonnes prioritaires, clavier adapté au champ, rien au survol, hauteur avec 100dvh, limites de Safari iOS (tous les navigateurs iOS sont WebKit : API de fichiers absentes).

## Catalogue des motifs appris (savoir-faire de l'utilisateur)

Chaque motif vient de demandes réelles. Il s'applique à tout outil, pas seulement au projet d'origine. Le catalogue grandit par la boucle d'apprentissage.

**M1 — L'outil de référence fait loi (souvent Excel).** Une grille se comporte comme le tableur de l'utilisateur. Test : cellule sélectionnée + frappe = saisie directe ; Entrée descend ; F2 / double-clic modifie ; Échap annule ; flèches et Tab ; copier-coller d'un bloc depuis Excel (y compris des valeurs « sales » comme « 25 min », « OK », « NOK ») ; Ctrl+Z / Ctrl+Y ; Ctrl+A ; sélection en glissant ; en-têtes et première colonne figés ; trier / cacher / surligner au clic sur l'en-tête ; collage dans un champ texte non intercepté par la grille.

**M2 — Budget vertical.** Test dans chaque profil du périmètre, le plus bas d'abord (ex. PC 125 % 1536×730, MacBook Air 1440×775) : seule la zone de travail défile (scrollHeight ≤ hauteur de fenêtre) ; barre du haut ≤ 72 px et sur une seule ligne ; zone de travail à ≤ 180 px du haut ; barre latérale repliable en bande d'icônes (pas masquée entièrement), icône visible pour chaque entrée ; densité compacte par défaut ; astuces en infobulle ou lien « Aide », pas en ligne permanente.

**M3 — Ce qui encombre.** Chercher activement les boutons en trop : action rare affichée en permanence, bouton qui double un raccourci connu, gros bouton secondaire, barre de filtres sur plusieurs lignes. Correction : action rare → menu de l'en-tête, menu « … » ou fenêtre ; filtres sur une ligne ; taille standard. Ne jamais retirer la fonction (voir M4).

**M4 — Découvrabilité.** Toute fonction est trouvable par un élément visible. Constat si une fonction n'existe qu'au clic droit, au survol, par raccourci, ou en bas de page alors qu'elle est fréquente ; si un onglet ou un groupe ne paraît pas cliquable ; si « Créer… » n'est pas là où l'utilisateur le cherche ; si une vue alternative (ex. « Par élève ») est cachée derrière un bouton en bas au lieu d'un choix en haut.

**M5 — Fenêtre, pas déplacement.** Calendrier, raccourcis, aide, messages, erreurs et confirmations s'ouvrent en fenêtre ou panneau superposé, sans pousser la page ni changer d'écran. Aucun window.alert / confirm / prompt : tous les messages passent par la fenêtre de l'application, au même style.

**M6 — Parité entre vues et tableaux.** Construire une matrice « capacité × vue » : chaque champ (titre, commentaire, N/A, effacer), chaque valeur et chaque capacité de tableau (tri, masquage, en-têtes figés, couleurs) disponible dans une vue doit l'être dans toutes les vues qui montrent la même donnée, et rester synchronisé dans les deux sens. Un trou = constat ; 🔴 si une donnée saisie dans une vue est invisible ou perdue dans l'autre.

**M7 — Une valeur négative ne ressemble pas à « fait ».** Un « Non », une absence, un échec se distinguent d'un « Oui » au premier coup d'œil (rouge + croix ; retard en orange) ; codes courts lisibles (P / A / minutes) ; chaque case à choix a un libellé visible sans survol ; case remplie ≠ case positive.

**M8 — Aucun échec silencieux.** Toute saisie, tout collage ou import refusé dit pourquoi et comment corriger, à côté de la donnée. Préférer une saisie tolérante (unités, synonymes OK/NOK, Oui/Non, Présent/Absent) à un refus.

**M9 — Couleurs sémantiques utiles.** Rouge / orange / vert doux mais lisibles (contraste calculé), à seuils explicites (ex. taux < 50 rouge, < 70 orange, ≥ 70 vert), dégradé à sens réglable pour les autres chiffres, appliqués partout où un chiffre est lu (grilles, tableau de bord, fiches, impression). Réglables par utilisateur si les usages diffèrent.

**M10 — Navigation regroupée par rôle et par tâche.** Réglages et fonctions apparentées en sous-onglets ; groupes par rôle ; libellés courts (« RH ») ; ≤ 7 entrées par niveau.

**M11 — Actions en masse.** Pour toute tâche répétée par élément : coller une liste depuis Excel, tout imprimer / exporter en une fois, importer plusieurs éléments par fichier, avec résumé avant écriture.

**M12 — Ordre naturel par défaut.** Dates de la plus ancienne à la plus récente, ajout à la fin ; l'inversion reste possible.

**M13 — Microcopie en situation.** Une confirmation dit la situation et l'action (« Aucune réponse pour cette activité. Passer à la suivante ? ») ; boutons = verbes (« Rester ici » / « Passer »), jamais « OK / Annuler » ambigus.

**M14 — Volume réaliste.** Tester avec le volume réel maximal (ex. 30 élèves, 40 séances, noms longs, toutes les activités) : mise en page, défilement et tailles doivent tenir.

**M15 — Manipulation directe.** Placer, déplacer et retirer se font en glissant (avec zone « poubelle » visible pendant le glisser), en plus du clic et du clavier. Une longue liste de choix d'objets riches (recettes, personnes, véhicules) s'affiche aussi en grille de cartes. Un produit ou un objet a son image partout où sa référence apparaît (catalogue, liste, panneau, impression), si la donnée existe. Test : peut-on déplacer un élément d'une case à l'autre et le retirer sans menu ? Voit-on l'objet sans lire son code ?

**M16 — Portée explicite d'une modification.** Quand on modifie une donnée partagée (recette, modèle, réglage) depuis un contexte précis (un repas, un jour, un pôle), l'outil demande à chaque fois « Partout » ou « Ici seulement », et une surcharge locale reste visible (badge « modifié pour ce repas ») et réversible. Le niveau fin peut surcharger le niveau général (ex. produit choisi par repas). Test : modifier depuis le contexte ; les autres usages changent-ils sans prévenir ?

**M17 — Chaque chiffre calculé se justifie.** Toute quantité, total ou statut calculé s'ouvre (clic ou icône ⓘ) sur une fenêtre qui montre le calcul : base, effectif, conversion, arrondi, source. Test : pour 3 chiffres pris au hasard, l'utilisateur peut-il dire d'où ils viennent sans lire le code ?

**M18 — Contexte actif visible partout.** Le séjour, le pôle, la base (en ligne / fichier local) en cours sont affichés dans chaque vue qui en dépend, modifiables depuis cette vue, et distingués par une couleur ou un thème réglable quand on peut se tromper de contexte. Test : changer d'onglet ; sait-on encore sur quel séjour/pôle/base on travaille ?

**M19 — Import par modèle.** Tout import par fichier propose un modèle téléchargeable qui porte les mêmes restrictions que l'outil (listes déroulantes, unités, formats), puis un aperçu avant écriture avec erreurs ligne par ligne (M8, M11).

**M20 — Toute liste se trie et se filtre.** Dès qu'une liste ou un tableau dépasse ~10 éléments (ingrédients, recettes, membres), il a recherche, tri et filtre, dans chaque vue (M6).

## Grille générale

### 1. Clarté et finalité
- On comprend en 5 s ce que fait l'outil et quoi faire en premier.
- Une action principale par écran, visuellement dominante (bouton primaire unique).
- Titres et libellés dans les mots de l'utilisateur et le glossaire du projet, pas du jargon technique (Nielsen #2).
- Premier lancement : état vide utile (explication + action « Commencer » ou données d'exemple).

### 2. Architecture et navigation
- Structure prévisible, ≤ 7 entrées principales (Miller/Hick) ; regrouper le reste (M10).
- L'utilisateur sait toujours où il est (onglet actif, titre, fil d'Ariane).
- Retour/annuler possible partout (Nielsen #3) ; pas d'impasse.
- Tâches fréquentes en ≤ 2 clics ; options avancées en divulgation progressive, sans les rendre introuvables (M4).

### 3. Hiérarchie visuelle et mise en page
- Hiérarchie par taille, graisse, couleur et espace — pas seulement par la taille (Refactoring UI).
- Grille et alignements cohérents ; échelle d'espacement fixe (4/8/12/16/24/32/48).
- Proximité = relation (Gestalt) : plus d'espace entre groupes qu'à l'intérieur.
- Largeur de texte 45–75 caractères ; pas de murs de texte.
- Densité adaptée : outil quotidien = dense mais aéré (M2) ; outil ponctuel = guidé.

### 4. Typographie
- 1 police (2 max), échelle de 4–6 tailles ; texte ≥ 13 px sur ordinateur (corps 14–16), ≥ 16 px sur mobile.
- Interligne 1,4–1,6 pour le texte ; chiffres tabulaires dans les tableaux.
- Pas de texte gris trop clair ni de MAJUSCULES longues.

### 5. Couleur
- Palette restreinte : 1 couleur d'accent, neutres en 8–10 nuances, couleurs sémantiques (M9).
- Contraste WCAG AA calculé : 4,5:1 texte, 3:1 gros texte et éléments d'interface.
- Jamais la couleur seule pour porter une info (M7).
- Mode sombre cohérent si proposé.

### 6. Composants et interactions
- Boutons : primaire / secondaire / tertiaire distincts ; libellé = verbe + objet.
- Cibles : seuils du Projet ; à défaut ≥ 24 px sur ordinateur, ≥ 44 px en tactile ; espacées (Fitts).
- États complets : repos, survol, focus, actif, désactivé, chargement.
- Composants que l'utilisateur connaît, y compris ceux de son outil de référence (Jakob, M1) ; cohérence partout (Nielsen #4).

### 7. Formulaires et saisie
- Libellés visibles au-dessus des champs (pas de placeholder comme libellé).
- Bon type de champ (date, nombre, liste, interrupteur).
- Valeurs par défaut intelligentes ; demander le minimum (Tesler).
- Validation en ligne, message à côté du champ, qui dit comment corriger (M8).
- Champs obligatoires/facultatifs indiqués ; saisie jamais perdue.

### 8. Retour système et états
- Retour visible < 100 ms ; chargement > 1 s = indicateur (Doherty, Nielsen #1).
- Les 5 états de chaque écran : vide, chargement, partiel, erreur, rempli.
- Confirmations dans l'application (M5) ; actions destructrices = confirmation ou « Annuler » après coup.
- Messages d'erreur humains : ce qui s'est passé + quoi faire, sans blâmer.

### 9. Prévention d'erreur et charge mentale
- Contraintes plutôt qu'erreurs (Nielsen #5).
- Reconnaître plutôt que se souvenir (#6).
- Raccourcis pour utilisateurs fréquents (#7), en plus d'un accès visible (M4).
- Sauvegarde automatique ou état « enregistré » clair.

### 10. Données, tableaux et visualisations
- Tableaux : en-têtes figés, tri, filtre, recherche, sur tous les tableaux (M6) ; nombres alignés à droite.
- Le bon graphique ; titre qui dit la conclusion ; légende directe.
- Totaux, tendances et alertes mis en avant (KPI en haut).
- Export/impression, unitaire et en masse (M11).

### 11. Responsive (selon les profils du périmètre)
- Tenir dans chaque profil sans défilement de page ni défilement horizontal involontaire (M2), du plus petit au plus grand.
- Grand écran : contrôles « grand écran » (largeur de lecture, vides, échelle, distance des actions, cartes orphelines).
- Mac : contrôles Mac (⌘ affiché, ⌫, alternative à F2, Safari).
- iPhone, seulement si demandé : contrôles iPhone. iPad exclu sauf demande.
- Le rapport donne un tableau de mesures par profil (une colonne par profil).

### 12. Accessibilité (WCAG 2.2 AA)
- Navigation complète au clavier, focus visible, ordre logique.
- Sémantique HTML (boutons = <button>, titres hiérarchisés, labels liés).
- Textes alternatifs ; aria seulement si nécessaire ; respect de prefers-reduced-motion.
- Zoom 200 % sans perte ; langue de la page déclarée.

### 13. Contenu et microcopie
- Ton constant, phrases courtes, tutoiement/vouvoiement cohérent (M13).
- Aide contextuelle (infobulle, exemple) au lieu d'un mode d'emploi séparé (#10).
- Dates, nombres, devises au format local (fr-BE).

### 14. Esthétique et finition
- Minimalisme : retirer ce qui ne sert pas la tâche (#8, M3).
- Identité cohérente entre mes outils (mêmes couleurs, police, composants) → idéalement un design system commun.
- Détails : coins, ombres, icônes d'un seul jeu, micro-animations utiles (150–250 ms).
- Ne ressemble pas à un template générique ; une intention visuelle claire.

## Format de sortie

1. **Verdict en 3 lignes** : note /10 globale, point fort principal, problème principal.
2. **Profils et besoins** (tableau), puis **sessions réelles** par rôle : étapes numérotées avec ✅ / ❌ / 🟡 / 🔴, et une ligne « Points faibles » par parcours.
3. **Mesures** (tableau par résolution) : valeur relevée, seuil, OK / KO / [Non mesuré].
4. **Catalogue des motifs** : M1 à Mn, passé / non passé, avec la preuve. Ajouter une section **« Manipulations attendues »** (M15 à M18) : pour chaque tâche fréquente, la manière la plus directe de la faire, et si l'outil la propose.
5. **Matrice de parité** (M6) si l'outil a plusieurs vues sur la même donnée.
6. **Tableau de scores** par section (1 à 14) : note /5 + un mot.
7. **Problèmes priorisés** (max ~15), du plus grave au moins grave. Pour chacun :
   - Gravité : 🔴 bloquant / 🟠 important / 🟡 confort
   - Constat précis (où, quoi, preuve)
   - Motif (M…) ou règle enfreinte (ex. Nielsen #1, WCAG 1.4.3, Fitts)
   - Critère de réussite mesurable (ex. « scrollHeight ≤ hauteur de fenêtre à 1366×768 »)
   - Correction concrète (valeurs, texte, code CSS/HTML si utile)
   - Effort : S / M / L
8. **Ce qui encombre** (M3) et **ce qui manque** (état vide, recherche, annuler…).
9. **Quick wins** : 3–5 corrections < 15 min au plus fort impact.
10. **Ce qui est déjà bien** (à garder) et **régressions** (points « déjà corrigés » qui réapparaissent).
11. **Hors périmètre** (backend, données, sécurité) en une ligne.
12. **Sources** : liens des recherches web + références.
13. **Prochaine étape** : appliquer les corrections, ou lancer iteration-adaptations / refonte-outil.

Règles : être critique et spécifique, jamais de compliment vide ; chaque remarque vérifiable et actionnable ; ne pas inventer ce qu'on n'a pas vu (dire « non vérifié ») ; ne jamais coter OK un point qu'une mesure permettait de vérifier ; ne pas reproposer un point refusé ou déjà corrigé.

## Boucle d'apprentissage (à chaque utilisation)

1. Quand l'utilisateur fait une remarque UX que l'audit n'avait pas relevée, ou corrige une remarque de l'audit : la rattacher à un motif existant (M…) et noter pourquoi son test ne l'a pas attrapée ; sinon créer un motif candidat (nom, demandes d'origine, test de détection, correction par défaut).
2. Chercher aussitôt **les autres occurrences du même type** dans tout l'outil (autres écrans, vues, tableaux) et les ajouter au rapport : l'analyse de l'utilisateur n'est jamais terminée, le skill généralise chaque remarque.
3. Enregistrer dans la mémoire du Projet (fichier savoir-faire UX) la règle telle que l'utilisateur l'a dite, et ce qui a été retenu, refusé ou reformulé.
4. En fin de session, si un motif a été créé ou un test renforcé, proposer la mise à jour de ce skill et d'ux-ui-designer avec propose_skills, pour garder les deux catalogues identiques.