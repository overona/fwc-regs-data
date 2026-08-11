# Florida Saltwater Fishing Regulation Data

Machine-readable Florida saltwater recreational fishing regulations, extracted
from the official [FWC website](https://myfwc.com/fishing/saltwater/recreational/)
and served as static JSON over GitHub Pages.

**These files are generated. Do not edit them by hand** — the next pipeline run
overwrites them. Corrections belong in the (private) generator repository.

## Endpoints

Base URL: `https://overona.github.io/fwc-regs-data/`

| File | Purpose |
|---|---|
| `fl/saltwater/manifest.json` | Small version pointer — the only file a running app polls |
| `fl/saltwater/latest.json` | Current dataset |
| `fl/saltwater/<version>.json` | Immutable snapshot of one version |
| `fl/saltwater/changelog.json` | Recent versions and what changed in each |

Clients should poll `manifest.json`, compare `version`, and download the
immutable `dataset_url` only when it differs — verifying the published
`sha256` before use.

## How the data is produced

Each FWC species page is fetched, converted to text, and read by an LLM into a
structured schema. **Every extracted value carries a verbatim quote that is
machine-verified to appear on the source page**, and every record carries its
source URL and fetch date. A human reviews and approves each update before it
is published here.

## Disclaimer

Provided for informational purposes with no warranty of accuracy or
completeness. Regulations change, and extraction can err. The
[FWC website](https://myfwc.com/fishing/saltwater/recreational/) is the
authoritative source — verify before you fish.

Regulation text and data originate from the Florida Fish and Wildlife
Conservation Commission.
