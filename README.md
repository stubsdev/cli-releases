# stubs CLI releases

Release binaries of `stubs`, the command-line tool for the [Stubs](https://stubs.dev) Protobuf registry. It works
with your existing `buf.yaml`. This repository holds only releases and the licence and notices: no source.

## Install
- **Homebrew** (macOS and Linux): `brew install stubsdev/tap/stubs`
- **Linux and macOS, from an archive:** download `stubs_<version>_<os>_<arch>.tar.gz` and `SHA256SUMS` from
  [Releases](https://github.com/stubsdev/cli-releases/releases), check it (below), and put `stubs` on your `PATH`.
  When stubs.dev launches, `curl -fsSL https://stubs.dev/install.sh | sh` will do this in one step.
- **Windows:** download `stubs_<version>_windows_amd64.zip` (or `arm64`) from
  [Releases](https://github.com/stubsdev/cli-releases/releases), and put `stubs.exe` on your `PATH`.
- **Container:** `docker run --rm ghcr.io/stubsdev/stubs-cli:<version> --version`
- **GitHub Actions:** [`stubsdev/setup-stubs`](https://github.com/stubsdev/setup-stubs)

Then run `stubs login`.

## Verify a download
Each release has a `SHA256SUMS` file, and a Sigstore bundle (`.sigstore.json`) for it and for every archive, signed
keylessly by the release workflow.

    sha256sum --check --ignore-missing SHA256SUMS
    cosign verify-blob --bundle SHA256SUMS.sigstore.json \
      --certificate-identity-regexp '^https://github\.com/stubsdev/stubs-cli/\.github/workflows/stubs-release\.yaml@refs/tags/v' \
      --certificate-oidc-issuer https://token.actions.githubusercontent.com SHA256SUMS

## Licence
Licensed under the Apache License 2.0. See [LICENSE](LICENSE) and [NOTICE](NOTICE), which includes third-party
attributions.
