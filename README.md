IRC weather bot for python2.7

Installation:
1. Install python2.7: `sudo apt install python2.7`
1. Install virtualenv: `sudo apt install python-virtualenv`
1. Create/go to virtual environment directory: `mkdir ~/virtualenvironment | cd ~/virtualenvironment`
1. Clone repository: `git clone https://github.com/dziban303/dziwx.git ~/virtualenvironment/dziwx`
1. Set up virtualenv: 
   * `virtualenv -p python2.7 ~/virtualenvironment/dziwx`
   * `cd ~/virtualenvironment/dziwx/bin`
   * `source activate`
   * `cd ~/virtualenvironment/dziwx/pywx`
1. Install requirements.txt: `pip install -r requirements.txt`
1. Edit config file `example_config.py`:
   - forecast_io_secret = API key for forecast.io / darksky.com
   - host, port = IRC server and port
   - nick = bot's nickname
   - pass = bot's IRC password
   - chans = Channels to join. Must use preceeding #, e.g. `"chans": ["#weather,#dziwx"],`
   - redlink, youtube, imgur fields = API keys for optional features
   - leave other stuff alone
   - save and rename to `local_config.py`
1. Run: `python pywx.py`

Notes: 
 - To add/edit acronyms for the `define` command, edit `acro.json`
 - To add/edit airports, edit `airports.dat`
 - To join password-protected channels, enter the password after the channel name in the `"chans"` field
 - To join multiple servers:
   - Copy `local_config.py` to `new_config.py` or whatever you want to call it, and populate it with the new server info
   - Copy `pywx.py`, name it `pywx2.py` or whatever you want to call it, and change the line therein from `from local_config import config` to `from new_config import config` replacing `new_config` with whatever your config file is named
   - Run `python pywx2.py`
   - Simultaneous use: `python pywx.py & python pywx2.py && fg`
