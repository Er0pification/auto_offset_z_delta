## Under construction!

## This is a modified version of this : https://github.com/hawkeyexp/auto_offset_z to use voron style autoZ with delta-printer

## Requirements:<br>
1) Physical Z-Endstop - reachable with both nozzle and probe, connected parralel to ABL probe
2) Probe - currently workig with magnetically coupled microswitch probe


## Configuration for klipper:

<pre><code>
[auto_offset_z]
center_xy_position:0,0      # Center of bed for example
endstop_xy_position:0,120   # Physical endstop nozzle over pin
speed: 100                      # X/Y travel speed between the two points
z_hop: 10                       # Lift nozzle to this value after probing and for move
z_hop_speed: 20                 # Hop speed of probe
offset_min: -1                  # Optional - by default -1 is used - used as failsave to raise an error if offset is lower than this value
offset_max: 1                   # Optional - by default 1 is used - used as failsave to raise an error if offset is higher than this value
endstop_min: 0                  # Optional - by default disabled (0) - used as failsave to raise an error if endstop is lower than this value
endstop_max: 0                  # Optional - by default disabled (0) - used as failsave to raise an error if endstop is higher than this value
offsetadjust: 0.0               # Manual offset correction option - start with zero and optimize during print with babysteps
                                  1) If you need to lower the nozzle from -0.71 to -0.92 for example your value is -0.21.
                                  2) If you need to move more away from bed add a positive value.
start_gcode:          <macro name for attaching the probe>
#before_switch_gcode: <macro name for attaching the probe AFTER probing the nozzle>
end_gcode:            <macro name for docking the probe>
</code></pre>
## Installation:

Login to your pi by ssh. Clone the repo to your homefolder with this command:

<pre><code>
git clone https://github.com/Er0pification/auto_offset_z_delta.git<br>
cd ~/auto_offset_z<br>
./install.sh<br>
</code></pre>

For further updates you can add it to moonraker's updated manager:

<pre><code>
[update_manager auto_offset_z]
type: git_repo
path: ~/auto_offset_z
origin: https://github.com/Er0pification/auto_offset_z_delta.git
install_script: install.sh
</code></pre>
