# Modèles de CV — démarches

Gabarits sources repris du portfolio (`_portfolio/cv/`), rendus accessibles ici pour **réécrire des CV ciblés sans toucher au sous-module**. Ce sont des **snapshots** : la source de vérité des faits (dates, employeurs, clients) reste `_portfolio/src/content/page/resume.md`, recopiée ici sous `cv-resume-reference.md`.

## Contenu

| Fichier | Rôle |
| --- | --- |
| `cv-enseignement.html` | Gabarit **enseignement** (cadrage Gameplay & IA · Enseignant / Coordinateur). Repris de `_portfolio/cv/cv.html`. |
| `cv-industrie.html` | Gabarit **logiciel / tech** (dev hands-on, temps réel, vision, parcours industriel). Repris de `_portfolio/cv/cv-industrie.html`. |
| `cv-resume-reference.md` | **Faits de référence** (parcours complet) — à consulter pour ne rien inventer. Repris de `resume.md`. |

Les ressources partagées **CSS + photo** vivent dans `../_assets/` (`cv.css`, `photo.jpg`). Les gabarits les référencent via `../_assets/…`.

> Convention de chemins : tout CV HTML se trouve à `01 - candidatures/<dossier>/cv-*.html` et pointe vers `../_assets/`. Comme `_modeles/` et chaque dossier de candidature sont au **même niveau**, le chemin `../_assets/` reste valide après duplication — rien à modifier.

## Créer un CV ciblé pour une nouvelle offre

1. Créer le dossier de la candidature : `01 - candidatures/<Entreprise - Poste>/`.
2. Y copier le gabarit le plus proche, p. ex. :
   ```bash
   cp "_modeles/cv-industrie.html" "<Entreprise - Poste>/cv-<entreprise>.html"
   ```
3. Recibler le contenu (sous-titre, résumé, ordre des expériences, tags de compétences) pour l'offre.
   **Ne jamais inventer de compétence** — vérifier chaque fait contre `cv-resume-reference.md`. Les écarts se traitent en posture d'apprentissage dans la lettre, pas en CV.
4. Garder les chemins `../_assets/cv.css` et `../_assets/photo.jpg` tels quels.
5. (Optionnel) Produire aussi une forme Markdown éditable `cv-<entreprise>.md`.

## Générer le PDF (Edge headless)

Depuis la racine du repo, en PowerShell — l'encodage `AbsoluteUri` gère espaces et accents du chemin :

```powershell
$edge = "C:\Program Files (x86)\Microsoft\Edge\Application\msedge.exe"
$html = "D:\_dev\repos\_work\Demarches\01 - candidatures\<Entreprise - Poste>\cv-<entreprise>.html"
$pdf  = "D:\_dev\repos\_work\Demarches\01 - candidatures\<Entreprise - Poste>\CV_Sebastien_Albert_<Entreprise>.pdf"
& $edge --headless=new --disable-gpu --no-pdf-header-footer `
  --user-data-dir="$env:TEMP\edge-pdf-profile" `
  --print-to-pdf="$pdf" ([System.Uri]$html).AbsoluteUri
```

Viser **1 page A4** (cocher mentalement : sidebar terracotta rendue, photo présente). Pour une lettre, partir d'un `lettre-*.html` (mise en page colonne unique, cf. la candidature Alstom).

## Rafraîchir les gabarits depuis le portfolio

Si les CV maîtres du portfolio évoluent, ré-importer (recâble aussi les chemins) :

```bash
SRC="D:/_dev/repos/_work/_portfolio"
DST="D:/_dev/repos/_work/Demarches/01 - candidatures/_modeles"
sed -e 's#href="cv.css"#href="../_assets/cv.css"#' -e 's#src="photo.jpg"#src="../_assets/photo.jpg"#' "$SRC/cv/cv.html"           > "$DST/cv-enseignement.html"
sed -e 's#href="cv.css"#href="../_assets/cv.css"#' -e 's#src="photo.jpg"#src="../_assets/photo.jpg"#' "$SRC/cv/cv-industrie.html" > "$DST/cv-industrie.html"
cp "$SRC/src/content/page/resume.md" "$DST/cv-resume-reference.md"
cp "$SRC/cv/cv.css"   "$DST/../_assets/cv.css"
cp "$SRC/cv/photo.jpg" "$DST/../_assets/photo.jpg"
```
