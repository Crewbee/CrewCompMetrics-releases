# CrewCompMetrics — experimental Linux releases

Download version-matched binaries, full corresponding source, checksums and installation notes from [Releases](https://github.com/Crewbee/CrewCompMetrics-releases/releases).

CrewCompMetrics is a native Qt telemetry widget with configurable local and remote PCs, saved metric selections, themes and automatic/manual sizing. Missing readings stay unavailable.

## Experimental alpha

The 0.4.0a1 alpha targets Linux x86_64 with Python 3.12+, compatible glibc and a working systemd user manager with cgroup v2 CPU/memory controls. Physical desktop validation covers Ubuntu 26.04.1 / GNOME 50.1. Ubuntu 24.04 and Debian 13 have container installation checks, not full desktop acceptance. True Glass is limited to the validated GNOME 50 / Mutter 18 Wayland configuration. Broader desktop validation is required for v1.0. No Snap or ARM build is provided.

Each release provides a binary `.tar.gz`, a full `-source.tar.gz`, and a `.sha256` file for each. Read the release notes and verify the checksum before extracting/installing. Optional APT installation of missing prerequisites is available; the default application installer uses offline Python wheels.

## Source and licensing

Original application code and generated/procedural theme artwork use GPL-3.0-or-later. Third-party licenses and notices are retained. The full corresponding-source archive includes application/native/artwork sources, build/install scripts and matching Qt/PySide/ICU sources. Download that named release asset: GitHub's automatically generated repository source snapshots contain this download repository, not the application source bundle.

This repository hosts reviewed releases and public documentation. It does not contain the private development repository's history.
