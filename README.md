compiling vorbis need ogg
compiling only vorbis for Android will stuck on find_package(ogg) because it will search on the llvm\sysroot of the ndk
i.e path get appended even if specifying -DOGG_ROOT to some path

so creating this parent adding subdir will manage to compile it successfully for Android

steps
1. create directory, cd to the directory
2. clone vorbis https://gitlab.xiph.org/xiph/vorbis.git
3. clone ogg https://gitlab.xiph.org/xiph/ogg.git
4. clone this repository
5. cd to the ogg-vorbis
5. run cmake commands
  1. cmake -B build -G Ninja -DANDROID_ABI=arm64-v8a -DANDROID_PLATFORM=android-21 -DANDROID_NDK=$ANDROID_NDK -DCMAKE_TOOLCHAIN_FILE=$ANDROID_NDK/build/cmake/android.toolchain.cmake -DCMAKE_INSTALL_PREFIX=build-published -DCMAKE_INSTALL_LIBDIR=lib -DCMAKE_INSTALL_INCLUDEDIR=include
  2. cmake --build build/
  3. cmake --install build/

tadaaaaaaaaaaaa!