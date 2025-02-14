
.. DO NOT EDIT.
.. THIS FILE WAS AUTOMATICALLY GENERATED BY SPHINX-GALLERY.
.. TO MAKE CHANGES, EDIT THE SOURCE PYTHON FILE:
.. "tutorials/01_usecase/04_cross_efficiency.py"
.. LINE NUMBERS ARE GIVEN BELOW.

.. only:: html

    .. note::
        :class: sphx-glr-download-link-note

        Click :ref:`here <sphx_glr_download_tutorials_01_usecase_04_cross_efficiency.py>`
        to download the full example code

.. rst-class:: sphx-glr-example-title

.. _sphx_glr_tutorials_01_usecase_04_cross_efficiency.py:


Cross efficiency
=========================

Preparing...

.. GENERATED FROM PYTHON SOURCE LINES 10-13

Import modules and prepare data.
------------------------


.. GENERATED FROM PYTHON SOURCE LINES 13-22

.. code-block:: default

    import matplotlib.pyplot as plt
    import pandas as pd

    from Pyfrontier.frontier_model import MultipleDEA

    df = pd.DataFrame(
        {"price": [3, 2, 4, 6, 4], "rent": [5, 2, 2, 1, 6], "output": [2, 1.5, 3, 2, 2]}
    )








.. GENERATED FROM PYTHON SOURCE LINES 23-26

.. code-block:: default


    dea = MultipleDEA("CRS", "in")
    dea.fit(df[["price", "rent"]].to_numpy(), df[["output"]].to_numpy())







.. GENERATED FROM PYTHON SOURCE LINES 27-28

.. code-block:: default

    dea.result[0]




.. rst-class:: sphx-glr-script-out

 .. code-block:: none


    MultipleResult(score=0.888889, id=0, dmu=DMU(input=array([3, 5]), output=array([2.]), id=0), x_weight=[0.333333, 0.0], y_weight=[0.444444], bias=0.0)



.. GENERATED FROM PYTHON SOURCE LINES 29-30

.. code-block:: default

    [r.score for r in dea.result]




.. rst-class:: sphx-glr-script-out

 .. code-block:: none


    [0.888889, 1.0, 1.0, 1.0, 0.666667]



.. GENERATED FROM PYTHON SOURCE LINES 31-32

.. code-block:: default

    dea.cross_efficiency




.. rst-class:: sphx-glr-script-out

 .. code-block:: none


    [0.7166663333333333, 0.8437494999999999, 0.937499875, 0.4444442777777778, 0.5416665833333334]



.. GENERATED FROM PYTHON SOURCE LINES 33-39

.. code-block:: default

    efficiency_matrix = dea._cross_efficiency_matrix()

    plt.figure()
    plt.imshow(efficiency_matrix, interpolation="nearest", vmin=0, vmax=1, cmap="Blues")
    plt.colorbar()
    plt.show()



.. image-sg:: /tutorials/01_usecase/images/sphx_glr_04_cross_efficiency_001.png
   :alt: 04 cross efficiency
   :srcset: /tutorials/01_usecase/images/sphx_glr_04_cross_efficiency_001.png
   :class: sphx-glr-single-img





.. GENERATED FROM PYTHON SOURCE LINES 40-51

References
------------------------
.. seealso::

   Author
      John Doyle and Rodney Green.
   Title
      *Efficiency and Cross-efficiency in DEA: Derivations, Meanings and Uses*,
    Journal of the Operational Research Society,
    1994.
    :numref:`10.1057/jors.1994.84`.

.. GENERATED FROM PYTHON SOURCE LINES 54-63

.. seealso::

   Author
      Sexton, Thomas R. and Silkman, Richard H. and Hogan, Andrew J..
   Title
      *Data envelopment analysis: Critique and extensions*,
    New Directions for Program Evaluation,
    1986.
    :numref:`https://doi.org/10.1002/ev.1441`.


.. rst-class:: sphx-glr-timing

   **Total running time of the script:** ( 0 minutes  0.233 seconds)


.. _sphx_glr_download_tutorials_01_usecase_04_cross_efficiency.py:

.. only:: html

  .. container:: sphx-glr-footer sphx-glr-footer-example


    .. container:: sphx-glr-download sphx-glr-download-python

      :download:`Download Python source code: 04_cross_efficiency.py <04_cross_efficiency.py>`

    .. container:: sphx-glr-download sphx-glr-download-jupyter

      :download:`Download Jupyter notebook: 04_cross_efficiency.ipynb <04_cross_efficiency.ipynb>`


.. only:: html

 .. rst-class:: sphx-glr-signature

    `Gallery generated by Sphinx-Gallery <https://sphinx-gallery.github.io>`_
