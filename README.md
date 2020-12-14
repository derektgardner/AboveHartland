# AboveHartland

[AboveHartland](https://twitter.com/abovehartland) is an ADS-B Twitter Bot running on a Raspberry Pi 3b.  It tracks airplanes and then tweets whenever an airplane flies overhead. It is a fork of [OverPutney](https://github.com/shbisson/overputney), which is a fork of the original [AboveTustin](https://github.com/kevinabrandon/abovetustin) bot. Simon Bisson modified it to work on a Piaware with Flightaware's fork of dump1090 and addied support for [Josh Douch's free ICAO lookup APIs](https://api.joshdouch.me/). He also modified it to use chromedriver for browser interactions rather than the deprecated PhantomJS webdriver. I have only made small modifications to the code to work for my needs.

 * Uses [tar1090](https://github.com/wiedehopf/tar1090) for ADSB message decoding, airplane tracking, and webserving.
 * Built on the [dump1090-fa](https://github.com/flightaware/dump1090) receiver software.
 * Works with Chromium chromedriver webdriver on Raspberry Pi.
 * It tweets an image of a map with the airplane's track and the decoded aircraft data displayed by tar1090.
 * It displays the flight name if available, or the reported icao code.
 * It displays altitude, ground speed and heading information of the airplane at it's closest point to the bot.
 * Gives different hashtags depending on airline operator, altitude, speed and time of day.
 * Adds aircraft registration, type, and owner using [Josh Douch's ICAO hex lookup APIs](https://api.joshdouch.me/). This functionality is limited at best. The API results are inconsistent. It is disabled on my personal installation.

## Dependencies
* Uses [tar1090](https://github.com/wiedehopf/tar1090) for ADSB message decoding, airplane tracking, and webserving.
* Uses [twitter](https://pypi.python.org/pypi/twitter) for tweeting.
* Uses [selenium](https://pypi.python.org/pypi/selenium) for screenshots with Chromedriver and Chromium.
* Uses [pillow](https://python-pillow.org/) for image processing.
* Uses [requests](https://pypi.org/project/requests/) for API calls.
* Uses [Chromedriver](https://chromedriver.chromium.org/) for headless web browsing.
* Builds on a running [Piaware](https://flightaware.com/adsb/piaware/build) or [dump1090-fa](https://github.com/flightaware/dump1090) Raspberry Pi-based ADS-B receiver and decoder with MLAT support, with web server and local databases.

## Notes

Add your Twitter keys and location in lat/long to `config` and rename as `config.ini` before running. The `./runbot.sh` script will launch the looping script `run_tracker.sh` (which ensures the tracker python code is running) as a background task with no interaction. Use `tail -f nohup.out` to monitor operations. `pkill -f tracker` will shut down the bot.

## AboveHartland forked from the [OverPutney](https://github.com/shbisson/overputney) code written by
* [Simon Bisson](https://github.com/shbisson)

## OverPutney forked from the [AboveTustin](https://github.com/kevinabrandon/AboveTustin) code written by
* [Kevin Brandon](https://github.com/kevinabrandon)
* [Joseph Prochazka](https://github.com/jprochazka)
