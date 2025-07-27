# deej fork with libayatana compatibility

I made this fork because the main branch uses an old library for the system tray, which current day ubuntu no longer uses, so it can not run.

**Who is this for?**
  - Ubuntu 20.04 LTS and newer
  - Linux Mint 20.x and newer (specifically tested on Mint 22)
  - Pop!_OS 20.04 and newer
  - Debian 11 and newer
  - theoretically any linux distribution that uses libayatana-appindicator3-dev instead of libappindicator3-dev

**Launch instructions**

**Prerequisites**
1. Install required system dependencies (if the os can't find libwebkit2gtk-4.0-dev you have to add a repository that has it):
  - libgtk-3-dev
  - libayatana-appindicator3-dev
  - libwebkit2gtk-4.0-dev

2. Add your user to the dialout group for Arduino access:
   ```bash
   sudo usermod -a -G dialout $USER
   ```
   Then log out and log back in for the changes to take effect.

**Setup:**
1. Connect your Arduino with the deej sketch flashed to a USB port
2. Find your Arduino's serial port:
   ```bash
   ls /dev/ttyACM* /dev/ttyUSB*
   ```
   (Usually `/dev/ttyACM0` for Arduino Nano/Uno)

3. Edit `config.yaml` and update the `com_port` setting:
   ```yaml
   com_port: /dev/ttyACM0  # or your actual port
   ```

4. Update slider mappings in `config.yaml` to use your apps:
   ```yaml
   slider_mapping:
     0: master
     1: firefox-bin          # example
     2: spotify
     3: discord
     4: steam
   ```

**Running deej:**
- Run directly: `./deej`
- Run without system tray: `DEEJ_NO_TRAY_ICON=1 ./deej`
- The application will appear in your system tray and start controlling volumes immediately

**Troubleshooting:**
- If you get "permission denied" on the serial port, make sure you're in the dialout group
- Check Arduino connection with: `cat /dev/ttyACM0` (should show slider values)
- Config file auto-reloads when changed, no need to restart deej



More detailed instructions and documentation are in the [repo's main page](https://github.com/omriharel/deej).

Enjoy!
