### Precompiled NW.js-compatible binaries for Node's serialport module
------------

Node.js' [serialport](https://www.npmjs.com/package/serialport) module uses native binaries to access the host's serial port. In most standard setups this is completely transparent to the user. However, if you want to use the *serialport* module within an NW.js application, you will need to manually recompile it. While recompiling the module is not impossible, it can be quite intimidating and time consuming your first time around.

So, instead of wasting time, you can simply download the precompiled binary that fits your environment. It basically goes like this. First, you install *serialport* as usual via `npm install serialport`. Then, you move the folder containing the appropriate binary inside the following folder:

`./node_modules/serialport/build/Release`

For example, if you are on Mac OS X (darwin) and want to use the module in version 0.12.3 of NW.js, your binary would be in this location:

`./node_modules/serialport/build/Release/node-webkit-v0.12.3-darwin-x64/serialport.node`

The name of the folder must match the exact version of NW.js you are using. Here is another example for Windows 7 (64bit) and NW.js version 0.13.0-beta4:

`./node_modules/serialport/build/Release/node-webkit-v0.13.0-beta4-win32-x64/serialport.node`

#### Submit

If you have binaries for other environments, please submit a pull request. Cheers!


#### Compilation Notes

##### Windows 7

* Installed Python 2.7.11
    * Checked option to add Python directory to path (during install)
    * Added `PYTHON` to system environment variables: `C:\Python27\python.exe`
* Installed Visual Studio Express for Windows Desktop with Update 4 (6.5GB!!)
* Installed Node.js 5.5.0
* Installed the following Node modules (globally):
    * `npm install -g nw-gyp`
    * `npm install -g node-gyp`
    * `npm install -g node-pre-gyp`
* Change directory to `./node_modules/serialport`
* Compile with `node-pre-gyp rebuild --runtime=node-webkit --target=0.13.0-beta4`
* Go back to project directory

Notes: node-pre-gyp actually picks nw-gyp or node-gyp depending on the target. Both modules must be 
installed.