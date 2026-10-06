# Graduate Student Development Brief

## Project title

**LLM-Powered Dashboard for Sea-Level “Bathtub” Inundation Mapping in South Florida**

## Starting point

The provided `index.html` is a working, static browser application for Naples, Florida. It already performs scenario selection, coastal-connectivity-constrained bathtub inundation, flood-depth display, and map visualization. Elevation and boundary data are embedded in the file.

## Development objective

Extend the baseline viewer into a transparent LLM-assisted dashboard that helps users select, compare, explain, and document inundation scenarios without allowing the language model to alter the physical calculations silently.

## Recommended functions

1. **Natural-language scenario setup** — Interpret requests such as “show a 2100 high-emissions scenario with a 4.5-foot tide,” then display the parsed numeric inputs for user confirmation.
2. **Plain-language explanations** — Explain water level, flooded area, maximum depth, assumptions, and limitations using the calculated dashboard outputs.
3. **Scenario comparison** — Compare two selected scenarios and summarize changes in inundated area and depth.
4. **Location-aware interpretation** — Explain results for a clicked or searched location while clearly distinguishing mapped evidence from general guidance.
5. **Exportable summary** — Produce a concise report containing inputs, outputs, map timestamp, method, limitations, and provenance.
6. **Guardrails** — Refuse to present screening results as forecasts, emergency instructions, parcel-scale determinations, or engineering design.

## Required design principle

Use deterministic code for all calculations. The LLM may translate user intent into proposed controls and explain verified outputs, but it should not invent scenario values, flood depths, affected areas, citations, or model results.

## Suggested architecture

```text
User question
    ↓
LLM intent parser
    ↓
Validated scenario controls
    ↓
Existing deterministic bathtub engine
    ↓
Structured results (water level, area, depth)
    ↓
LLM explanation with assumptions and warnings
```

## Security constraint

GitHub Pages serves static browser files. Never embed a private LLM API key in `index.html`. Route model requests through an authenticated backend or serverless function, apply rate limits, restrict allowed operations, and return only the data needed by the browser.

## Suggested student deliverables

- Revised dashboard source code and deployment instructions
- Working GitHub Pages front end
- Protected LLM service or a documented local/mock mode
- Prompt and response schema
- Input-validation and guardrail tests
- Scenario comparison and report export
- Short technical report describing data, assumptions, architecture, evaluation, limitations, and reproducibility

## Evaluation criteria

- Correct preservation of the original bathtub calculations
- Transparent unit conversion and scenario provenance
- No unsupported or fabricated quantitative statements
- Clear separation of model calculations and LLM explanations
- Secure secret handling
- Accessible and responsive interface
- Reproducible deployment and documented limitations
