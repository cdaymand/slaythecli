# slaythecli
SlayTheCli: A console client for the game Slay The Spire

This repository is a tutorial on how to use the SlayTheCli client/server in order to play Slay the Spire from a console.
You will need a copy of Slay the Spire (which by the way is one of the greatest video game of all time) and to install the mod CommunicationMod https://steamcommunity.com/sharedfiles/filedetails/?l=french&id=2131373661

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
7. Edit your CommunicationMod config file and set the command to python3 path_to_slaythecli.py in server mode
* **Windows:** `%LOCALAPPDATA%\ModTheSpire\CommunicationMod\config.properties`
* **Linux:** `~/.config/ModTheSpire/CommunicationMod/config.properties`
* **Mac:** `~/Library/Preferences/ModTheSpire/CommunicationMod/config.properties`

```
#Sat Jul 11 13:50:20 CEST 2020
command=/home/charles/spirecomm/slaythecli.py server
runAtGameStart=true
```
