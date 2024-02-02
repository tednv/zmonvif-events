# zmonvif-events

A JS CLI tool that attempts to bridge the gap between your ONVIF camera's motion detection and Zoneminder.

## Why?
In a typical Zoneminder installation the server will do video processing to determine which frames have motion. Unfortunately this task is quite CPU intensive. 

Fortunately some ONVIF cameras have built in motion detection features, which notify subscribers when an event occurs. 

This tool connects to an ONVIF camera and subscribes to these messages. When the motion state changes, it uses Zoneminder's API to arm the selected monitor

## Install

```bash
root@zm2:/usr/local/bin# npm install -g tednv/zmonvif-events
```

## Usage

```bash
root@zm2:/usr/local/bin# ./zmonvif-events --help
usage: zmonvif-events [-h] [-v] -z ZM_BASE_URL -i ZM_MONITOR_ID -n ZM_USERNAME
                      -w ZM_PASSWORD -c HOSTNAME [-u USERNAME] [-p PASSWORD]


ONVIF motion detection events bridge to Zoneminder

Optional arguments:
  -h, --help            Show this help message and exit.
  -v, --version         Show program's version number and exit.
  -z ZM_BASE_URL, --zm-base-url ZM_BASE_URL
                        Base URL for the Zoneminder instance (with trailing
                        slash)
  -i ZM_MONITOR_ID, --zm-monitor-id ZM_MONITOR_ID
                        The ID of the monitor in Zoneminder
  -n ZM_USERNAME, --zm-username ZM_USERNAME
                        The username for Zoneminder API
  -w ZM_PASSWORD, --zm-password ZM_PASSWORD
                        The password for Zoneminder API
  -c HOSTNAME, --hostname HOSTNAME
                        hostname/IP of the ONVIF camera
  -u USERNAME, --username USERNAME
                        username for the ONVIF camera
  -p PASSWORD, --password PASSWORD
                        password for the ONVIF camera
```

**Example**

```bash
root@zm2:/usr/local/bin# ./zmonvif-events -z http://zm2/zm -i 1 -n admin -w xxxxxxxxxxxxx -c camXXXXXXX -u admin -p xxxxxxxxxxxxx
[monitor 1]: Started
```