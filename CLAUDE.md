# cc-edge-claude-code-otel

Cribl Edge pack for Claude Code telemetry collection (session logs, OTLP).

## Version Policy

This pack uses **semantic versioning**, independent of any other Cribl pack in this ecosystem.

### Rules for AI agents

- **Patch bumps** (`X.Y.Z → X.Y.Z+1`): AI may bump for bug fixes, performance improvements, and minor corrections.
- **Minor bumps** (`X.Y.z → X.Y+1.0`): AI may bump for new features, new inputs, or non-breaking changes.
- **Major bumps** (`X.y.z → X+1.0.0`): **Human only.** Never bump the major version without explicit human approval.

### Release workflow

1. Make changes on a feature branch, PR against `main`
2. Update `package.json` version (minor or patch only)
3. Update the `## Release Notes` section in `README.md` with the new version entry
4. Merge PR to main
5. Create the GitHub release directly — no local build needed:
   ```sh
   gh release create vX.Y.Z --generate-notes --repo JacobPEvans-personal/cc-edge-claude-code-otel
   ```
   `.github/workflows/release.yml` triggers on `release: published`, builds the `.crbl` archive from
   `data default package.json README.md`, and uploads both a versioned and fixed-name asset to the
   release automatically.
6. Update the pinned release URL for this pack in its consumer (`orbstack-kubernetes`,
   `k8s/monitoring/cribl-edge-standalone/statefulset.yaml`) to point at the new tag.

## File Operations

- Read files with the Read tool (NEVER cat, head, tail)
- Edit existing files with the Edit tool (NEVER sed, awk)
- Create new files with the Write tool (NEVER echo >, heredocs)
- Search file contents with the Grep tool
- Find files with the Glob tool
