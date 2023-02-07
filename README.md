# Simple-p6-Setup

- [Creating a repository](#creating-a-repository)
- [Cloning your repository](#cloning-your-repository)
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

![image](https://user-images.githubusercontent.com/45451201/217267551-9134512a-6462-4637-963e-d1e5e9519f29.png)

## Writing tests

This template comes with the [Doctest](https://github.com/doctest/doctest) testing library.

## CI
