.. SRT procedures documentation master file, created by
   sphinx-quickstart on Mon Aug  7 16:44:28 2017.
   You can adapt this file completely to your liking, but it should at least
   contain the root `toctree` directive.

===================
Problem identification
===================

Depending on the problem, you can be able to resolve it.
The first thing is to identify the origin of the error.
Check the presence of error messages on the different monitor panels, the
jlog, ACS and the ACU control panel. 


MinorServo
=========

Errors, warning and failure of the MinorServoBoss can be related to the crash of the server that manages the minor servos: MSCU.
Check first if the server crashed and restart it if needed. Ask the project friend to complete the procedure from viewer01 (VLBI console). The instructions are on this link:
https://srtsupervisoronduty.readthedocs.io/it/latest/sd/srt/procedures/minor_servo.html#mscu-restart.

After restarting the server it is necessary to restart the containers of the minor servos on the discos-manager computer.


Quicklook
=========

If the Quicklook stop running correctly and is frozen to a previous session, you can restart it from a terminal with the user “observer”:

``$ su - discos service quicklook restart`` 

Please, ask the project friend to complete the procedure with the password.


Monitor panels
=========

Look at the `9 panels <http://discos.readthedocs.io/en/latest/user/srt/source/Appendix_A.html>`_. The error messages usually come out in red.

.. ATTENTION:: **operatorInput**

Check that the command you have insterted is written correctly. If the error is not
related to a typo, try to identify the origin of the problem. Check
the different panels (Scheduler, MinorServo, Receivers, etc...) and the jlog.


.. ATTENTION:: **Scheduler**
 
:ref:`srt-scheduler` when the schedule is not running
correctly. If the Scan/SubScan number is proceeding correctly, the
FAILURE can be associated with skipped scans because of the too high
or too low elevation of the source (> 85° or < 5°). 

*Solution*: Stop the schedule with  ``> stopSchedule`` and 
check the elevation of the target with `CASTIA <http://www.ira.inaf.it/Observing/castia/site/index.php>`_.
Then start again the schedule with ``>
startSchedule=[projectID]/[schedulename].scd,[N]`` when the target is
visible.


.. ATTENTION:: **Receivers**

If the local oscillator (LO) value is set to 0 on the **Receivers** panel while you have
inserted a correct value (in MHz) on the operatorInput, the LO container is probably
down (check also the operatorInput and jlog errors). Contact the
person in charge of the observations (observer’s friend) to resolve
the problem.



Jlog
====

.. ATTENTION:: **LoggingClient**

Error messages on the LoggingClient appear in red while warning are in
yellow.
If the **Subscan skipped** message appears, the scheduler is skipping
subscans because of a too high or low elevation of the target (see
previous section).




ACU control panel
====

If one or different boxes appear in yellow (warning) or red (error), put the mouse on
the box and read the associated message.

.. ATTENTION:: **Servo DC warning**

If the **wa_Servo_DC_Warn** label appears on the yellow warning box, the observations must be **immediately** interrupted. Give the following commands to stow the antenna:

``> antennaPark``

``> servoPark``

``> asPark``

Communicate the problem to the person in charge of the observations, as indicated by your project friend.


.. ATTENTION:: **Servo system and axis errors**

After the stow of the antenna, errors related to the main servo system
or to the azimuth/elevation axes may occur.

To solve the problem, give the following commands in the
operatorInput console:

``> antennaReset``

``> antennaTrack``

Wait 10 seconds. If the errors disappear, you can proceed to the observations by setting first the minor servo setup ``> servoSetup[code]``, with ``[code=LLP,PPP,CCB,KKG]``.

Instead, if the errors remain, give again the previous commands:

``> antennaReset``

``> antennaTrack``
 
Wait 10 seconds. If the errors disappear, you can proceed to the observations. Please, set first the minor servo setup as indicated before.

If the errors persist:

- push the **emergency stop button**

- release the **emergency stop button**

``> antennaReset``

``> antennaTrack``

At this point, the problem should be resolved. You can proceed with the observations. Please, set first the minor servo setup as indicated before.

If the problem persits, please contact the person in charge of
the observations (observer’s friend).


.. ATTENTION:: **Power errors**

In the case of **err_Power_Error** label, look at the jlog window. The
**MAIN POWER ERROR** message should appear, being assigned a CRITICAL
priority. To resolve the problem, give the following commands in the
operatorInput console:

``> antennaReset``

``> antennaTrack``

If the error message is different or the problem still unresolved, contact the person in charge of
the observations (observer’s friend).


Wind velocity
========

.. ATTENTION:: **MeteoClient**

Check regularly the wind velocity using the ``$> meteoClient &`` on
a shell of nuraghe-mng. For observations in K-band, the wind speed
should not exceed 30 km/h (value to be checked) otherwise the pointing
accuracy will probably be lost. 

.. ATTENTION:: **Unstow of the antenna**

:ref:`srt_windspeed`
If you want to continue the observations without redoing the setup from the beginning (receiver, bandwidth, attenuations, etc...), you can simply unstow the antenna and start again the observations where you left off, following the sequence of commands:

``> antennaUnstow``

``> antennaTrack``

``> startSchedule=[schedulename].scd,[N]`` where you were previously.


Stow of the antenna
=============

.. ATTENTION:: **Put the antenna in stow with the green button**

In the case the control software has some problems or is disable and you cannot
communicate anymore with the antenna, you can use the ``green button``
to park the antenna. The green button is located close to the red
emergency stop button in the control-room.

When the antenna is parked, look at the ACU monitor, wait until
**Axis blocked** appears in red (:numref:`srt_ACU_axis_blocked`).
Only at this moment, you can press on the ``emergency stop button``
(:numref:`srt_ACU_redbutton`).



