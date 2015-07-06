# Launch Script for MODO

Launch Script is an improved version of MODO's default script.run.  It's based on the way the built in script editor works and runs code in the same manner.

## Installation
1. Hit Download ZIP on the right
2. From MODO go to System > Open Content Folder
3. Extract the contents of the zip to the Kits folder, should be Kits/launchScript-master

## Use
1. From the modo command window, enter ```launchScript "/foo/bar/someScript.py"```

## Benefits
- Persistent compiler!!!
	- This means that you can initialize tools, include paths, set environment variables, etc and any further scripts you run will be run in that same context
	- Ex: We have an initModo script that runs on startup and adds Python's site packages to the system path, sets the current_app environment variable to modo, etc
- Runtime blessing
	- Scripts executed with launchScript can bless commands, views, etc at runtime
	- Everything can still only be blessed once but at least you don't have to shove everything in an lxserv folder :)
- Proper Python magic variables
	- ```__file__``` is set to the filepath of the script you're running
	- ```__name__``` is set to ```'__main__'``` so tools using that convention will work
- Runs everything as Python, no need to put #python at the top of your files
- Sets an empty sys.argv.  MODO doesn't set this by default which causes errors in certain libraries

## Drawbacks
- You have to restart MODO when updating libraries as they're only loaded once.  You can use reload() but that's a bad habit, besides MODO takes like 6 seconds to start
