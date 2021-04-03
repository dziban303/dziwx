# IRC weather bot for python2.7

### Installation:

1. Install python2.7: `sudo apt install python2.7`
1. Install virtualenv: `sudo apt install python-virtualenv`
2. Ensure libffi is installed: `sudo apt install build-essential libssl-dev libffi-dev`
3. Create/go to virtual environment directory: `mkdir ~/virtualenvironment | cd ~/virtualenvironment`
4. Clone repository: `git clone https://github.com/dziban303/dziwx.git ~/virtualenvironment/dziwx`
5. Set up virtualenv: 
   * `virtualenv -p python2.7 ~/virtualenvironment/dziwx`
   * `cd ~/virtualenvironment/dziwx/bin`
   * `source activate`
   * `cd ~/virtualenvironment/dziwx/pywx`
6. Install requirements.txt: `pip install -r requirements.txt`
7. Edit config file `example_config.py`:
   - forecast_io_secret = API key for forecast.io / darksky.com
   - host, port = IRC server and port
   - nick = bot's nickname
   - pass = bot's IRC password
   - chans = Channels to join. Must use preceeding #, e.g. `"chans": ["#weather,#dziwx"],`
   - redlink, youtube, imgur fields = API keys for optional features
   - leave other stuff alone
   - save and rename to `local_config.py`
8. Run: `python pywx.py`
9. To quit: `Ctrl-C` terminates the bot and returns you to the shell.

#### Notes: 
 - To add/edit acronyms for the `define` command, edit `acro.json`
 - To add/edit airports, edit `airports.dat`
 - To join password-protected channels, enter the password after the channel name in the `"chans"` field
 - To join multiple servers:
   - Copy `local_config.py` to `new_config.py` or whatever you want to call it, and populate it with the new server info
   - Copy `pywx.py`, name it `pywx2.py` or whatever you want to call it, and change the line therein from `from local_config import config` to `from new_config import config` replacing `new_config` with whatever your config file is named
   - Run `python pywx2.py`
   - Simultaneous use: `python pywx.py & python pywx2.py && fg`

#### Airports.dat formatting:
 The `airports.dat` file is from the OpenFlights database. More info can be found [here](https://openflights.org/data.html).
 - Fields: `airport_id,name,city,country,faa,icao,lat,long,alt,tz,dst`
   - **Airport_id** is a unique identifier. When adding new airports, just use a sequential number.
   - **Name** is the common name of the airport.  
   - **City** and **country** are difficult concepts to explain so I will just hope you know what they are.  
   - The **FAA** code is a three-to-five alphanumeric code unique to the airport; in many cases it is identical to the IATA code.  
   - The **ICAO** code is yet another unique identifier, and consists of a four-letter code. (For more on these codes, see [this wikipedia page](https://en.wikipedia.org/wiki/Location_identifier) 
   - **Latitude** and **longitude** are the airport's coördinates.  
   - **Altitude** is the airport's height above sea level, *in feet*. 
   - **Tz** is the *standard time* timezone offset from UTC; e.g., Eastern Standard Time is UTC-5, so `-5` is entered, while Japan Standard Time is UTC+9, so `+9` is used.
   - **Dst** indicates when Daylight Saving Time (or Summer Time) is used: Use `E` (Europe), `A` (US/Canada), `S` (South America), `O` (Australia), `Z` (New Zealand), `N` (None) or `U` (Unknown).
