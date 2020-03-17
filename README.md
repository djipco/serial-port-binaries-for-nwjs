### Precompiled NW.js-compatible binaries for Node's serialport module
------------

Important note: there is now a new way to use the serial port inside NW.js projects. Check out: [chrome-apps-serialport](https://github.com/djipco/chrome-apps-serialport)!

------------

Node.js' [serialport](https://www.npmjs.com/package/serialport) module uses native binaries to access the host's serial port. In most standard setups this is completely transparent to the user. However, if you want to use the *serialport* module within an NW.js application, you will need to manually recompile it. While recompiling the module is not impossible, it can be quite intimidating and time consuming your first time around.

So, instead of wasting time, you can simply download the precompiled binary that fits your environment. It basically goes like this. First, you install *serialport* as usual via `npm install serialport`. Then, you move the folder containing the appropriate binary inside the following folder:

`./node_modules/serialport/build/Release`

For example, if you are on Mac OS X (darwin) and want to use the module in version 0.12.3 of NW.js, your binary would be in this location:

`./node_modules/serialport/build/Release/node-webkit-v0.12.3-darwin-x64/serialport.node`

The name of the folder must match the exact version of NW.js you are using. Here is another example for Windows 7 (64bit) and NW.js version 0.13.0-beta4:

`./node_modules/serialport/build/Release/node-webkit-v0.13.0-beta4-win32-x64/serialport.node`

#### Submit

If you have binaries for other target platforms, I'd love to add them here. Please submit a pull 
request.

Here are my own personal compilation notes for the currently available targets:

##### Compilation Notes for Windows 7

* Installed Python 2.7.11
    * Checked option to add Python directory to path (during install)
    * Added `PYTHON` to system environment variables: `C:\Python27\python.exe`
* Installed [Visual Studio Express for Windows Desktop with Update 4](https://www.microsoft.com/en-us/download/details.aspx?id=44914) (6.5GB!!)
* Installed [Node.js 5.5.0](https://nodejs.org/dist/v5.5.0/node-v5.5.0-x64.msi)
* Installed mandatory Node modules (globally):
    * `npm install -g nw-gyp`
    * `npm install -g node-gyp`
    * `npm install -g node-pre-gyp`
* Change directory to `./node_modules/serialport`
* Compile with `node-pre-gyp rebuild --runtime=node-webkit --target=0.13.0-beta4`
* Go back to project directory

Notes: `node-pre-gyp` actually picks `nw-gyp` or `node-gyp` depending on the target. Both modules must be installed.


##### Compilation Notes for Mac OS X

The compiled binary for v0.13.0-beta4 makes NW.js crash. An issue has been filed: https://github.com/nwjs/nw.js/issues/4338


##### Useful articles

* https://github.com/nwjs/nw.js/wiki/build-native-modules-with-nw-gyp
* https://github.com/rwaldron/johnny-five/wiki/Getting-started-with-Johnny-Five-and-Node-Webkit
* https://github.com/nwjs/nw-gyp
