# HSTRC
My Senior Capstone Project, A remote control controlled by hand signals.


## The Hardware setup

- A LattePanda is running the java app
- A leap Device is connected to the Latte Panda
- the Latte Panda has a built in arduino board that the IR blaster is hooked into

## software classes

- ArduinoConnection class is what writes to the arduino on the latte panda.

- HandHandler class is what connects to the leap controller and uses their api calls. to
look at the hands. it also turns the hands into a data format I use.

- The arduino / sketch is running a simple switch statement corresponding the letter in the signal map 
to the IR signal.

## Software walkthrough:
populate maps corresponding to sleep time and character, each code gets a hand signal, a letter, and a sleep time.
the letter is what is sent through the arduinoConnection to the switch statement running on the arduino sketch.

In the testing phase of the project I used a GUI I made to see all the hand data that the Leap was 
seeing , Live. the gui was not necessary for function and was for the building process only.
(would tell me the leap device status, hand coordinates, etc)
we then ensure that the leap device is connected and running. entering a loop to look
for hands, it sleeps until one is visible.

if a hand is visible it will get the hand data many times (50 in this case) and determine the most
common hand position, done by saving each hand snapshot to an array and picking the one that occured the most.
this is done to ensure accuracy as the leap wasnt perfect and sometimes gave false finger information.

from this it will check to make sure the signal that it received is in the map, and then send the map
key (the character) to the arduino, whos switch state will send the correct infra red blast. after which
the app will sleep for the designated amount of time, until it can repeat the process.

(since there were no standardized IR codes for TV's it was difficult to work with multiple TV's
, my solution is that you dont need to change any of the java code, just update the sketch on
the arduino sketch.)

###### Presentation
- A presentation of my senior project can be found here: https://vimeo.com/270807172
