# Weiterleitung von burgovia.ch zu kalatg.ch

Diese statische Website ist für GitHub Pages vorbereitet. Sie leitet alle
Aufrufe von `https://burgovia.ch` direkt an `https://kalatg.ch/` weiter.

## 1. GitHub-Repository erstellen

1. Auf GitHub ein neues **öffentliches** Repository erstellen, beispielsweise
   `burgovia-redirect`.
2. Den gesamten Inhalt dieses Ordners in das Repository laden. Die Dateien
   `index.html`, `404.html`, `CNAME` und `.nojekyll` müssen im Hauptverzeichnis
   des Repositorys liegen.
3. Unter **Settings > Pages** bei **Build and deployment** die Quelle
   **Deploy from a branch** auswählen.
4. Branch **main** und Verzeichnis **/(root)** auswählen und speichern.

## 2. DNS bei Hostpoint anpassen

Die bisherigen `A`- und `AAAA`-Einträge von `burgovia.ch`, die auf Hostpoint
zeigen, durch die GitHub-Pages-Adressen ersetzen.

### A-Einträge für burgovia.ch

| Typ | Name | Wert |
| --- | --- | --- |
| A | `burgovia.ch` | `185.199.108.153` |
| A | `burgovia.ch` | `185.199.109.153` |
| A | `burgovia.ch` | `185.199.110.153` |
| A | `burgovia.ch` | `185.199.111.153` |

### Optionale AAAA-Einträge

| Typ | Name | Wert |
| --- | --- | --- |
| AAAA | `burgovia.ch` | `2606:50c0:8000::153` |
| AAAA | `burgovia.ch` | `2606:50c0:8001::153` |
| AAAA | `burgovia.ch` | `2606:50c0:8002::153` |
| AAAA | `burgovia.ch` | `2606:50c0:8003::153` |

Die bestehenden Mail-Einträge müssen unverändert erhalten bleiben:

- MX für den Mailempfang bei Hostpoint
- SPF-TXT für Hostpoint und MailerSend
- DKIM-CNAMEs `ms1._domainkey` und `ms2._domainkey`
- CNAME `mta`
- DMARC-TXT

## 3. HTTPS aktivieren

Nach erfolgreicher DNS-Erkennung unter **Settings > Pages** die Option
**Enforce HTTPS** aktivieren. GitHub stellt das Zertifikat automatisch aus;
die Ausstellung kann nach einer DNS-Änderung etwas dauern.

Erst wenn `https://burgovia.ch` ohne Zertifikatswarnung erreichbar ist, sollte
die Kontoprüfung bei MailerSend erneut eingereicht werden.

## Ziel ändern

Falls die Weiterleitung später auf eine andere Adresse zeigen soll, muss die
URL in `index.html` und `404.html` jeweils an drei Stellen ersetzt werden.
