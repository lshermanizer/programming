## 1a. Install LaTex compiler `TexLive`

Download exe from https://www.tug.org/texlive/acquire-netinstall.html

Install to C:\Apps 


I got an error when trying to compile a document:
```
C:\Apps\texlive\2021\bin\win32\runscript.tlu:935: C:\Apps\texlive\2021\bin\win32\runscript.tlu:858: no appropriate script or program found: fmtutil
Running the command C:\Apps\texlive\2021\bin\win32\fmtutil-user.exe
kpathsea: Running mktexfmt pdflatex.fmt The command name is C:\Apps\texlive\2021\bin\win32\mktexfmt
Process exited with error(s)
```

I found an answer at https://tex.stackexchange.com/questions/539040/no-appropriate-script-or-program-found-fmtutil.

I went to https://ctan.org/tex-archive/systems/win32/w32tex/TLW64 and downloaded both files. Follow the README and expand the .zip file -> put the `win64` folder into `bin` -> update PATH as stated in the README

This still didn't work.


## 1b. Try again


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


## 2. Install LaTex editor `TeXstudio`

