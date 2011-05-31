String manipulation and processing
==================================

.. function:: strPos(%haystack, %needle)

	Searches for %needle in the %haystack with case-sensitivity. Returns the index of the beginning of %needle in %haystack on success and -1 when it cannot be found.

.. function:: striPos(%haystack, %needle)

	Searches for %needle in the %haystack without case-sensitivity. Returns the index of the beginning of %needle in %haystack on success and -1 when it cannot be found.

.. function:: strStr(%haystack, %needle)

	Searches for %needle in the %haystack with case-sensitivity. Returns the index of the beginning of %needle in %haystack on success and -1 when it cannot be found.

.. function:: strReplace(%str, %old, %new)

	Replaces all instances of %old in %str with %new and returns the result.
	.. code-block:: none

		==> strReplace("Hello, World!","World","Jeff");
		Hello, Jeff!

.. function:: strLen(%str)

	Returns the number of characters in %str.

.. function:: strLwr(%str)

	Returns all characters in %str in lower-case form.

.. function:: strUpr(%str)

	Returns all characters in %str in upper-case form.

.. function:: strUpr(%str)

	Returns all characters in %str in upper-case form.

.. function:: strUpr(%str)

	Returns all characters in %str in upper-case form.

.. function:: strCmp(%str1, %str2)

	Compares %str1 and %str2 *lexicographically*, i.e. in dictionary order, with case-sensitivity.
	Returns -1 if %str1 is less than %str2 (%str1 comes before %str2 in the dictionary), 0 if they are equal (%str1 and %str2 would be in the same place in the dictionary) and 1 if %str1 is greater than %str2 (%str1 comes after %str2 in the dictionary).

	.. code-block:: none

		==> strCmp("bob","bane")
		1
		==> strCmp("bob","cat")
		-1
		==> strCmp("cat","cat")
		0

.. function:: striCmp(%str1, %str2)

	Compares %str1 and %str2 *lexicographically*, i.e. in dictionary order, without case-sensitivity.
	Returns -1 if %str1 is less than %str2 (%str1 comes before %str2 in the dictionary), 0 if they are equal (%str1 and %str2 would be in the same place in the dictionary) and 1 if %str1 is greater than %str2 (%str1 comes after %str2 in the dictionary).

.. function:: stripChars(%str, %chars)

	Removes every instance of any character in %chars from %str and returns the result.

.. function:: stripMLControlChars(%str)

	Removes any Torque Markup Language tags from %str and returns the result.
