# Sessió: Teleprompter (2026-11-27)

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
- Velocitat 10–300 px/s, mida de lletra 28–120 px (conserva la posició de lectura).
- Línia de lectura central: efecte d'escala i opacitat segons la distància al centre
  (constants `MIN_SCALE`, `MIN_OPACITY`, `PUSH` al JS).
- Franja de lectura alta amb les línies veïnes empeses cap a fora.
- Mode clar / fosc.
- Cronòmetre gran (a dalt a la dreta): compta amunt, s'engega amb Play, s'atura amb Pause,
  es posa a zero amb Reinicia o en obrir un arxiu nou.
- Roda del ratolí per moure el text a mà.

## Provat
Amb Chrome (Playwright): càrrega d'arxiu, play/pausa, canvi de mida, tema clar/fosc,
cronòmetre. Sense errors de consola. No provat: slider de velocitat en moviment, mòbil.

## Estat
- Repo privat: https://github.com/jmm70/teleprompter-jmm (branca `main`, 1 commit).
- `index.html` està complet al commit (inclou mode clar, català i cronòmetre).
  Aquest `SESSION.md` encara no s'ha afegit al repo.
- Pendent: desplegar a Vercel (importar el repo des del panell, o `npx vercel --prod`).
- Servidor local de prova: `python3 -m http.server 8000` a la carpeta del projecte.

## Idees futures
- Cronòmetre amb compte enrere (durada prevista).
- Mode mirall, dreceres de teclat, suport `.docx`/`.pdf`.
