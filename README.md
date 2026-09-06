# scoop-bucket

A personal [Scoop](https://scoop.sh) bucket.

```powershell
scoop bucket add stan-ely https://github.com/stan-ely/scoop-bucket
```

| Manifest | What it is | Install |
| --- | --- | --- |
| `qrdrop` | Send a file straight from one device to another, end-to-end encrypted — the CLI | `scoop install stan-ely/qrdrop` |
| `qrdrop-app` | The same thing as a desktop app | `scoop install stan-ely/qrdrop-app` |
| `whisperforge` | GPU-accelerated speech-to-text CLI | `scoop install stan-ely/whisperforge` |

`qrdrop` and `qrdrop-app` are two different things and both are real: the first is
the command-line tool, installed from the npm registry tarball with Node from the
main bucket; the second is the desktop application, installed as a portable binary
from the project's GitHub releases. Installing one does not give you the other.

## These manifests are generated

`qrdrop.json` and `qrdrop-app.json` are written by release workflows in
[stan-ely/qrdrop](https://github.com/stan-ely/qrdrop) — `.github/workflows/publish.yml`
and `.github/workflows/app-release.yml` respectively. **Hand edits here are overwritten
on the next release.** Change the generator in that repository instead.

## A note on qrdrop-app and code signing

The desktop app is not code-signed — there is no Windows code-signing certificate
behind the project. Windows SmartScreen may warn about it. That warning is accurate:
nobody has vouched for the binary. Every file it is installed from carries a build
provenance attestation, which is a verifiable claim about where it was built and is
not a signature:

```powershell
gh attestation verify <file> --repo stan-ely/qrdrop
```
