## Credits 
1) forked from `https://github.com/hominoids/sgminer-arm` 
2) for Android Port `https://github.com/Pyogenics` 


# how to build && install

building dependency ```pkg up && pkg upg && pkg i build-essential libtool cmake yasm make wget git libjansson libgmp opencl-headers libmicrohttpd libuv* clang binutils```

add OPENCL LIB PATH to .bashrc

```
nano ~/.bashrc

export LD_LIBRARY_PATH=$PREFIX/lib:/vendor/lib64:/vendor/lib64/egl
```

press `control+x` then type `y` exit from termux && re-open termux

now check opencl

```
git clone https://github.com/Oblomov/clinfo
cd clinfo
make
./clinfo.real

```


then install gcc because clang cannot compile `sgminer-android`

```

curl -LO https://its-pointless.github.io/setup-pointless-repo.sh

bash setup-pointless-repo.sh

pkg i gcc-10 libgccjit-10-dev libgomp-10 bthread

```

now you should install OpenCL driver for (Adreno && Arm-Mali)

```
Adreno

ln -s /system/vendor/lib64/libOpenCL.so $PREFIX/lib/libOpenCL.so

ARM-Mali

ln -s /system/vendor/lib64/egl/libmali.so $PREFIX/lib/libOpenCL.so
```
#### edit this line, after add save && exit
```
nano $PREFIX/include/bthread.h
```
#### add this line 
```
#include <pthread.h>
```
