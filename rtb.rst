Return To Blockland (3.5)
=========================

All the APIs are from the official API documentation by Ephialtes.


.. function:: RTB_registerPref(%PrefName, %Category, %VariableName, %VariableType, %AddOnName, %DefaultValue, %RequiresRestart, %HostOnly[, %Callback])
   
   Arguments:

   * %PrefName: The visible name in the RTB GUI.
   * %Category: The category in the RTB GUI.
   * %VariableName: The actual variable name.
   * %VariableType: The type of the pref. Usable templates:

     * "list %text %value %text %value" etc
     * "bool"
     * "int %min %max"
     * "string %max"

   * %AddOnName: The name of the Add-On (isn't used yet but required).
   * %DefaultValue: The default value.
   * %RequiresRestart: Does the server need to be restarted before taking effect?
   * %HostOnly: Can only the host change this option?
   * %Callback: What function to call after the pref is changed. The function is passed both the old value and the new pref.

   Notes:

   The prefs a client sees are only refreshed when the client is becoming a super-admin.
