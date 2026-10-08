# Archive manifest - orbit

Authority: `authorities/orbit` @ 0.1.0 - generated 2026-10-08T23:02:03+00:00 UTC

| file | role | sha256 (first 16) | size |
|---|---|---|---|
| `.site-state.json` | refresh state (pack hash, version, artifact set) | `81a16056c01d06ec` | 1192 |
| `agent-brief.md` | asset | `e37396bccae12d3d` | 2225 |
| `audit.jsonl` | machine-recorded authority call trace | `1fb633c5722cb391` | 39692 |
| `brief.md` | build brief | `6c6d5d4122ee3d9d` | 2289 |
| `index.html` | page | `4ae5cb1d6b78261e` | 55941 |
| `log.md` | build log (agent, 1:1 with audit.jsonl) | `f8a8dc335ddbaef6` | 30455 |
| `refresh-log.md` | refresh log (generated layers vs pack) | `27d77d396fbed48c` | 2794 |
| `run-authority` | audited runner (build-time tool) | `6820fc2e2533a95e` | 1030 |
| `styles.css` | stylesheet | `8338eac07da19115` | 10366 |
| `.design-authority/gaps.jsonl` | gap store (filed gaps) | `ff3c62d888d6c0ee` | 1576 |

External references: 1 (must be 0).


Verify: `python3 tools/archive_authority_assets.py --verify orbit`
