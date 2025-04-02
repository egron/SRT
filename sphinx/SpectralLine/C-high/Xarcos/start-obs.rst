.. SRT procedures documentation master file, created by
   sphinx-quickstart on Mon Aug  7 16:44:28 2017.
   You can adapt this file completely to your liking, but it should at least
   contain the root `toctree` directive.


.. toctree::
   :maxdepth:1
  
.. _start-SLCXa:

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

#. Insert your project number :

    ``> project=[projectID]``    |logo| :numref:`srt_scheduler`

#. Initial setup :

    ``> antennaReset`` |logo| :numref:`srt_scheduler`

    ``> setupCCB``  |logo| :numref:`srt_receivers` |logo| :numref:`srt_ACU_green`

#. Select the active surface shape (Shaped configuration for C-band observations) :

    ``> asSetup=S``   |logo| :numref:`srt_activesurface`

#. Insert the Local Oscillator value in MHz :

    ``> setLO=[freq]``  |logo| :numref:`srt_receivers`
    
    
#. To perform the pointing and focus optimization (if they are not already included in your schedule), follow the link below: 

      :ref:`pointing-focus`    

#. Select and configure the XARCOS backend in C-band :

    ``> chooseBackend=XArcos``   |logo| :numref:`srt_scheduler`

    ``$ genericBackendTui BACKENDS/XBackends``  |logo| :numref:`srt_backendXarcos`

    ``> initialize=XC00``

#. The ``initialize`` command, which is also inserted in the schedule (.bck) directly, sets all XARCOS parameters such as frequency, bandwidth and sample rate. You can check that the backend parameters are correct in the BACKENDS/XBackends Tui, or modify them by using, i.e., the following command:

    ``> setSection=[sect],[startFreq],[bw],*,*, [sampleRate],*``

    with :

      - ``[sect]``: 0 in full-Stokes observations ;
      - ``[startFreq]`` corresponds to the initial frequency in the
        125-250 MHz range from the LO value ;
      - ``[bw]`` the bandwidth : 125.0, 62.5, 31.25, 15.625, 7.8125,
        3.90625, 1.953125, 0.9765625 or 0.48828125 MHz ; 
      - ``[sampleRate]``: in MHz, must be twice the bandwidth.
      - ``*`` : indicates the number of feeds, polarization mode and
        frequency channels, respectively. Let the asterix (``*``) for
        Xarcos observations.

#. Report the ground temperature, relative humidity, atmospheric pressure, and wind speed :

    ``> wx``


#. Begin the schedule by indicating the start scan [N] or subscan [N_n] in the SCD file :

    ``> startSchedule=[schedulename].scd,[N]`` |logo| :numref:`srt_scheduler`
