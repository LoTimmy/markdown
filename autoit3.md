
``` 
#cs --------------------------
 Author:         Timmy Lo
 Date: Jan 7, 2015
 Script Function:
#ce --------------------------
#NoTrayIcon

#include <GUIConstantsEx.au3>
#include <IE.au3>
#include <WindowsConstants.au3>
#include <Process.au3>

RegWrite("HKEY_CURRENT_USER\Software\Microsoft\Internet Explorer\Main\FeatureControl\FEATURE_BROWSER_EMULATION", _ProcessGetName(@AutoItPID), "REG_DWORD", "0x2AF8")
RegWrite("HKEY_LOCAL_MACHINE\Software\Microsoft\Internet Explorer\Main\FeatureControl\FEATURE_BROWSER_EMULATION", _ProcessGetName(@AutoItPID), "REG_DWORD", "0x2AF8")

; GUI
; $hGUI = GUICreate("Example", 640, 580, (@DesktopWidth - 640) / 2, (@DesktopHeight - 580) / 2, BitOR($WS_OVERLAPPEDWINDOW, $WS_CLIPSIBLINGS, $WS_CLIPCHILDREN))
$hGUI = GUICreate("Example", @DesktopWidth - 40, @DesktopHeight - 100, (@DesktopWidth - 853) / 2, (@DesktopHeight - 600) / 2, BitOR($WS_OVERLAPPEDWINDOW, $WS_CLIPSIBLINGS, $WS_CLIPCHILDREN))
GUISetIcon(@SystemDir & "\mspaint.exe", 0)
WinSetState($hGUI, "", @SW_MAXIMIZE )

$oIE = ObjCreate("Shell.Explorer.2")
;GUICtrlCreateObj($oIE, 10, 40, 600, 360)
GUICtrlCreateObj($oIE, 0, 0, @DesktopWidth - 40, @DesktopHeight - 100)

; Display the GUI.
GUISetState(@SW_SHOW, $hGUI)

_IENavigate($oIE, "http://getbootstrap.com/")

; Waiting for user to close the window
While 1
  Local $iMsg = GUIGetMsg()
  Select
    Case $iMsg = $GUI_EVENT_CLOSE
      ExitLoop
  EndSelect
WEnd

GUIDelete()

Exit

```

----------


----------
### :books: 參考網站：