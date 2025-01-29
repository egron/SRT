.. SRT procedures documentation master file, created by
   sphinx-quickstart on Mon Aug  7 16:44:28 2017.
   You can adapt this file completely to your liking, but it should at least
   contain the root `toctree` directive.


.. toctree::
   :maxdepth: 1
  

Start the observations
======================

$ : commands to insert in a shell   
 
> : commands to insert in the operatorInput panel

#. Insert your project number

    ``> project=[projectID]``

#. Initial setup

    ``> antennaReset``

    ``> setupCCB``


#. Select the active surface shape (Shaped configuration for C-band observations)

    ``> asSetup=S``

#. Insert the Local Oscillator value in MHz

    ``> setLO=[freq]``

#. Select the Total Power backend

    ``> chooseBackend=BACKENDS/TotalPower``

#. Insert the bandwidth (300, 730, 1250 or 2000 MHz) and choose the sample rate (in MHz) :

    ``> setSection=0,*, [bw],*,*,[sampleRate],*``

    ``> setSection=1,*, [bw],*,*,[sampleRate],*``

#. Put the antenna at 45 deg of elevation and attenuate the signal in order to obtain values between 750 and 1100 counts (linear range of the backend) :

    ``> goTo=*,45d``

    ``> getTpi``

    ``> setAttenuation=0,[att]``	with [att] between 0 and 15 dB

    ``> setAttenuation=1,[att]``	with [att] between 0 and 15 dB

    ``> getTpi``

#. Check the tsys (typical values)

    ``> tsys``

#. Begin the schedule by indicating the start scan [N] or subscan [N_n] in the SCD file :

    ``> startSchedule=[projectID]/[schedulename].scd,[N]``
