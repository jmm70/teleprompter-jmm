# Teleprompter

Teleprompter web senzill: obre un arxiu `.txt` o `.md`, prem Play i el text es desplaça
amb la línia de lectura ampliada al centre de la pantalla.

- Play / Pause, Reinicia
- Velocitat (10–120 px/s) i mida de lletra
- Mode clar i fosc
- Cronòmetre i durada estimada de lectura
- Botó **Prova** per carregar un text de mostra

És un únic `index.html` sense dependències ni build. Per provar-lo en local:

```bash
python3 -m http.server 8000
```

i obre http://localhost:8000.

## Llicència

- **Codi** (`index.html`): [MIT](LICENSE).
- **Text de mostra** (`benjamin-itaca.md`): © Juan Mateu, tots els drets reservats.
  Publicat originalment a [Desacord](https://desacord.substack.com/p/el-temps-furtat-benjamin-i-el-problema).
  No està cobert per la llicència MIT; s'inclou només com a exemple per provar l'aplicació.
