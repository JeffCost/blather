#Blather
Blather is a speech recognizer that will run commands when a user speaks preset sentences.

##Requirements
1. pocketsphinx
2. gstreamer (and what ever plugin has pocket sphinx support)
3. pyside (only required for the Qt based UI)
4. pygtk (only required for the Gtk based UI)

##Usage
0. move commands.tmp to ~/.config/blather/commands.conf and fill the file with sentences and command to run
1. Run Blather.py, this will generate ~/.config/blather/sentences.corpus based on sentences in the 'commands' file
2. quit blather (there is a good chance it will just segfault)
3. go to <http://www.speech.cs.cmu.edu/tools/lmtool.html> and upload the sentences.corpus file
4. download the resulting XXXX.lm file to the ~/.config/blather/language directory and rename to file to 'lm'
5. download the resulting XXXX.dic file to the ~/.config/blather/language directory and rename to file to 'dic'
6. run Blather.py
    * for Qt GUI, run Blather.py -i q
    * for Gtk GUI, run Blather.py -i g
    * to start a UI in 'continuous' listen mode, use the -c flag
    * to use a microphone other than the system default, use the -d flag
7. start talking

####Bonus
once the sentences.corpus file has been created, run the language_updater.sh script to automate the process of creating and downloading language files.

####Examples
To run blather with the GTK UI and start in continuous listen mode:
./Blather.py -i g -c

To run blather with no UI and using a USB microphone recognized and device 2:
./Blather.py -d 2

####Finding the Device Number of a USB microphone
There are a few ways to find the device number of a USB microphone.

* `cat /proc/asound/cards`
* `arecord -l`
