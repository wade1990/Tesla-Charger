# Tesla-Charger
Reverse Engineering of the Tesla 10Kw charger and development of an open source control board.

PCB Files in DesignSpark 8 format.

Fully built and tested boards and bare PCBs available here :
http://www.evbmw.com/index.php/evbmw-webshop

Support forum : https://openinverter.org/forum/

19/10/17 : Uploaded two files : 
ph_frames.csv this file contains the 3 messages required to run phase module 1 in the Gen 2 charger
power_run_ph1.csv this is a capture of phase 1 starting up , ramping up to 8.5A DC 320VDC, 15.5A AC, 230v 50hz
Mains switched manually around message number 700 in ph_frames.csv


21/10/17 : Uploaded two files : 
power_run_ph1_arduino_2a_365vdc.csv
Tesla_chg1_1.ino
Crude arduino sketch to run one power module in the gen2 charger. Runs on an arduino due on CAN1


01/11/17 : Uploaded design files for Version 1 open source logic board for the Tesla Gen 2 charger. As of this date this design is totally unchecked and untested. Do not build this. It could blow up your house , car or cat. Based on the Arduino Due SAM3X8E microcontroller. Stay tuned.


05/11/17 : Updated Design files and PCBs ordered for prototype builds.

17/11/17 : BOM uploaded for the V1 board.


08/12/17 : Added Tesla_charger_Tom_v2_test.ino source file. Should run all 3 phases with the V1 logic board. Untested.

20/12/17 : Added design files for V2 Charger control board. Major changes :

Added 2M Serial EEPROM for parameter storage

Changed to a Vertical type B USB socket.

27/02/18 : Error found on the V2 board. Missing grounds on Q1 and D5. Affects EVSE control only. Will ammend in a rev3 board asap.

28/02/18 : V3 design files released with grounds fixed. Also new S/W thanks to Tom DeBree released but untested as of today. Also pictures of mod required on V1 and V2 boards.

02/05/18 : V3 board and new software tested and working in my BMW E31 project car.

03/01/19 : Added an excellent user manual for the V3 logic board compiled by EVWest.

20/01/19 : Added a Beta Software directory to the Repo. Major changes as of this date :


-Stop sending power module can messages when charger not running - Working.


-Correct reading of charger Fault and Enable feedback signals - Working.


-Correct AC present flag so only sets if more than 70V AC is on each module - Working.


-Reset charger on detection of power module fault - Testing.


-Shutdown on exceeding a preset HV Battery voltage - Working. 


-Evse read routine now in 500ms loop to prevent false triggering -Working.



Recommend using this version.

27/01/19 : Added counter/timer to autoshutdown routine to prevent false triggering on transients.

06/02/19 : On request by a customer:

Added manual control mode for use of charger without EVSE. Digital one in when brought to +12v commands the charger to start
and when brought low commands charger off.

This mode also control HVDC via digital out 1 and AC mains via a contactor via Digital out 2.-Untested as of this date.

19/06/19 : Added schematic for V4 logic board design. V4 has the following upgrades over V3 :

-Changed from Type B USB to Mini. This will allow the charger lid to close without modification.

-Added extra stage of filtering to proximity signal.

-Single wire CAN capability added using the NCV7356. Now uses the exact same switching method between pwm control pilot and sw can as used in the Tesla charger / bms boards. This will allow use of Tesla destination charging, Chademo adapter,CCS adapter and possibly supercharging. All software dependent.

-Added two high power DC low side contactor drivers for use with DC fast charge or as general outputs.

-Added 3rd CAN channel based around the MCP2517 controller. Allows for high speed as well as FD Can. This extra can channel will allow the Tesla charger to act as a Chademo controller. Just add contactors and a hall current sensor.

-Two extra filtered and protected 12v digital inputs. General use or chademo control.

-One extra filtered and protected analog input. General use or hall current sensor for chademo control.

Untested as of this date.


Enjoy!
