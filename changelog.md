# change log 
## v113:
* add boost factor in inputs.yaml (can be used in hassio for forecast weather temperature boosts)
## v112:
* set the thermostat to single point only (dual point takes the mean of target_temperature_high and target_temperature_low and the hystereris is not taken into calculation)
## v111:
* heating_channel_PID.yaml:
add autotune button + sensors
delete interval check (useless)
## v110:
* add heating_channel_remote_controlled.yaml template
## v109:
* add heating_channel_tanh.yaml template
* rename heating_channel.yaml template to heating_channel_linear.yaml template
## v108:
* add heating_channel_PID.yaml template
* test PID in config (commented out)
## v107:
* add 3 climate presets
## v106:
* valve calibration on boot delay moved to config
* schedule reboot moved to config
* add 200ms delay for gpio switching (allow for switching time and any discharge)
* enable webserver by default
* enable fallback hotspot (captive portal) in case wifi connection fails
* add message if min movement is not reached
## v105:
* Packages as template : https://esphome.io/guides/configuration-types.html#packages-as-templates
* board type and framework moved to config.yaml
* ntp settings moved to config
* switch interlock replaced with on_turn_on action (not compatible with templates)
* removing internal_temperature sensor as causing many logs : [D][internal_temperature:052]: Ignoring invalid temperature (success=0, value=53.3)
## v104:
* opamp version = new BEMF triggers
## v103:
* remove rollback function as it cause troubles with cover position status + add device_class: shutter to cover
## v102 :
* add endstop_rollback_percent and enable it in sensor_bemf.yaml + test change endstop cover to feedback cover + better calibration script.
## v101:
* inputs.yaml : add substitution for bemf_trigger values cause bemf_trigger do not survive hassio reboot
## v100:
* climate.yaml : 11.11.2021 : remove away_config (temperature do not survive reboot : https://github.com/esphome/issues/issues/2680##issuecomment-966863690
## V99 :
* divide into packages :https://esphome.io/guides/configuration-types.html##config-substitutions
## V95 :
* default_mode: heat_cool (https://github.com/esphome/issues/issues/2680##issuecomment-966006171)
## V94 :
* substitution for default_target_temperature_low + high
* disable web_server as not needed anymore for debug
## V93 :
* substitution for temperature function (round(((diff_temp+1)/2)/0.1)*0.1;)
## V92 :
* minimum movement of valve 0.01 replaced with number.min_movement_change (if (abs(current_position - target_position) > id(min_movement).state/100) {)
## V91 :
* add timezone substitution
## V90:
* logger sensor + text_sensor + homeassistant.sensor : ERROR
* disable schedule valve_maintenance as it's triggered on reboot once a week
## v89 : 
* add check for CLIMATE_MODE_OFF 
* add default_mode: auto to thermostat
## v85 :
* Rollback function tested (bug)
* add esp32: routine
* flash_write_interval: 60min
* Substitution for names
* replace check_interval loop in climate.thermostat by interval (or time)
Number for parameters like BEMF triggers
One BEMF trigger param per channel
add idle global variable for thermostat
Re test pid climate with that parameters  for low temperature heating :  kp: 30 ki: 0.005 kd: -24000
Test current_base_cover : done but do not work  as expected : endstop triggered as FLT_MAX parameter is reach but FLT_MAX is position. I do not understand.
