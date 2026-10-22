# DSH Replica

A native DeepSeek Harness bundle preserving 11 product-engineering workflows from the MIT-licensed [Replica skill pack](https://github.com/Jakeschincariol/replica-skill).

**Status:** Ported source archive and local checks are available; this GitHub repository is being bootstrapped and does not yet contain the complete source tree. Do not install from GitHub until the full tree is pushed.

## Workflows

- `replica-recon`: map screens, flows, data model and features
- `replica-architect`: plan stack, schema, APIs and build sequence
- `replica-design`: design tokens, components and contrast checks
- `replica-build`: implement the original app's functional equivalent clean-room style
- `replica-backend`: implement auth, storage, billing and official API integrations
- `replica-test`: plans, tests, bug reports and fix loop
- `replica-diff`: weighted feature parity and screenshot layout comparison
- `replica-entrepreneur`: evidence-backed customer-feedback analysis
- `replica-brand`: original name/palette/voice and leftover scan
- `replica-launch`: landing page, pricing and app-store listing checks
- `replica-deploy`: production preflight and explicit go-live gate

The package includes six standard-library Python utilities, reusable templates, an embedded DSH Skill provider, structural validation, CI, and tests.

## Port archive

Download the [full source ZIP from this ChatGPT response] if the repository is still incomplete. The archive should be uploaded/extracted into this repository before using the DSH installer.

## Clean-room and safety boundaries

Rebuild functionality and UX patterns; do not copy proprietary source, logos, text, licensed assets, catalogues, private APIs, or owned customer networks. Use permitted public information and the user's own account only. Never invent review claims or quotations. Keep reference screenshots out of shipped products. Never store credentials in the repo. Production deployment must stop for any failed preflight and requires explicit user approval.

The Skills do not grant extra file, shell, browser, network, Python, credential or deployment permissions. Use only capabilities available in the installed Harness and respect its confirmation policies.

## Install after full publication

Use the plugin/bundle command documented for your installed DSH version, for example:

```bash
dsh plugin --profile web add "github:mulqizamzam/dsh-replica#main"
```

Restart the Harness and verify the bundle is active. Confirm the exact command for your DSH release in the [official DeepSeek Harness repository](https://github.com/deepseek-ai/deepseek-harness).

## Validate locally

Requirements: Python 3.8+ for utilities; the currently inspected DSH root manifest requires Node.js `^22.19.0 || >=24.0.0`.

```bash
python scripts/validate_dsh_plugin.py .
python -m unittest discover -s tests -v
node tests/test_provider.mjs
python skills/replica-design/contrast.py skills/replica-design/tokens.json
```

## Attribution and license

MIT. The upstream project was authored by Jake Schincariol; retain the attribution in [NOTICE.md](NOTICE.md) and the upstream terms in [LICENSE](LICENSE). This port is not affiliated with or endorsed by DeepSeek.
