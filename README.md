Certainly! Here's an improved version of your README with headers and clearer instructions.

---

# Project Setup and Build Instructions

This guide provides step-by-step instructions to set up, build, and generate your microcontroller project using CubeMX, CMake, and Ninja.

## Table of Contents

1. [Prerequisites](#prerequisites)
2. [Initial Project Setup](#initial-project-setup)
3. [Building the Project](#building-the-project)
4. [Generating the Project using CubeMX](#generating-the-project-using-cubemx)
5. [Modifying CMake Configuration](#modifying-cmake-configuration)

---

## Prerequisites

Ensure you have the following tools installed:

- **CubeMX**
- **CMake**
- **Ninja**
- **GCC ARM Toolchain**

---

## Initial Project Setup

1. **Run CMake configuration** (only once):

   In the root project directory, execute the following command to configure the build system:

   ```bash
   cmake -Bbuild -G Ninja -DCMAKE_TOOLCHAIN_FILE=path\to\gcc-arm-none-eabi.cmake -DCMAKE_BUILD_TYPE=Debug -DCMAKE_EXPORT_COMPILE_COMMANDS=true
   ```

2. **Build the project**:

   After configuring CMake, every time you change your code and want to build the project, enter the `build` folder and run the following:

   ```bash
   ninja -j8
   ```

---

## Generating the Project using CubeMX

1. **Create a new project in CubeMX**:

   - Open CubeMX and create a new project with the selected microcontroller.
   - Configure the pins, peripherals, and clocks as needed.

2. **Configure Project Manager Settings**:

   - In the "Project Manager" tab, set the project name.
   - Set the "Project Location" to the folder containing your projects (e.g., the `experiments` folder).
   - Set the "Toolchain Folder Location" by appending `CubeMX` to the location, so that startup assembly code, linker scripts, and other toolchain files are placed in a separate folder.

3. **Set Code Generator Options**:

   - In the "Code Generator" tab, tick the option:
   
     ```  
     Generate peripheral initialization as a pair of '.c/.h' files per peripheral
     ```

---

## Modifying CMake Configuration

1. **Copy the CMake template files**:

   Copy the files from the `cmake_template` folder and paste them into the root directory of your project.

2. **Edit `CMakeLists.txt`**:

   - Set the correct microcontroller family and model by modifying the following lines:
   
     ```cmake
     set(MCU_FAMILY _______)
     set(MCU_MODEL _______)
     ```

   - Under the `# Headers` comment, include any directories you want to add.  
     Similarly, for `# Sources`, specify the source files for your project.

   - You can exclude unnecessary template `.c` files if needed.

---

## Building the Project

1. **Run CMake configuration** (if you haven't already):

   From the root directory, run:

   ```bash
   cmake -Bbuild -G Ninja -DCMAKE_TOOLCHAIN_FILE=path\to\gcc-arm-none-eabi.cmake -DCMAKE_BUILD_TYPE=Debug -DCMAKE_EXPORT_COMPILE_COMMANDS=true
   ```

2. **Build the project**:

   Enter the `build` folder:

   ```bash
   cd build
   ```

   Then, run Ninja to compile the project:

   ```bash
   ninja -j8
   ```

   **Result:** Once the build process is complete, you will have an ELF file ready to flash onto your microcontroller.

---

## Conclusion

Badabing badaboom now you have an elf file that you can flash onto your microcontroller.