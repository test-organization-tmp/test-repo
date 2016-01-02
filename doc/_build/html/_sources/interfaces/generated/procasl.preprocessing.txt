.. AUTO-GENERATED FILE -- DO NOT EDIT!

preprocessing
=============


.. _procasl.preprocessing.Average:


.. index:: Average

Average
-------

`Link to code <None>`__

Compute average functional across time, keeping the affine of
first scan.

Notes
~~~~~
This is a reimplementation of the averaging method of
average_2010.m from the GIN toolbox.

Inputs::

        [Mandatory]
        in_file: (an existing file name)
                list of images filenames to average

        [Optional]
        ignore_exception: (a boolean, nipype default value: False)
                Print an error message instead of throwing an exception in case the
                interface fails to run

Outputs::

        mean_file: (a list of items which are a list of items which are an
                 existing file name or an existing file name)
                The average image file

.. _procasl.preprocessing.GetM0:


.. index:: GetM0

GetM0
-----

`Link to code <None>`__

Save the M0 scan from ASL 4D image (first scan).

Inputs::

        [Mandatory]
        in_file: (an existing file name)
                The input 4D ASL image filename

        [Optional]
        ignore_exception: (a boolean, nipype default value: False)
                Print an error message instead of throwing an exception in case the
                interface fails to run

Outputs::

        m0_file: (an existing file name)
                The first scan image filename

.. _procasl.preprocessing.GetTagControl:


.. index:: GetTagControl

GetTagControl
-------------

`Link to code <None>`__

Save the tag/control sequence of a 4D ASL image (removes first scan).

Inputs::

        [Mandatory]
        in_file: (an existing file name)
                The input 4D ASL image filename

        [Optional]
        ignore_exception: (a boolean, nipype default value: False)
                Print an error message instead of throwing an exception in case the
                interface fails to run

Outputs::

        tag_ctl_file: (an existing file name)
                The tag/control sequence image filename

.. _procasl.preprocessing.Realign:


.. index:: Realign

Realign
-------

`Link to code <None>`__

Realign functional scans. Default parameters are those of the GIN
pipeline.

Notes
~~~~~
This is a reimplementation of the realignement method from
myrealign_pasl_2010.m of GIN toolbox.

Examples
~~~~~~~~
import procasl.preprocessing as asl
realign = asl.Realign
realign.inputs.in_file = 'functional.nii'
realign.inputs.register_to_mean = False
realign.inputs.correct_tagging = True
out_realign = realign.run()
print(out_realign.realigned files, out_realign.realignement_parameters)

Inputs::

        [Mandatory]
        in_file: (an existing file name)
                The filename of the input functional ASL 4D image.
        register_to_mean: (a boolean, nipype default value: True)
                Indicate whether realignment is done to the mean image

        [Optional]
        control_scans: (a list of items which are an integer)
                control frames numbers
        correct_tagging: (a boolean, nipype default value: False)
                True/False correct for tagging artifact by zeroing the mean
                difference between control and tag.
        ignore_exception: (a boolean, nipype default value: False)
                Print an error message instead of throwing an exception in case the
                interface fails to run
        paths: (a list of items which are an existing directory name)
                Paths to add to matlabpath
        tag_scans: (a list of items which are an integer)
                tag frames numbers

Outputs::

        realigned_files: (a list of items which are a list of items which are
                 an existing file name or an existing file name)
                The resliced files
        realignment_parameters: (a list of items which are an existing file
                 name)
                Estimated translation and rotation parameters

.. _procasl.preprocessing.Rescale:


.. index:: Rescale

Rescale
-------

`Link to code <None>`__

Correct for T1 relaxation between different slices. This is a
reimplementation of the rescaling method of
correction_scalefactors_philips_2010.m from the GIN toolbox,
courtesy of...
PASL images are acquired in EPI single shot with slices from
bottom to up of the brain.
For PASL,
CBF (ml/100g/min) = deltaM / (2 * M0b * tao * exp(-TI / T1b) * qTI)
and
M0b = Rwm * M0WM * exp((1/T2wm-1/T2b)*TE)
or M0b=Rcsf*M0csf*exp((1/T2csf-1/T2b)*TE)
or M0b = MPD / (1 - exp(-TR / T1_tissue)),
TI is the inversion time for different slice;
T1b is the constant relaxation time of arterial blood.
tao is actually TI1 in QUIPPS II
qTI is close to unit, and is set to 0.85 in Warmuth 05. In addition, we
introduce the label efficiency in the calculation.
Rwm  - proton density ratio between blood and WM1.06 in Wong 97. 1.19 in
Cavosuglu 09; T2wm and T2b are 55 msec and 100 for 1.5T, 40 and 80 for 3T,
30 and 60 for 4T;
Rcsf - proton density ratio between blood and csf, 0.87 in Cavosuglu,
T2csf is 74.9 ms for 3T.
M0WM means the mean value in an homogenous white matter region, and it
could be selected by drawing an ROI in the M0 image.
Please refer to: 1) Buxton et al, 1998 MRM 40:383-96, 2) Warmuth C.,
Gunther M. and Zimmer G. Radiology, 2003; 228:523-532.
Note (Nov 19 2010): T2wm and T2b at 3T were changed to 44.7 and 43.6,
T2csf if used was set to 74.9 according to Cavusoglu 09 MRI

Examples
~~~~~~~~
from procasl.preprocessing as asl
rescale = asl.Rescale
rescale.inputs.in_file = 'raw_asl.nii'
rescale.inputs.ss_tr = 35.
rescale.inputs.t_i_1 = 800.
rescale.inputs.t_i_2 = 1800.
out_rescale = rescale.run()
print(out_rescale.rescaleed files)

Inputs::

        [Mandatory]
        in_file: (an existing file name)
                list of images filenames to rescale
        ss_tr: (a float)
                Single slice repetition time, in ms
        t_i_1: (a float)
                Bolus length, in ms
        t_i_2: (a float)
                Inversion time (time from the application of the labelingpulse to
                image acquisition, Aslop 2014), in ms

        [Optional]
        ignore_exception: (a boolean, nipype default value: False)
                Print an error message instead of throwing an exception in case the
                interface fails to run
        label_efficiency: (a float, nipype default value: 0.98)
                labeling efficiency
        t1_blood: (a float, nipype default value: 1650.0)
                T1 of the blood in ms

Outputs::

        rescaled_file: (a list of items which are a list of items which are
                 an existing file name or an existing file name)
                The rescaled image file

.. module:: procasl.preprocessing


.. _procasl.preprocessing.add_prefix:

:func:`add_prefix`
------------------

`Link to code <None>`__



Adds a prefix to a filename

Parameters
~~~~~~~~~~
prefix : str
    Prefix to append to the filename

in_file : str
    Input file name.

Returns
~~~~~~~
out_file : str
    Output file name


.. _procasl.preprocessing.apply_mask:

:func:`apply_mask`
------------------

`Link to code <None>`__



Masks input with a binary mask_file.


.. _procasl.preprocessing.binarize_mask:

:func:`binarize_mask`
---------------------

`Link to code <None>`__






.. _procasl.preprocessing.compute_brain_mask:

:func:`compute_brain_mask`
--------------------------

`Link to code <None>`__



Computes binary brain mask using FSL BET.


.. _procasl.preprocessing.compute_mask:

:func:`compute_mask`
--------------------

`Link to code <None>`__



Compute a brain mask from a 4D or a3D image.


.. _procasl.preprocessing.get_scans_number:

:func:`get_scans_number`
------------------------

`Link to code <None>`__



Return the number of scans for a 4D image.


.. _procasl.preprocessing.save_first_scan:

:func:`save_first_scan`
-----------------------

`Link to code <None>`__






.. _procasl.preprocessing.select_scans:

:func:`select_scans`
--------------------

`Link to code <None>`__



Save a selected scan volumes from a 4D image.

