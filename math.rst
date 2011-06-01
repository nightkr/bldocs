Mathematical operations
=======================

.. function:: mAbs(%n)

	Returns the absolute value (the distance from 0 on the number line) of %n.

	.. code-block:: none

		==> mAbs(-5);
		5
		==> mAbs(5);
		5

.. function:: mAcos(%n)

	A `Trigonometrical <http://en.wikipedia.org/wiki/Trigonometry>`_ function that returns the arc-cosine of %n, in radians.

.. function:: mAsin(%n)

	A `Trigonometrical <http://en.wikipedia.org/wiki/Trigonometry>`_ function that returns the arc-sine of %n, in radians.

.. function:: mAtan(%n)

	A `Trigonometrical <http://en.wikipedia.org/wiki/Trigonometry>`_ function that returns the arc-tangent of %n, in radians.

.. function:: mCos(%n)

	A `Trigonometrical <http://en.wikipedia.org/wiki/Trigonometry>`_ function that returns the cosine of %n.

.. function:: mSin(%n)

	A `Trigonometrical <http://en.wikipedia.org/wiki/Trigonometry>`_ function that returns the sine of %n.

.. function:: mTan(%n)

	A `Trigonometrical <http://en.wikipedia.org/wiki/Trigonometry>`_ function that returns the tangent of %n.

.. function:: mCeil(%n)

	Rounds %n up and returns the result.

.. function:: mFloor(%n)

	Rounds %n down and returns the result.

.. function:: mClamp(%n, %min, %max)

	Clamps %n between %min and %max. If %n is smaller than %min it returns %min, if %n is larger than %max it returns %max, otherwise it returns %n.

	.. code-block:: none

		==> mClamp(5,1,10);
		5
		==> mClamp(-2,1,10);
		1
		==> mClamp(23,1,10);
		10

.. function:: mClamp(%n, %min, %max)

	Clamps %n between %min and %max, supporting floating (decimal) point numbers. If %n is smaller than %min it returns %min, if %n is larger than %max it returns %max, otherwise it returns %n.

.. function:: mDegToRad(%n)

	Converts %n from radians to degrees and returns the result.

.. function:: mRadToDeg(%n)

	Converts %n from degrees to radians and returns the result.

.. function:: mFloatLength(%n, %length)

	Returns the floating (decimal) point value of %n with only %length number of decimal places with the last decimal place rounded.

	.. code-block:: none

		==> mFloatLength(3.14159265,4);
		3.1416

.. function:: mLog(%n)

	Returns the natural logarithm of %n.

.. function:: mLog(%n)

	Returns the natural logarithm of %n.

.. function:: mPow(%n, %x)

	Returns %n to the power of %x.

	.. code-block:: none

		==> mPow(2,2);
		4
		==> mPow(2,4);
		16
		==> mPow(16, 1 / 2);
		4

.. function:: mSqrt(%n)

	Returns the square root of %n. This is the same as mPow(%n, 1 / 2);
