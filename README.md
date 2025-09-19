# ReturnGuard (Mobile‑First, OCR+Barcode, Offline)

Lokales Tool zur Verwaltung von Rückgabefristen & Garantien. Läuft komplett im Browser (IndexedDB), inklusive **OCR** (Tesseract.js) und **QR/Barcode-Scan** (ZXing). Keine Cloud, keine Accounts.

## Inhalte
- `index.html` – gesamte App in einer Datei, inkl. UI & Logik.

## Nutzung (lokal)
- Datei `index.html` im Browser öffnen (Chrome, Firefox, Safari).  
- Hinweis: Kamera/OCR/Benachrichtigungen benötigen **https** (oder `http://localhost`).

## Veröffentlichung auf GitHub (inkl. GitHub Pages)
1. Auf github.com ein neues **öffentliches** Repository erstellen (z. B. `returnguard`).
2. Im Repo: **Add file → Upload files** → `index.html` (und optional `README.md`) hochladen.
3. **Settings → Pages** → `Branch: main`, `Folder: /(root)` → **Save**.
4. Nach ~1–2 Minuten ist die App online unter `https://<DEIN-USER>.github.io/<REPO-NAME>/`.

## Berechtigungen & Daten
- **Kamera**: für Barcode‑Scan und Foto‑OCR (nur nach expliziter Zustimmung).
- **Benachrichtigungen**: lokale Reminder; funktionieren nur über **https**.
- **Datenhaltung**: lokal via IndexedDB. Export/Import als JSON/CSV/ICS möglich.

## Projekt-Log

| Datum (UTC) | Browser | Plattform | Schritt | Ergebnis |
| --- | --- | --- | --- | --- |
| 2025-09-19 | Chromium (Playwright, headless) | Linux-Container | Service Worker-Registrierung | ❌ `Failed to register a ServiceWorker: The URL protocol of the script ('blob:…') is not supported.` |
| 2025-09-19 | Chromium (Playwright, headless) | Linux-Container | OCR (Offline, Beispielbild) | ❌ `Tesseract is not defined` – keine Offline-Bundle für OCR geladen. |
| 2025-09-19 | Chromium (Playwright, headless) | Linux-Container | ZXing Barcode-Scan (Offline) | ❌ `ZXing`-Namespace nicht verfügbar (Bibliothek nicht offline geladen). |
| 2025-09-19 | Chromium (Playwright, headless) | Linux-Container | ZIP-Export aus Nachweis-Dialog (Offline) | ❌ Kein Evidence-File im Dialog (`#ev_list` bleibt leer), Export nicht ausgelöst. |
