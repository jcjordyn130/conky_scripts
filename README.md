# conky_scripts
These are scripts I made to run Conky to an external X server for the display inside of my gaming PC.

This does not use SSH, but instead, uses the TCP X11 protocol. My in-case display is running on a Raspberry Pi Zero 2W in USB network mode to the host, so there's no security risk as it's a private network.

#### Basic Operation
There's three scripts, two essential for conky:
- conky_service:
    Runs conky from a systemd service, this script kills conky during suspend prep because it crashes on resume when connected
  to a non-existent X display. It restarts on resume when the network is back up.
- conky_gpu
    This script parses the JSON output from amdgpu-top and provides a simple CLI to obtain the wanted values.
  This was made to avoid complex shell syntax inside of conky.
- conky_host_watcher
    This script runs on the system with the remote display. It turns off the display when the host goes down.
  Later it will be customized to run custom code and then sleep, for ex: a screensaver.
  
