.. SRT procedures documentation master file, created by
   sphinx-quickstart on Mon Aug  7 16:44:28 2017.
   You can adapt this file completely to your liking, but it should at least
   contain the root `toctree` directive.


.. toctree::
   :maxdepth: 1

.. _start-SPKSa:

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

    ``> project=[projectID]`` |logo| :numref:`srt_scheduler`

#. Initial setup

    ``> antennaReset``

    ``> setupKKG`` |logo| :numref:`srt_receivers_KKG`


#. Select the active surface shape (Shaped configuration for K-band observations)

    ``> asSetup=S`` |logo| :numref:`srt_activesurface`

#. Insert the Local Oscillator value in MHz

    ``> setLO=[freq]`` |logo| :numref:`srt_receivers_KKG`
    
#. Follow the link below to perform the pointing and focus optimization (if not already included in your schedule) :

      :ref:`pointing-focus`

#. Select and configure the SARDARA backend in K-band

    ``> chooseBackend=Sardara`` |logo| :numref:`srt_scheduler`

    ``$ genericBackendTui BACKENDS/Sardara``

    ``> initialize=[code]``

     with :

       - ``[code]`` = SK00S : central feed only and full Stokes observations ;
       - ``[code]`` = SK00  : central feed only and total intensity observations ;
       - ``[code]`` = SK77S : 7 feeds and full Stokes observations ;
       - ``[code]`` = SK77  : 7 feeds and total intensity observations ;
       - ``[code]`` = SK03S : feeds 0 and 3 only and full Stokes observations ;
       - ``[code]`` = SK03  : feeds 0 and 3 only and total intensity observations ;
       - ``[code]`` = SK06S : feeds 0 and 6 only and full Stokes observations ;
       - ``[code]`` = SK06  : feeds 0 and 6 only and total intensity observations.

    Important note: the *initialize* command requires a few more seconds comapared to the other command in order to operate.

#. Set the different parameters of the backend:

    ``> setSection=[sect],*,[bw],*,*,[sampleRate],[bin]`` |logo| :numref:`srt_genericBackend_KKG`

     with :

        - ``[sect]`` = 0, 1, 2, 3, 4, 5, 6 in full Stokes observations
          ;
        - ``[sect]`` = 0, 1, 2, 3, 4, 5, 6, 7, 8, 9, 10, 11,12, 13 in
          total intensity observations ;
        - ``[bw]`` the bandwidth in MHz (420 or 1500) ;
        - ``[sampleRate]`` in MHz (840 for 420 MHz of bw or 3000 for 1500 MHz of bw) ;
        - ``[bin]`` the frequency channels (1024 or 16384).

#. Choose the integration time in ms (e.g. n=10 corresponds to 100 spectra/sec)

    ``> integration=[n]``


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
          

#. Put the antenna at 45 deg of elevation before checking that the signal is in the linear range of the backend:

    ``> goTo=*,45d`` |logo| :numref:`srt_mount`

#. Check that the getTpi command is working correctly before proceeding:

     ``> getTpi``
     
     If getTpi=0,0 then there is a problem, you need to ask for help. 
     If getTpi=(a few millions) then proceed.

#. Attenuate the signal based on the rms range [20;22] and check the value on the interface.

    ``> getRms``

    ``> setAttenuation=[sect],[att]``    with [att] the attenuation from 0 to 15 dB. |logo| :numref:`srt_genericBackend_KKG`

    Important note 1: You have to set the attenuation accordingly to the values obtained with getRms. It could happen that the rms value of the sections 4, 5, 6, 7, 8, 9, 11, 12, 13, 14, 15 (feeds 2, 3, 4, 5, 6) does not reach 22. In this case, the attenuation has to be set to 0. 
  
    Important note 2: The section 10 does not work, do not consider the related    getRms and tsys values.   

#. Check the tsys (typical values up to 100 K)

    ``> tsys`` |logo| :numref:`srt_genericBackend_KKG`

#. Report the ground temperature, relative humidity, atmospheric pressure, and wind speed :

    ``> wx``


#. Begin the schedule by indicating the start scan [N] or subscan [N_n] in the SCD file :

    ``> startSchedule=[schedulename].scd,[N]``  |logo| :numref:`srt_scheduler`
    
    
    
    
..   Important note 1: For the sections 0, 1, 2 and 3 (feeds 0 and 1), you have to set the attenuation accordingly to the values obtained with getRms. For the other sections the attenuation has to be set to 0 since the rms does not reach 30.  
    
..    To read back the position of the dewar :

         ``> derotatorGetPosition``
