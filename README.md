# CMake Template

(**If you clone it, you better delete this README.md file**)

My personal CMake template for all of my projects in C++

Template tested in Windows/Linux and on VS Code/Visual Studio

## How to use it

1. Clone it. If you don't know how, well, you need to learn basics

2. Rename cloned folder to your project name (recommend don't use spaces)

3. Open it in your favourite IDE
    - VS Code (I usually use *Ctrl+K* *Ctrl+O*)
    - Visual Studio (inside folder "Open with Visual Studio")

4. In CMakeLists.txt follow comments, setting to your project. You must check:
    - CMake minimum version (recommend not below 3.12)
    - Project name
    - C++ language standard

5. Update remote `origin` to your GitHub (or another remote git service) package.
I usually just write this commands
    - `git remote remove origin`
    - `git remote add origin <paste your link here>`


Big thanks to @meemknight, this template based on his guide 
(and many other texts through entire internet)
