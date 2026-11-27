# Sessió: Teleprompter (2026-11-27 / 2026-11-28)

## Objectiu
Teleprompter web per obrir un guió, amb play/pausa, velocitat, i el text desplaçant-se
i engrandint-se a la línia central de lectura. Desplegament a Vercel.

## Decisions
- Formats d'arxiu: `.txt` i `.md` (el Markdown només se'n treuen els símbols, no es renderitza).
- Stack: HTML/CSS/JS pur, un únic `index.html`, sense build.
- Extres: només slider de mida de lletra (sense mode mirall ni dreceres de teclat).
- Idioma de la interfície: català, excepte "Play" / "Pause" (en anglès).
- Mode clar per defecte; l'elecció es guarda a `localStorage` (clau `theme`).

## Funcionalitat final
- Obrir arxiu, Play/Pause, Reinicia.
- Velocitat 10–120 px/s, mida de lletra 28–120 px (conserva la posició de lectura).
- Línia de lectura central: efecte d'escala i opacitat segons la distància al centre
  (constants `MIN_SCALE`, `MIN_OPACITY`, `PUSH` al JS).
- Franja de lectura alta amb les línies veïnes empeses cap a fora.
- Mode clar / fosc.
- Cronòmetre gran (a dalt a la dreta): compta amunt, s'engega amb Play, s'atura amb Pause,
  es posa a zero amb Reinicia o en obrir un arxiu nou.
- Roda del ratolí per moure el text a mà.
- Botó **Prova** (a la dreta de la barra): carrega `benjamin-itaca.md` (text de mostra).
  Fa un `fetch`, per tant cal servidor (no funciona amb `file://`); a Vercel va bé.
- **Durada estimada** i **Queda** sota el cronòmetre: distància de desplaçament / velocitat (px/s).
  Depèn de la mida de lletra i l'amplada de pantalla, no és una estimació en paraules per minut.
- El botó de càrrega es diu "Obre un arxiu" (no "Puja", perquè no es guarda enlloc).

## Provat
Amb Chrome (Playwright): càrrega d'arxiu, play/pausa, canvi de mida, tema clar/fosc,
cronòmetre, botó Prova, durada estimada. Sense errors de consola. No provat: slider de velocitat en moviment, mòbil.

## Estat
- Repo **públic**: https://github.com/jmm70/teleprompter-jmm (branca `main`).
- Desplegat a **Vercel** (des del repo de GitHub; cada `git push` a `main` el redesplega).
- Llicència MIT (`LICENSE`), titular Juan Mateu, 2026. Cobreix tot el repo, `benjamin-itaca.md` inclòs.
- `benjamin-itaca.md` és públic (al repo i servit pel botó Prova a Vercel).
  És un text de l'autor ja publicat al seu Substack. El `README.md` l'exclou de la MIT (tots els drets reservats).
- Qualsevol pot veure, clonar i fer fork/pull requests; només el propietari pot fer push.
- Servidor local de prova: `python3 -m http.server 8000` a la carpeta del projecte (no cal per a Vercel).

## Idees futures
- Cronòmetre amb compte enrere (durada prevista).
- Mode mirall, dreceres de teclat, suport `.docx`/`.pdf`.
