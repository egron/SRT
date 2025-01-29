.. SRT procedures documentation master file, created by
   sphinx-quickstart on Mon Aug  7 16:44:28 2017.
   You can adapt this file completely to your liking, but it should at least
   contain the root `toctree` directive.


.. toctree::
   :maxdepth: 1

.. _stop-session-Xarcos:

End of the session
======================

>  : commands to insert in the operatorInput panel

.. |logo| image:: monocle_.png
..    :width: 20pt
..    :height: 20pt
..   :align: left
|logo|: check on the monitor

======================

Your observations are now finished, we can stop the schedule and park
the antenna.

On discos-console
-----------------

.. On nuraghe-obs1 ------------------

1. Stop your schedule :

   ``> haltSchedule``    *the schedule stops at the end of the on-going subscan.*

   Important note: do not stop Xarcos schedule with **stopSchedule**.


2. Park the minor servo, active surface and antenna

   ``> goTo=180d,89d`` |logo| :numref:`srt_mount`

   ``> servoPark`` |logo| :numref:`srt_minorservo_end`

   ``> asPark`` |logo| :numref:`srt_activesurface_2`

   ``> antennaPark`` |logo| :numref:`srt_mount_antennareset`  |logo| :numref:`srt_ACU_stowpin`



Block the axes of the antenna
------------------------------

Look at the ACU monitor, wait until
**Axis blocked** appears in red. It can take a few minutes after the command
``> antennaPark`` has been given (:numref:`srt_ACU_axisblocked`).

Only at this moment, you can press on the emergency stop button
(:numref:`srt_ACU_redbutton`).
