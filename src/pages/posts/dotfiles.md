---
layout: "../../layouts/BlogPost.astro"
title: "How to store dotfiles"
description: "Let me introduce my way of storing dotfiles on a versioning platform"
pubDate: "Sept. 24 2023"
# updatedDate: "19 Dec. 2022"
heroImage: "/heroes/welcome.jpg"
---

# How to store dotfiles

## Introduction

### Disclaimer

Everything that compose this article is  written by a student which may make some mistakes. Please let me know if you find some or if you have some comments !

### Why versioning dotfiles ?

When you are switching from one computer to another all the time, it is not really convenient to copy manually your config files like your `.zshrc`, `vimrc` etc... There is plenty of solutions to automate this process but I adopted the one I saw in [this article](https://www.atlassian.com/git/tutorials/dotfiles).

It is a nice one because the only tool you need is `git` (with a Github repository for example).

For the following of this tutorial I will assume that you have `git` installed on a Unix-like operating system.

## How to ?