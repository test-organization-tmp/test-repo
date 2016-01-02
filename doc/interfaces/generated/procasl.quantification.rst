.. AUTO-GENERATED FILE -- DO NOT EDIT!

quantification
==============


.. _procasl.quantification.QuantifyCBF:


.. index:: QuantifyCBF

QuantifyCBF
-----------

`Link to code <None>`__

Inputs::

        [Mandatory]
        m0_file: (an existing file name)
                M0 image filename
        perfusion_file: (an existing file name)
                perfusion image filename
        tr: (a float, nipype default value: 0.0)
                TR, in ms

        [Optional]
        ignore_exception: (a boolean, nipype default value: False)
                Print an error message instead of throwing an exception in case the
                interface fails to run
        t1_gm: (a float, nipype default value: 1331.0)
                Gray matter T1 value, in ms

Outputs::

        cbf_file: (a list of items which are a list of items which are an
                 existing file name or an existing file name)
                The CBF filename

.. module:: procasl.quantification


.. _procasl.quantification.compute_perfusion:

:func:`compute_perfusion`
-------------------------

`Link to code <None>`__



Compute the mean perfusion image from a functional ASL sequence. The
ASL sequence is assumed aligned.

Parameters
~~~~~~~~~~
in_file : str
    The filename of the input functional ASL 4D image.

ctl_scans : list of int or None, optional
    Indexes of control volumes.

tag_scans : list of int or None, optional
    Indexes of tagged volumes, same length as ctl_scans.


Returns
~~~~~~~
out_file : str
    The filename of the output perfusion image.

