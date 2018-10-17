# ccminer lyra2re edition

Based on Christian Buchner's &amp; Christian H.'s CUDA project
based on the Fork by tpruvot@github with X14,X15,X17,WHIRL,Blake256 and LYRA2 support , and some others, check the [README.txt](README.txt)
Based on sp-hash@github and KlausT@github fork

djm34: BTC donation address: 
1NENYmxwZGHsKFmyjTc5WferTn5VTFb7Ze

A part of the recent algos were originally wrote by [djm34](https://github.com/djm34).

This variant was tested and built on Linux (ubuntu server 14.04) and VStudio 2013 on Windows 8.1

Note that the x86 releases are generally faster than x64 ones on Windows.

# macOS High Sierra Build Instruction

### Requirements:

1. Xcode 9.4.1 for building Macports packages
2. Xcode 8.2.1 for building ccminer
3. Install Xcode 9.4.1 at default location /Applications/Xcode.app
4. Install Xcode 8.2.1 at different location /Applications/Xcode-8.2.1/Xcode.app

### Installing Dependencies:

	sudo xcode-select -s /Applications/Xcode.app
	sudo port install coreutils
	sudo port install autoconf
	sudo port install automake
	sudo port install curl
	sudo port install openssl
	sudo port install libomp-devel
	sudo port install pkgconfig
	sudo xcode-select -s /Applications/Xcode-8.2.1/Xcode.app
	
### Build and Install

	chmod +x autogen.sh
	chmod +x configure
	./autogen.sh
	LDFLAGS="-L/opt/local/lib/libomp" CPPFLAGS="-I/opt/local/include/libomp" ./configure
	make
	sudo make install

OpenMP support does not seem to work, but passing those LDFLAGS and CPPFLAGS are required to successfully build ccminer. Tested on macOS High Sierra 10.13.6 with NVidia Web Driver 387.10.10.10.40.105, CUDA Driver 396.148, CUDA Toolkit 9.2.148, and GTX1050 Ti as eGPU (Akitio Thunder2).

# Dependencies for Windows built

This project requires some libraries to be built :

- OpenSSL (prebuilt for win)

- Curl (prebuilt for win)

- pthreads (prebuilt for win)

The tree now contains recent prebuilt openssl and curl .lib for both x86 and x64 platforms (windows).

To rebuild them, you need to clone this repository and its submodules :
    git clone https://github.com/peters/curl-for-windows.git compat/curl-for-windows

There is also a [Tutorial for windows](http://cudamining.co.uk/url/tutorials/id/3) on [CudaMining](http://cudamining.co.uk) website.

