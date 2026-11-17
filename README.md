# Asahi Control Center — 2.0 RC1

<img width="2560" height="1536" alt="Screenshot_20261116_230213" src="https://github.com/user-attachments/assets/425033e6-e1d6-4d44-ac3e-1b0f6b4127d8" />

A native Rust/GTK4 control center for Apple Silicon Macs running Asahi Linux. The interface uses the navy, blue-violet and turquoise styling of Asahi Startup Disk.

## Features

- **Overview:** battery status and health, device details, selected temperatures, charging controls, and system status.
- **Power & Battery:** current battery information, supported charging start/stop thresholds, and available power profiles.
- **Temperatures:** live readings from available kernel sensors.
- **Fans:** detected fan tachometers; fanless machines are supported.
- **This Mac:** automatically detected model, kernel and Linux distribution.
- **Settings:** monitoring interval and dashboard sensor selection.
- **About:** version, developer, and application information.

Hardware controls are capability-dependent. An unsupported sysfs charging threshold or unavailable power-profile service cannot be enabled by the application.

## Build and install

Requires Rust/Cargo, `pkg-config`, GTK4 development files, and a Linux system. On Gentoo, install the matching development dependencies using Portage before building.

```sh
unzip Asahi-Control-Center-2.0-RC1-final.zip
cd Asahi-Control-Center-2.0-RC1-final
chmod +x install.sh to install or chmod +x uninstall.sh to uninstall
./install.sh to install or ./uninstall.sh to uninstall
```

The installer compiles a release binary, installs it to `/usr/local/bin/asahi-control-center`, and installs the desktop entry and bundled icons. Run the application from your launcher or with `asahi-control-center`.

To compile without installing:

```sh
cargo build --release
```

## Full uninstall

```sh
./uninstall.sh
```

The uninstaller removes the installed binary, desktop entry, bundled icons, and application-specific preferences/cache for the invoking desktop user. **Saved settings are not retained.** It does not remove system libraries or other Asahi applications.

## Notes

- Privileged changes may prompt for administrator authorization through `pkexec`.
- Sensor names and available controls are determined by the running kernel and installed services.
- This is a **release candidate**; test charging thresholds and power-profile switching on supported hardware before relying on them.
- This source archive has been checked for packaging integrity and installer syntax, but a full GTK4 build and visual test on Gentoo have not been completed here.

## Release information

**Version:** 2.0 RC1 (`2.0.0-rc1` in Cargo)  
**Developer:** Ryan  
**Framework:** Rust / GTK4

### Overview icon consistency
Charging Controls and Live Temperatures now use matching cyan/blue illustrated SVG icons with PNG fallback, alongside Power Profile and System Status.
