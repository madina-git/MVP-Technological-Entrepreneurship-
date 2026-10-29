# Project structure

```text
depsentry-mvp/
├── index.html              # Full MVP: HTML, CSS, and JavaScript
├── README.md               # Main project description and setup
├── START_HERE_RU.md        # Local launch instructions in Russian
├── MVP_VALIDATION.md       # MVP criteria and validation plan
├── .gitignore              # Common local/editor files excluded from Git
└── docs/
    ├── PROJECT_STRUCTURE.md
    └── DEFENSE_GUIDE_RU.md
```

## Why is the website in one file?
This is a deliberately lightweight static MVP. Keeping markup, styles, and browser-side logic in `index.html` means it can be opened locally without Node.js, package installation, a build process, or a server. The README and documentation are separate so the product implementation stays easy to run and inspect.

## Main execution flow
1. The user supplies a supported dependency manifest or a pasted list.
2. Browser-side JavaScript parses package names and exact versions.
3. The browser sends package/version queries to the public OSV.dev API.
4. Findings are displayed with severity and advisory links; OSV fixed-version thresholds are combined into one target per affected package, with an explicit warning when a complete target cannot be confirmed.
5. The combined target includes a heuristic Low risk / May break label based on the version line; it is not a compatibility guarantee.
6. The user can export JSON or use the browser print dialog to save a PDF.
7. Scan history is stored in the current browser's local storage.

## Trust boundaries
The original manifest is read in the browser and is not uploaded to a DepSentry backend because this MVP has no backend. Package names and exact versions are sent to OSV.dev for lookups. Do not use confidential internal package names if sending those names to a public API is not acceptable.
