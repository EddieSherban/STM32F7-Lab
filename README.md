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

1. **Run CMake configuration** (only need to run this once):

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

   **Result:** Badabing badaboom now you have an elf file that you can flash onto your microcontroller.

---

## Modifying the Project

Now, you just have to save your edited files and run "ninja -j8" to rebuild your project from the "build" folder. You can always go into CubeMX to modify your peripherals and settings, just be sure to run "ninja -j8" after doing so.