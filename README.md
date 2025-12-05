# BluBrowser for [BLUI](https://github.com/getnamo/BLUI-unreal)

## What?
This is the CEF code of the child process for BLUI. It's a modified CefSimple example to include the `blu_event` function which notifies BLUI of Javascript events in the UE4 game engine.

See https://bitbucket.org/chromiumembedded/cef/wiki/Home for general information on CEF.

## How do I compile this? (Windows only right now)
* Get zip from [CEF Builds Site](https://cef-builds.spotifycdn.com/index.html)
* download CMake - https://cmake.org/download/
* Replace the code in CefSimple with the code in this repository, the original project has some configuration that needs to be kept for output to work correctly.
* Run `cmake .` in downloaded folder to generate .sln (may need to use `-DENABLE_DOXYGEN_DOT=OFF option` for cmake to succeed)
* It should compile out of the box for CEF 128 to make the `BluBrowserProcess`, but will need `/MT` on `libcef_dll_wrapper` to compile the static library for unreal before copying that portion.
  * (If you want to build the wrapper lib for use in unreal) Open the solution in Visual Studio and change the project options (C++ -> Code Generation -> Runtime Library) in "libcef\_dll\_wrapper" to output a "multi-threaded DLL", and build.
  * (If you want to build the blu_browser.exe process) Switch "libcef\_dll\_wrapper" to output "Multi-threaded (/MT)"
* Build the solution, and it will produce the proper dlls, lib files, or the child process exe.

## Related guide issues

https://github.com/getnamo/BLUI-Unreal/issues/29

https://github.com/getnamo/BLUI-Unreal/issues/60
