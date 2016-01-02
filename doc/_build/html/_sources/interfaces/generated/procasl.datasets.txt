.. AUTO-GENERATED FILE -- DO NOT EDIT!

datasets
========


.. module:: procasl.datasets


.. _procasl.datasets.load_heroes_dataset:

:func:`load_heroes_dataset`
---------------------------

`Link to code <None>`__



Loads the NeuroSpin HEROES dataset.

Parameters
~~~~~~~~~~
n_subjects : int or None, optional
    Number of subjects to load, default to loading all subjects.

subjects_parent_directory : str, optional
    Path to the dataset folder containing all subjects folders.

dataset_pattern : dict, optional
    Input dictionary. Keys are the names of the images to load, values
    are strings specifying the unique relative pattern specifying the
    path to these images within each subject directory.

Returns
~~~~~~~
dataset : dict
    The absolute paths to the images for all subjects. Keys are the same
    as the files_patterns keys, values are lists of strings.

