# Handy-Button: Website manuell aktualisieren

Nach einer Änderung auf booking.com kann die Website sofort aktualisiert werden — 
ohne GitHub-Account, mit einem Tipp auf dem Handy.

## 1. GitHub Token erstellen

1. GitHub → Settings → Developer Settings → Personal Access Tokens → **Fine-grained**
2. Token name: `Website Update Button`
3. Repository access: **Only select repositories** → `Alpenstrasse/Website`
4. Permissions: **Actions → Write** (sonst nichts)
5. Token kopieren und sicher aufbewahren

## 2. iOS Kurzbefehl einrichten

1. **Kurzbefehle** App öffnen → **+** neuer Kurzbefehl
2. Aktion hinzufügen: **"URL-Inhalt abrufen"**
3. Konfigurieren:
   - **URL:** `https://api.github.com/repos/Alpenstrasse/Website/actions/workflows/deploy.yml/dispatches`
   - **Methode:** POST
   - **Header:**
     - `Authorization` → `Bearer ghp_DEIN_TOKEN_HIER`
     - `Accept` → `application/vnd.github.v3+json`
   - **Body:** JSON → Schlüssel `ref`, Wert `main`
4. Zweite Aktion: **"Mitteilung anzeigen"** → `Website wird aktualisiert!`
5. Benennen: **"Website aktualisieren"**
6. Teilen → **Zum Home-Bildschirm**

## 3. Benutzen

Ein Tipp auf das Icon → die Website generiert sich neu mit aktuellen Buchungsdaten.
Dauer: ca. 2 Minuten bis die Änderung live ist.

## Hinweise

- Die Website aktualisiert sich auch automatisch alle 6 Stunden
- Der Token kann nur diese eine Aktion auslösen, sonst nichts
- Bei Token-Ablauf: neuen Token erstellen und im Kurzbefehl ersetzen
