# Asahi-Control-Center
Power and settings, including fan control, power profiles, and temperature monitoring.
# Asahi Control Center v1.4.4

<img width="2550" height="1572" alt="Screenshot_20261115_181230" src="https://github.com/user-attachments/assets/9ba4e7f3-3bf2-4ff0-abae-12844f0c7659" />


### Highlights

- Dark, rounded interface with purple accents and a custom glossy blue battery icon.
- Battery charge, health and available battery information.
- Charging start/end thresholds **when exposed by the kernel**; supported changes may require Polkit administrator authorization.
- Temperature monitoring with optional simplified, meaningful sensor names.
- Fan readings when supported; no manual fan control.
- Available power-mode display and selection when supported by the host system.
- Apple Silicon Mac identification and hardware overview.
- OpenRC and systemd installation selection; no background monitoring daemon required.
- KDE application-menu launcher and an uninstall script.

## Requirements

**Required**

- Linux on a supported Apple Silicon Mac with an Asahi-compatible kernel and exposed hardware interfaces.
- Python 3 with `venv`/`ensurepip` support.
- Qt 6 / **PySide6 >= 6.5**. The installer first tries the system PySide6 package and otherwise attempts installation in a local Python virtual environment using pip; an internet connection may be required.
- Bash and standard Linux command-line utilities.
- A graphical desktop environment with Qt 6 support (designed for KDE Plasma; other Linux desktops may work).

**Optional / feature-dependent**

- `pkexec` (Polkit) and a graphical authentication agent for charging-threshold writes requiring elevated permissions. Your distribution's policy may disallow the write.
- `powerprofilesctl` or a writable supported platform-profile interface for power-mode changes.
- Hardware/kernel interfaces under `/sys/class/power_supply`, `/sys/class/hwmon`, and thermal sysfs for the corresponding readings.
- `kbuildsycoca6` and `desktop-file-validate` for KDE menu-cache updates and desktop-entry validation.

**Important:** Charging thresholds, fan data, and power modes are not available on every Mac or Linux kernel. The application cannot enable functionality that the underlying driver does not expose.

## Installation

   ```bash
  unzip Asahi-Control-Center-v1.4.3-final.zip
  cd Asahi-Control-Center-v1.4.3-final
  chmod +x install.sh
  ./install.sh
   ```

4. Choose **systemd**, **OpenRC**, or **Auto** when prompted.
5. Open **Asahi Control Center** from the KDE application menu, or run:

   ```bash
   bash launch.sh
   ```

**Do not run the installer as root.** It installs a user-local virtual environment, launcher, and icons. No manual `chmod` step is required.

### Uninstall

From the original extracted application directory:

```bash
bash uninstall.sh
```

The uninstaller removes the per-user launcher and installed icons. Review the uninstall script for retained files and logs before deleting the application directory.

### Troubleshooting

If the application does not launch, start it using `bash launch.sh` from a terminal. For error details, inspect:

```bash
tail -n 100 ~/.local/state/asahi-control-center/launch.log
```

If the KDE taskbar shows an old icon, remove the old pinned launcher, reinstall, then pin the newly installed application.

## Release notes — 1.4.3

- Refined rounded charging controls and centered percentage readouts.
- Added a glossy blue battery icon and KDE launcher integration.
- Fixed the Settings checkbox painting crash caused by an invalid Qt pen-cap constant.
- Improved the simplified-sensor-name preference update behavior.
- Corrected desktop-entry categories to avoid duplicate KDE menu-category warnings.
- Made the installer and launcher resilient to archive extraction that drops executable permissions.
- Retained **Developer: Ryan** in the About information.

### Testing and limitations

Source syntax, shell syntax, and ZIP integrity have been checked in previous packaging iterations. This release has **not** been fully verified on all Asahi Linux hardware, desktop configurations, or Polkit setups. The interface image above is a concept preview rather than an actual captured screenshot.

## License

A software license is **not specified in the current source package**. Add a `LICENSE` file before presenting the repository as open source or accepting contributions under a particular license.
