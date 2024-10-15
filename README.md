run this command in root project directory...__
cmake -Bbuild -G Ninja -DCMAKE_TOOLCHAIN_FILE=path\to\gcc-arm-none-eabi.cmake -DCMAKE_BUILD_TYPE=Debug -DCMAKE_EXPORT_COMPILE_COMMANDS=true__

then change to build folder and run this to build the project...__
ninja -j8__