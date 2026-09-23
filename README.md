# RMTI Sandbox — Disaster Science
drmarolla/rmti-disaster-science-sandbox   https://zenodo.org/badge/DOI/10.5281/zenodo.22909082.svg
**An interactive reference implementation of the Risk Mechanism Theory Index (RMTI) for urban, infrastructure and disaster-risk assessment.**
By Dr. Cesar Marolla

### ▶ Open the live sandbox: [https://drmarolla.github.io/rmti-disaster-science-sandbox/]

> **Educational and research use only.** This sandbox is a teaching companion. Its scores are relative, rubric-based indices, not forecasts, engineering assessments or actuarial figures. It is **not** a substitute for a professionally validated hazard or risk assessment, and it is not an emergency-management or life-safety decision tool. Please read [DISCLAIMER.md](DISCLAIMER.md).

## What it is

RMTI scores risk on one bounded 0–1 scale: likelihood, exposure and vulnerability raise the score, and resilience brings it down. In the Urban & Infrastructure domain:

- **Exposure** carries population and siting,
- **Vulnerability** carries fiscal, governance and service fragility,
- **Resilience** carries coping and continuity capacity, and
- **Consequence** is scored on a five-level scale from negligible to catastrophic.

## What you can do

- **Urban & Infrastructure tab:** load a worked city example (Bamako, Lagos, Lilongwe, Nairobi, Dar es Salaam, Lusaka), move the sliders, and compare the score *now* against a planned resilience investment. The example inputs are teaching illustrations, not official assessments of those cities.
- **Custom / Your Field tab:** type the name of your own field and case (for example a supply chain, an ESG portfolio, a port or a power grid), optionally relabel the five inputs, and save cases as chips for the current browser session.
- Read the score, its tier, the relative expected-loss index, the per-capita view and the size of the risk reduction from the planned investment.

## The model

The sandbox implements the RMTI scoring equations. All inputs are on a 0–1 scale unless noted.

| Quantity | Equation |
|---|---|
| Inherent risk | `IR = L · E · V` |
| Residual risk score | `R = IR · (1 − ρ)` (bounded 0–1) |
| Expected annual loss (relative index) | `EAL = L · C · (1 − ρ)` |
| Log-normalized exposure helper | `E_log(N) = [log10(N) − log10(N_min)] / [log10(N_max) − log10(N_min)]`, clamped to 0–1 |

`L` = likelihood, `E` = exposure, `V` = vulnerability, `ρ` = resilience, `C` = consequence. Resilience enters as `(1 − ρ)`, never as `ρ`, so more coping capacity always lowers the score. The consequence level (1–5) maps to `C = 0.10, 0.30, 0.50, 0.75, 1.00`.

**Fixed tier bands** (set in advance and not adjustable in the tool):

| Tier | R |
|---|---|
| Low | < 0.05 |
| Moderate | 0.05 – 0.15 |
| High | 0.15 – 0.35 |
| Severe | 0.35 – 0.60 |
| Critical | ≥ 0.60 |

Rounding follows the half-up convention so that browser results match the Python reference implementation of the model.

## Privacy

The sandbox is a single self-contained HTML file. All calculations run in your browser. There are no accounts, no analytics and no server that receives what you type. Saved cases exist only in the open browser tab and disappear when you reload or close it. The page does load its web fonts from Google Fonts, so your browser contacts that service to display them; nothing you enter is sent.

## Run it yourself

Download `index.html` and open it in any modern browser, or host it for free on GitHub Pages, Netlify or Vercel. On GitHub Pages: *Settings → Pages → Deploy from a branch → `main` / root*.

## Cite this software

Use GitHub's **Cite this repository** button (right-hand sidebar; it reads `CITATION.cff`). Released versions are archived on Zenodo, and the DOI is shown in this repository once it has been assigned.

Please also cite the RMTI publication on which the method rests:

> Marolla, C. (2025). Enhancing urban resilience to California wildfires: A systemic risk mechanism design and theory framework for a comprehensive risk assessment. *International Journal of Management and Data Analytics, 5*(1), 60–77. https://doi.org/10.5281/zenodo.14948760

## Related work

- Marolla, C. *Risk by Design: Integrating Disaster, Environment, and Health in the Urban Century.* CRC Press / Taylor & Francis. *In preparation.*
- The oncology and public-health surveillance version of the sandbox is a separate tool with its own scope and notices: [https://drmarolla.github.io/rmti-oncology-sandbox/](https://drmarolla.github.io/rmti-oncology-sandbox/).

## License

The software is released under the [MIT License](LICENSE). The MIT License covers the code. The RMTI method, rubrics and tier structure are the author's published work and should be cited when used.

This is an independent academic tool. It is not an official product of the World Bank Group or of any other institution.
