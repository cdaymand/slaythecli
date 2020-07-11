# SlayTheCli
SlayTheCli: A console client for the game Slay The Spire

This repository is a tutorial on how to use the SlayTheCli client/server in order to play Slay the Spire from a console.
You will need a copy of Slay the Spire (which by the way is one of the greatest video game of all time) and to install 2 mods.
* CommunicationMod
* BaseMod

# Installation
1. You will need to clone the sources of 2 github repositories forked from ForgottenArbiter (Big thanks to him for his work : https://github.com/ForgottenArbiter) on the branch slaythecli. As I will continue to work a lot on these 2 repositories, currently you will have to use my branches to access the last version of SlayTheCli. Once finished I will send a merge request to ForgottenArbiter to make the installation process easier. 
```bash
git clone --branch slaythecli https://github.com/cdaymand/spirecomm.git
git clone --branch slaythecli https://github.com/cdaymand/CommunicationMod.git
```
2. Install maven on your system in order to build a version of the CommunicationMod which adds description to card.
3. Go to the CommunicationMod repository folder and generate the modified version of CommunicationMod.jar
```bash
cd CommunicationMod/
mvn package
```
4. Locate the original CommunicationMod.jar from the game (make a backup copy) and replace it with the one generated on the target folder by maven.
5. Install python3 and pip3 on your system
6. Go to the spirecomm repository folder and install the python3 requirements with pip3
```bash
cd ../spirecomm/
pip3 install -r slaythecli_requirements.txt
```
7. Edit your CommunicationMod config file and set the command to python3 path_to_spirecomm/slaythecli.py server
* **Windows:** `%LOCALAPPDATA%\ModTheSpire\CommunicationMod\config.properties`
* **Linux:** `~/.config/ModTheSpire/CommunicationMod/config.properties`
* **Mac:** `~/Library/Preferences/ModTheSpire/CommunicationMod/config.properties`

example:
```
#Sat Jul 11 13:50:20 CEST 2020
command=python3 /home/foo/spirecomm/slaythecli.py server
runAtGameStart=true
```
The slaythecli.py python3 program takes some arguments
```
usage: slaythecli.py [-h] [--ip [IP]] [--port [PORT]] [-v] {client,server}

positional arguments:
  {client,server}  client or server

optional arguments:
  -h, --help       show this help message and exit
  --ip [IP]        The server IP to bind to
  --port [PORT]    The server port
  -v, --verbose    Add some logging
```
8. You can try running the server yourself :
```
python3 /home/foo/spirecomm/slaythecli.py server
```
If everything is working fine, you should see a message saying "ready"

9. For updates, just use a "git pull" command from the 2 folders and regenerate a CommunicationMod.jar file if there was any change.

# Start Slay the CLI

1. Start Slay the Spire with only BaseMod and CommunicationMod ticked (Other mods may work but it's not guaranteed)
2. Check that CommunicationMod started with the following logs in the ModTheSpire logs
```
   - Communication Mod
   - communicationmod.CommunicationMod
20:45:24.190 INFO communicationmod.DataReader> Received message: ready
20:45:24.191 INFO communicationmod.CommunicationMod> Received message from external process: ready
   - 115ms
Done.
```
3. Start SlayTheCli in client mode :
```
python3 /home/foo/spirecomm/slaythecli.py server
```
And that's it

# known issues
* SlayTheCli is not compatible with the watcher at the moment
* Some unexpected behavior may happens if you play from the game at the same time
* Sometimes you may encounter exception error from the cli, in these case, just use ctrl+c until you leave the program. Normally you will be able to reopen the client just after (if the exception can be reproduced, open an issue, I will try to fix the bug as soon as possible)

If you encounter any bugs, don't hesitate to open an issue on this repository with some logs or explanation.

# A last word
SlayTheCli tries to be as user friendly as possible by hiding indexes and commands sent to the game. But you can still send direct commands from the "other" command which allows to directly enter your command.
I also invite you to read the documentation from the CommunicationMod : https://github.com/ForgottenArbiter/CommunicationMod and you can add the option --verbosity to slaythecli client in order to see the commands sent to server when you play
