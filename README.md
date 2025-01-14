# ecfantemp

## An ectool wrapper to simplify fan / temperature reading and configuration

It displays and accepts temperature parameters in Celsius, Fahrenheit or Kelvin
and doesn't force you to set *all* the bloody thermal parameters every time
you want to change a single setting. Unlike `ectool` that was clearly written
to be used solely by robots, this script tries to make its use more appropriate
for human beings.

If you don't need ectool to control your fan, this probably isn't for you.
I wrote this to control the fan on my AMD Framework 13 laptop.

## What does it look like?

```
$ ecfantemp
Issuing 'show' command, see -h for more.

Sensor               Temperature    Off-Max Ratio  Fan Off(<=)    Fan Max(>=)
0 (local_f75303@4d)  40.8°C (314K)  3.0%           39.8°C (313K)  69.8°C (343K)
1 (cpu_f75303@4d)    40.8°C (314K)  0.8%           45.8°C (319K)  53.8°C (327K)
2 (ddr_f75303@4d)    41.8°C (315K)  4.0%           39.8°C (313K)  79.8°C (353K)
3 (cpu@4c)           40.8°C (314K)  4.0%           39.8°C (313K)  79.8°C (353K)

Fan 0 [===|       ] 2259 RPM (32.2% duty)
```

## Help

(This README document may be out of date - best check the script itself)

```
$ ecfantemp -h
...
When run without options, 'show $ECF_TEMP_UNIT' is issued.
The following environment variables can also be set to alter behaviour:
ECF_MAX_RPM, ECF_RPM_NAG_OFF, ECF_TEMP_UNIT, ECF_SHOW_CALLS and ECF_WATCH_RATE.

Usage:
  ecfantemp <watch|show|info|set> [options] [option] [..]

Options:
  show    Show the current sensor temperatures, fan speed(s) and common info.
  watch   Same as 'show' but runs in a loop a la 'watch'.
  info    Show the thermal parameters/values for warn, high, halt, off and max.
  set     Set fan or sensor parameters. The syntax is one of:
          fan    <speed in RPM or off/auto/max> [fan ID]
          sensor <sensor number> <warn|high|halt|off|max> <degrees[unit]>

Examples:
    ecfantemp show
    ecfantemp set fan 5000   # set fan 0 to 5000 RPM
    ecfantemp set fan auto 2 # set fan 2 to automatic control
    ecfantemp set sensor 1 warn 90C
    ecfantemp watch K
    ecfantemp info C
```

## Requirements
 * `ectool` for your platform (https://github.com/DHowett/framework-ec, https://chromium.googlesource.com/chromiumos/platform/ec/, ...)
 * `column` from util-linux (may ship as `bsdextrautils`, `util-linux`, ... you probably have it already)
 * `bc` (usually ships as just `bc`)
 * The regular bandits: `bash`, `seq`, `mktemp`, `sudo`

## Contact

You can reach me via github: [https://github.com/gammy](https://github.com/gammy)

