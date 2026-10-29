# MVP-Technological-Entrepreneurship-
# DepSentry — Working MVP

**Course:** Technology Entrepreneurship  
**Group:** CS-2406  
**Members:** Isak Madina, Tolganay Syrym, Madina Zhunis

## What the MVP does

DepSentry is a browser-based dependency vulnerability checker for student developers, freelancers, and small software teams. A user uploads a dependency manifest or lockfile, DepSentry reads package names and exact versions in the browser, checks them against the live public **OSV.dev vulnerability API**, and produces a prioritised report with advisory links and available fixed-version guidance.

### Supported inputs
- `package.json` — works when dependency versions are exact. If it uses ranges such as `^` or `~`, upload `package-lock.json` instead.
- `package-lock.json` — reads installed package versions from the lockfile.
- `requirements.txt` — use pinned versions such as `requests==2.32.0`.
- `pom.xml` — reads Maven dependency coordinates and concrete versions.
- A pasted list of package names and exact versions.

The MVP supports up to 150 dependencies per scan. It intentionally rejects missing/ranged versions instead of silently pretending that a non-exact version was checked. Each live query uses OSV.dev's `/v1/query` endpoint, which returns vulnerability records for a package and version. If the API is unreachable, the app displays an error and does **not** replace live findings with fake results.

## User journey
1. Open **New scan** from the sidebar or dashboard.
2. Enter a project name and upload a supported manifest, or paste dependency data.
3. Press **Check dependencies**. DepSentry parses the file in the browser and queries OSV.dev for each exact package version.
4. Review the findings sorted by severity and the combined update recommendation for each affected package. DepSentry selects the highest numeric fixed-version threshold reported across that package's advisories, shows a conservative **Low risk** / **May break** estimate based on the version line, and flags advisories without a published numeric fix.
5. Export a JSON report or use **Save PDF** in the browser print dialog.
6. Reopen previous reports from **Reports**. History is stored in the current browser only.

## Privacy and data handling
- The manifest is read locally in the browser; the original file and application source code are not uploaded to a DepSentry server.
- Package names and exact versions are sent to OSV.dev to query public vulnerability records. Do not use confidential package names if that disclosure is not acceptable for your project.
- Reports are saved in browser local storage. They are not synchronised between devices and can be removed if browser storage is cleared.
- Optional report feedback is also saved only in browser local storage; it is not transmitted to DepSentry or OSV.dev.

## Run locally
1. Extract the ZIP archive.
2. Open `index.html` in a current version of Chrome, Edge, or Firefox.
3. Select **New scan**, click **Load example**, then **Check dependencies**. An internet connection is required for live OSV.dev results.

No framework, package installation, or build step is required. For the live API, use a modern browser and a network that permits HTTPS requests to `api.osv.dev`.

## Publish as a public demo
1. Create a GitHub repository named `depsentry-mvp`.
2. Upload all project files and the `docs/` folder from this archive, preserving the folder structure. The main site file is `index.html`.
3. In **Settings → Pages**, choose **Deploy from a branch**, branch `main`, folder `/ (root)`, and save.
4. Wait for deployment and open `https://YOUR-USERNAME.github.io/depsentry-mvp/`.

GitHub Pages hosts the static interface. The live vulnerability checks are performed by OSV.dev's public API, not by a DepSentry backend.

## Scope and limitations — be transparent in the presentation
- This is a functional **MVP prototype**, not a production security product.
- The account/profile screen is a demonstration profile, not real authentication.
- There is no backend, cloud account, shared/team workspace, billing, or server-side report storage.
- It checks known advisories returned by OSV.dev; an empty result does not prove a package is secure.
- Combined update guidance compares same-major updates with broader release-branch upgrades and counts the findings each target is expected to address from OSV.dev data. If a complete target cannot be confirmed, the report says so. The Low risk / May break label is only an estimate based on likely breaking-change boundaries (major version, or minor version before 1.0), not a compatibility guarantee; re-scan and test updates before release.
- The dashboard and report history show only scans actually completed in this browser; no sample vulnerabilities are mixed into live results.

See `START_HERE_RU.md` for local launch and defense instructions, `docs/DEFENSE_GUIDE_RU.md` for a short oral-defense guide, `docs/PROJECT_STRUCTURE.md` for the code layout, and `MVP_VALIDATION.md` for the assignment-criteria checklist and validation plan.

## References
- OSV.dev. (n.d.). *API documentation*. https://google.github.io/osv.dev/api/
- OSV.dev. (n.d.). *POST /v1/query*. https://google.github.io/osv.dev/post-v1-query/
- GitHub. (n.d.). *What is GitHub Pages?* https://docs.github.com/en/pages/getting-started-with-github-pages/what-is-github-pages
