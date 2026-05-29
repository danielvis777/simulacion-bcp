# CLAUDE.md — simulacion-bcp

## Project Overview

This repository contains the assets for an **educational phishing simulation** conducted under the name of Banco BCP (Banco de Crédito del Perú). Its sole purpose is security awareness training: employees receive a simulated phishing email and, if they click the link, they land on a page that explains what happened and reinforces safe behavior.

## Repository Structure

```
simulacion-bcp/
├── plantilla_email.html   # Phishing email template (sent to participants)
├── landing.html           # Landing page shown after clicking the link
└── participantes.csv      # Participant list with tracking hashes
```

### File Details

| File | Role |
|------|------|
| `plantilla_email.html` | HTML email that mimics BCP's brand. Contains `«Nombre»` and `«Enlace»` placeholders that must be replaced per recipient before sending. |
| `landing.html` | Static page hosted at the phishing URL. Congratulates the user for identifying a phishing attempt (or informs them they clicked a simulated link). No server-side logic. |
| `participantes.csv` | Plain CSV with three columns — `Nombre`, `Correo`, `Hash` — used to personalize emails and track who clicked via unique URL hashes. |

## Placeholder Convention

`plantilla_email.html` uses **guillemet-style placeholders** (`«…»`) for dynamic values:

| Placeholder | Replace with |
|-------------|--------------|
| `«Nombre»` | Recipient's full name from `participantes.csv` |
| `«Enlace»` | Tracking URL embedding the recipient's `Hash` value |

Never send the template with unreplaced placeholders.

## participantes.csv Schema

```
Nombre,Correo,Hash
Juan Pérez,juan@tuempresa.com,user123
```

- **Nombre**: Full name used in email greeting.
- **Correo**: Destination email address.
- **Hash**: Unique token appended to the landing URL for per-user click tracking (e.g., `https://<host>/landing.html?h=user123`).

Hashes must be unique per participant. Do not reuse hashes across campaigns.

## Development Workflow

This project has no build system, package manager, or server-side code. All files are static.

### Typical Campaign Workflow

1. Update `participantes.csv` with the current participant list.
2. For each row, produce a personalized copy of `plantilla_email.html` by substituting `«Nombre»` and `«Enlace»`.
3. Host `landing.html` at the domain used for `«Enlace»`.
4. Send personalized emails via your mailer of choice.
5. Monitor click events by watching for incoming requests carrying known `Hash` values.

### Editing Templates

- Edit `plantilla_email.html` with any text/HTML editor. Keep the BCP brand colors (`#003366` navy, `#ff6600` orange) consistent.
- The footer already marks this as **"Ejercicio Educativo"** (educational exercise) in small text — do not remove this disclosure.
- `landing.html` is intentionally brief. Keep its message clear and positive.

## Key Conventions

- **Language**: All user-facing copy is in Spanish (es-PE).
- **No tracking pixels or external analytics**: the only tracking mechanism is the per-user hash in the URL.
- **No secrets in the repo**: do not commit real employee emails or sensitive hashes to version control. The `participantes.csv` currently contains example/dummy data.
- **Static only**: do not introduce server-side code, databases, or npm packages without explicit discussion.

## Branches

| Branch | Purpose |
|--------|---------|
| `main` | Stable, production-ready assets |
| `claude/claude-md-docs-GTMlg` | AI-assisted documentation and improvements |

Always develop on a feature branch and merge to `main` via pull request.

## Security & Ethics Notes

- This simulation is authorized by the organization running it.
- The email template includes a small-print disclosure identifying it as a simulation.
- Do not modify the project to harvest real credentials or remove the educational disclosure.
- Participant data (even dummy data) should be handled according to the organization's data privacy policy.
