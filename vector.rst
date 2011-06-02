Vectors
=======

Vectors are represented as 3 word strings. All vectors in TorqueScript follow the X Y Z format. X axis being left/right, Y being forward/back and Z being up/down.

.. function:: vectorAdd(%a,%b)

	Adds vector %a to vector %b and returns the result.

	.. code-block:: csharp

		==> vectorAdd("-5 10 0","5 4 -2");
		0 14 -2

.. function:: vectorSub(%a,%b)

	Subtracts vector %b from vector %a and returns the result. This is the same as adding the inverse of %b to %a.

.. function:: vectorDot(%a,%b)

	Performs a dot product between %a and %b and returns the result. This is the same as (%ax * %bx + %ay * %by + %az * %bz).

	.. code-block:: csharp

		==> vectorDot("5 3 4","4 3 5");
		49
		==> 5 * 4 + 3 * 3 + 4 * 5
		49

.. function:: vectorCross(%a,%b)

	Returns the cross product of vector %a and vector %b.

.. function:: vectorDist(%a,%b)

	Returns the distance between vector %a and vector %b. This is the same as (mSqrt(mPow(%bx - %ax,2) + mPow(%by - %ay,2) + mPow(%bz - %az,2)));

.. function:: vectorLen(%a)

	Returns the length/magnitude of vector %a. This is the same as (mSqrt(mPow(%ax,2) + mPow(%ay,2) + mPow(%az,2)));

.. function:: vectorNormalize(%a)

	Returns the normalized/unit vector of vector %a. This is the same as (%a / vectorLen(%a));

Examples
--------

Getting the rotation between two points (by Truce):

.. code-block:: csharp

	function rotBetween(%a,%b)
	{
		%v = vectorNormalize(vectorSub(%b,%a));
		%x = getWord(%v,0);
		%y = getWord(%v,1);
		%yaw = mATan(%x,%y) - $pi / 2;
		%pitch = 0 - mATan(getWord(%v,2),mSqrt(%x * %x + %y * %y));
		%xy = 0 - %pitch * 180 / $pi;
		%z = -90 - %yaw * 180 / $pi;
		return eulerToAxis(%xy SPC 0 SPC %z);
	}
