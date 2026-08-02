# Handover for the Next Prompt

## Repository

- Repository: `AGENTS.GUIDANCE`
- Workspace: `Z:\S\Unsynced\REPOS\BASE\AGENTS.GUIDANCE`
- Branch: `main`
- Published `HEAD` and `origin/main`: `3111a6d` (`Add perspective-based guidance entry points`)
- Documentation only: Markdown guidance, no application runtime.

## Current Worktree

The current work is intentionally local and has not been committed or pushed:

- `IMPLEMENTATION-PLAN.md`
- `engineering/humans/maintenance/documentation-register.md`
- `engineering/humans/readme.md`
- `engineering/humans/reference/catalogues/deliverable-systems.md`
- `engineering/humans/reference/catalogues/deliverables.md`
- `engineering/humans/reference/catalogues/qualities.md`
- `engineering/humans/reference/catalogues/readme.md`
- `engineering/humans/reference/catalogues/registries.md`
- `engineering/humans/reference/catalogues/regulatory-obligations.md`
- `engineering/humans/reference/catalogues/sdlc.md`
- `engineering/readme.md`
- `HANDOVER.md`
- new directory: `engineering/humans/delivery/`

`.vscode/` is local editor state and must remain excluded from commits.

## Handover Objectives

This document exists to let the next prompt continue the work quickly without reconstructing the conversation. It should preserve:

- the current repository and publication state;
- the reasoning behind the current information architecture;
- the distinction between published work and local worktree changes;
- the user's intended audience, objectives and terminology;
- the writing and navigation style expected in human-facing guidance;
- the validation commands and known path conventions; and
- the next decisions or actions that still require human judgment.

The broader repository objectives are to make meaningful software understandable, dependable and able to change; connect product purpose to delivery, operation, support, maintenance and retirement; make responsibilities, boundaries and evidence visible; and help different roles contribute to one cohesive outcome without creating duplicate bodies of guidance.

## Audience and Continuation Context

The next prompt is an engineering collaborator continuing work with the repository owner. It should assume that the user values long-term secure, performant, maintainable and understandable guidance over the smallest immediate edit. It should inspect current files before editing because the user may move or revise paragraphs between prompts.

## What Has Been Done

The repository has been developed into a human and agent engineering-guidance corpus. Published work includes:

- human and agent guidance routes;
- audit evidence and repository assessment;
- registry catalogue and Release Manager/Change Manager boundaries;
- choice-preserving human navigation;
- a meaningful-software and organisational-reputation introduction;
- perspective-based navigation from the engineering entry page.

The local work adds an explanatory delivery perspective. Delivery is described as wider than development: it includes software, data, configuration, infrastructure, dependencies, supporting material, responsibilities, operations, support, maintenance, recovery and retirement.

## Current Engineering Entry Structure

`engineering/readme.md` currently presents these separate perspectives under `Many ways into the guidance`:

1. **Delivery Team Roles**: stakeholder contributions and handoffs.
2. **Product Management and Lifecycle**: Product Manager objectives, Product Owner outcomes, Delivery Guidance, SDLC, deliverables and registries.
3. **Architecture**: systems, deliverable systems, models, domains, capabilities and external dependencies.
4. **Technical Leadership and Development**: Technical Lead Guidance, Deliverable Systems, Developer Guidance, LDMs, layers, vertical slices and contracts.
5. **Quality**: system quality, data quality and quality in use.
6. **Assurance**: testing, security, obligations, controls and evidence.
7. **Operating**: availability, capacity, resilience, observability, support, diagnosis and recovery.

The user specifically asked for these subjects to remain distinct. Do not collapse Quality into Assurance or Lifecycle into Operating. Delivery Guidance belongs with Product Management and Lifecycle. Deliverable Systems belongs under Architecture and Technical Leadership/Development.

## Catalogue Transition Work

The catalogue boundary was reviewed with fresh eyes because early links risked dropping readers into dense reference lists. The following changes were made:

- `engineering/humans/reference/catalogues/readme.md` now explains that catalogues are a shared reference layer inside the wider human route, not a separate world or mandatory journey.
- The catalogue index offers question-based entry points rather than a prescribed direction.
- Main catalogue destinations link back to Delivery Guidance where useful:
  - deliverable systems;
  - deliverables;
  - registries;
  - quality perspectives;
  - regulatory obligations;
  - SDLC.
- Those catalogue-to-delivery links use `../../delivery/readme.md` because catalogue pages are under `engineering/humans/reference/catalogues/`.
- Catalogue pages retain local onward links to neighbouring catalogues, checklists, development guidance and orientation pages.

## Writing Style

Human-facing guidance should be plain, explanatory, inclusive and choice-preserving. Explain why a subject matters before sending the reader to a dense reference page. Use short, direct paragraphs and concrete transitions. Keep related subjects distinct when they carry different questions, responsibilities or evidence.

The writing should:

- connect software to the people, organisations and outcomes that depend on it;
- describe delivery as wider than development;
- name responsibility, authority, handoff, evidence and lifecycle consequence where they matter;
- preserve uncertainty or unresolved decisions instead of inventing certainty;
- distinguish illustrative guidance from project authority, legal advice or universal technology rules; and
- use headings and links to help readers grow their understanding without forcing a single route.

Human-facing navigation should avoid reading gates such as:

- `Start with ...`
- `Read this first ...`
- `Read in this order ...`
- `Choose the page ...`
- language that makes an introduction feel like homework.

Technical rules, checklist prompts, reference material and agent conventions may still use direct or procedural language where that is their purpose.

Do not create parallel homes for catalogue concepts. Prefer a narrative perspective that explains why an authoritative catalogue matters and links to it.

## Validation

The known repository-wide validation command is PowerShell:

```powershell
git diff --check
$root = (Get-Location).Path
$missing = @()
Get-ChildItem -Recurse -File -Filter *.md |
  Where-Object { $_.FullName -notmatch '[.]git[\\/]' } |
  ForEach-Object {
    $source = $_
    $text = Get-Content -Raw -LiteralPath $source.FullName
    [regex]::Matches($text, '\[[^\]]*\]\(([^)]+)\)') |
      ForEach-Object {
        $target = $_.Groups[1].Value.Trim()
        if ($target -notmatch '^(https?://|mailto:|#)') {
          $path = ($target -split '#')[0]
          if ($path) {
            $resolved = [System.IO.Path]::GetFullPath((Join-Path $source.DirectoryName $path))
            if (-not (Test-Path -LiteralPath $resolved)) {
              $missing += ('{0}:{1}' -f $source.FullName.Substring($root.Length + 1), $target)
            }
          }
        }
      }
  }
if ($missing.Count) { $missing; exit 1 }
else { 'All repository Markdown relative links resolve.' }
```

The last validation passed after correcting the catalogue-to-delivery paths. `git diff --check` also passed.

## Recommended Next Prompt

1. Read this file and the current `git status --short`.
2. Read the current `engineering/readme.md` before editing; the user has been moving paragraphs manually.
3. Decide whether the current entry-page prose is now coherent before making more structural changes.
4. Review the local delivery perspective and catalogue transition changes as one navigation increment.
5. Run the validation above.
6. Update the implementation plan and documentation register only if the next changes create a new governed increment.
7. Stage intended files only, excluding `.vscode/`, then commit and push when the user explicitly asks for publication.

## Principles to Preserve

- Optimise for the most valuable enduring outcome, not the smallest immediate structure.
- Keep delivery broader than development.
- Keep human explanation and agent conventions aligned in intent but different in density.
- Keep roles, responsibilities, authority, evidence and lifecycle consequences visible.
- Do not claim the corpus is production-complete for regulated systems merely because navigation is improved.
