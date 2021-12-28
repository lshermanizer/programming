## 1. Install LaTex compiler `TexLive`

### 1.1 Install `TexLive`

Download exe from https://www.tug.org/texlive/acquire-netinstall.html

Install to `C:\Apps`, it takes a long time. The executables are in `C:\Apps\texlive\2021\bin\win32` and are 32-bit. Add this to `PATH`.

### 1.2 Update `TexLive`

`tlmgr` is the name of the package and configuration manager included in TeX Live. 

If the following:
```
tlmgr update --all

tlmgr.pl: Local TeX Live (2020) is older than remote repository (2021).
Cross release updates are only supported with
  update-tlmgr-latest(.sh/.exe) --update
See https://tug.org/texlive/upgrade.html for details.
```

It means that there's a mismatch in the version of the installed Tex Live and the version of remote repo. Do this:
```
tlmgr option repository ftp://tug.org/historic/systems/texlive/2020/tlnet-final
tlmgr.pl: setting default package repository to ftp://tug.org/historic/systems/texlive/2020/tlnet-final
tlmgr.pl: updating C:/texlive/2020/tlpkg/texlive.tlpdb
```

Then I'm able to to:
```
tlmgr update --self
tlmgr update --all
tlmgr install doublestroke
```

### 1.3 Get 64-bit executables

This won't be enough. When I run `texstudio`, it will look for `pdflatex.exe` in `bin\wins64`.

I follow the instructions in https://www.tug.org/texlive/windows.html, download and run `tl64.bat` batch file (run in Admin mode) which creates 64-bit executables in `C:\Apps\texlive\2021\bin\win64`. Then update `PATH` to put the `win64` path ahead of `win32`. This works.


## 2. Install LaTex editor `TeXstudio`

Voila!

