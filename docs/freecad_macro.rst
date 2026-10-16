FreeCAD Macro
=============

The model on the main page (a 1 m x 1 m x 20 cm steel sheet with the initials "GM" carved 5 cm deep) was built by this FreeCAD macro, ``build_gm_sheet.FCMacro``. The macro ran inside the FreeCAD GUI while ``recordmydesktop`` recorded the screen, so every step appears in the video.

* Download: :download:`build_gm_sheet.FCMacro <build_gm_sheet.FCMacro>`
* View on GitHub: `docs/build_gm_sheet.FCMacro <https://github.com/greysonbmiller/eco-libre-volunteer-test/blob/main/docs/build_gm_sheet.FCMacro>`_

What it does
------------

#. Creates a new document and a PartDesign ``Body``.
#. Opens a sketch on the ``XY_Plane`` in the **Sketcher** workbench and draws a fully constrained 1000 mm x 1000 mm square, one line at a time.
#. **Pads** the square 200 mm and sets the Body's material to *Steel*.
#. Opens a second sketch on the ``XY_Plane``, offset 200 mm so it sits on the top face, and draws the outlines of block letters **G** and **M** (500 mm tall, 80 mm strokes).
#. **Pockets** the letters 50 mm deep.
#. Checks the result (valid solid, 1000 x 1000 x 200 mm bounding box, removed volume equals letter area x 50 mm), saves ``gm-eco-libre-volunteer-test.FCStd``, and takes the screenshot shown on the main page.

In the GUI it pauses between steps and opens the Pad and Pocket dialogs, so you can watch each step happen. Run headless, it skips the pauses.

How to run it
-------------

In the FreeCAD GUI, use **Macro -> Macros...**, choose the folder containing the macro, select it, and click **Execute**. You can also pass it on the command line (FreeCAD from Flathub shown):

.. code-block:: bash

   # in the GUI
   flatpak run org.freecad.FreeCAD build_gm_sheet.FCMacro

   # headless
   flatpak run --command=FreeCADCmd org.freecad.FreeCAD build_gm_sheet.FCMacro

It saves its output next to the macro, or in ``$GM_OUT_DIR`` if set. It was tested with FreeCAD 1.1.4.

.. note::

   The lines that set the document's license metadata (CC BY-SA 4.0) and the default output folder were added after the recording. The committed ``.FCStd`` had its license set to match.

Source
------

.. literalinclude:: build_gm_sheet.FCMacro
   :language: python
   :linenos:
