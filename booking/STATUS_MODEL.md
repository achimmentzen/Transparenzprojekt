# Booking Status Model

## Zustände

- REQUESTED – Anfrage eingegangen.
- DOUBLE_OPT_IN_PENDING – Bestätigung per E-Mail ausstehend.
- CONFIRMED – organisatorisch bestätigt.
- MANUAL_REVIEW – persönliche Prüfung erforderlich.
- REJECTED – abgelehnt.
- EXPIRED – Double-Opt-in nicht rechtzeitig bestätigt.
- DUPLICATE – bereits vorhandene oder doppelte Anfrage erkannt.
- CANCELLED – Termin storniert.
- WITHDRAWN – Einwilligung widerrufen.
- COMPLETED – Termin abgeschlossen.

## Übergänge

REQUESTED → DOUBLE_OPT_IN_PENDING

DOUBLE_OPT_IN_PENDING → CONFIRMED

DOUBLE_OPT_IN_PENDING → MANUAL_REVIEW

DOUBLE_OPT_IN_PENDING → EXPIRED

CONFIRMED → CANCELLED

CONFIRMED → WITHDRAWN

CONFIRMED → COMPLETED

MANUAL_REVIEW → CONFIRMED | REJECTED

Eine neue Einwilligung ist erforderlich, wenn sich der vereinbarte Rahmen wesentlich ändert.
