# ZSTART
Update and Manage the ISPF ZSTART auto-start variable

IBM has provided since z/OS 2.1 in ISPF the ability to define a set of ISPF
commands to be invoked each time ISPF starts. This list is stored in the ISPF
Profile Variable ZSTART under the ISR Profile.  This list can be considered
similar to the Windows Startup Folder.

To simplify reviewing and updating this startup list a new ISPF dialog is being
made available using the ZSTART REXX exec that is access on any ISPF command
line:  TSO %ZSTART

The format of the startup list is:

  1. Multiple commands on a line must be separated by a colon (;)
  2. TSO Commands must be prefixed by TSO
     - the same as is required when manually invoked under ISPF
  3. ISPF commands require no prefix

Sample:

  Start 3.4;start QW;Swap 1

This sample will create three ISPF screens. The first is the default
ISPF Primary Options Menu, and then it will start a second session
with ISPF 3.4. After starting the ISPF 3.4 display it will start a
third session with MVS QuickRef and then Swap back to the first
session.

IF ISPF is started with an option (e.g. ISPF 3.4) then the ZSTART
variable startup list will be ignored.

Note: When the variable is saved the string "ISPF;" will be prefixed
to it as that is a requirement but there is no need for it in this
dialog.
