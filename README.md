# Simple-p6-Setup

This template contains all the things you need to get started with a clean and modern C++ project (formatter, linter, tests, continuous integration, etc.).
**It works on all platforms (Windows, Linux, MacOS).**

> **Please read the first three chapters very carefully as this project requires some specific setup, in particular when downloading (cloning) the repository.**

- [Setting up](#setting-up)
  - [Creating a repository](#creating-a-repository)
  - [Downloading your repository](#downloading-your-repository)
  - [Compiling](#compiling)
  - [Clangd](#clangd)
  - [Formatter](#formatter)
  - [Linter](#linter)
- [Coding](#coding)
  - [Renaming the project](#renaming-the-project)
  - [Folder structure](#folder-structure)
  - [p6](#p6)
- [Going further](#going-further)
  - [Writing tests](#writing-tests)
  - [Continuous Integration (CI)](#continuous-integration-ci)
  - [Warnings as errors](#warnings-as-errors)

## Setting up

### Creating a repository

First, create your own repository based on this one. If you are using GitHub you can use this repository as a template:

![image](https://user-images.githubusercontent.com/45451201/217287736-20058d69-f0ed-40ff-b4e5-cfd852e2ba82.png)

Otherwise simply create a repository on your own and copy-paste all the files in this repo to your new repo.

### Downloading your repository

Run this command inside the directory where you want to put this project:

```
git clone --recursive your_repo_url
```

**NB:** The `--recursive` is very important here because [we make use of submodules](https://julesfouchy.github.io/Learn--Clean-Code-With-Cpp/lessons/git-submodules/).

### Compiling

If that is not already done, [install a compiler](https://julesfouchy.github.io/Learn--Clean-Code-With-Cpp/lessons/install-a-compiler/).

If that is not already done, [setup your IDE for C++ development](https://julesfouchy.github.io/Learn--Clean-Code-With-Cpp/lessons/ide/).

Once that is done, open the project folder in your IDE: it will detect the CMakeLists.txt file automatically and you can just run the project:
![image](https://user-images.githubusercontent.com/45451201/217290500-bd09bc81-861f-4da9-b3c6-fef5e28a83f6.png)

You should see this, with the circle following your mouse cursor:

![initial-window](https://user-images.githubusercontent.com/45451201/217267551-9134512a-6462-4637-963e-d1e5e9519f29.png)

🎉 Congrats you are **almost** done! But keep reading, we will now install amazing tools that will make your life so much easier!

### Clangd

First, you need to [install and setup *clangd*](https://julesfouchy.github.io/Learn--Clean-Code-With-Cpp/lessons/clangd/). It will provide even better C++ support than the default extensions, and is also required for the other tools to work.

### Formatter

[Setup clang-format](https://julesfouchy.github.io/Learn--Clean-Code-With-Cpp/lessons/formatting-tool/).

### Linter

[Setup clang-tidy](https://julesfouchy.github.io/Learn--Clean-Code-With-Cpp/lessons/static-analysers/).

## Coding

### Renaming the project

If you want to rename the project (called "Simple-p6-Setup" by default), you need to change it in 3 places:
- In the `CMakeLists.txt`, change the line `project(Simple-p6-Setup)`
- In the `.github/workflows/build_and_run_tests.yml`, change the line `TARGET: Simple-p6-Setup`
- In the `src/main.cpp`, change the line `auto ctx = p6::Context{{.title = "Simple-p6-Setup"}};`

### Folder structure

All your source files (.cpp) and header files (.hpp) need to go in the `src` folder. It is recommended to have the corresponding .cpp and .hpp next to each other:

```
src
   main.cpp
   some_folder
      some_file.cpp
      some_file.hpp
      another_file.cpp
      another_file.hpp
   another_folder
      a_third_file.cpp
      a_third_file.hpp
```

### p6

*p6* is a 2D-drawing library that is designed to be extremely simple to use. In order to learn how to use it, [read their tutorials](https://julesfouchy.github.io/p6-docs/tutorials/the-context). (Note that you can skip the first chapter "Creating a project" as this template already does everything you need).

## Going further

### Writing tests

This template comes with the [Doctest](https://github.com/doctest/doctest) testing library all set up.
You can simply write something like

```cpp
TEST_CASE("Addition is commutative")
{
    CHECK(1 + 2 == 2 + 1);
    CHECK(4 + 7 == 7 + 4);
}
```

in *any* source file and the tests will run whenever you run your project. You will see their output in the console:

![tests-output](https://user-images.githubusercontent.com/45451201/217270153-73d865d0-dc25-4176-b5eb-af2e9afb507e.png)

To learn more about Doctest, see https://github.com/doctest/doctest/blob/master/doc/markdown/tutorial.md

### Continuous Integration (CI)

> NB: This requires that you are using GitHub. GitLab also provides the same kinds of services, but you will have to set them up on your own, this template doesn't provide the necessary config files.

Whenever you make a commit, GitHub servers will automatically try to build your code and run your tests and, if anything fails, it will warn you. CI is an essential part of development, as it ensures that you notice immediately if you break something. It also allows you to test your code on all the platforms (Windows, Linux, MacOS) and all the compilers (Clang, GCC, MSVC) and benefit from all the warnings they have to offer.

You can see the progress (and eventual errors) of your tests in the *Actions* tab of your GitHub repository.

![image](https://user-images.githubusercontent.com/45451201/217274801-37bc38bd-055a-4a84-89b9-e2d56c798b2f.png)

You will also receive an email if something fails.

### Warnings as errors

Warnings are usually only considered as errors during the CI process (so that any warning is considered a failure and gets reported to you).
If you want to have warnings as errors in your local project too (typically in order to fix a warning shown by the CI):
 - <kbd>CTRL</kbd> + <kbd>SHIFT</kbd> + <kbd>P</kbd> (to open VSCode's command palette)
 - Search for `CMake: Edit CMake Cache (UI)`
 - Turn `WARNINGS_AS_ERRORS` ON and then save
![image](https://user-images.githubusercontent.com/45451201/217280969-48939e75-0bad-4a9f-bdf6-08e37649c4c6.png)