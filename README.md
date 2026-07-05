# PMO as Code — starter template

Run your PMO from version-controlled, testable Markdown documents. This
template gives you a working [PMO as Code](https://pmoascode.com/)
repository powered by [docassert](https://github.com/c4g-john/docassert):
documents are **unit-tested on every pull request**, requirements trace end to
end, and project status is **derived from the documents** — never typed into a
slide.

**[Use this template ↗](../../generate)** to create your repo, then:

## First 10 minutes

1. **Make the gate binding** — require the checks on `main`
   (Settings → Branches, or):

   ```bash
   gh api -X PUT repos/OWNER/REPO/branches/main/protection --input - <<'JSON'
   { "required_status_checks": { "strict": true, "contexts": ["audit", "consistency"] },
     "enforce_admins": false, "required_pull_request_reviews": null, "restrictions": null }
   JSON
   ```

2. **Turn on the status dashboard** — Settings → Pages → Source: **GitHub
   Actions**, then add a repository variable `DOCASSERT_PAGES` = `true`
   (Settings → Secrets and variables → Actions → Variables). Every push to
   `main` then publishes a portfolio index plus a page per project.

3. **Optional: AI advisory checks** — add `ANTHROPIC_API_KEY` as an Actions
   secret. Structural checks gate without it; the key adds advisory scoring
   (see docassert's [privacy note](https://github.com/c4g-john/docassert#privacy)).

## Add your first real project

```bash
pipx install docassert          # or: pip install docassert

docassert new project --code AUR --name "Aurora — Customer Onboarding"
# → documents/PRJ-002-AUR/project.md   (ids auto-number; DEMO holds 001)
docassert new charter --project PRJ-002-AUR
docassert projects --out projects.yaml
docassert validate documents/**/*.md
```

Open a pull request — the audit and consistency checks run automatically and
post their results as comments. Then delete `documents/PRJ-001-DEMO/` (it
exists so day one starts green-ish).

> **Why is my status amber?** The demo project is on the `lean-startup`
> profile, which expects a charter, BRD, PRD, and test cases. Missing ones show
> on the project page as gaps — advisory while the project is `proposed`,
> blocking once it's `active`. That's the product working.

## What's in the box

```
documents/PRJ-001-DEMO/   one starter project (anchor + draft charter)
projects.yaml             generated project registry (checked in CI)
STATUS.md                 derived status snapshot
.github/workflows/        the gate (audit + consistency) and the dashboard
.claude/skills/           the doc-to-pmo skill — Claude Code can convert your
                          existing Word/PDF docs into testable documents
```

The audit criteria, schemas, templates, and profiles ship inside docassert —
run `docassert init` if you want to customize the standard for your org.

## The execution bridge (optional)

Once your user stories are approved, the bridge can run delivery from them:
Feature issues per product requirement, Story sub-issues per story, a scope
guard that flags any issue not matching the documents, and features that close
when their last story lands. Set the repository variable `BRIDGE_ENABLED` to
`true` and the three `bridge-*`/`feature-closeout` workflows take over.
Scope stays in the documents; the guide on the site covers adding a Projects
board on top.

## Learn more

- **Quickstart & concepts:** https://pmoascode.com/
- **The tool:** https://github.com/c4g-john/docassert · https://docassert.com
- **A fully built-out example:** https://github.com/c4g-john/pmo-as-code-pipeline
  (live dashboard [here](https://c4g-john.github.io/pmo-as-code-pipeline/))

*This template intentionally ships without a LICENSE — your documents are
yours. Add one if you open-source your repo.*