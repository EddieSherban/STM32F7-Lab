1. run this command in root project directory...  
cmake -Bbuild -G Ninja -DCMAKE_TOOLCHAIN_FILE=path\to\gcc-arm-none-eabi.cmake -DCMAKE_BUILD_TYPE=Debug -DCMAKE_EXPORT_COMPILE_COMMANDS=true  

2. then enter the build folder and run this to build the project...  
ninja -j8  
you only need to run the first command **ONCE**. The second command is run every time you change your code and build the project.  
  
Generating 