**note:** [Download our releases][release_download] | [History of our releases][release_history]

0.4.2 Akihabara (tag 1T???)
---------------------------

  - added `flash.display.Sprite` class  
    should allow to use MXMLC to compile  
    SWF depending on SWC and produce  
    bytecode compatible SWF for redtamarin

  - updated components, documentation  
    and AVMGLUE API to take into account  
    the `Sprite` class

  - added `apt-cyg` to our own repo  
    in `extras/cygwin`

  - changed `apt-cyg` download path to  
    https://raw.githubusercontent.com/corsaair/redtamarin/master/extras/cygwin/apt-cyg  
    fix [#72 problem with apt-cyg in redtamarin-setup.bat](https://github.com/Corsaair/redtamarin/issues/72)

  - added support for binfmt_misc  
    in `extras/linux`  
    see https://github.com/Corsaair/redtamarin/wiki/LinuxBinfmt_misc


0.4.1 Akihabara (tag 1T180)
---------------------------

  - added `patch` to versioning  
    `version.major=0`  
    `version.minor=4`  
    `version.patch=1`  
    `version.serie=1`  
    `version.cycle=T`  
    `version.build=180`  
      
    see [Redtamarin Version](https://github.com/Corsaair/redtamarin/wiki/RedtamarinVersion)

  - change in API  
    we changed the format of the description
    from: `redtamarin-0.4-beta[1T180]`  
    to: `redtamarin-0.4.1.1T180-beta`  
    example:  
    `Runtime.description = redtamarin-0.4.1.1T180-beta`  
    also  
    `Runtime.redtamarin = 0.4.1S131`  
    replaced by  
    `Runtime.version = 0.4.1.1T180`  
    but version is an `Object`  
    so you can also access  
    `Runtime.version.major = 0`  
    `Runtime.version.minor = 4`  
    `Runtime.version.patch = 1`  
    `Runtime.version.serie = 1`  
    `Runtime.version.cycle = T`  
    `Runtime.version.build = 180`  
      
    also  
    `Runtime.version = 2.1 cyclone`  
    replaced by  
    `Runtime.AVMversion = 2.1 cyclone`

  - added new properties  
    `Runtime.tag = 1T180`  
    `Runtime.codename = Akihabara`  
    `Runtime.label = beta`

  - `Runtime.redtamarin` is marked deprecated  
    and will be removed in 0.4.3

  - added `flash.system.Security` mock  
    for redtamarin SWC compatiblity

  - cleaned up comments in `shell.OperatingSystem`  
    see [Impl Of OperatingSystem](https://github.com/Corsaair/redtamarin/wiki/ImplOfOperatingSystem)

  - added complete OS detection in `shell.OperatingSystem`  
    mainly based on env vars, files and parsing

  - updated builds for Windows / Mac OS X / Linux  
    to be in sync with the wiki documentation  
    see [Developer Environment](https://github.com/Corsaair/redtamarin/wiki/DeveloperEnvironment)

  - added some options to the build  
    for Mac OS X, now we can select the Mac OS X SDK  
    and some updates in `configure.py` to supports all  
    SDK: `104u`, `105`, `106`, `107`, `108`, `109`, `1010` or `1011`  
    for Windows, the build autodetect the python exe  
    for Linux, some updates in `configure.py` to supports GCC 4.8.*  
    and `build.makejobs` which allow to setup the number  
    of make jobs to run silmutaneously (default to 3 for dual core)

  - fixed `shell.RunMode` documentation

  - added `shell.ShellType`  
    `ShellType.RUNTIME` for when executed by redshell  
    `ShellType.PROJECTOR` for when executed by a projector  
    `ShellType.SCRIPT` for when executed as a shell script

  - new property in Program  
    `Program.type = ShellType.RUNTIME;`

  - implemented issue #14  
    [need to support projectors arguments](https://github.com/Corsaair/redtamarin/issues/14)

  - added extras  
    in `extras/windows/`  
    `redtamarin-setup.bat`  
    the Redtamarin Windows Environment Setup  
    batch file for end-users who want to sue redtamarin  
    in `extras/cygwin`  
    `redtamarin-dev-setup.bat`  
    same as above bur for developers who want to compile under Windows  
    also updated `readme.txt` with usage/documentation/tutorial/etc.

  - add build/build32and64
    bash script helper to build both 32-bit and 64-bit binaries under Windows

  - added `shell.Cygwin` helper class  
    it can detect if Cygwin is installed, the install dir  
    and allow to call bash even from cmd.exe or other non-bash  
    environment like running as CGI

  - fixed `C.stdlib.exec()` asdoc

  - fixed `C` package  
    implementation of `argc`, `argv` and `environ` have changed  
    and now the doc is showing in asdoc  
    note: we need to sync changes with as3shebang  
    **DON'T DO THAT**  
    see https://github.com/Corsaair/redtamarin/issues/58

  - duplicated asdoc for `src/as3/C/globals.as`  
    see: https://github.com/Corsaair/redtamarin/wiki/specific-asdoc-for-Redtamarin

  - updated Redtamarin asdoc main page  
    logo, link to wiki doc etc.  
    and basic descriptions

  - removed `Program.findShell`  
    replaced by internal static function `_findShell`  
    we do not want the user or have no need to override this anymore  
    also removed `Program.setShell`  
    updated `boot.as` to reflect the changes

  - updated `Program.filename`  
    not a constant anymore  
    because we want to be able to override it  
    from a shell scripts

  - fixed `shell.Domain` asdoc

  - fixed `shell.Environment` asdoc

  - updated `shell.Environment`  
    was bit broken, use `Program.environ` now

  - fully implemented `shell.Environment` features

  - added a new property `Program.environment`  
    which returns a synchronised Environment instance

  - edited a lot of asdoc

  - added `set_binary_mode()` in `C.conio`

  - rewrite some asdoc  
    set some rules for special cases  
    now we use asdoc stubs for cases where  
    asdoc can not generate the HTML doc  
    files ending in `_asdoc.as`

  - re-implemented `HardwareInformation` memory usage

  - fixed `FileSystem.isHidden()` for Windows

  - added `mkdirp()` in `C.sys.stat` from betalib

  - added `which()` in `C.unistd` from betalib

  - added `fcopy()` in `C.stdio` from betalib

  - added bash scripts to build deb packages  
    `make_deb_mac32`  
    `make_deb_mac64`  
    `make_deb_nix32`  
    `make_deb_nix64`  
    `make_deb_win32`  
    `make_deb_win64`  
    note:  
    we build all our packages from Linux  
    except for the windows one who needs  
    to be build from WIndows with wpkg


0.4.0 Akihabara (from tag 1T174)
--------------------------------

  - release redtamarin SDK as zip files


0.4.0 Akihabara (from tag 1T000)
--------------------------------

  - now we include `ErrorConstant.as`  
    to be able to throw native errors from AS3

  - lots of update to clean up documentation with asdoc

  - added `VMPI_GetEnviron`

  - implemented `FileSystem` class AS3 and native

  - started to implement `flash.filesystem` and `flash.net` package  
    not finished

  - added undocumented class `flash.system.SecurityPrivilege`

  - implemented `C.sys.socket`

  - implemented `C.sys.select`

  - implemented `C.arpa.inet`

  - updated `C.netdb`, and others socket related API

  - sockets and select are working for OS X

  - sockets and select are working for Linux

  - updated Windows native API so now socket and file descriptor  
    can be inerchangeable which then allow to use `close()` on sockets

  - updated Windows API so socket functions automatically initialize winsock

  - updated `exit()` function to automatically cleanup winsock  
    note: even without explictly calling `exit()` winsock will be cleaned up  
    at condition the exit is normal, for abnormal exit winsock will be untouched

  - sockets and select are working for Windows


0.4.0 Akihabara (from tag 1S540)
--------------------------------

  - added `C.dirent` basic `closedir`, `opendir`, `readdir`

  - added more dirent: `dirfd`, `fdopendir`, `rewinddir`, `seekdir`, `telldir`

  - added in `C.fcntl`: `creat` and `open`

  - MAC OS X does not have `fdopendir` so we implmented it

  - added non-standard function `getdirentries()` impl. in AS3

  - refactor on `fcntl`, now asdoc indicate when options are compatible
    for POSIX(mac/linux), WIN (Windows only, MAC (Macintosh only), and NIX (Linux only)

  - in `fcntl`, added `openat()` and `fcntl()` for POSIX (mac/linux)

  - in asdoc added WIN, MAC, NIX and POSIX as "Runtime Versions" target  
    how to use:  
    `@langversion 3.0`  
    `@playerversion AVM 0.4`  
    `@playerversion POSIX +`

  - oh and from now on we doublecheck our POSIX compatibility with gnulib  
    we can not compile with gnulib but at least we can correct few things  
    this and there

  - changed source and sdk path to use "macintosh" and not "darwin" or "osx"

  - added new folder "extras"

  - added extra for DocBlockr package used with Sublime Text

  - reimplemented fully `errno.h`,  
    now we support all constants for all OS

  - fully implemented `limits.h`,  
    with support/compat for all OS

  - added the option to generate fat swc for `redtamarin.swc`

  - update includes and sync for Linux

  - fixed windows build

  - update includes and sync for windows

  - compile under Windows but some implementations are missing  
    eg. some POSIX function will return `-1` and set `errno = ENOSYS`

  - fixed redtamarin description for Windows  
    cygwin will not accept `'--enable-desc=redtamarin-0.0-unknown[0A000]'`  
    and display "AVMPLUS_DESC is not supported on windows via cygwin make.  Ignoring description."
    so we also generate an include on the fly 'src/as3/shell/description.incl'  
    fixed: `Runtime.description`, `Runtime.redtamarin`

  - Windows fix: `stat`, now we have correct file size, date stamp etc.

  - Windows fix: the basic event loop (alpha quality) is working,  
    yep Windows can `goAsync()` too

  - Windows implement: `HardwareInformation.memory`,  
    `HardwareInformation.memoryUsage`, `HardwareInformation.memoryPeakUsage`

  - Windows implement for `C.sys.stat`:  
    `chmod()`, `mkdir()`, `stat()` now supports UTF-8

  - Windows implement for `C.stdlib`:  
    `getenv()`, `putenv()`, `setenv()`, `unsetenv()`,  
    `realpath()`, `system()` now supports UTF-8

  - Windows implement: `Program.environ` now supports UTF-8

  - Windows implement for `C.stdio`:  
    `perror()`, `popen()`, `remove()`, `rename() now supports UTF-8

  - Windows implement for `C.unistd`:  
    `access()`, `chdir()`, `getcwd()`, `getlogin()`, `rmdir()`, `unlink()` now supports UTF-8  
    note: not `gethostname()` because `GetHostNameW` is min supported by WIN8+

  - Windows implement for `C.string`:  
    `strchr()`, `strdup()`, `strerror()`, `strlen()`, `strncpy()`, etc. now supports UTF-8

  - Windows note: `execv()`, `execve()`, `execvp()` do not now supports UTF-8 yet

  - stabilize macintosh build, some fixes and bolts

  - removed FileIO class

  - added/implemented `FileSystem` class


0.4.0 Akihabara (from tag 1R000)
--------------------------------

  - BRAND NEW REFACTOR NO BACKWARD COMPATIBILITY

  - updated to latest tamarin-redux tips `5571cf86fc68`

  - reorganized directory structure

  - patched `configure.py` to support OSX 10.8 SDK

  - new ant build

  - integrate good asc.jar (not in repo)

  - integrate asc2.jar from FlasCC 1.0 (not in repo)

  - reuse $AVMSHELL_EXE (ant var) in $AVM and $AVMSHELL_TOOL (env vars)  
    which can be either avmshell-release, avmshell-debug, avmshell-debug-debugger

  - cleanup `shell_toplevel.as`  
    removed all extraneous tests, ns, metadata  
    removed all avmplus package (AbstractBase, NativeBase, CheckBase, etc.)  
    removed all test library code for API versioning

  - cleanup `SystemClass.h` and `SystemClass.cpp` to be in sync with as3 class

  - cleanup `ShellCore.cpp`, removed `VMCFG_VERIFYALL` and `config.verifyonly` check  
    for `NativeBaseClass`, `ShellCoreFriend1Class`, `ShellCoreFriend2Class`, etc.

  - moved `flash.errors.*` classes to `flash_errors_classes.as` and updated builtin scripts

  - now we integrate avmglue in `shell_toplevel.py`  
    tested with `flash.errors.*` package

  - `manifest.mk` now have VMPI extensions (eg. all the *2.h files)

  - `manifest.mk` now includes api/clib and api/shell

  - updated `VMPI_getOperatingSystemVersionNumbers(int*, int*, int*)`  
    under OSX 10.8 ‘Gestalt’ is deprecated and there is no replacement  
    for now we return `0.0.0`  
    need to do a new implementation later

  - reimplemented clib  
    errno.as/CErrnoClass.h/CErrnoClass.cpp  
      removed get/set errno  
      replaced by an ErrorNumber class and an errno const  
    stdlib.as/StdlibClass.h/StdlibClass.cpp  
      updated StdlibClass::exit to support workers  
    unistd.as/UnistdClass.h/UnistdClass.cpp  
      updated UnistdClass::sleep to reuse vmthread

  - moved all avmplus/shell/avmglue AS3 classes in the `/src/as3/` directory

  - updated `exactgc.py` with the correct paths  
    before:  
    `gen(prefix = 'avmshell', inputfiles = 'shell_toplevel.as DebugCLI.h ShellCore.h SystemClass.h', outputdir = outdir, srcdir = shelldir, ns = 'avmshell')`  
    `gen(prefix = 'extensions', inputfiles = 'DomainClass.h Domain.as ../extensions/*.h ../extensions/*.as', outputdir = outdir, srcdir = shelldir, ns = 'avmplus')`  
    after:  
    `gen(prefix = 'avmshell', inputfiles = '../as3/avmplus/System.as DebugCLI.h ShellCore.h SystemClass.h', outputdir = outdir, srcdir = shelldir, ns = 'avmshell')`  
    `gen(prefix = 'extensions', inputfiles = 'DomainClass.h ../as3/avmplus/Domain.as ../extensions/*.h ../extensions/*.as', outputdir = outdir, srcdir = shelldir, ns = 'avmplus')`

  - for API versioning ALWAYS include `/src/core/api-versions.as`  
    when generating documentation from asdoc  
    but in `builtin.py` never include `/src/core/api-versions.as`  
    as we include it by default

  - added public method `getShellClasses()` to `ShellCore`  
    to easily get the shell_toplevel ClassManifest

  - clean redtamarin logo for asdoc

  - now build a `redtamarin.abc`  
    (that merge `builtin.abc` and `shell_toplevel.abc`)  
    see src/ for `redtamarin.py`

  - both components `redtamarin.swc` and `redtamarin.abc` reuse the same  
    `redtamarin.as` file from src/

  - `shell_toplevel.py` use the same `redtamarin.as` than `redtamarin.py`

  - forced to update the way we deal with versioning  
    only builtins can use `CONFIG::AIR_1_0` etc.  
    when you are defining avmglue API you need to use `AVMGLUE::AIR_1_0`  
    also when you compile `shell_toplevel.py` and `redtamarin.py`  
    you will need to define `'-config AVMGLUE::REDTAMARIN=true'`  
    to create the namespace

  - documented zavm2.intrinsics.memoryz and integrated in asdoc  
    if it keeps going like that our doc will be better than Adobe

  - and tons more stuff


0.3.2 (no codename)
-------------------

  - in toplevel modified the `getClassByName()` signature to  
    `public function getClassByName( name:String, domain:Domain = null ):Class`

  - moved most of `flash.utils.*` from avmglue into `toplevel.abc`

  - removed `System.profile` initialization in anonymous package

  - `System.profile` is lazy inited now

  - `System.OperatingSystem`, now `_parseLinuxReleaseFile` has a try/catch  
    fix issue 44 and 46

  - added `pathSeparator` in `FileSystem`

  - now the `Domain` class use `avmplus.FileSystem`  
    fix issue 38

  - added `getErrno()`/`setErrno()` functions in `C.errno.*`

  - added getter/setter `receiveTimeout` in `avmplus.Socket`  
    see issue 47

  - added getter/setter `sendTimeout` in `avmplus.Socket`  
    see issue 47

  - added property `readableTimeout` in `avmplus.Socket`  
    see issue 47

  - added property `writableTimeout` in `avmplus.Socket`  
    see issue 47

  - added `blocking` getter/setter in `avmplus.Socket`

  - added constants to `C.errno`  
    `EWOULDBLOCK`, `EINPROGRESS`, `EALREADY`, `EDESTADDRREQ`, `EMSGSIZE`, `EPROTOTYPE`,  
    `ENOPROTOOPT`, `EADDRINUSE`, `EADDRNOTAVAIL`, `ELOOP`, `EHOSTDOWN`, `EHOSTUNREACH`

  - now we send the correct socket error message under WIN32

  - added static version property in `Socket`  
    under WIN32 returns "Winsock 2.2" or "Winsock 2.1", etc.  
    under OSX/Linux returns "Berkeley sockets"

  - added a static `isSupported()` method in `Socket`  
    return `false` in very special cases  
    (eg. a very old version of Windows who could not  
    initialize winsock for ex)

  - added static method `getErrorMessage()` to `Socket`  
    to returns the correct message string from a socket error

  - now use a pre-compiled `asc.jar` for the time being  
    later when we will be able to sync with tamarin-redux  
    then we should be able to build ASC from sources again

  - added the interface `StandardStream` in `avmplus`

  - added the `hack_sys` namespace

  - added `stderrWrite( bytes:ByteArray ):void` in `System`

  - moved `getStdinLength()`, `stdinRead()`, `stdinReadAll()`, `stdoutWrite()`, `stderrWrite()`  
    under the namespace `hack_sys`

  - added implementation of `StandardStreamOut`, `StandardStreamErr` and `StandardStreamIn`

  - added `stdout`, `stderr`, `stdin` properties in `avmplus.System`

  - added `NONBLOCKING_ENABLE`, `NONBLOCKING_DISABLE` in `C.stdio`

  - added `O_TEXT`, `O_BINARY` in `C.stdio`

  - added `kbhit()` in `C.stdio` to know when keyboard hit

  - added `con_stream_mode()` in `C.stdio` to change console to non-blocking or blocking mode

  - added `con_trans_mode()` in `C.stdio `to change console to binary or text mode

  - updated `getRedtamarinVersion()` in `avmplus.System` to "0.3.2"


0.3.1 (no codename)
-------------------

  - added build for OS X 10.5 Leopard

  - added build for components: `builtin.swc`, `clib.swc` and `redtamarin.swc`

  - removed `debugger()` from `avmplus.*` package

  - removed `Capabilities` class from `flash.system.*` package (will be re-added in avmglue)

  - removed `getTimer()` from toplevel (will be re-added in avmglue)

  - fixed `System.exec()` - issue 30  
    was not declared as static

  - added `avmplus.profiles.*` with `Profile`, `TamarinProfile`, `RedTamarinProfile`, etc.

  - added `System.profile`

  - fixed `FileSystem.exists` - issue 28  
    no we use `access( filename, F_OK ) == 0`  
    instead of a native impl.

  - fixed small memory leak in sockets - issue 29  
    every 'new' need a 'delete' even on the heap

  - avmglue v1 is available on its own repo

  - added `System.eval()`


0.3.0 (Infectious Grooves)
--------------------------

- created `C.socket` AS3 for C socket const   
  (POSIX only, eg. AF_INET, SOCK_STREAM, etc.)

- added `error` const for sockets in `C.errno.*` AS3   
  (POSIX only eg. ENOTCONN, ECONNREFUSED etc.)

- created `CSocketClass`

- created `Socket`, `PosixSocket`

- added socket methods to `Platform`, `PosixPartialPlatform`

- created `SocketClass` and `avmplus.Socket` AS3

- documentation

- port to WIN32 impl of `WinSocket`  
  `SOCKET` are casted as `int`  
  small changes

- added `gethostbyaddr()` and `gethostbyname()`

- forced to use a `VMPI_gethostbyaddr()` for some small  
  difference between POSIX and WIN32

- sync with tamarin-redux tip `d8b78be5b40f` (22/12/2010)

- better integration of redtamarin features  
  `/VMPI/VMPI.h`  -> original Tamarin  
  `/VMPI/VMPI2.h` -> redtamarin extensions  
  `/platform/mac/mac-platform.h`  -> original Tamarin  
  `/platform/mac/mac-platform2.h `-> redtamarin extensions  
  `/VMPI/PosixPortUtils.cpp`  -> original Tamarin  
  `/VMPI/PosixPortUtils2.cpp` -> redtamarin extensions  
  etc.

- added `chdir()` and `unlink()`

- re-integrated all of clib, tested only on OSX

- changed some logic in `ShellCore` and `avmshell`  
  now when you embed your abc in a projector  
  you don't need to use -- before passing your arguments

- System API now have a `programFilename` getter that returns `argv[0]`  
  `System.executablePath` and `VMPI_getExecutablePath` removed

- re-integrated all of clib for WIN32 and tested

- fixed VMPI_realpath for WIN32

- re-integrated all of clib for UNIX and tested

- re-integrated all `OperatingSystem`

- re-integrated all `FileSystem`

- changed and moved System, now it's more redtamarin centric  
  eg. we add what we need for our API

- a lot of work on `FileSystem` added: `currentDirectory`, `parentDirectory`,  
  `extensionSeparator`, `drives`, `lineEnding`, `separators`, `getFileSize()`,  
  `getLastModifiedTime()`, `getBasenameFromPath()`, `getDirectoryFromPath()`,  
  `getExtension()`, `hasDriveLetter()`, `isEmptyDirectory()`, `isSeparator()`,  
  `isNotDotOrDotdot()`, `listFilesWithFilter()`, `listFilesWithRegexp()`,  
  `remove()`, `removeFile()`, `removeDirectory()`, `stripTrailingSeparators()`

- added beta features to read/write binary to stdin/stdout  
  `stdinLength`, `isStdinEmpty()`, `stdinRead()`, `stdinReadAll()`, `stdoutWrite()`

- added more functions to `FileSystem`: `isAbsolutePath()`, `absolutePath()`,  
  `containsPath()`, `copyFile()`, `copyFiles()`, `createDirectory()`,  
  `endsWithSeparator()`, `ensureEndsWithSeparator()`, `normalizePath()`, etc.

- added system locale detection  
  `OperatingSystem.language`, `OperatingSystem.country`,  
  `OperatingSystem.locale`, `OperatingSystem.codePage`

- added `C.unistd` `getpid()` and `System.pid`

- added `FileSystem.homeDirectory` and `FileSystem.rootDirectory`

- added `System.shell` and `System.popen()`

- added `Socket.localAddresses`

- added `getpeername()`, `getsockname()` in `C.socket.*`

- added socket instance `local` and `peer` property  
  to get the "address:port" on connected sockets

- refactored `receiveFrom` and `sendTo` with real implementation of `recvfrom()` and `sento()`

- refactored `Socket`, now everything use `ByteArray` on the C++ side  
  methods using `String` on the AS3 side use `readUTFBytes()`

- `Socket.bind()` can define the interface where to bind  
  (before was hard coded "127.0.0.1")

- now receive functions can define a custom buffer  
  `receive()` default buffer is `1024`  
  `receiveFrom()` default buffer is `512`

- added utility methods `receiveAll()` etc.

- the AS3 Socket class is now dynamic  
  and have callback functions for all methods  
  eg. `connect()` -> `onConnect()`, `bind()` -> `onBind()`  
  those callbacks can be overrided by the user  
  eg. `mysock.onBind = function() { //do whatever }`

- added readable/writable properties to `Socket`  
  they reuse a non-blocking `select()` in the background

- added `Socket.maxConnectionQueue` and `Socket.maxConcurrentConnection`

- fixed a memory bug with Socket where the buffer was GC'ed and crashed (added a write barrier)

- fixed a bug with `send()` etc., needed to null terminate the `ByteArray` data

- "hacked" `FD_SETSIZE` to change the limit of concurrent connections to `4096` :p  
  `FD_SETSIZE` is limited to `1024` under OS X (maybe the same for Ubuntu?)  
  and limited to `64` under Windows

- removed `INADDR_ANY` and `INADDR_BROADCAST` in `C.socket.*`

- added `MSG_DONTWAIT` in `C.socket.*`

- added `SetNoSigPipe()` to `socket.h`  
  now by default we desactivate `SIGPIPE`

- fixed bugs in `receiveAll()` and `receiveBinaryAll()`


0.2.9 (no codename)
-------------------

  - added `VMPI_chmod`

  - updated `VMPI_getFileMode` for WIN32

  - added `dirent.h` implementation for WIN32

  - added `listFiles()` in `avmplus.FileSystem` AS3

  - added `VMPI_getOperatingSystem`, `VMPI_isNullTerminated`, `VMPI_int2char`

  - added `avmplus.OperatingSystem` AS3

  - added `VMPI_gethostname`, `VMPI_getUserName`

  - added `gethostname()` and `getlogin()` in `C.unistd.*` AS3

  - full Operating System informations (name, nodename, username, hostname, release, version, machine,  
    vendor, vendorName, vendorVersion, vendorDescription, codeName)

  - added `VMPI_sleep` POSIX

  - added `sleep()` in `C.unistd.*` AS3 (POSIX only)

  - added `VMPI_getDiskSpace`, `VMPI_getTotalDiskSpace`

  - added `getFreeDiskSpace()`, `getTotalDiskSpace()`, `getUsedDiskSpace()` in `avmplus.FileSystem` AS3


0.2.8 (no codename)
-------------------

  - added `VMPI_rmdir`, `VMPI_mkdir`, `VMPI_remove`, `VMPI_rename`

  - added `C.stdio` in AS3 and `StdioClass` in C/C++

  - added `VMPI_realpath` POSIX use `realpath()`, WIN32 use `GetFullPathNameA()`

  - added `rmdir()`, `mkdir()` in `C.unistd.*`

  - added `remove()`, `rename()` in `C.stdio.*`

  - added `realpath()` in `C.stdlib.*`

  - added `S_IFMT`, `S_IFIFO`, ... `S_RWXU`, `S_IRUSR`, etc. to `C.unistd.*`

  - added `VMPI_getFileMode`, `VMPI_isRegularFile`, `VMPI_isDirectory` (POSIX)

  - added `getFileMode()`, `isRegularFile()`, `isDirectory()` in `avmplus.FileSystem` AS3

  - added `strmode()` in `C.string.*` AS3


0.2.7 (no codename)
-------------------

  - added `VMPI_access`, `VMPI_getcwd`, `VMPI_setenv`, `VMPI_unsetenv`

  - added `C.string`, `C.errno` in AS3 and `CStringClass`, `CerrnoClass` in C/C++

  - all tested under OS X 10.6 / Windows XP SP2 / Ubuntu 8.04


0.2.6 (no codename)
-------------------

  - reorganized everything

  - tamarin-redux is sync'ed on redshell repo

  - our `/tamarin-redux` is updated from a redshell hg archive

  - now we use gclient on top of svn

  - `/trunk` contains only redtamarin changes  
    mainly: extensions, platform, shell, VMPI

  - added `VMPI_getExecutablePath` to replace `argv[0]`

  - added `System.executablePath` in `avmplus.*` AS3


0.2.5 (no codename)
-------------------

  - added `System.executablePath` to get `argv[0]`

  - added locale/language/languages support  
    user can override the default locale  
    with env vars `LC_ALL` and/or `LANG`

  - added full flash platform API mock



[release_download]: https://github.com/Corsaair/redtamarin/releases
[release_history]: https://github.com/Corsaair/redtamarin/wiki/RedtamarinReleases