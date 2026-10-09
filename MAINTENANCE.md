# ReinfyTeam maintenance

## Upstream compatibility watch

The `Check upstream compatibility` workflow checks the latest stable releases of Axolotl-PM and DevTools against the tested baselines in [`maintenance-baseline.json`](maintenance-baseline.json).

The scheduled run reports newer stable releases but does not change source, dependency pins, workflow references or releases. Use `workflow_dispatch` with `fail_on_update` enabled when a compatibility review should be a required check.

When an update is reported:

1. Review the release notes and resolve the exact release tag to its commit.
2. Run the affected ReinfyTeam repository gates: Composer validation, PHPStan max, tests, PHAR build/inspection and isolated Axolotl-PM runtime smoke as applicable.
3. Update only the affected repository and this organization-owned baseline after the gates pass.
4. Keep the previous tested tag and commit in the progress record as the rollback reference.

This watch is specific to ReinfyTeam. It does not modify or report thebigcrafter repository state.
