# Urlaubsplaner 2027 – Filiale 6544

Eine Seite, in der Mitarbeiter ihre Urlaubstage eintragen (deutsch/polnisch), mit Auswertung (Passwort) und PDF-Liste im A4-Format.

## 1. Datenbank einrichten (Firebase, kostenlos)

Damit alle Eintragungen an einer gemeinsamen Stelle landen, braucht die Seite eine kleine Datenbank.

1. Auf https://console.firebase.google.com ein Projekt erstellen (Google Analytics kann aus bleiben).
2. Im Projekt: **Build → Realtime Database → Datenbank erstellen**, Region Europa wählen.
3. Reiter **Regeln**: den Inhalt von `database.rules.json` einfügen und **Veröffentlichen**.
4. Oben in der Datenbank steht die Adresse, z. B. `https://mein-projekt-default-rtdb.europe-west1.firebasedatabase.app`. Kopiere sie in `config.js` bei `databaseURL`.

## 2. Auf GitHub veröffentlichen

1. Auf https://github.com ein neues Repository anlegen (z. B. `urlaubsplaner`).
2. **Add file → Upload files** und die Dateien `index.html` und `config.js` hochladen.
3. **Settings → Pages → Build and deployment**: Source = *Deploy from a branch*, Branch = `main`, Ordner = `/ (root)`, speichern.
4. Nach etwa einer Minute ist die Seite erreichbar unter `https://<dein-name>.github.io/<repo-name>/`. Diesen Link an die Mitarbeiter schicken.

## Auswertung

Ganz unten auf der Seite: **Auswertung** → Passwort → Tabelle mit Konflikten, allen Mitarbeitern und dem Button **Liste als PDF (A4)**.

## Wichtige Hinweise

- Bei kostenlosen GitHub-Konten ist ein Repository mit Pages öffentlich. Die Namen der Mitarbeiter, die Wochenstunden und das Auswertungs-Passwort stehen im Code von `index.html` und sind damit im Internet lesbar.
- Die Datenbankregeln erlauben jedem mit der Adresse Lesen und Schreiben. Das Passwort schützt nur die Ansicht der Auswertung, nicht die Daten.
- Alle Eintragungen zurücksetzen: in `index.html` den Wert `RESET_ID` ändern und die Einträge unter `profiles` in der Firebase-Datenbank löschen.
