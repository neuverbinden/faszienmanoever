# Fascial Maneuvers Workshop – Landingpage

Statische Landingpage (kein Build-Tool, kein Framework, kein Backend) für den
"Fascial Maneuvers" Workshop (Human Garage), Mannheim, 30. August 2026,
im Studio "Q7 30 – flow yoga and more".

## Architektur-Entscheidungen (bewusst, nicht ändern ohne Rücksprache)

- Reines HTML/CSS/JS, kein Framework, kein npm/Build-Schritt — der Betreiber
  wollte explizit keine zusätzlichen kostenpflichtigen Dienste (kein Vercel).
- Hosting: GitHub Pages, Repo https://github.com/neuverbinden/faszienmanoever,
  live unter https://neuverbinden.github.io/faszienmanoever/.
- Buchung: Stripe Payment Link (kein eigener Server nötig), Kapazitätslimit
  wird direkt im Stripe-Dashboard über "limit number of payments" gesetzt.
  Early-Bird-Preis wurde bewusst verschoben (aktuell nur ein fester Preis).
- **Beta-Modus ist aktuell aktiv**: `robots.txt` sperrt alles, beide HTML-Seiten
  haben `<meta name="robots" content="noindex,nofollow">`, und die
  Custom-Domain `faszienmanöver.de` (Punycode `xn--faszienmanver-rmb.de`) ist
  absichtlich noch NICHT verbunden — die `CNAME`-Datei liegt lokal, ist aber
  in `.gitignore` eingetragen. Zum vollständigen Livegang: CNAME aus
  .gitignore entfernen, `git add -f CNAME`, committen/pushen, Custom Domain +
  DNS setzen, noindex/robots.txt entfernen.
- DSGVO-Grundsätze: keine Google Fonts CDN (System-Font-Stack), keine
  Analytics/Tracker. Impressum ist extern verlinkt
  (https://mein.online-impressum.de/neuverbinden-de/), nicht lokal gepflegt.
  `datenschutz.html` ist ein Entwurf und braucht vor echtem Livegang eine
  Prüfung (z. B. e-recht24.de oder Anwalt/Anwältin).
- Kontaktformular: forms.app (https://lx2cqpcb.forms.app/kontaktformular),
  bewusst als Click-to-Load-Iframe eingebaut (lädt erst nach Klick auf
  "Kontaktformular laden"), damit keine Drittanbieter-Cookies ohne Aktion
  des Besuchers geladen werden.
- Hero: Hintergrundvideo (`images/hero.mp4`, autoplay/muted/loop) mit
  dunklem Overlay für Textkontrast, Fotos liegen als Streifen direkt darunter.

## Offene Inhalte (noch nicht final)

- Testimonials: teils noch Platzhalter. Update 2026-07-27: Der Betreiber hat
  bewusst entschieden, eine Google-Rezension von neuverbinden.de (seinem
  anderen Geschäft, 1:1-Coaching) als Testimonial zu verwenden (Ute), obwohl
  das ein anderes Business betrifft — mit expliziter Quellenangabe
  "Google-Rezension Neuverbinden" in der Rolle/Ort-Zeile, damit klar bleibt,
  worauf sich die Bewertung bezieht. Frühere Regel ("nicht verwenden, da
  irreführend") ist damit für diesen einen Fall aufgehoben; bei weiteren
  Neuverbinden-Bewertungen auf der gleichen offenen Kennzeichnung bestehen.
- FAQ "Frage 4" in `Dokumente\Texte.txt` ist vom Nutzer bewusst leer gelassen
  (in Arbeit) — nicht überschreiben oder löschen.
- E-Mail-Adresse für Kontaktformular-Benachrichtigungen noch offen — das ist
  keine Einstellung im Code dieser Website (das Formular ist nur ein iframe
  von forms.app), sondern muss direkt im forms.app-Konto unter den
  Benachrichtigungs-Einstellungen hinterlegt werden.

## Workflow

- Texte werden vom Betreiber in `Dokumente\Texte.txt` gepflegt (nicht in Git,
  siehe .gitignore) — bei Änderungswunsch diese Datei lesen statt Text im
  Chat einzufordern.
- `git push`/Login-pflichtige Git-Befehle muss der Nutzer selbst in einem
  eigenen Terminal ausführen (nicht über eine restriktive Shell ohne
  interaktive Prompts).
- GitHub Pages Source: "Deploy from a branch" → `main` → `/ (root)`. Falls
  ein Redeploy nötig ist: Source erst auf "None" + Save, dann zurück auf
  Branch/main/root + Save, oder einen neuen Commit pushen.
