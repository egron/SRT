.. SRT procedures documentation master file, created by
   sphinx-quickstart on Mon Aug  7 16:44:28 2017.
   You can adapt this file completely to your liking, but it should at least
   contain the root `toctree` directive.


.. toctree::
   :maxdepth:1
  
.. _start-SLKXa:

Start the observations
======================

$ : commands to insert in a shell   
 
> : commands to insert in the operatorInput panel

.. |logo| image:: monocle_.png
..    :width: 20pt
..    :height: 20pt
..   :align: left
|logo|: check the execution on the monitor


======================

#. Insert your project number

    ``> project=[projectID]``    |logo| :numref:`srt_scheduler`

#. Initial setup

    ``> antennaReset`` |logo| :numref:`srt_ACU_axis_blocked` 

    ``> setupKKG``  |logo| :numref:`srt_receivers_KKG` |logo| :numref:`srt_ACU_green`

#. Select the active surface shape (Shaped configuration for K-band observations)

    ``> asSetup=S``   |logo| :numref:`srt_activesurface`

#. Insert the Local Oscillator value in MHz

    ``> setLO=[freq]``  |logo| :numref:`srt_receivers_KKG`


#. To perform the pointing and focus optimization (if they are not already included in your schedule), follow the link below: 

      :ref:`pointing-focus`

#. Select and configure the XARCOS backend in K-band 

    ``> chooseBackend=XArcos``   |logo| :numref:`srt_scheduler`

    ``$ genericBackendTui BACKENDS/XBackends``  |logo| :numref:`srt_backendXarcos`

    ``> initialize=[code]``    

    with :

    * ``[code]=XK00`` : central feed only.
      4 full Stokes sections with bandwidths of 62.5 MHz, 8 MHz, 2 MHz
      and 0.5 MHz, each having 2048(x4) channels ;

    * ``[code]=XK77`` : 7 feeds.
      Full Stokes sections are recorded, each having a 62.5 MHz
      bandwidth and 2048(x4) channels ;

    * ``[code]=XK03`` : feeds 0 and 3 only.
      Each feed produces two full Stokes sections respectively having
      bandwidths of 62.5 MHz and 4 MHz and 2048(x4) channels ;

    * ``[code]=XK06`` : feeds 0 and 6 only. 
      Each feed produces two full Stokes sections respectively having
      bandwidths of 62.5 MHz and 4 MHz and 2048(x4) channels.


#. The ``initialize`` command, which is also inserted in the schedule (.bck) directly, sets all XARCOS parameters such as frequency, bandwidth and sample rate. You can check that the backend parameters are correct in the BACKENDS/XBackends Tui [[FIGURA]], or modify them by using, i.e., the following command that you have to repeat for each section number [sect]:

    ``> setSection=[sect],[startFreq],[bw],*,*, [sampleRate],*``

    with :

    * ``[sect]`` = 0, 1, 2, 3, 4, 5, 6 in full-Stokes observations ;
    * ``[startFreq]`` corresponds to the initial frequency in the
      125-250 MHz range from the LO value ;
    * ``[bw]`` the bandwidth : 125.0, 62.5, 31.25, 15.625, 7.8125,
      3.90625, 1.953125, 0.9765625 or 0.48828125 MHz ;
    * ``[sampleRate]`` its value (in MHz) must be twice the bandwidth ;
    * ``*`` refers to the number of feeds, polarization mode and
      frequency channels, respectively. Let is like this.



#. If you want to use the multi-feed derotator to prevent field rotation during long acquisition, select the derotator configuration :

    ``> derotatorSetConfiguration=[config]``   with ``[config]`` = BSC, CUSTOM or FIXED.

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

    ``> derotatorGetPosition`` 

#. Report the ground temperature, relative humidity, atmospheric pressure, and wind speed :

    ``> wx``


#. Begin the schedule by indicating the start scan [N] or subscan [N_n] in the SCD file :

    ``> startSchedule=[schedulename].scd,[N]`` |logo| :numref:`srt_scheduler`
