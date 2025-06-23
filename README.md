# CMake Template

(**If you clone it, you better delete .git/ folder and this README.md file**)

My personal CMake template for all of my projects in C++

Template tested in Windows/Linux and on VS Code/Visual Studio

Required: `git`, `cmake`, C++ compiler, `vcpkg`

## How to use it

1. Clone/download it. If you don't know how, well, you need to learn basics

2. Rename cloned folder to your project name

3. Open it in your favourite IDE
    - VS Code (I usually use *Ctrl+K* *Ctrl+O*)
    - Visual Studio (inside folder "Open with Visual Studio")

4. In CMakeLists.txt follow comments, setup your project. You must update:
    - CMake minimum version (I recommend not below 3.10)
    - C++ language standard (I recommend not below C++11)
    - Replace `PROJECT_NAME` to your project name
    - Replace `PROJECT_NAME_SRC` to your project name + any `src` prefix
    - Replace `PROJECT_NAME_TEST` to your project name + any `test` prefix

5. Delete `.git/` folder and this `README.md`

6. Initialize git, add all and create first commit

Congratulation! You setup this template
