---
Title: UniDokkan SDK (for Modules)
Sort: 5
---
---
### What is it?
This SDK is used to create modules that get loaded into Dokkan.

These modules can execute their own code in Dokkan's address space, hook/redirect Dokkan's own functions, and create their own UI inside of Dokkan.

<br /><br />

### What is required?

 - Python 3
 - Optional - A reverse engineering tool
	 - [Ghidra](https://ghidra-sre.org/)
	 - [IDA Pro](https://www.hex-rays.com/products/ida/index.shtml)
 - Optional - A C++, cmake and ninja compatible IDE
	 - [Visual Studio 2019]([https://visualstudio.microsoft.com/downloads/](https://visualstudio.microsoft.com/downloads/))
	 - [VS Code](https://code.visualstudio.com/)
	 - [CLion](https://www.jetbrains.com/clion/)

<br /><br />

### Where do I get it?
Downloads are currently only available in the `#underground` channel on the UniDokkan Discord server. Once hook modules are supported by the public UniDokkan Patcher, the SDK will be made available to everyone.

<br /><br />

### What is included?

 - `deps/` - Contains nearly all the required dependecies to build a module
	 - `deps/download_deps.py` - Execute this python script to download and extract the dependencies for your system (Windows or Linux). It will download the [Android NDK](https://developer.android.com/ndk/downloads), [CMake](https://cmake.org/download/), and [Ninja](https://github.com/ninja-build/ninja/releases).<br /><br />
 - `dokkan-sdk-*/` - The main code for the SDK that your module will link to.
	 - `dokkan-sdk-*/cocos2d/` - Contains a modified version of [Cocos2D](https://github.com/cocos2d/cocos2d-x/tree/cocos2d-x-3.17.1)
	 - `dokkan-sdk-*/public/` - Contains code that I wrote or reverse engineered for integration with Dokkan. 
		 - `dokkan-sdk-*/public/dokkan/` - Contains Dokkan specific classes for interoperability between your module and Dokkan. This will be updated overtime as more classes get reverse engineered.
		 - `dokkan-sdk-*/public/unidokkan/` - Contains UniDokkan specific code/references for integration with the UniDokkan Patcher and UniDokkan Patches.<br /><br />
 - `projects/` - This is where your projects that will use the SDK go.
	 - `projects/template/` - An empty template project that already includes build scripts and connects to the UniDokkan SDK.
	 - `projects/demo-title-screen/` - A fully working example of a module. Places a "Hello World" text box on Dokkan's title screen.

<br /><br />

### How to get started?

 1. Make a copy of the `projects/template` folder and name it your project's name.<br /><br />
 2. Open `projects/[YOUR PROJECT NAME]/CMakeLists.txt`<br /><br />
	 - Edit `set(PROJECT_NAME "template")` 
		 - Set the name of your project. This will be the file name of the module that gets built.<br /><br />
	 - Edit `set(DOKKAN_SDK_REV "r2")` .
		 - Set the revision of the `dokkan-sdk-*/` folder. 
		 - Usually the latest revision is the best choice but if there are any breaking changes you may want to stay with an older revision.<br /><br />
	 - Edit `option(BUILD_COCOS2D "Include Cocos2D Library" OFF)`
		 - If your project is adding or modifying the Dokkan UI, this needs to be set to `ON`.
		 - This will increase build times and module file size (by about 4MB).<br /><br />
	 - Edit `set(PROJECT_LIBS dokkansdk)`
		 - If you are adding additional cmake compatible C/C++ libraries:
			 - Include `add_subdirectory([LIBRARY PATH], "${CMAKE_BINARY_DIR}/[LIBRARY NAME]")`
			 - Update `set(PROJECT_LIBS dokkansdk LIBRARY_NAME)`<br /><br />
 3. Add/Edit code in the `projects/[YOUR PROJECT NAME]/src/` folder.<br /><br />
	 - All code in any folder inside `src/` will be included in the build.<br /><br />
	 - You must have exported `unidokkan_init`. This is your module's entry point. The template project does this for you.<br /><br />
 4. Execute one of the build scripts in `projects/[YOUR PROJECT NAME]/`<br /><br />
	 - `win-build.bat` if you are building on Windows<br /><br />
	 - `linux-build.sh` if you are building on Linux<br /><br />
	 - The `*-clean.*` files will delete the build folder. If you modify `CMakeLists.txt` you should run this.<br /><br />
 5. If your build encountered no errors, your module will be built to `projects/[YOUR PROJECT NAME]/build/lib[YOUR PROJECT NAME].so`
Unidokkan for iOS
---
