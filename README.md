# Human History Timeline

Single-page browser timeline for historical events, including clearly separated factual, probable, hypothetical, traditional, and auto-reference entries.

## Run Locally

Open `timeline.html` directly in a browser, or serve the folder:

```sh
python3 -m http.server 4173
```

Then visit `http://localhost:4173/timeline.html`.

## Event Schema

Curated events live in the `EVENTS` array in `timeline.html`.

```js
{
  id: 'e_example',
  name: 'Example Event',
  year: -1200,
  minTier: 3,
  cat: 'society',
  imp: 0.55,
  loc: [39.96, 26.24, 11, 'Display Location'],
  span: [-1250, -1180],
  evidence: 'hypothesis',
  confidence: 0.32,
  source: 'Short source or provenance note.',
  desc: 'One-sentence summary.',
  detail: 'Longer explanation shown in the side panel.'
}
```

Required fields: `id`, `name`, `year`, `minTier`, `cat`, `imp`, `desc`, `detail`.

Optional fields:
- `loc`: `[lat, lng, zoom, label]` for the map.
- `span`: `[startYear, endYear]` for events or periods that cover a range.
- `evidence`: defaults to `proven` for curated events.
- `confidence`: `0` to `1`; defaults by evidence type.
- `source`: short provenance note shown in the detail panel.

## Evidence Types

- `proven`: Well-supported by direct sources, archaeology, dated artifacts, inscriptions, or broad scholarly consensus.
- `probable`: Likely or broadly accepted, but date, location, cause, or exact framing remains approximate.
- `hypothesis`: Debated reconstruction or proposed explanation.
- `traditional`: Legendary, religious, oral, or literary tradition shown for context.
- `reference`: Auto-loaded Wikipedia reference item that still needs curation.

The top evidence filters can hide or show each type. On the canvas, proven events are solid, hypotheses are hollow/dashed, traditional entries have a diagonal mark, probable entries have an extra ring, and auto-reference items are quieter.
