This repository is a very slight modification of https://github.com/menpo/conda-metis.
Its aim is to help installing the METIS library on Windows, to use it in [ClustViz](https://github.com/guglielmosanchini/ClustViz) 
and [ClustVizGUI](https://github.com/guglielmosanchini/ClustVizGUI).

#How to install METIS library on Windows 10:

- download and install Cmake (https://cmake.org/download/)
- open the Command Prompt, go to the ClustViz project folder and execute (you can always manually download the zip and extract it in the project folder):
```bash
powershell -command "& { iwr https://github.com/guglielmosanchini/conda-metis/archive/master.zip -OutFile conda-metis-master.zip }"
powershell -nologo -noprofile -command "& { Add-Type -A 'System.IO.Compression.FileSystem'; [IO.Compression.ZipFile]::ExtractToDirectory('conda-metis-master.zip', '.'); }"
cd conda-metis-master
.\vsgen
move /y gk_arch.h GKlib/gk_arch.h
cd build/windows
msbuild METIS.sln
setx METIS_DLL your_path_to_here\conda-metis-master\build\windows\libmetis\Release\metis.dll
```
The last line could have also been:
```bash
set METIS_DLL=your_path_to_here\conda-metis-master\build\windows\libmetis\Release\metis.dll
```
but the latter is local, whereas the former is global.
These instructions have been taken from [here](https://stackoverflow.com/questions/54458470/install-metis-library-for-python3-on-windows7?noredirect=1&lq=1)
and [here](https://stackoverflow.com/questions/50675790/how-to-install-metis-package-in-python-on-windows), with slight modifications.

Other useful commands could be:
```bash
reg add HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\MSBuild\4.0 /v MSBuildOverrideTasksPath /d "C:\Program Files (x86)\Microsoft Visual Studio\2017\BuildTools\MSBuild\15.0\Bin" /f
reg add HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\MSBuild\ToolsVersion\4.0 /v MSBuildToolPath /d "C:\Program Files (x86)\Microsoft Visual Studio\2017\BuildTools\MSBuild\15.0\Bin" /f
```


