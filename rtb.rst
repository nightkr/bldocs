Return to Blockland
===================

See the `official RTB modding documentation <http://www.returntoblockland.com/files/RTB_Documentation.pdf>`_ written by the RTB developer, Ephialtes, for more information.

.. function:: RTB_registerPref(%prefName, %category, %variableName, %variableType, %addOnName, %defaultValue, %requiresRestart, %hostOnly[, %callback])

	Registers a preference that can be changed in the RTB Server Control interface. This should only be called while the server is starting up.

	%prefName is the name of the preference that will be displayed in the Server Control menu.

	%prefCategory is the category to display the preference in. Preferences with the same category are displayed together.

	%variableName is the global variable name to link the RTB preference to. For example, *$Duplicator::Timeout*.

	%variableType is the type of the variable that this preference will be.

		- **"bool"** will only accept true or false values and will appear as a checkbox in the Server Control interface.

		- **"list text value text value text value"** for a list. This will appear as a popup box in the Server Control interface. For each selectable option you want you need to include a text (the text to display in the selectable option) and the value (the value to set the preference to when the option is selected). For example, *"list North 0 South 1 East 2 West 3 Up 4 Down 6"*.

		- **"int min max"** will accept an integer (whole number) between min and max and will appear as a textbox that auto corrects non-numbers. For example, *"int 1 10"* will result in a textbox that allows you to enter numbers between 1 and 10.

		- **"string length"** will accept a string with a maximum character limit of length. It appears as a textbox.

	%addOnName is the name of your add-on. It needs to be the file name without the .zip extension. For example, *"Tool_Duplicator"*.

	%defaultValue is the default value for the preference. When the preference is first registered (say, if the user just downloaded) the preference is set to this value. Otherwise it is set to the saved value for the preference. This is also used when a user clicks the Defaults button in the Server Control interface.

	%requiresRestart is a boolean value that will tell the user on the Server Control interface that they must restart the server for the changes to apply. It doesn't actually force the server to restart though.

	%hostOnly is a boolean value that makes the preference only editable by the server host in the Server Control menu.

	%callback is *optional*, it is the name of a function to call when the value of the preference is edited via the Server Control menu. The function is called with the old value as the first argument and the new value as the second argument.
	
	.. code-block:: csharp

		RTB_registerPref("Duplicator Timeout","Duplicator","$Duplicator::Timeout","int 0 60","Tool_Duplicator",40,0,0);

.. function:: RTB_registerGUI(%guiFile)

	Registers a GUI, %guiFile being the path to the GUI, with RTB. The GUI will be sent to all RTB users that join the server. This is essentially server-side GUIs. The restrictions on the client-side are very strict and RTB will block off any GUIs while they are downloading if they are found to be malicious. See the `RTB modding documentation <http://www.returntoblockland.com/files/RTB_Documentation.pdf>`_ for more detailed information.

.. function:: RTB_addInfoTip(%tipMessage,%noBindTipMessage,%category)

	%tipMessage is the message to display when the tip is shown. It accepts Torque Markup Language formatting, as well as an additional (<key:keybindFunctionName>) markup tag to show the key mapping of a keybind.

	%noBindTipMessage is the message to display when a keybind markup tag in %tipMessage doesn't have a binding. It also accepts Torque Markup Language formatting.

	%category is un-used currently but in the future it will be used to group tips together.

Examples
--------

The *correct* method for registering an RTB preference:

.. code-block:: csharp

	if(isFile("Add-Ons/System_ReturnToBlockland/server.cs"))
	{
		if(!$RTB::RTBR_ServerControl_Hook)
		{
			//This sets the RTB preference system up. Don't remove this code!
			if(isFile("Add-Ons/System_ReturnToBlockland/hooks/serverControl.cs"))
				exec("Add-Ons/System_ReturnToBlockland/hooks/serverControl.cs");
			else
				exec("Add-Ons/System_ReturnToBlockland/RTBR_ServerControl_Hook.cs");
		}
		//Register your RTB prefs now and do any other RTB-based things.
	}
	else
	{
		//The user doesn't have RTB so just set the global variables to their default value or do your own non RTB things
	}

Using the RTB preference system functionality in a server command:

.. code-block:: csharp

	if(isFile("Add-Ons/System_ReturnToBlockland/server.cs"))
	{
		if(!$RTB::RTBR_ServerControl_Hook)
		{
			if(isFile("Add-Ons/System_ReturnToBlockland/hooks/serverControl.cs"))
				exec("Add-Ons/System_ReturnToBlockland/hooks/serverControl.cs");
			else
				exec("Add-Ons/System_ReturnToBlockland/RTBR_ServerControl_Hook.cs");
		}
		RTB_registerPref("Enabled","Kill Mod","$Kill::Enabled","bool","Script_KillMod",1,0,0,"killModToggled");
		RTB_registerPref("Host Only","Kill Mod","$Kill::HostOnly","bool","Script_KillMod",0,0,1);
		RTB_registerPref("Kill Message","Kill Mod","$Kill::Message","string 100","Script_KillMod","Sorry %1, you were killed by %2.",0,0);
	}
	else
	{
		$Kill::Enabled = 1;
		$Kill::HostOnly = 0;
		$Kill::Message = "Sorry %1, you were killed by %2.";
	}
	function serverCmdKill(%client,%targetName)
	{
		if(!%client.isAdmin || !$Kill::Enabled || ($Kill::HostOnly && %client.bl_id != getNumKeyID()))
			return;
		%targetClient = findClientByName(%targetName);
		%targetPlayer = %targetClient.player;
		if(isObject(%targetPlayer))
		{
			%message = strReplace($Kill::Message,"%1",%client.getPlayerName());
			%message = strReplace(%message,"%2",%targetClient.getPlayerName());
			messageClient(%targetClient,'',%message);
			%targetPlayer.kill();
		}
	}
	function killModToggled(%oldValue,%newValue)
	{
		if(%newValue)
			echo("Kill mod is now enabled.");
		else
			echo("Kill mod is now disabled.");
	}
