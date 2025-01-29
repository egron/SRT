.. SRT procedures documentation master file, created by
   sphinx-quickstart on Mon Aug  7 16:44:28 2017.
   You can adapt this file completely to your liking, but it should at least
   contain the root `toctree` directive.
.. toctree::
   :maxdepth: 1

.. _Restart-Discos:

===================
Restart Discos
===================

#. On the **discos-manager computer**, open a terminal and give the following command:

    ``discos -start``

   The graphical interface of the ACS Command Center appears (:numref:`srt_acs_2`).

   Check that ``remote`` and  ``use native ssh`` are correctly selected in the **Common settings** panel.

   Click on ``Start`` in the **Acs suite** panel. 
 
   In the **Containers** panel, click on the global green triangle located below the individual triangles to open all of the containers.

   On the **Deployment Info** panel, check that the 35 containers appear progressively.
 
 
 
#. On the **discos-console computer**, open a terminal and give the following command:

    ``discosConsole`` 

   The 9 panels appear:

     - **operatorInput** (:numref:`srt_operatorinput`)
     - **AntennaBoss** (:numref:`srt_antennaboss`)
     - **GenericBackend** (:numref:`srt_genericBackend`)
     - **Mount** (:numref:`srt_mount`)
     - **Observatory** (:numref:`srt_observatory`)
     - **Receivers** (:numref:`srt_receivers`)
     - **Scheduler** (:numref:`srt_scheduler`)
     - **MinorServo** (:numref:`srt_minorservo`)
     - **ACS custom logging client** (:numref:`srt_jlog`)

   


   From a virtual desktop, open a new terminal to start the **active surface** and write:

    ``SRTActiveSurfaceGUIClient &``

   The related graphical interface is now open. Wait a few minutes until the single squares (representing the attuators) become green. The status of the active surface is in the "WARNING" configuration (:numref:`srt_as_park`).
   
   From a virtual desktop, open two new terminals to start the panels related to the **Meteo Client** and the **Calibration Tool Client** (if necessary) and write, rispectively:
   
  ``meteoClient &``
  
  ``calibrationtoolclient MANAGEMENT/CalibrationTool &``
  
  The graphical interfaces related to the meteo Client (:numref:`srt_meteo`) and  the calibration Tool Client (:numref:`srt_calibrationtool`) are now open and updated in real time. 
  






.. Please, follow the steps in the order.

.. #. On **nuraghe-mng**, go on the MNG virtual desktop. Open a shell and launch Nuraghe.

    ``nuragheConsole -start``

    The ACS Command Center will appear.


.. #. In the *Common Settings* section located on the upper left of the ACS interface, select 

    ``localhost(single-machine project)``


.. #. In the *Acs Suite* section, click on  ``Start`` (green triangle with Start).


.. #. On the bottom left of the ACS interface, click on the ``ACS`` tab. Wait about one minute to check that the system is running. When it is ready, the following message appears **ACS is up and running** in the log tab of ACS.


.. #. In the *Containers* section, click on the single green triangles to start each container. It is not necessary to wait for the closing of the Deployment info window of each container. The name of the containers appear progressively in the log tab with the message ``ContainerStatusMsg: Ready``. 


.. #. On **nuraghe-AS**, open two shells if they are not already there. On the first one, write 

    ``asContainers``

    On the second one, write  ``SRTActiveSurfaceGUIClient &``

    The graphical interface of the active surface appears. The active
    surface is ready when it is green (it takes several minutes).


.. #. On **nuraghe-mng**, check that the you have now **33 containers**.


.. #. Go on the CONSOLE virtual desktop of **nuraghe-mng**. Open a shell and execute the following command

    ``nuragheConsole``

    Eight panels appear:

     - **operatorInput** (:numref:`srt_operatorinput`)
     - **AntennaBoss** (:numref:`srt_antennaboss`)
     - **GenericBackend** (:numref:`srt_genericBackend`)
     - **Mount** (:numref:`srt_mount`)
     - **Observatory** (:numref:`srt_observatory`)
     - **Receivers** (:numref:`srt_receivers`)
     - **Scheduler** (:numref:`srt_scheduler`)
     - **MinorServo** (:numref:`srt_minorservo`)


.. Nuraghe is now ready! 
