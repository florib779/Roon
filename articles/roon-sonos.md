# Roon and Sonos

## HTTP Commands

HTTP Command                                             | Description
---                                                      | ---
http://IP-SONOS-DEVICE:1400/advconfig.htm                | Set the root bridge (FirstZP and Priority to "enabled").
http://IP-SONOS-DEVICE:1400/xml/device_description.xml   | Device description.
http://IP-SONOS-DEVICE:1400/reboot                       | Reboot the Sonos Box.
http://IP-SONOS-DEVICE:1400/region.htm                   | Set WLAN region (for Europe).
http://IP-SONOS-DEVICE:1400/status                       | Status page.
http://IP-SONOS-DEVICE:1400/status/ifconfig              | &nbsp;
~http://IP-SONOS-DEVICE:1400/status/perf~                | &nbsp;
~http://IP-SONOS-DEVICE:1400/status/scanresults~         | Scanresults shows you all WLAN connections that were reached by Sonos.
~http://IP-SONOS-DEVICE:1400/status/topology~            | Shows the Sonos topology with all Sonos players and media servers.
~http://IP-SONOS-DEVICE:1400/status/tracks_summary~      | With this command you can display the number of tracks.
http://IP-SONOS-DEVICE:1400/support/directsubmit         | This submits a diagnostic and then returns the code in a web page.
http://IP-SONOS-DEVICE:1400/support/review               | Overview of the Sonos Box. The network matrix can also be called up here
http://IP-SONOS-DEVICE:1400/tools.htm                    | Network tools like ping, traceroute, nslookup.
http://IP-SONOS-DEVICE:1400/wifictrl?wifi=off            | Turns off the WIFI until the next reboot.
http://IP-SONOS-DEVICE:1400/wifictrl?wifi=persist-off    | Turns off the WIFI interface completely. If you only want to work with network cable.

## Alexa voice commands with Sonos-Roon combination

Voice commands that I have successfully tested. On the activation word is waived at this actuator.

English Command | German Command                                     | Description
---             | ---                                                | ---
&nbsp;          | Lautstärke auf 3 (30 %) in (Raumname)              | 
&nbsp;          | Leiser/lauter in (Raumname)                        | 0-10 volume levels
&nbsp;          | (Mach Lautstärke-Stufe Stufen leiser)              | 
&nbsp;          | (Mach Lautstärke-Stufe Stufen lauter)              | 
&nbsp;          | Ton aus in (Raumname)                              | 
&nbsp;          | Ton ein in (Raumname)                              | 
&nbsp;          | Pause in (Raumname)                                | 
&nbsp;          | Fortsetzen in (Raumname)                           | After resuming playback stops after a short time
&nbsp;          | Nächster Song                                      | 
&nbsp;          | Stoppe die Musikwiedergabe in 3 Minuten            | 
&nbsp;          | Wer ist der Sänger von [Band]?                     | 
&nbsp;          | Was war das [Zahl] Album von [Künstler/ Künstler]? | 

## Other Commands

Echo 3-Band Equalizer

## Links

* [Roon Knowledge Base](https://help.roonlabs.com/portal/en/kb/articles/sonos)
* [node-sonos-http-api](https://github.com/jishi/node-sonos-http-api)
* https://freetime.mikeconnelly.com/archives/tag/sonos
