NW.js port for Raspberry Pi 
============================= 

[NW.js](http://nwjs.io/ "NW.js web site") (formely node-webkit) binary compiled for the **ARMv6** used by Raspberry Pi. It also runs on Raspberry Pi 2 and Raspberry Pi 3 since they are backward compatible with ARMv6. Other compatible hardware could also run this binary althoguh it has not been tested yet.


## Instructions
1. **You need a _package.nw_** which is just a _.zip_ file with _.nw_ extension that contains your project (at least, it needs an _index.html_ and a _package.json_ inside). The included _package.nw_ is just an example using the [Yasminoku](https://github.com/jalbam/yasminoku "Yasminoku repository") game. Since this is only a port, if you need it you can go to the [official web site of NW.js] (http://nwjs.io/ "NW.js project") and read the documentation to know more about _package.nw_, _package.json_, etc.

2. Optional: **merge _nw_ and _package.nw_** into a single file with the following command:
	```
	cat nw package.nw > Your_new_binary_file
	```
	
3. **Edit _fix_libudev.so.0_ and _fix_libudev.so.1_** and replace _Your_new_binary_file_ found in their code by the real name of your binary file (if you did not merge _nw_ and _package.nw_ together, then replace it by just _nw_).

4. If you need it, **give executable permissions** (and other desired permissions) to _Your_new_binary_file_ (or _nw_) using the **_chmod_** command (as root).

5. Try to **run the binary**:
	```
	./Your_new_binary_file
	```
	If you did not merge the _nw_ and _package.nw_ files in one single file (as explained in _step 2_), you should run this command instead:
	```
	./nw
	```

6. In the case the system complains about **_libudev.so.0_** when you try to run the binary, just type the following command:
	```
	./fix_libudev.so.0
	```
	Likewise, if needed, do the same for **_libudev.so.1_** running this:
	```
	./fix_libudev.so.1
	```
	Note: these two commands above will only work if you have followed the _step 3_ properly before. Each of them only needs to be executed once and never again.

7. If all works well, you can **distribute your project**. You will need these files at least (in the same folder): _libffmpegsumo.so_, _nw.pak_ and _Your_new_binary_file_ (or _nw_ and _package.nw_ instead). I would recommend including _fix_libudev.so.0_ and _fix_libudev.so.1_ optionally (modified as explained in _step 3_) if you think others might need them.


## Versions
node-webkit (now called NW.js) version: v.0.7.0-pre 

Node.js version: v0.10.12


## Tested on
* "**Raspberry Pi Model B** Revision 2.0 Mounting holes" with 512MB RAM (revision 000e) using **Raspbian GNU/Linux 7 "wheezy"** (Linux raspberrypi **4.1.19+ #858 armv6l** GNU/Linux).
* "**Raspberry Pi 3 Model B** PCB Revision 1.2" with 1024MB RAM (revision a02082) using **Raspbian GNU/Linux 8 "jessie"** (Linux raspberrypi **4.1.19-v7+ #858 SMP armv71** GNU/Linux).


## Compatibility
* **Raspberry Pi Zero**, all models (untested)
* **Raspberry Pi**, all models
* **Raspberry Pi 2**, all models (untested)
* **Raspberry Pi 3**, all models
* **Other devices** with compatible hardware (untested)


## Credits
The original binary was shared by [Nils Måsén "piksel" (aka "spaculo")](https://github.com/piksel "piksel's GitHub account") at <https://www.youtube.com/watch?v=MqNUYk9Y8jY> so thank you very much! :)