# Contributing to WAF Whisper

Thanks for your interest in improving WAF Whisper.

## Ground rules

- **Authorized use only.** Do not submit issues, PRs, or output that involve
  targets you were not authorized to test.
- Keep changes focused; one logical change per pull request.
- Match the existing style (standard library + `requests`, phase banners, ANSI
  status columns).

## Development

```bash
git clone https://github.com/R00t3dbyFa17h/WAF-Whisper.git
cd WAF-Whisper
pip3 install -r requirements.txt
python3 -m py_compile waf_whisper.py   # basic sanity check
```

## Pull requests

1. Fork and create a feature branch.
2. Make your change and verify `python3 -m py_compile waf_whisper.py` passes.
3. Update `README.md` / `CHANGELOG.md` if behavior or flags changed.
4. Open the PR with a clear description of what and why.

## Reporting bugs

Open an issue with your OS, Python version, the exact command, and the output
(redact any client or target data).
