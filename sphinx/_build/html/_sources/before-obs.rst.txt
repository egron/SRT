.. SRT procedures documentation master file, created by
   sphinx-quickstart on Mon Aug  7 16:44:28 2017.
   You can adapt this file completely to your liking, but it should at least
   contain the root `toctree` directive.


.. toctree::
   :maxdepth:1

.. _before-obs:

======================
Important checks
======================

Some checks need to be performed before starting the observations.

.. important:: Before observing, check that the ``emergency stop button`` is not pressed.

On discos-manager (ACS)
------------------------

Check that all of the **35 containers** are active on ACS (:numref:`srt_acs`).

.. warning:: If the number of containers is 0 instead of 35 in ACS, you have to start ACS (see the :ref:`Restart-Discos` procedure in the  Discos from Scratch section).

.. <https://srtsupervisoronduty.readthedocs.io/it/latest/sd/srt/procedures/nuraghe.html#avvio-di-nuraghe>`_

.. Check also that the log client **jlog** is open in order to track possible error messages.
.. In case it is not open, type ``$ jlog &`` on a shell.


On discos-console (observer computer)
--------------------------------------

On the CONSOLE virtual desktop, check the presence of the 9 panels (:numref:`srt_vistaglobale`):
   - **operatorInput** (:numref:`srt_operatorinput`)
   - **AntennaBoss** (:numref:`srt_antennaboss`)
   - **GenericBackend** (:numref:`srt_genericBackend`)
   - **Mount** (:numref:`srt_mount`)
   - **Observatory** (:numref:`srt_observatory`)
   - **Receivers** (:numref:`srt_receivers`)
   - **Scheduler** (:numref:`srt_scheduler`)
   - **MinorServo** (:numref:`srt_minorservo`)
   - **ACS custom logging client** (:numref:`srt_jlog`)
   
.. In case it is not open, type ``$ jlog &`` on a shell;

Check also that:

   - the interface of the **Meteo client** is open to check the wind
     velocity in real time (it should be < 60 km/h)
     (:numref:`srt_meteo`). If the interface is closed, type ``$
     meteoClient &`` on a shell;

   - the **quicklook** is open. If it is closed, open it by clicking on the
    **quicklook.html** icon on the desktop of discos-console;

   - the **active surface** is green (:numref:`srt_activesurface`).
.. warning:: The active surface does not work properly if a large fraction (a whole sector) becomes red. It is a problem in K-band observations (:numref:`srt_AS-fraction-red`);

.. warning:: If the **calibrationtool client** is already open or if you need to open it later during your observation to perform pointing and/or focus optimization, remember, do not close it during the whole session. To open it, type ``$ calibrationtoolclient MANAGEMENT/CalibrationTool &`` on a shell.

Upload your shedules (.scd, .lis, .bck and .cfg files) and check them:

   *From your computer:*

   ``$ scp [schedulename.*] [projectID]@discos-dev:./schedules/``

   *On discos-console:*

   ``$ ssh -X [projectID]@discos-dev``

   ``$ cd /home/[projectID]/schedules``

   ``$ scheduleChecker [schedulename.scd]``
   
   
..   *From your computer:*

   ``$ scp [schedulename.*] [projectID]@discos-console:./schedules/``

   *On discos-console:*

   ``$ ssh -X [projectID]@discos-console``

   ``$ cd /home/[projectID]/schedules``

   ``$ scheduleChecker [schedulename.scd]``


.. Upload your shedules (.scd, .lis, .bck and .cfg files) and check them :

..   *From your computer:*

..   $ scp  [schedulename.*] observer@nuraghe-obs1:/archive/schedules/[projectID]``

..   *On nuraghe-obs1:*

..   $ cd /archive/schedules/[projectID]``

..   $ scheduleChecker [schedulename.scd]``
