# CrewCompMetrics — experimental Linux releases

Download version-matched binaries, full corresponding source, checksums and installation notes from [Releases](https://github.com/Crewbee/CrewCompMetrics-releases/releases).

CrewCompMetrics is a native Qt telemetry widget with configurable local and remote PCs, saved metric selections, themes and automatic/manual sizing. Missing readings stay unavailable.

## A note from Crewbee

Hi, this is Crewbee.

I've created this desktop widget to give me telemetry on all of my devices shared between my connected home network PCs in one polished interface with lots of visual customization. I am a long-time Linux user for work, and I've finally made the jump to Linux for my home system recently.

I was disappointed with the lack of solutions for a telemetry widget for Linux, and I decided to create my own using the available Qt libraries and telemetry data-gathering software, including CoolerControl in headless mode and other basic device metric sources. I also used Codex to drive the implementation.

The objective of this app is to allow users to see telemetry data for their devices across multiple PCs connected over LAN. The aim is to cover CPUs, GPUs, drives, RAM, motherboard sensors, fans, and AIO sensors wherever the hardware and Linux drivers expose those readings. Unsupported readings remain unavailable.

The current release is Alpha and may have compatibility issues with your specific setup. I'm working toward broader compatibility for v1. If you'd like to download the Alpha anyway, Ubuntu 26.04.1 is the primary tested desktop environment, though available readings will depend on your hardware and drivers.

The tested setup uses Python 3.14.4, PySide6 6.12.0, and GNOME Wayland. The package bundles PySide6 6.12.0, and the installer can install supported missing system dependencies when you use `--install-dependencies`. Python 3.12 or newer must already be available to run the installer. It does not install or replace your desktop environment; compositor Glass requires the supported GNOME 50 / Mutter 18 Wayland setup.

Any input that you have would be helpful. I will continue to work on this and get to a v1 release as soon as possible. I will update this release as soon as the compatibility version is available.

Enjoy! :]

Sincerely,  
Crewbee

## Experimental alpha

The 0.4.0a2 alpha targets Linux x86_64 with Python 3.12+, compatible glibc and a working systemd user manager with cgroup v2 CPU/memory controls. Desktop validation covers Ubuntu 26.04 / GNOME 50. Ubuntu 24.04 and Debian 13 have container installation checks, not full desktop acceptance. True Glass is limited to the validated GNOME 50 / Mutter 18 Wayland configuration. Broader desktop validation is required for v1.0. No Snap or ARM build is provided.

## Download and install 0.4.0a2

**Download the app archive, not just its checksum file.**

| File | What it contains |
| --- | --- |
| [crewcompmetrics-0.4.0a2-linux-x86_64.tar.gz](https://github.com/Crewbee/CrewCompMetrics-releases/releases/download/v0.4.0a2/crewcompmetrics-0.4.0a2-linux-x86_64.tar.gz) | **The app and installer.** Download and extract this to install. |
| [crewcompmetrics-0.4.0a2-linux-x86_64.tar.gz.sha256](https://github.com/Crewbee/CrewCompMetrics-releases/releases/download/v0.4.0a2/crewcompmetrics-0.4.0a2-linux-x86_64.tar.gz.sha256) | A small text file used to verify the app archive. **It contains no app or installer.** |
| `crewcompmetrics-0.4.0a2-source.tar.gz` and its `.sha256` | Full corresponding source and its checksum, for inspection, rebuilding or redistribution. Not needed for normal installation. |

### 1. Download both the app archive and its checksum

Open a terminal as your normal user. These commands work from your home directory and require `wget`:

```bash
mkdir -p ~/Downloads/crewcompmetrics-alpha &&
cd ~/Downloads/crewcompmetrics-alpha &&
wget -O crewcompmetrics-0.4.0a2-linux-x86_64.tar.gz https://github.com/Crewbee/CrewCompMetrics-releases/releases/download/v0.4.0a2/crewcompmetrics-0.4.0a2-linux-x86_64.tar.gz &&
wget -O crewcompmetrics-0.4.0a2-linux-x86_64.tar.gz.sha256 https://github.com/Crewbee/CrewCompMetrics-releases/releases/download/v0.4.0a2/crewcompmetrics-0.4.0a2-linux-x86_64.tar.gz.sha256 &&
sha256sum -c crewcompmetrics-0.4.0a2-linux-x86_64.tar.gz.sha256
```

Continue only if verification prints `crewcompmetrics-0.4.0a2-linux-x86_64.tar.gz: OK`.
If a download or verification fails, stop and resolve it before installing.
The `-O` options replace same-named downloads in this dedicated folder when retrying.

### 2. Extract and install

```bash
cd ~/Downloads/crewcompmetrics-alpha &&
tar -xf crewcompmetrics-0.4.0a2-linux-x86_64.tar.gz &&
cd crewcompmetrics-0.4.0a2-linux-x86_64 &&
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

## Configure your PCs

Fresh installs discover the local hostname and monitor only that PC. The bundled
`hosts.example.json` contains dummy names. Copy it to your private configuration folder
and replace its values with your own hostnames and SSH targets as described in
`docs/pc-configuration.md`. Your SSH configuration resolves your chosen server hostname
or LAN address; no developer LAN address or remote target is built in.

Existing installations retain their host profile, credentials, themes and saved selections.
The app never copies your SSH private keys into a release or onto another user's machine.

## Release contents

This release replaces 0.4.0a1. Earlier download assets have been withdrawn. Public
packages exclude personal host profiles, captured telemetry and internal maintenance
scripts. Source and wheel contents are checked before publication. The application
extension identifier and public project author attribution remain part of the software.

## Source and licensing

Original application code and generated/procedural theme artwork use GPL-3.0-or-later. Third-party licenses and notices are retained. The full corresponding-source archive includes application/native/artwork sources, build/install scripts and matching Qt/PySide/ICU sources. Download that named release asset: GitHub's automatically generated repository source snapshots contain this download repository, not the application source bundle.

This repository hosts reviewed releases and public documentation. It does not contain the private development repository's history.
