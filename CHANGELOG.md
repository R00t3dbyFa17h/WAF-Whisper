# Changelog

All notable changes to WAF Whisper are documented here. The format is based on
[Keep a Changelog](https://keepachangelog.com/en/1.1.0/) and this project
adheres to [Semantic Versioning](https://semver.org/spec/v2.0.0.html).

## [5.1.0] — 2026
### Added
- Extracted into a standalone, installable project (`pip install .`, `waf-whisper` entry point).
- Packaging (`pyproject.toml`), CI, SECURITY and CONTRIBUTING docs.
- Markdown bypass report + auto-generated PoC skeleton.
- Blind time-based verification phase.

### Notes
- Previously distributed inside the `hacking-tools` monorepo; history begins fresh here.
- See `README.md` for the full version history of the evasion engine (1.0 → 5.1).
