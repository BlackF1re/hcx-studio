# Releasing HCX Studio

HCX Studio uses Semantic Versioning and automated GitHub releases.

## Release checklist

1. Update the version in `pyproject.toml`.
2. Add the release notes to `CHANGELOG.md`.
3. Run the complete local validation:

   ```bash
   ./scripts/check.sh
   python -m build
   python -m twine check dist/*
   ```

4. Commit and push the release preparation.
5. Create and push a matching annotated tag:

   ```bash
   git tag -a v0.2.0 -m "HCX Studio 0.2.0"
   git push origin v0.2.0
   ```

The `Release` workflow verifies that the tag matches the package version, repeats the tests and package checks, generates SHA-256 checksums and provenance, and publishes the wheel and source distribution to a GitHub Release.

## Version policy

- patch releases fix defects without intentionally changing the public workflow;
- minor releases add compatible functionality;
- major releases may introduce incompatible project, engine or workflow changes.

Do not manually upload locally built packages to a release. The workflow output is the canonical release artifact set.
