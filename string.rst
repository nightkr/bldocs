Strings
=======

Manipulation
------------

.. function:: getSubStr(%string,%index[,%length])

	Returns the characters in %string from %index, *optionally* only returning %length characters from the start of %index.

.. function:: strStr(%haystack, %needle)

	Searches for %needle in the %haystack *with* case-sensitivity. Returns the index of the beginning of %needle in %haystack on success and -1 when it cannot be found.

.. function:: strReplace(%str, %old, %new)

	Replaces all instances of %old in %str with %new and returns the result.

	.. code-block:: csharp

		==> strReplace("Hello, World!","World","Jeff");
		Hello, Jeff!

.. function:: strLwr(%str)

	Returns all characters in %str in lower-case form.

.. function:: strUpr(%str)

	Returns all characters in %str in upper-case form.

.. function:: stripChars(%str, %chars)

	Removes every instance of any character in %chars from %str and returns the result.

.. function:: stripMLControlChars(%str)

	Removes any Torque Markup Language tags from %str and returns the result.

.. function:: strTrim(%str)

	Removes any white space from the left and right of %str and returns the result.

.. function:: trim(%str)

	Removes any white space from the left and right of %str and returns the result.

.. function:: ltrim(%str)

	Removes any white space from the left of %str and returns the result.

.. function:: rtrim(%str)

	Removes any white space from the right of %str and returns the result.

.. function:: stripTrailingSpaces(%str)

	Removes any spaces or underscores from %str and returns the result.

Processing
----------

.. function:: strPos(%haystack, %needle)

	Searches for %needle in the %haystack *with* case-sensitivity. Returns the index of the beginning of %needle in %haystack on success and -1 when it cannot be found.

.. function:: striPos(%haystack, %needle)

	Searches for %needle in the %haystack *without* case-sensitivity. Returns the index of the beginning of %needle in %haystack on success and -1 when it cannot be found.

.. function:: strLen(%str)

	Returns the number of characters in %str.

.. function:: strCmp(%str1, %str2)

	Compares %str1 and %str2 **lexicographically**, i.e. in dictionary order, **with** case-sensitivity.
	Returns -1 if %str1 is less than %str2 (%str1 comes before %str2 in the dictionary), 0 if they are equal (%str1 and %str2 would be in the same place in the dictionary) and 1 if %str1 is greater than %str2 (%str1 comes after %str2 in the dictionary).

	.. code-block:: csharp

		==> strCmp("bob","bane")
		1
		==> strCmp("bob","cat")
		-1
		==> strCmp("cat","cat")
		0

.. function:: striCmp(%str1, %str2)

	Compares %str1 and %str2 **lexicographically**, i.e. in dictionary order, *without* case-sensitivity.
	Returns -1 if %str1 is less than %str2 (%str1 comes before %str2 in the dictionary), 0 if they are equal (%str1 and %str2 would be in the same place in the dictionary) and 1 if %str1 is greater than %str2 (%str1 comes after %str2 in the dictionary).

Words
-----

Strings containing words, seperated by a space (" "), can also be processed and manipulated.

.. function:: firstWord(%str)

	Returns the first word in %str.

	.. code-block:: csharp

		==> firstWord("Bob has a nice car.");
		Bob

.. function:: restWords(%str)

	Returns every word in %str except for the first.

	.. code-block:: csharp

		==> firstWord("Bob has a nice car.");
		has a nice car.

.. function:: getWord(%str,%index)

	Returns the word at %index in %str.

	.. code-block:: csharp

		==> getWord("Bob has a nice car.",1);
		has

.. function:: getWordCount(%str)

	Returns the word count of %str.

.. function:: getWords(%str,%startIndex[,%endIndex])

	Returns all words in %str from %startIndex, or *optionally* all words from %startIndex to %endIndex.

.. function:: removeWord(%str,%index)

	Removes the word at %index in %str and returns the result.

.. function:: setWord(%str,%index,%word)

	Sets the the word in %str at %index to %word and returns the result.

Tokenizing
----------

.. function:: nextToken(%string, %variableName, %delimeter)

	%string is the string containing tokens seperated by %delimiter. This function will split the string into seperate tokens (using %delimiter to split) and make a variable named %variableName in the scope with the next token's value.

	.. code-block:: csharp

		function tokenExample(%string)
		{
			%tokens = %string;
			while(%tokens !$= "")
			{
				%tokens = nextToken(%tokens,"token",":");
				echo(%token);
			}
		}
		==> tokenExample("Hello:this:is:being:tokenized");
		Hello
		this
		is
		being
		tokenized
