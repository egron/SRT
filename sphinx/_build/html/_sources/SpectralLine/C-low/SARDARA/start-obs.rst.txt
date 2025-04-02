.. SRT procedures documentation master file, created by
   sphinx-quickstart on Mon Aug  7 16:44:28 2017.
   You can adapt this file completely to your liking, but it should at least
   contain the root `toctree` directive.


.. toctree::
   :maxdepth:1

.. _start-SLClowSa:

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

    ``> project=[projectID]`` |logo| :numref:`srt_scheduler`

#. Initial setup :

    ``> antennaReset`` |logo| :numref:`srt_ACU_axis_blocked` |logo| :numref:`srt_ACU_green`

    ``> setupCCG`` |logo| :numref:`srt_receivers`

#. Select the active surface shape (Shaped configuration for C-band observations) :

    ``> asSetup=S`` |logo| :numref:`srt_activesurface`

#. Insert the Local Oscillator value in MHz :

    ``> setLO=[freq]`` |logo| :numref:`srt_receivers`


#. Follow the link below to perform the pointing and focus optimization (if not already included in your schedule) :

      :ref:`pointing-focus`
      

#. Select and configure the SARDARA backend :

    ``> chooseBackend=BACKENDS/Sardara`` |logo| :numref:`srt_scheduler`

    ``$ genericBackendTui BACKENDS/Sardara``

    ``> initialize=SCC00S`` for full-stokes observations or
    ``> initialize=SCC00`` for total intensity observations.

#. Set the different parameters of the backend :

    ``> setSection=[sect],*,[bw],*,*,[sampleRate],[bin]``  |logo| :numref:`srt_genericBackend`

    with :

      - ``[sect]``: 0 in full-stokes observations and ``[sect]``: 0, 1 in non full-stokes observations ;
      - ``[bw]`` the bandwidth in MHz (420 or 1500) ;
      - ``[sampleRate]`` in MHz (840 for 420 MHz of bw or 3000 for 1500 MHz of bw) ;
      - ``[bin]`` the frequency channels (1024 or 16384).

#. Choose the integration time in ms (e.g. n=10 corresponds to 100 spectra/sec) :

    ``> integration=[n]``

#. Put the antenna at 45 deg of elevation before checking that the signal is in the linear range of the backend:

    ``> goTo=*,45d`` |logo| :numref:`srt_mount`

#. Check that the getTpi command is working correctly before proceeding:

     ``> getTpi``
     
     If getTpi=0,0 then there is a problem, you need to ask for help. 
     If getTpi=(a few millions) then proceed.

#. Attenuate the signal based on the rms range [20;22] and check the value on the interface :

    ``> getRms``

    ``> setAttenuation=[sect],[att]``    with [att] the attenuation from 0 to 15 dB.   |logo| :numref:`srt_genericBackend`

#. Check the tsys (typical values 30-35 K)

     ``> tsys`` |logo| :numref:`srt_genericBackend`

#. Report the ground temperature, relative humidity, atmospheric pressure, and wind speed :

    ``> wx``


#. Begin the schedule by indicating the start scan [N] or subscan [N_n] in the SCD file :

     ``> startSchedule=[schedulename].scd,[N]``  |logo| :numref:`srt_scheduler`
