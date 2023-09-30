# Copying file path from Windows to Linux format

```{code}
Clipboard := "J:\folder\folder\folder\"

Numpad1::
    temp := Clipboard
    if InStr(temp,":\")
		Clipboard := Strreplace(SubStr(temp, InStr(temp,":") + 1),"\","/")
return

Numpad2::
	temp := Clipboard
    if InStr(temp,"/")
        Clipboard := "J:" . Strreplace(temp,"/","\")
return
```

# Shortcut to copy path of selected file in Explorer
[LINK](https://www.autohotkey.com/boards/viewtopic.php?t=51793)

```{code}
#IfWinActive, ahk_class CabinetWClass
q:: ;Explorer window - copy focused item path (if item selected) else folder path
#IfWinActive, ahk_class ExploreWClass
q:: ;Explorer window - copy focused item path (if item selected) else folder path
WinGet, hWnd, ID, A
ControlGetFocus, vCtlClassNN, % "ahk_id " hWnd
if !(vCtlClassNN = "DirectUIHWND3")
{
	SendInput, ^c
	return
}

vPath := ""
for oWin in ComObjCreate("Shell.Application").Windows
	if (oWin.HWND = hWnd)
	{
		vPath := oWin.Document.FocusedItem.Path
		if (vPath = "")
			vPath := oWin.Document.Folder.Self.Path
		else
		{
			vIsSelected := 0
			for oItem in oWin.Document.SelectedItems
				if (vPath = oItem.Path)
				{
					vIsSelected := 1
					break
				}
			if !vIsSelected
				vPath := oWin.Document.Folder.Self.Path
		}
		break
	}
oWin := oItem := ""
Clipboard := vPath
MsgBox, % vPath
return
#IfWinActive
```
