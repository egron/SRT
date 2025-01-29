.. SRT procedures documentation master file, created by
   sphinx-quickstart on Mon Aug  7 16:44:28 2017.
   You can adapt this file completely to your liking, but it should at least
   contain the root `toctree` directive.


.. toctree::
   :maxdepth:1

.. _Check-fig:


Control Room
===================

       .. _srt_control_room:

       .. figure:: srt_control_room.png
	  :align: center

          SRT control room layout.


ACS Command Center
===================

       .. _srt_acs:

       .. figure:: srt_acs.png
	  :align: center

          The **ACS** monitor shows the state of the containers related to each DISCOS component.
          The state of each container can be verified in the section highlighted in blue.
	  The blue arrow indicates the number of containers (35 when the system is ready).


ACS Command Center
===================

       .. _srt_acs_2:

       .. figure:: srt_acs_2.png
	  :align: center

	  In the **Common settings** panel of the ACS monitor, the ``remote``  and  the ``use native ssh`` items must be selected as indicated by the green arrows. The ``Start`` and  the ``global green triangle`` buttons highlighted in green must be used to restart the **Acs suite** and the **Containers**, respectively. The ``Kill`` button highlighted in red must be used to close the ACS panel during the Shutdown of Discos.


Active Surface
===============

       .. _srt_activesurface:

       .. figure:: srt_activesurface.png
	   :align: center

	   This monitor shows the status of the actuators in a graphical representation of the **Active Surface** and its configuration.


Active Surface
==============

       .. _srt_activesurface_2:

       .. figure:: srt_activesurface_2.png
	   :align: center

           After parking the active surface by using ``> asPark``, in the **Active Surface** monitor the status of the ``Actual Profile`` box is ``Park``.

..	   The **Active Surface** monitor after parking the active surface by using ``> asPark``


Active Surface
==============

       .. _srt_as_parabolic:

       .. figure:: srt_as_parabolic.png
	   :align: center

	   The **Active Surface** monitor in the parabolic configuration.


Active Surface
==============

       .. _srt_as_park:

       .. figure:: srt_as_park.png
	   :align: center

	   The status of the **active surface** is ``WARNING`` after the "Restart Discos" procedure.



Logging Display
===============

       .. _srt_jlog:

       .. figure:: srt_jlog.png
	   :align: center

	   The **Logging Display** shows the log messages related to
	   the observation. New messages are shown over the
	   previous ones.


Meteo Client
=============

       .. _srt_meteo:

       .. figure:: srt_meteo.png
	   :align: center

           The **Meteo Client** window shows the atmospheric temperature
           and wind parameters (including wind direction) using a
           graphic interface.



==============
Discos-console
==============

       .. _srt_vistaglobale:

       .. figure:: srt_vistaglobale.png
	  :align: center

          **Discos-console** is the machine where you run the system and where
	  you should find the input terminal and all the monitors. It is also
	  the destination for your schedules.


OperatorInput
=============

       .. _srt_operatorinput:

       .. figure:: srt_operatorinput.png
	   :align: center

           In the **input console** the users can write Nuraghe commands. The prompt is just a sequential number enclosed in <>.
           If a command is properly read, the system replies by repeating the command itself, followed by the operation results
           (if they are foreseen).


AntennaBoss
===========

       .. _srt_antennaboss:

       .. figure:: srt_antennaboss.png
           :width: 15cm
	   :align: center

           The **AntennaBoss** monitor shows the target info, indicating the commanded and actual positions pointed by
           the antenna. It also gives a feedback on the pointing
           accuracy and on the overall antenna status.


GenericBackend
===============

       .. _srt_genericBackend:

       .. figure:: srt_genericBackend.png
	   :align: center

	   The monitor **GenericBackend** shows the backend setup parameters related to each section.

       .. _srt_genericBackend_KKG:

       .. figure:: srt_genericBackend_KKG.png
	   :align: center

           The monitor **GenericBackend** in the K-band configuration.


Mount
======

       .. _srt_mount:

       .. figure:: srt_mount.png
           :width: 15cm
	   :align: center

	   Observers need to focus only on the **Mount** status (indicated by the green box) and on the actual position of the axis expressed in Azimuth and Elevation (shown in blue), compared to the commanded positions (actual positions with the label "Cmd Az." and "Cmd El.").

       .. _srt_mount_antennareset:

       .. figure:: srt_mount_antennareset.png
           :width: 15cm
	   :align: center

           The **Mount** monitor after the park of the antenna by using ``> antennaPark``


Observatory
===========

       .. _srt_observatory:

       .. figure:: srt_observatory.png
           :width: 15cm
	   :align: center

           The **Observatory** monitor shows the station time and coordinates.



ReceiversBoss
==============

       .. _srt_receivers:

       .. figure:: srt_receivers.png
           :width: 15cm
	   :align: center

	   The **ReceiverBoss** monitor summarizes the frontend setup parameters.
           The bottom part is devoted to the derotator (dewar positioner), when available.


       .. _srt_receivers_LLP:

       .. figure:: srt_receivers_LLP.png
           :width: 15cm
	   :align: center

           The **ReceiverBoss** monitor in the L-band configuration.


       .. _srt_receivers_KKG:

       .. figure:: srt_receivers_KKG.png
           :width: 15cm
	   :align: center

           The **ReceiverBoss** monitor in the K-band configuration.



Scheduler
=========

        .. _srt_scheduler:

     	.. figure:: srt_scheduler.png
           :width: 15cm
	   :align: center

           The **Scheduler** monitor shows the details on the selected data acquisition devices and on the running schedule, if any.

        .. _srt_scheduler_end:

     	.. figure:: srt_scheduler_end.png
           :width: 15cm
	   :align: center

           The **Scheduler** monitor after the interruption of the current subscan by using ``> stopSchedule`` or ``> haltSchedule``


MinorServo
===========

       .. _srt_minorservo:

       .. figure:: srt_minorservo.png
           :width: 15cm
	   :align: center

	   The **MinorServo** monitor shows the current setup code and the minor-servo status and movement. In this case the image refers to the C-band configuration.

       .. _srt_minorservo_LLP:

       .. figure:: srt_minorservo_LLP.png
           :width: 15cm
	   :align: center

           The **MinorServo** monitor in the L-band configuration.

       .. _srt_minorservo_KKG:

       .. figure:: srt_minorservo_KKG.png
           :width: 15cm
	   :align: center

           The **MinorServo** monitor in the K-band configuration.

       .. _srt_minorservo_end:

       .. figure:: srt_minorservo_end.png
           :width: 15cm
	   :align: center

           The **MinorServo** monitor after the park of the minor servos by using ``> servoPark``



Calibration tool client
========================

       .. _srt_calibrationtool:

       .. figure:: calibrationtool_cut.png
	   :align: center

           In the **Calibration tool client** window the subscan
           currently being acquired is shown in real-time (upper
           plot), even if in a low-resoltution. In the lower plot, the
           last completed subscan - in its full sampling - is
           shown. We can read the information about the pointing
           of focus offsets ("peakoffsets"), the beam size ("HPBW"), etc.

       .. _srt_focus:

       .. figure:: srt_focus.png
	   :align: center

           **Calibration tool client** window related to a focus subscan.

GenericBackendX
================

       .. _srt_backendXarcos:

       .. figure:: generic-backend-Xarcos.png
	   :align: center

           A second **GenericBackend** panel shows the setup
	   parameters of each section of Xarcos.



Primary Control Panel ACU
==========================

       .. _srt_ACU_green:

       .. figure:: srt_ACU_green.png
	   :align: center

           Primary Control Panel ACU.

	   
SEADAS
=======

       .. _seadas_disabled:
      
       .. figure:: seadas_disabled.jpg
           :align: center

           Seadas GUI. On the top right, the red box signals that the control of the antenna is DISABLED.



       .. _seadas_enabled:
       
       .. figure:: seadas_enabled.jpg
           :align: center
	
           Seadas GUI. On the top right, the green box signals that the control of the antenna is now ENABLED.


       .. _session_mode:
       
       .. figure:: session_mode.jpg
           :align: center

           Seadas GUI. On the top left, circled in black, the Session Mode combo box where the option Schedule needs to be selected in order to start the observations through your pre-prepared schedule.


       .. _schedule_management:

       .. figure:: schedule_management.jpg
           :align: center

	   Seadas GUI. Pop-up window where the schedule can be uploaded by clicking on the button `Load sched`.


	    
       .. _schedule_management_full:

       .. figure:: schedule_management_full.jpg
	   :align: center

           Seadas GUI pop-up window for schedule management. The uploaded schedule lines will appear on the top panel. The ones selected for observations will appear in the bottom panel.
