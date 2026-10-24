# CrewCompMetrics — experimental Linux releases

Download version-matched binaries, full corresponding source, checksums and installation notes from [Releases](https://github.com/Crewbee/CrewCompMetrics-releases/releases).

CrewCompMetrics is a native Qt telemetry widget with configurable local and remote PCs, saved metric selections, themes and automatic/manual sizing. Missing readings stay unavailable.

## Experimental alpha

The 0.4.0a1 alpha targets Linux x86_64 with Python 3.12+, compatible glibc and a working systemd user manager with cgroup v2 CPU/memory controls. Physical desktop validation covers Ubuntu 26.04.1 / GNOME 50.1. Ubuntu 24.04 and Debian 13 have container installation checks, not full desktop acceptance. True Glass is limited to the validated GNOME 50 / Mutter 18 Wayland configuration. Broader desktop validation is required for v1.0. No Snap or ARM build is provided.

## Download and install 0.4.0a1

**Download the app archive, not just its checksum file.**

| File | What it contains |
| --- | --- |
| [crewcompmetrics-0.4.0a1-linux-x86_64.tar.gz](https://github.com/Crewbee/CrewCompMetrics-releases/releases/download/v0.4.0a1/crewcompmetrics-0.4.0a1-linux-x86_64.tar.gz) | **The app and installer.** Download and extract this to install. |
| [crewcompmetrics-0.4.0a1-linux-x86_64.tar.gz.sha256](https://github.com/Crewbee/CrewCompMetrics-releases/releases/download/v0.4.0a1/crewcompmetrics-0.4.0a1-linux-x86_64.tar.gz.sha256) | A small text file used to verify the app archive. **It contains no app or installer.** |
| `crewcompmetrics-0.4.0a1-source.tar.gz` and its `.sha256` | Full corresponding source and its checksum, for inspection, rebuilding or redistribution. Not needed for normal installation. |

### 1. Download both the app archive and its checksum

Open a terminal as your normal user. These commands work from your home directory and require `wget`:

```bash
mkdir -p ~/Downloads/crewcompmetrics-alpha &&
cd ~/Downloads/crewcompmetrics-alpha &&
wget -O crewcompmetrics-0.4.0a1-linux-x86_64.tar.gz https://github.com/Crewbee/CrewCompMetrics-releases/releases/download/v0.4.0a1/crewcompmetrics-0.4.0a1-linux-x86_64.tar.gz &&
wget -O crewcompmetrics-0.4.0a1-linux-x86_64.tar.gz.sha256 https://github.com/Crewbee/CrewCompMetrics-releases/releases/download/v0.4.0a1/crewcompmetrics-0.4.0a1-linux-x86_64.tar.gz.sha256 &&
sha256sum -c crewcompmetrics-0.4.0a1-linux-x86_64.tar.gz.sha256
```

Continue only if verification prints `crewcompmetrics-0.4.0a1-linux-x86_64.tar.gz: OK`.
If a download or verification fails, stop and resolve it before installing.
The `-O` options replace same-named downloads in this dedicated folder when retrying.

### 2. Extract and install

```bash
cd ~/Downloads/crewcompmetrics-alpha &&
tar -xf crewcompmetrics-0.4.0a1-linux-x86_64.tar.gz &&
cd crewcompmetrics-0.4.0a1-linux-x86_64 &&
python3 install.py --install-dependencies &&
python3 install.py --diagnose
```

Run the installer as your **normal user**, not with `sudo python3`.
The optional dependency step requests administrator access only when APT needs to install
missing system packages on Ubuntu 24.04/26.04 or Debian 13. Review APT's confirmation.
If prerequisites are already installed, you can use `python3 install.py` instead.
On other distributions, install prerequisites manually as described in `docs/dependencies.md`.

**Run `install.py` from the extracted folder.** Running it from `~` before extraction
causes the error `can't open file '/home/your-user/install.py'`.
The `.sha256` file cannot be extracted into an installer.

### 3. Launch

Open **CrewCompMetrics** from your applications menu, or run:

```bash
~/.local/bin/crewcompmetrics
```

There is no `apt-get install crewcompmetrics` package yet. APT installs optional system
dependencies; the widget itself is installed from the downloaded bundle.
Read `INSTALL.md` and `docs/dependencies.md` inside the extracted folder for prerequisites,
collector-only installation and optional features.

## Source and licensing

Original application code and generated/procedural theme artwork use GPL-3.0-or-later. Third-party licenses and notices are retained. The full corresponding-source archive includes application/native/artwork sources, build/install scripts and matching Qt/PySide/ICU sources. Download that named release asset: GitHub's automatically generated repository source snapshots contain this download repository, not the application source bundle.

This repository hosts reviewed releases and public documentation. It does not contain the private development repository's history.
