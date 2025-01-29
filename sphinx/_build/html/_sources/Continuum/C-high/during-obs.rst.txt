.. SRT procedures documentation master file, created by
   sphinx-quickstart on Mon Aug  7 16:44:28 2017.
   You can adapt this file completely to your liking, but it should at least
   contain the root `toctree` directive.


.. toctree::
   :maxdepth:1
  

Check during the observations
==============================

$ : commands to insert in a shell   
 
> : commands to insert in the operatorInput panel


#. Data are correctly written in the directory

	On nuraghe-obs2, check that the data are written in your project section:
	
	``$ cd/archive/data/[projectID]/``

#. Quick-look of the data

	On nuraghe-obs2:

	``$ idl``

	``IDL> .r fitslook``

	``IDL> fitslook``
	
	Note that in the quick-look plots, the subscans are shown with a short delay   		with respect to the real observations.

#. Antenna's monitors

	Check that everything section is green. If a red box appears, put the cursor on 	it and look at the error message.

	Contact and report the error messages to the responsible of the observation 		(observer friend?).

#. Panels

        * Scheduler : status OK, green

	During the tracking, @ is green while it is red during the slewing of the antenna.

	Check the update of the number of scan/subscan according to your schedule. Scans will be skipped if the target is not visible at the 		moment of the observations.

	If you realize that the scan/subscan number is frozen or that the tracking @ is red while the antenna is tracking the source, stop the 		on-going schedule with 

	``> antennaStop``    (in the operatorInput)

	then start again the schedule:

	``> antennaStart=[projectID]/…scd,n``     (with n the number of scan)

     	.. image:: srt_scheduler.png 
	   :align: center

 	* AntennaBoss : status OK, green.
		
     	.. image:: srt_antennaboss.png 
	   :align: center


 	* Mount : READY, READY, OK green (CHECK!!!!) while the antenna is pointing a source.

    	.. image:: srt_mount.png 
	   :align: center

 
 	* MinorServo; tracking @ is green, the status ids OK and green.

    	.. image:: srt_minorservo.png 
	   :align: center


 	* Receivers : status OK, green.

	If the derotator (dewar) is used, check the configuration and status (ready green).

    	.. image:: srt_receivers.png 
	   :align: center


#. Active surface

 	Sometimes, not all of the small squares of the active surface are green. Do not worry for that. Instead, it can be problematic if a 		large fraction of the active surface becomes red.


	* Check that the state of the active surface corresponds to your choice (shaped, shaped fixed, parabolic, parabolic fixed).


 	* “Ok” should be green during the observations.

    	.. image:: srt_activesurface.png 
	   :align: center


#. Log

 	* The log file (jlog) contains warning and error messages. Warning messages are indicated in yellow while error messages are in red.

 
 	* Check the possible error messages. Try to understand the origin of the problem and to solve it. In case of persistent/complex problem, contact and report the error messages and the associated UT to the responsible of the observation (observer friend?).




    	.. image:: srt_jlog.png 
	   :align: center


#. Calibration tool client


    	.. image:: srt_calibrationtool.png 
	   :align: center

#. Weather parameters

 	 On nuraghe-obs1, activate the meteo client:

	``$ meteoClient``

        If the wind speed exceeds 61 km/h, the antenna must be stowed.

    	.. image:: srt_meteo.png 
	   :align: center

	
