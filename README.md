# Simple-p6-Setup

- [Creating a repository](#creating-a-repository)
- [Cloning your repository](#cloning-your-repository)
- [Compiling](#compiling)
- [Writing tests](#writing-tests)
- [CI](#ci)

## Creating a repository

First, create your own repository based on this one. If you are using GitHub you can use this repository as a template

Otherwise simply create a repository on your own and copy-paste all the files in this repo to your new repo.

## Cloning your repository

```
git clone --recursive your_repo_url
```

The `--recursive` is very important because [we make use of submodules](https://julesfouchy.github.io/Learn--Clean-Code-With-Cpp/lessons/git-submodules/).

## Compiling

![initial-window](https://user-images.githubusercontent.com/45451201/217267551-9134512a-6462-4637-963e-d1e5e9519f29.png)

## Writing tests

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

## CI

![image](https://user-images.githubusercontent.com/45451201/217274801-37bc38bd-055a-4a84-89b9-e2d56c798b2f.png)
