# GLFW

[![Build status](https://github.com/glfw/glfw/actions/workflows/build.yml/badge.svg)](https://github.com/glfw/glfw/actions)
[![Build status](https://ci.appveyor.com/api/projects/status/0kf0ct9831i5l6sp/branch/master?svg=true)](https://ci.appveyor.com/project/elmindreda/glfw)
[![Coverity Scan](https://scan.coverity.com/projects/4884/badge.svg)](https://scan.coverity.com/projects/glfw-glfw)

## Introduction

GLFW is an Open Source, multi-platform library for OpenGL, OpenGL ES and Vulkan
application development.  It provides a simple, platform-independent API for
creating windows, contexts and surfaces, reading input, handling events, etc.

GLFW natively supports Windows, macOS and Linux and other Unix-like systems.  On
Linux both X11 and Wayland are supported.

GLFW is licensed under the [zlib/libpng
license](https://www.glfw.org/license.html).

You can [download](https://www.glfw.org/download.html) the latest stable release
as source or Windows binaries, or fetch the `latest` branch from GitHub.  Each
release starting with 3.0 also has a corresponding [annotated
tag](https://github.com/glfw/glfw/releases) with source and binary archives.

The [documentation](https://www.glfw.org/docs/latest/) is available online and is
included in all source and binary archives.  See the [release
notes](https://www.glfw.org/docs/latest/news.html) for new features, caveats and
deprecations in the latest release.  For more details see the [version
history](https://www.glfw.org/changelog.html).

The `master` branch is the stable integration branch and _should_ always compile
and run on all supported platforms, although details of newly added features may
change until they have been included in a release.  New features and many bug
fixes live in [other branches](https://github.com/glfw/glfw/branches/all) until
they are stable enough to merge.

If you are new to GLFW, you may find the
[tutorial](https://www.glfw.org/docs/latest/quick.html) for GLFW 3 useful.  If
you have used GLFW 2 in the past, there is a [transition
guide](https://www.glfw.org/docs/latest/moving.html) for moving to the GLFW
3 API.

GLFW exists because of the contributions of [many people](CONTRIBUTORS.md)
around the world, whether by reporting bugs, providing community support, adding
features, reviewing or testing code, debugging, proofreading docs, suggesting
features or fixing bugs.


## Compiling GLFW

GLFW itself requires only the headers and libraries for your OS and window
system.  It does not need the headers for any context creation API (WGL, GLX,
EGL, NSGL, OSMesa) or rendering API (OpenGL, OpenGL ES, Vulkan) to enable
support for them.

GLFW supports compilation on Windows with Visual C++ 2010 and later, MinGW and
MinGW-w64, on macOS with Clang and on Linux and other Unix-like systems with GCC
and Clang.  It will likely compile in other environments as well, but this is
not regularly tested.

There are [pre-compiled Windows binaries](https://www.glfw.org/download.html)
available for all supported compilers.

See the [compilation guide](https://www.glfw.org/docs/latest/compile.html) for
more information about how to compile GLFW yourself.


## Using GLFW

See the [documentation](https://www.glfw.org/docs/latest/) for tutorials, guides
and the API reference.


## Contributing to GLFW

See the [contribution
guide](https://github.com/glfw/glfw/blob/master/docs/CONTRIBUTING.md) for
more information.


## System requirements

GLFW supports Windows XP and later and macOS 10.8 and later.  Linux and other
Unix-like systems running the X Window System are supported even without
a desktop environment or modern extensions, although some features require
a running window or clipboard manager.  The OSMesa backend requires Mesa 6.3.

See the [compatibility guide](https://www.glfw.org/docs/latest/compat.html)
in the documentation for more information.


## Dependencies

GLFW itself needs only CMake 3.1 or later and the headers and libraries for your
OS and window system.


## Changelog

**New**
 - Bugfix: MacOS Applications not correctly handeling _glfwInputError(GLFW_FEATURE_UNAVAILABLE, "Cocoa: Regular windows do not have icons on macOS");
    MacOS should never implement or give paremeter to include window icons in the first place, very poor choice on the master repo. 

 **Previous**
 - Added `GLFW_PLATFORM` init hint for runtime platform selection (#1958)
 - Added `GLFW_ANY_PLATFORM`, `GLFW_PLATFORM_WIN32`, `GLFW_PLATFORM_COCOA`,
   `GLFW_PLATFORM_WAYLAND`, `GLFW_PLATFORM_X11` and `GLFW_PLATFORM_NULL` symbols to
   specify the desired platform (#1958)
 - Added `glfwGetPlatform` function to query what platform was selected (#1655,#1958)
 - Added `glfwPlatformSupported` function to query if a platform is supported
   (#1655,#1958)
 - Added `glfwInitAllocator` for setting a custom memory allocator (#544,#1628,#1947)
 - Added `GLFWallocator` struct and `GLFWallocatefun`, `GLFWreallocatefun` and
   `GLFWdeallocatefun` types (#544,#1628,#1947)
 - Added `glfwInitVulkanLoader` for using a non-default Vulkan loader (#1374,#1890)
 - Added `GLFW_RESIZE_NWSE_CURSOR`, `GLFW_RESIZE_NESW_CURSOR`,
   `GLFW_RESIZE_ALL_CURSOR` and `GLFW_NOT_ALLOWED_CURSOR` cursor shapes (#427)
 - Added `GLFW_RESIZE_EW_CURSOR` alias for `GLFW_HRESIZE_CURSOR` (#427)
 - Added `GLFW_RESIZE_NS_CURSOR` alias for `GLFW_VRESIZE_CURSOR` (#427)
 - Added `GLFW_POINTING_HAND_CURSOR` alias for `GLFW_HAND_CURSOR` (#427)
 - Added `GLFW_MOUSE_PASSTHROUGH` window hint for letting mouse input pass
   through the window (#1236,#1568)
 - Added `GLFW_CURSOR_CAPTURED` cursor mode to confine the cursor to the window
   content area (#58)
 - Added `GLFW_POSITION_X` and `GLFW_POSITION_Y` window hints for initial position
   (#1603,#1747)
 - Added `GLFW_ANY_POSITION` hint value for letting the window manager choose (#1603,#1747)
 - Added `GLFW_PLATFORM_UNAVAILABLE` error for platform detection failures (#1958)
 - Added `GLFW_FEATURE_UNAVAILABLE` error for platform limitations (#1692)
 - Added `GLFW_FEATURE_UNIMPLEMENTED` error for incomplete backends (#1692)
 - Added `GLFW_WAYLAND_APP_ID` window hint string for Wayland app\_id selection
   (#2121,#2122)
 - Added `GLFW_ANGLE_PLATFORM_TYPE` init hint and `GLFW_ANGLE_PLATFORM_TYPE_*`
   values to select ANGLE backend (#1380)
 - Added `GLFW_X11_XCB_VULKAN_SURFACE` init hint for selecting X11 Vulkan
   surface extension (#1793)
 - Added `GLFW_NATIVE_INCLUDE_NONE` for disabling inclusion of native headers (#1348)
 - Added `GLFW_BUILD_WIN32` CMake option for enabling Win32 support (#1958)
 - Added `GLFW_BUILD_COCOA` CMake option for enabling Cocoa support (#1958)
 - Added `GLFW_BUILD_X11` CMake option for enabling X11 support (#1958)
 - Added `GLFW_LIBRARY_TYPE` CMake variable for overriding the library type
   (#279,#1307,#1497,#1574,#1928)
 - Added `GLFW_PKG_CONFIG_REQUIRES_PRIVATE` and `GLFW_PKG_CONFIG_LIBS_PRIVATE` CMake
   variables exposing pkg-config dependencies (#1307)
 - Made joystick subsystem initialize at first use (#1284,#1646)
 - Made `GLFW_DOUBLEBUFFER` a read-only window attribute
 - Updated the minimum required CMake version to 3.1
 - Updated gamepad mappings from upstream
 - Disabled tests and examples by default when built as a CMake subdirectory
 - Renamed `GLFW_USE_WAYLAND` CMake option to `GLFW_BUILD_WAYLAND` (#1958)
 - Removed `GLFW_USE_OSMESA` CMake option enabling the Null platform (#1958)
 - Removed CMake generated configuration header
 - Bugfix: The CMake config-file package used an absolute path and was not
   relocatable (#1470)
 - Bugfix: Video modes with a duplicate screen area were discarded (#1555,#1556)
 - Bugfix: Compiling with -Wextra-semi caused warnings (#1440)
 - Bugfix: Built-in mappings failed because some OEMs re-used VID/PID (#1583)
 - Bugfix: Some extension loader headers did not prevent default OpenGL header
   inclusion (#1695)
 - Bugfix: Buffers were swapped at creation on single-buffered windows (#1873)
 - Bugfix: Gamepad mapping updates could spam `GLFW_INVALID_VALUE` due to
   incompatible controllers sharing hardware ID (#1763)
 - Bugfix: Native access functions for context handles did not check that the API matched
 - Bugfix: `glfwMakeContextCurrent` would access TLS slot before initialization
 - Bugfix: `glfwSetGammaRamp` could emit `GLFW_INVALID_VALUE` before initialization
 - Bugfix: `glfwGetJoystickUserPointer` returned `NULL` during disconnection (#2092)


## Cocoa Updates

 **New**
 - [Cocoa] Manually removed MacOS (Cocoa) window icon dependancy and calls (#1838)

 **Previous**
 - [Cocoa] Added support for `VK_EXT_metal_surface` (#1619)
 - [Cocoa] Added locating the Vulkan loader at runtime in an application bundle
 - [Cocoa] Moved main menu creation to GLFW initialization time (#1649)
 - [Cocoa] Changed `EGLNativeWindowType` from `NSView` to `CALayer` (#1169)
 - [Cocoa] Changed F13 key to report Print Screen for cross-platform consistency
   (#1786)
 - [Cocoa] Disabled macOS fullscreen when `GLFW_RESIZABLE` is false
 - [Cocoa] Removed dependency on the CoreVideo framework
 - [Cocoa] Bugfix: `glfwSetWindowSize` used a bottom-left anchor point (#1553)
 - [Cocoa] Bugfix: Window remained on screen after destruction until event poll
   (#1412)
 - [Cocoa] Bugfix: Event processing before window creation would assert (#1543)
 - [Cocoa] Bugfix: Undecorated windows could not be iconified on recent macOS
 - [Cocoa] Bugfix: Touching event queue from secondary thread before main thread
   would abort (#1649)
 - [Cocoa] Bugfix: Non-BMP Unicode codepoint input was reported as UTF-16
   (#1635)
 - [Cocoa] Bugfix: Failing to retrieve the refresh rate of built-in displays
   could leak memory
 - [Cocoa] Bugfix: Objective-C files were compiled as C with CMake 3.19 (#1787)
 - [Cocoa] Bugfix: Duplicate video modes were not filtered out (#1830)
 - [Cocoa] Bugfix: Menu bar was not clickable on macOS 10.15+ until it lost and
   regained focus (#1648,#1802)
 - [Cocoa] Bugfix: Monitor name query could segfault on macOS 11 (#1809,#1833)
 - [Cocoa] Bugfix: The install name of the installed dylib was relative (#1504)
 - [Cocoa] Bugfix: The MoltenVK layer contents scale was updated only after
   related events were emitted
 - [Cocoa] Bugfix: Moving the cursor programmatically would freeze it for
   a fraction of a second (#1962)
 - [Cocoa] Bugfix: `kIOMasterPortDefault` was deprecated in macOS 12.0 (#1980)
 - [Cocoa] Bugfix: `kUTTypeURL` was deprecated in macOS 12.0 (#2003)
 - [Cocoa] Bugfix: A connected Apple AirPlay would emit a useless error (#1791)
 - [Cocoa] Bugfix: The EGL and OSMesa libraries were not unloaded on termination
 - [Cocoa] Bugfix: `GLFW_MAXIMIZED` was always true when `GLFW_RESIZABLE` was false
 - [Cocoa] Bugfix: Changing `GLFW_DECORATED` in macOS fullscreen would abort
   application (#1886)
 - [Cocoa] Bugfix: Setting a monitor from macOS fullscreen would abort
   application (#2110)
 - [Cocoa] Bugfix: The Vulkan loader was not loaded from the `Frameworks` bundle
   subdirectory (#2113,#2120)


## Contact

On [glfw.org](https://www.glfw.org/) you can find the latest version of GLFW, as
well as news, documentation and other information about the project.

If you have questions related to the use of GLFW, we have a
[forum](https://discourse.glfw.org/), and the `#glfw` IRC channel on
[Libera.Chat](https://libera.chat/).

If you have a bug to report, a patch to submit or a feature you'd like to
request, please file it in the
[issue tracker](https://github.com/glfw/glfw/issues) on GitHub.

