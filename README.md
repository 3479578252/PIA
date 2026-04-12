# PIA Tools

A lightweight web-based suite for conducting Privacy Impact Assessments in Australia.

---

## Overview

PIA Tools is a collection of standalone, browser-based assessment forms designed to help teams evaluate and document their privacy obligations before or during a project. It covers both health information (under Victorian law) and personal information (under Commonwealth law).

The suite is built with simplicity in mind:

- **No backend required** — all logic runs in the browser
- **No data leaves your device** — responses are stored in `localStorage` only
- **No build step** — served as static HTML from a minimal Node.js server
- **PDF export** — generate a printable report at the end of each assessment

The tools are appropriate for project managers, privacy officers, analysts, and developers who need to assess privacy risk and document their reasoning without specialist tooling.

---

## Regulatory Context

The tools are aligned to two key Australian privacy frameworks:

- **Health Records Act 2001 (Vic)** — establishes 11 **Health Privacy Principles (HPPs)** governing the handling of health information by organisations in Victoria. The health-focused tools in this suite are structured around these principles.
- **Privacy Act 1988 (Cth)** — establishes 13 **Australian Privacy Principles (APPs)** governing personal information held by Australian Government agencies and many private sector organisations. The personal information tool is structured around these principles.

These tools do not constitute legal advice. If you are uncertain about your obligations, consult a legal representative.

---

## Tools

| Tool | File | Time | Description |
|------|------|------|-------------|
| Hub | `index.html` | — | Landing page with guidance on choosing the right tool |
| Threshold Check | `threshold.html` | ~5 min | 10 yes/no questions to determine whether a PIA is needed |
| Short Assessment — Health Info | `shortform.html` | ~10–20 min | 8-step wizard for lower-risk projects involving health information (HPP-aligned) |
| Short Assessment — Personal Info | `shortform-personal.html` | ~10–20 min | 8-step wizard for lower-risk projects involving personal information (APP-aligned) |
| Full PIA | `pia.html` | ~30–40 min | Comprehensive 20-step wizard which is currently aimed at covering all 11 Health Privacy Principles |

### Choosing the right tool

- **Not sure if a PIA is needed?** Start with the Threshold Check.
- **Lower-risk project involving health information?** Use the Short Assessment — Health Info.
- **Lower-risk project involving personal (non-health) information?** Use the Short Assessment — Personal Info.
- **Complex, high-risk, or large-scale project involving sensitive health information?** Use the Full PIA.

---

## Getting Started

**Prerequisites:** [Node.js](https://nodejs.org/) (any modern version)

```bash
git clone <repo-url>
cd pia
node server.js
```

Then open [http://localhost:3000](http://localhost:3000) in your browser.

The server serves static files from the working directory on port 3000. No dependencies need to be installed.

---

## Usage

### Threshold Check (`threshold.html`)

Answer 10 yes/no questions about your project (data types involved, scale, sensitivity, third-party sharing, etc.). The tool calculates a recommendation — whether a full PIA is warranted — and can export the result as a PDF.

### Short Assessment — Health Information (`shortform.html`)

An 8-step guided form covering:

1. Project details and context
2. Types of health information involved
3. Purpose of collection and use
4. Access and disclosure controls
5. Security measures
6. Retention and destruction
7. Risk identification and mitigation
8. Summary and sign-off

Produces a PDF report with risk ratings and compliance indicators against the Health Privacy Principles.

### Short Assessment — Personal Information (`shortform-personal.html`)

An 8-step guided form covering similar ground to the health form, but oriented to personal (non-health) information and the Australian Privacy Principles — including sections on sensitive information (APP 3.3), direct marketing (APP 7), automated decision-making, and third-party vendor controls (APP 11.1).

Produces a PDF report with risk ratings and compliance indicators against the APPs.

### Full PIA (`pia.html`)

A comprehensive 20-step wizard structured in five logical groups:

1. **Setup** — project overview, scope, and stakeholders
2. **Data** — data inventory, flows, and retention
3. **HPP Analysis** — detailed analysis against each of the 11 Health Privacy Principles
4. **Assessment** — overall risk rating and mitigation planning
5. **Finalise** — sign-off, recommendations, and PDF export

Each HPP section includes embedded guidance, a compliance rating, and space to record evidence. The tool supports iterative use across multiple assessment cycles.

---

## Data & Privacy

- All form data is stored in your browser's `localStorage` — it never leaves your device
- No data is transmitted to any server
- PDF reports are generated entirely client-side using [html2pdf.js](https://github.com/eKoopmans/html2pdf.js) and [jsPDF](https://github.com/parallax/jsPDF)
- Progress is saved automatically as you type; you can close and return at any time
- Each tool includes a **Reset** button to permanently clear all saved data for that form
- No cookies, no analytics, no third-party data collection

---

## Project Structure

```
pia/
├── server.js                    # Node.js HTTP server (port 3000)
├── index.html                   # Hub / landing page
├── threshold.html               # Threshold check tool
├── shortform.html               # Short form — health information
├── shortform-personal.html      # Short form — personal information
├── pia.html                     # Full PIA tool - health information
└── LICENSE                      # MIT License
```

---

## License

This project is licensed under the [MIT License](LICENSE).
