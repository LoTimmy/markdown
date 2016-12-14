
### NSIS 


makensis.exe myscript.nsi


Comments

```
; Comment
# Comment

# Comment \
    Another comment line (see `Long commands` section below)

/*
Comment
Comment
*/

Name /* comment */ mysetup

File "myfile" ; Comment
```


```
;Include Modern UI

!include "MUI2.nsh"
```

```
;Name and file
Name "Silent"
OutFile "silent.exe"
```

```
Icon MyProgSetup.ico
```
```
;Default installation folder
InstallDir "$LOCALAPPDATA\Modern UI Test"
```

```
;Request application privileges for Windows Vista
RequestExecutionLevel user
```

**SILENT**
```
SilentInstall silent
AutoCloseWindow true

WindowIcon off
```

```
Exec '"$INSTDIR\someprogram.exe"'
Exec '"$INSTDIR\someprogram.exe" some parameters'
```

```
Name "Silent"
OutFile "silent.exe"
InstallDir "C:\MyProg"
RequestExecutionLevel user

SilentInstall silent
AutoCloseWindow true
WindowIcon off

Page directory
Page instfiles
  
Section ""
  SetOutPath $INSTDIR
  File MyProgram.exe
SectionEnd
```


```
Name "Silent"
OutFile "silent.exe"
;InstallDir "C:\MyProg"
InstallDir $TEMP
RequestExecutionLevel user

LoadLanguageFile "${NSISDIR}\Contrib\Language files\English.nlf"

VIProductVersion "1.2.3.4"
VIAddVersionKey /LANG=${LANG_ENGLISH} "ProductName" "Test Application"
VIAddVersionKey /LANG=${LANG_ENGLISH} "Comments" "A test comment"
VIAddVersionKey /LANG=${LANG_ENGLISH} "CompanyName" "Fake company"
VIAddVersionKey /LANG=${LANG_ENGLISH} "LegalTrademarks" "Test Application is a trademark of Fake company"
VIAddVersionKey /LANG=${LANG_ENGLISH} "LegalCopyright" "Copyright Fake company"
VIAddVersionKey /LANG=${LANG_ENGLISH} "FileDescription" "Test Application"
VIAddVersionKey /LANG=${LANG_ENGLISH} "FileVersion" "1.2.3"

Icon "MyProgSetup.ico"

SilentInstall silent
AutoCloseWindow true
WindowIcon off

Page directory
Page instfiles
  
Section ""
  SetOutPath $INSTDIR
  File MyProgram.exe
  Exec '"$INSTDIR\someprogram.exe" some parameters'
SectionEnd
```


### :books: 參考網站：
- [nsis](http://nsis.sourceforge.net/Docs/Chapter4.html)

---
