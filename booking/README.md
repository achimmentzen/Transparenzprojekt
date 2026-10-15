---
title: "Booking Architecture – Living Sculpture"
layout: default
---

# Booking Architecture

Technische Spezifikation für ein automatisiertes Anfrage- und Terminverfahren des Living-Sculpture-/Transparenzprojekts.

## Ziel

Das System soll Anfragen strukturiert entgegennehmen, Vollständigkeit und Plausibilität prüfen, einen Double-Opt-in durchführen und – soweit die festgelegten Regeln erfüllt sind – einen Termin organisatorisch bestätigen.

Die öffentliche technische Dokumentation verwendet bewusst neutrale Begriffe. Konkrete persönliche oder intime Angaben gehören weder in das Repository noch in öffentliche Logs.

## Angebotsklassen

1. **Performance / Beobachtung** – Teilnahme oder Besuch ohne vereinbarten Körperkontakt.
2. **Körperbezogener Termin** – nur innerhalb eines vorher beschriebenen und ausdrücklich bestätigten Rahmens.
3. **Individuell vereinbarter/intimer Rahmen** – gesonderte Anfrage; niemals automatische Zusage.

Die genaue Beschreibung eines Termins wird nur im geschützten Buchungssystem gespeichert.

## Ablauf

REQUESTED → DOUBLE_OPT_IN_PENDING → CONFIRMED

Mögliche Alternativzustände:

REJECTED · EXPIRED · DUPLICATE · CANCELLED · WITHDRAWN · MANUAL_REVIEW

## Verbindliche technische Regeln

- Mindestalter: 18 Jahre.
- Eine Anfrage wird erst nach erfolgreichem Double-Opt-in weiterverarbeitet.
- Jede konkrete Einwilligung bleibt widerrufbar.
- Eine frühere Zustimmung oder eine Projektdelegation ersetzt keine aktuelle Zustimmung zu einer konkreten Handlung.
- Individuelle/intime Anfragen gehen immer in MANUAL_REVIEW.
- Automatisierung darf keine Zustimmung einer anderen Person ersetzen.
- Dubletten und offensichtlich missbräuchliche Anfragen werden zurückgehalten.
- Kalender- und E-Mail-Texte bleiben neutral und enthalten keine sensiblen Details.
- Keine Zugangsdaten, Tokens oder personenbezogenen Buchungsdaten im Git-Repository.

## Empfohlene technische Umsetzung

Frontend/Formular → n8n Webhook → Validierung → Dubletten-/Plausibilitätsprüfung → Double-Opt-in → Regelprüfung → Kalenderprüfung → Bestätigung oder MANUAL_REVIEW.

Für produktiven Betrieb sollten zusätzlich Rate-Limiting und CAPTCHA bzw. ein vergleichbarer Missbrauchsschutz vorgeschaltet werden.
