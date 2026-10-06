# Naples Sea-Level Bathtub Inundation Viewer

This repository contains a GitHub Pages–ready interactive viewer for screening sea-level-rise and tide inundation in coastal Naples, Florida. It is the baseline application for the graduate-student project **LLM-Powered Dashboard for Sea-Level “Bathtub” Inundation Mapping in South Florida**.

## Live viewer features

- Satellite basemap with attribution
- 2050 and 2100 scenario selectors
- SSP2-4.5 and SSP5-8.5 presets
- Adjustable sea-level-rise and tide values
- Coastal-connectivity-constrained bathtub inundation
- Flood-depth hover readout and opacity control
- Built-in method, scenario, and limitation documentation
- Embedded elevation and boundary data; no separate data download is required

## Repository files

| File | Purpose |
| --- | --- |
| `index.html` | Complete interactive viewer and embedded data |
| `.nojekyll` | Publishes the static files directly without a Jekyll build |
| `README.md` | Project and deployment documentation |
| `PROJECT_BRIEF.md` | Suggested graduate-student LLM development scope |

## Publish with GitHub Pages

1. Sign in to GitHub and create a new repository. A suggested name is `south-florida-bathtub-dashboard`.
2. Extract the provided ZIP file on your computer. Do **not** upload the ZIP itself.
3. Open the repository and choose **Add file → Upload files**.
4. Upload the four extracted files listed above, keeping `index.html` in the repository root.
5. Add a commit message such as `Add bathtub inundation viewer`, then commit the files to `main`.
6. Open **Settings → Pages**.
7. Under **Build and deployment**, set **Source** to **Deploy from a branch**.
8. Select branch **main**, folder **/(root)**, and click **Save**.
9. After deployment finishes, use **Visit site** on the Pages settings screen.

For a project repository, the public URL normally follows this pattern:

```text
https://YOUR-USERNAME.github.io/south-florida-bathtub-dashboard/
```

GitHub notes that publication can take up to about 10 minutes after a change is pushed.

## Updating the site

To publish a revised viewer, replace `index.html` in the repository and commit the change to `main`. GitHub Pages will redeploy automatically from the configured source.

## Important deployment notes

- GitHub Pages is a public static-hosting service in the normal configuration. Do not place passwords, API keys, private data, or unpublished sensitive information in the repository or HTML.
- The current viewer does not require a backend. It loads Leaflet and the Esri satellite tiles through the internet.
- A public LLM feature should not place an OpenAI or other provider API key directly in browser JavaScript. Use a protected server-side or serverless endpoint for model calls.
- The current calculations are screening-level bathtub results, not a dynamic hydraulic simulation.

## Local preview

The file can be opened directly in a modern browser. A small local web server is preferable for development:

```bash
python -m http.server 8000
```

Then open `http://localhost:8000/`.

## Technical summary

The selected water level is calculated as sea-level rise plus tide after converting tide from feet to meters. Cells at or below that level are potential flood cells. The viewer retains only connected cells seeded from low coastal/source-water elevations and calculates depth as total water level minus DEM elevation.

## Data and interpretation

Verify the elevation datum, scenario source, DEM provenance, and licensing before research publication or operational use. Results depend on DEM resolution and vertical accuracy and do not explicitly simulate storm surge dynamics, waves, drainage infrastructure, levees, culverts, groundwater, or time-varying flow.
