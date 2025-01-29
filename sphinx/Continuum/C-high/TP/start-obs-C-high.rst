.. SRT procedures documentation master file, created by
   sphinx-quickstart on Mon Aug  7 16:44:28 2017.
   You can adapt this file completely to your liking, but it should at least
   contain the root `toctree` directive.


.. toctree::
   :maxdepth:1

.. .. _start-obs:

Start the observations
======================

All of the following commands are given on nuraghe-mng.

$  : commands to insert in a shell
>  : commands to insert in the operatorInput panel


.. |logo| image:: monocle_.png
..    :width: 20pt
..    :height: 20pt
..   :align: left
|logo|: check the execution on the monitor


======================

#. Insert your project number

    ``> project=[projectID]``    |logo| :numref:`srt_scheduler`


#. Initial setup

    ``> antennaReset``   |logo| :numref:`srt_ACU_axis_blocked`

    ``> setupCCB`` |logo| :numref:`srt_receivers`  |logo| :numref:`srt_ACU_green`


#. Select the active surface shape (Shaped configuration for C-band observations)

    ``> asSetup=S``   |logo| :numref:`srt_activesurface`

#. Insert the Local Oscillator value in MHz

    ``> setLO=[freq]`` |logo| :numref:`srt_receivers`

#. Select the Total Power backend

    ``> chooseBackend=BACKENDS/TotalPower`` |logo| :numref:`srt_scheduler`

#. Insert the bandwidth (300, 730, 1250 or 2000 MHz) and choose the sample rate (in MHz) :

    ``> setSection=0,*,[bw],*,*,[sampleRate],*`` |logo| :numref:`srt_genericBackend`

    ``> setSection=1,*,[bw],*,*,[sampleRate],*``

#. Put the antenna at 45 deg of elevation and attenuate the signal in order to obtain values between 750 and 1100 counts (linear range of the backend) :

    ``> goTo=*,45d`` |logo| :numref:`srt_mount`

    ``> getTpi``

    ``> setAttenuation=0,[att]``          with [att] between 0 and 15 dB |logo| :numref:`srt_genericBackend`

    ``> setAttenuation=1,[att]``	with [att] between 0 and 15 dB (only integers)

    ``> getTpi``

#. Check the tsys (typical values 30-35 K)

    ``> tsys`` |logo| :numref:`srt_genericBackend`


#. Report the ground temperature, relative humidity, atmospheric pressure, and wind speed :

    ``> wx``


#. Follow the link below to perform the pointing and focus optimization (if not already included in your schedule). You can skip the first part since you have already set the parameters associated to the Total Power :


      :ref:`pointing-focus`


#. If the pointing and focus operations are included in your schedule, open the calibrationtool client in a terminal to display the pointing and focus plots in real time (if not already open) :

    ``$ calibrationtoolclient MANAGEMENT/CalibrationTool``  |logo| :numref:`srt_calibrationtool`


#. Begin the schedule by indicating the start scan [N] or subscan
 [N_n] in the .scd file :

    ``> startSchedule=[schedulename].scd,[N]`` |logo| :numref:`srt_scheduler`
