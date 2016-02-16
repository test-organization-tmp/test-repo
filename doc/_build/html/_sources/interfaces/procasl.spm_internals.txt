.. AUTO-GENERATED FILE -- DO NOT EDIT!

spm_internals
=============


.. module:: procasl.spm_internals


.. _procasl.spm_internals.affine_to_params:

:func:`affine_to_params`
------------------------

`Link to code <None>`__



Transforms a (4, 4) affine matrix transform to an 1D array of 12
parameters. Mimics the spm function spm_imatrix.

Parameters
~~~~~~~~~~
affine : numpy.ndarray of shape (4, 4)
    The affine transformation matrix.

Returns
~~~~~~~
params : numpy.ndarray of shape (12, )
    Parameters of the transform, in the following order:
    Tx, Ty, Tz, pitch, roll, yaw
    and possibly 3 zooms and 3 shears


.. _procasl.spm_internals.insure_trigo:

:func:`insure_trigo`
--------------------

`Link to code <None>`__






.. _procasl.spm_internals.params_to_affine:

:func:`params_to_affine`
------------------------

`Link to code <None>`__



Transforms parameters to an affine matrix transform.
Mimics the spm function spm_matrix.

Parameters
~~~~~~~~~~
params : 1D numpy.ndarray of size 6 or 12
    Parameters of the transform, in the following order:
    Tx, Ty, Tz, pitch, roll, yaw
    and possibly 3 zooms and 3 shears

Returns
~~~~~~~
affine : numpy.ndarray of shape (4, 4)
    The affine transformation matrix.


.. _procasl.spm_internals.rotation_matrix:

:func:`rotation_matrix`
-----------------------

`Link to code <None>`__



Returns (2, 2) rotation matrix for a given angle.


.. _procasl.spm_internals.spm_affine:

:func:`spm_affine`
------------------

`Link to code <None>`__



Returns the affine transform of a nifti image.
Mimics the spm function spm_get_space.

Parameters
~~~~~~~~~~
in_file : str
    Path to an existant nifti image.

Returns
~~~~~~~
affine : numpy.ndarray of shape (4, 4)
    The affine transformation matrix.

Notes
~~~~~
This function uses nibabel to read the affine transform and corrects the
translation part to match the affine output of spm.

