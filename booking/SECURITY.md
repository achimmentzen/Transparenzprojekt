# Booking Security and Privacy

## Keine Geheimnisse in GitHub

Nicht speichern:

- API-Keys
- OAuth tokens
- Webhook secrets
- Passwörter
- echte Buchungsdatensätze
- sensible Kontakt- oder Intimdetails

## Double-Opt-in

Der Bestätigungslink soll einen zufälligen, einmaligen Token enthalten und nach einer kurzen Frist ablaufen. Der Token darf nicht die eigentlichen Buchungsdaten enthalten.

## Dublettenprüfung

Mindestens folgende Merkmale können für die technische Prüfung kombiniert werden:

- normalisierte E-Mail-Adresse
- gewünschter Zeitraum
- vorhandene Booking-ID
- bereits bestätigte Anfrage

Eine Dublettenprüfung darf nicht als alleinige Grundlage für eine Ablehnung dienen, wenn dadurch legitime Personen fälschlich ausgeschlossen werden könnten.

## Intime oder individuelle Anfragen

Solche Anfragen werden technisch nur erfasst und zur persönlichen Prüfung weitergeleitet. Eine automatisierte Terminbestätigung ist dafür nicht vorgesehen.

## Einwilligung

Ein Widerruf hat Vorrang vor früheren Zustimmungen. Das System muss einen Widerruf in den Status WITHDRAWN überführen können.

## Logging

Logs sollen nur technische Ereignisse enthalten. Sensible Inhalte gehören nicht in öffentlich einsehbare Logs oder Commit-Nachrichten.
