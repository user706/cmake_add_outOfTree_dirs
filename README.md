Install msys2 https://www.msys2.org/

After installation:
Open up MSYS2 MSYS shell (C:\msys64\msys2_shell.cmd)

```bash
# copy paste the following lines to get gcc
pacman -S --needed mingw-w64-x86_64-gcc   \
                   mingw-w64-i686-gcc     \
                   make                   \
				   cmake                  \
                   mingw-w64-x86_64-ninja \
                   mingw-w64-i686-ninja
				   
```

```bat
setx PATH "%PATH%;C:\msys64\mingw32\bin;C:\msys64\mingw64\bin"              &:: this is for needed mingw dlls

rem Check like this:
rundll32 sysdm.cpl,EditEnvironmentVariables
````


The open the project in Visual Studio 2017 with: File->Open->CMake

go to: **target_device\full_variant\CMakeLists.txt** (there you'll also find a CMakeSettings.json)

The the menu-item CMake often hangs in "Cancel Cache Generation".

Right-clicking CMakeLists.txt does not show "Build"...

Only on rare occasions... does it work.
