.. SRT procedures documentation master file, created by
   sphinx-quickstart on Mon Aug  7 16:44:28 2017.
   You can adapt this file completely to your liking, but it should at least
   contain the root `toctree` directive.


.. toctree::
   :maxdepth:1

.. _start-CoKTP:

Start the observations
======================

$ : commands to insert in a shell

> : commands to insert in the operatorInput panel


.. |logo| image:: monocle_.png
..    :width: 20pt
..    :height: 20pt
..   :align: left
|logo|: check on the monitor


======================

#. Insert your project number :

    ``> project=[projectID]`` |logo| :numref:`srt_scheduler`

#. Initial setup :

    ``> antennaReset`` |logo| :numref:`srt_ACU_axis_blocked`

    ``> setupKKG``  |logo| :numref:`srt_receivers_KKG` |logo| :numref:`srt_ACU_green`


#. Select the active surface shape (Shaped configuration for K-band observations) :

    ``> asSetup=S`` |logo| :numref:`srt_activesurface`

#. Insert the Local Oscillator value in MHz :

    ``> setLO=[freq]``  |logo| :numref:`srt_receivers_KKG`

#. Select the Total Power backend :

    ``> chooseBackend=TotalPower`` |logo| :numref:`srt_scheduler`

#. For each section [sect], insert the bandwidth ([bw]=300, 730, 1250 or 2000 MHz) and the sample rate (in MHz) :

    ``> setSection=[sect],*,[bw],*,*,[sampleRate],*`` |logo| :numref:`srt_genericBackend_KKG`

    Reminder : in K-band there are 7 feeds, so 14 sections with
    ``[sect]`` = 0, 1 , 2, 3, 4, 5, 6, 7, 8, 9, 10, 11, 12, 13.

#. If you want to use the multi-feed derotator to prevent field rotation during long acquisition, select the derotator configuration :

    ``> derotatorSetConfiguration=[config]``   with ``[config]`` = BSC, CUSTOM or FIXED. |logo| :numref:`srt_receivers_KKG`

        - BSC is for Best Coverage Space (automatic rotation of the
          dewar in order to best cover the scanned area).

        - CUSTOM : the user has to choose the angle of the dewar axis
          with the y-axis of the scanning frame that will be kept
          during the whole duration of the acquisition :
          ``>  derotatorSetPosition=[ang]d``     with ``[ang]`` the
          dewar angle in degrees.

        - FIXED : the dewar keeps a fixed postion w.r.t the horizon,
          no rotation is applied. To specify a static angle :
          ``>  derotatorSetPosition=[ang]d``     with ``[ang]`` the
          dewar angle in degrees.


    To read back the position of the dewar :

    ``> derotatorGetPosition``  |logo| :numref:`srt_receivers_KKG`

#. Put the antenna at 45 deg of elevation and attenuate the signal for the 14 sections [sect] in order to obtain values between 750 and 1100 counts (linear range of the backend) :

     ``> goTo=*,45d``   |logo| :numref:`srt_mount`

     ``> getTpi``

     ``> setAttenuation=[sect],[att]``	with [att] between 0 and 15 dB |logo| :numref:`srt_genericBackend_KKG`

     ``> getTpi``

#. Check the tsys (typical values up to 100 K) :

    ``> tsys`` |logo| :numref:`srt_genericBackend_KKG`

#. Report the ground temperature, relative humidity, atmospheric pressure, and wind speed :

    ``> wx``

#. Follow the link below to perform the pointing and focus optimization (if not already included in your schedule). You can skip the first part since you have already set the parameters associated to the Total Power :

      :ref:`pointing-focus`

#. If the pointing and focus operations are included in your schedule, open the calibrationtool client in a terminal to display the pointing and focus plots in real time (if not already open) :

    ``$ calibrationtoolclient MANAGEMENT/CalibrationTool``  |logo| :numref:`srt_calibrationtool`

#. Begin the schedule by indicating the start scan [N] or subscan [N_n] in the SCD file :

    ``> startSchedule=[schedulename].scd,[N]`` |logo| :numref:`srt_scheduler`
