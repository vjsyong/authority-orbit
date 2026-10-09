# Agent brief: build under the Orbit Interface System authority

Authority repo: `authority-orbit` (v0.1.0, format 0.1). A minimal interface system derived from the NASA Graphics Standards Manual (1976) for the Design Authority portability spike. Carries no NASA marks.

Reference build (what "look like this" means for this authority):
  https://designauthority.seanyong.xyz/authorities/orbit/site/
Every recorded selector, state and note, in one directory:
  https://designauthority.seanyong.xyz/authorities/orbit/site/#artefacts

Build an interface that conforms to THIS authority alone.

## Setup (public repos, MIT; stdlib-only CLI)

Get the pack - either route works; the zip also carries this authority's
reference build, fonts and manifests:

Route A - bundle zip (one download):

    curl -fsSL -o orbit-site.zip https://designauthority.seanyong.xyz/authorities/orbit/site/download/orbit-site.zip
    python3 -c "import zipfile; zipfile.ZipFile('orbit-site.zip').extractall('orbit-authority')"

Route B - git (the pack is its own repository):

    git clone --depth 1 https://github.com/vjsyong/authority-orbit.git /tmp/authority-orbit

Tooling (same for both routes):

    git clone --depth 1 https://github.com/vjsyong/design-authority.git /tmp/design-authority
    cd /tmp/design-authority
    export PACK=/tmp/authority-orbit      # Route B
    # or, from where you unzipped:  export PACK="$PWD/orbit-authority/pack"   # Route A

Sanity check (prints the authority overview):

    python3 tools/da.py --pack "$PACK" overview

## The loop, for every design decision

1. Resolve each need in natural language:
   python3 tools/da.py --pack "$PACK" resolve "primary button" --json
2. Inspect every record before adopting it:
   python3 tools/da.py --pack "$PACK" inspect <id>
3. ADOPT THE RECORDED SELECTOR along with the recorded values: the
   verification contract below addresses elements by their recorded class
   names (.cta, .card, .dlg, .ledger, .badge, ...). Keep those names on the
   elements you build; if you must deviate, declare it in verify.map.json
   (see Verify below).
4. Adopt only records shipped by this authority. Never borrow another's
   components, values or classes.
5. When the authority is silent: build from the nearest recorded pieces, keep
   the improvisation visible (an HTML comment plus data-improv="<reason>"),
   and file it:
   python3 tools/da.py --pack "$PACK" gap-add --need "<need>" \
     --context '{"source":"<your app>"}' --workspace .design-authority

## Verify before you claim done

This pack does not ship a verification contract yet, so run the checks you
can: quote recorded values from the artefacts directory, resolve and inspect
every decision, and file a gap wherever the authority is silent
(`da.py gap-add`). When a `verification.json` contract ships in this pack,
run it before claiming done:

    python3 tools/da_verify.py --pack "$PACK" --target <your-app-dir> --out .verify

## House rules

- Quote recorded values (colours, sizes, radii, type) from the records; never
  invent values that a record can give you.
- Copy selectors and states from the artefacts directory, not from memory.
- Plain HTML/CSS is enough; the authority requires no framework.
- An agent's own report is evidence, not proof. Re-read the artifacts, then
  run the verification contract.

## Take it away

- Download the reference build in one file (page, styles, fonts, the pack, the
  full audit trail):
  https://designauthority.seanyong.xyz/authorities/orbit/site/download/orbit-site.zip
- Inside the zip, `site/` is the shipped build and `pack/` is the same authority
  data this CLI reads; `site/MANIFEST.md` lists sha256 hashes for everything.
- `quickstart.sh` wires the pack and prints the first commands.
