# La Mia Agenda — progetto Android (Capacitor)

Questo pacchetto contiene il progetto completo per generare un **file APK reale** della tua agenda,
usando il codice che avevi già (con notifiche native, canali Android, allarmi esatti, azioni sulla notifica).

Non devi installare Android Studio: la build avviene automaticamente su GitHub, in cloud.

## Passo 1 — Crea un repository GitHub
1. Vai su github.com e crea un account (se non ce l'hai già)
2. Crea un nuovo repository (può essere privato), es. `la-mia-agenda`

## Passo 2 — Carica questi file nel repository
Puoi farlo dal sito di GitHub stesso (drag & drop di tutta la cartella), oppure da terminale:

```bash
cd cartella-del-progetto
git init
git add .
git commit -m "Prima versione agenda"
git branch -M main
git remote add origin https://github.com/TUO-USERNAME/la-mia-agenda.git
git push -u origin main
```

## Passo 3 — Lascia lavorare GitHub Actions
Appena il codice arriva su GitHub, parte automaticamente la build (la trovi nella scheda **Actions** del repository).
Dopo 3-5 minuti circa, in fondo alla pagina della build trovi un file scaricabile chiamato **agenda-apk** (uno zip che contiene `app-debug.apk`).

## Passo 4 — Installa l'APK sul telefono
1. Scarica lo zip dal telefono (o da PC e poi trasferiscilo)
2. Estrai `app-debug.apk`
3. Aprilo sul telefono: Android chiederà di **consentire l'installazione da questa sorgente** — accetta
4. L'app "La Mia Agenda" comparirà tra le tue app, con la sua icona

## Passo 5 — Attiva le notifiche nell'app
1. Apri l'app
2. Tocca "🔔 Controlla permessi" nel banner in alto
3. Concedi il permesso notifiche
4. Se richiesto, concedi anche "Allarmi e promemoria" (necessario per gli orari esatti anche a schermo spento)
5. Usa il pulsante "🧪 Test tra 20 secondi" per verificare: blocca lo schermo e aspetta

## Nota sul suono
Il codice originale faceva riferimento a un file audio personalizzato (`agenda_chime.wav`) che non era incluso:
l'ho tolto per evitare errori, quindi ora la notifica userà il **suono di notifica predefinito di Android**
(comunque udibile, con vibrazione). Se in futuro vuoi un suono personalizzato "dolce", possiamo aggiungerlo:
serve solo un file .wav breve da inserire in `android/app/src/main/res/raw/`.

## Ogni volta che modifichi il codice
Basta modificare `www/index.html`, fare di nuovo `git add . && git commit -m "..." && git push`,
e GitHub genera automaticamente un nuovo APK aggiornato.
