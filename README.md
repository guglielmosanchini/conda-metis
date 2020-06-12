How to install METIS library on Windows 10

download and install Cmake, pip install metis, download and extract https://github.com/menpo/conda-metis on desktop,
open command prompt, go to conda-metis-master, modify CMakeLists.txt and execute .\vsgen, modify \GKlib\gk_arch.h,
use Developer command line for VisualStudio, go to path_to_your_metis_dir\build\windows\ and execute msbuild METIS.sln,
, go to command prompt and set...

- set METIS_DLL=C:\Users\your_username\Desktop\conda-metis-master\build\windows\libmetis\Release\metis.dll
altenatively setx METIS_DLL C:\Users\your_username\Desktop\conda-metis-master\build\windows\libmetis\Release\metis.dll

https://stackoverflow.com/questions/54458470/install-metis-library-for-python3-on-windows7?noredirect=1&lq=1
https://stackoverflow.com/questions/50675790/how-to-install-metis-package-in-python-on-windows

powershell -command "& { iwr https://github.com/guglielmosanchini/conda-metis/archive/master.zip -OutFile conda-metis-master.zip }"
powershell -nologo -noprofile -command "& { Add-Type -A 'System.IO.Compression.FileSystem'; [IO.Compression.ZipFile]::ExtractToDirectory('conda-metis-master.zip', '.'); }"
.\vsgen
"C:\ProgramFiles(x86)\Microsoft Visual Studio\2019\BuildTools\MSBuild\Current\Bin\MSbuild.exe" conda-metis-master\build\windows\METIS.sln
setx METIS_DLL C:\Users\your_username\Desktop\conda-metis-master\build\windows\libmetis\Release\metis.dll


"C:\Program Files (x86)\Microsoft Visual Studio\2017\BuildTools\Common7\Tools\VsDevCmd"
C:\Program Files (x86)\Microsoft Visual Studio\2017\BuildTools\MSBuild\Current\Bin\MSbuild.exe
set VCTargetsPath=C:\Program Files (x86)\Microsoft Visual Studio\2019\Professional\MSBuild\Microsoft\VC\v160
