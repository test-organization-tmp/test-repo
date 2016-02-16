

.. _sphx_glr_tutorials_plot_parse.py:


====================
The Header Docstring
====================

When writting latex in a Python string keep in mind to escape the backslashes
or use a raw docstring
.. math:: \sin (x)
Closing this string quotes on same line
Direct first comment
with second line


.. code-block:: python


    import numpy as np




.. rst-class:: sphx-glr-horizontal






.. code-block:: python

    A = 1

    import matplotlib.pyplot as plt




.. rst-class:: sphx-glr-horizontal





There is no need to always alternate between code and comment blocks
Now there is free repetition of both

And a single line of hashes can split your blocks

Latex in the comments does not need to be escaped

.. math::
   \sin


.. code-block:: python


    def dummy():
        """This should not be part of a 'text' block'"""

        ######################################
        # Comment inside code to remain here
        pass

    # this should not be part of a 'text' block




.. rst-class:: sphx-glr-horizontal






####################################################################

Making a line cut in sphinx

.. warning::
    The next kind of comments are not supported and become to hard to escape
    so just don't code like this.

.. code-block:: python

    def dummy2():
        """Function docstring"""
    ####################################
    # This comment inside python indentation
    # breaks the block structure and is not
    # supported
        dummy2



.. code-block:: python


    """Free strings are not supported they remain part of the code"""




.. rst-class:: sphx-glr-horizontal





New lines can be included in you block comments and the parser
is capable of retaining this significant whitespace to work with sphinx

So the reStructuredText headers survive
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^


.. code-block:: python



    print('one')

    print('two')



.. rst-class:: sphx-glr-horizontal



**Script output**:

.. rst-class:: sphx-glr-script-out

  ::

    one
    two



.. code-block:: python

    B = 1




.. rst-class:: sphx-glr-horizontal





End comments

That's all folks !

.. literalinclude:: plot_parse.py



**Total running time of the script:**
(0 minutes 0.001 seconds)



**Download Python source code:** :download:`plot_parse.py <plot_parse.py>`
