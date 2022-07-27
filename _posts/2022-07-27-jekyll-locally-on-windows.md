---
layout: post
title: Jekyll Locally On Windows
description: Running Jekyll Locally for running github-pages on Windows
---

# Pengenalan
Jekyll is a static site generator. It takes text written in your favorite markup language and uses layouts to create a static website. You can tweak the site’s look and feel, URLs, the data displayed on the page, and more.

# Installation
Jekyll is a [Ruby Gem](https://jekyllrb.com/docs/ruby-101/#gems) that can be installed on most systems.

Requirements
* [Ruby](https://www.ruby-lang.org/en/downloads/) version **2.5.0** or higher, including all development headers (check your Ruby version using `ruby -v`)
* [RubyGems](https://rubygems.org/pages/download) (check your Gems version using `gem -v`)
* [GCC](https://gcc.gnu.org/install/) and [Make](https://www.gnu.org/software/make/) (check versions using `gcc -v`, `g++ -v`, and `make -v`)

# Jekyll on Windows
While Windows is not an officially-supported platform, it can be used to run Jekyll with the proper tweaks.

## Installing Ruby, Gem and Jekyll
The easiest way to install Ruby and Jekyll is by using the [RubyInstaller](https://rubyinstaller.org/) for Windows.

RubyInstaller is a self-contained Windows-based installer that includes the Ruby language, an execution environment, important documentation, and more.

We only cover RubyInstaller-2.4 and newer here. Older versions need to install the [Devkit manually](https://github.com/oneclick/rubyinstaller/wiki/Development-Kit).

1. Download and install a **Ruby+Devkit** version from [RubyInstaller Downloads](https://rubyinstaller.org/downloads/). Use default options for installation.
2. Run the `ridk install` step on the last stage of the installation wizard. This is needed for installing gems with native extensions. You can find additional information regarding this in the [RubyInstaller Documentation](https://github.com/oneclick/rubyinstaller2#using-the-installer-on-a-target-system). From the options choose `MSYS2 and MINGW development tool chain`.
3. Open a new command prompt window from the start menu, so that changes to the `PATH` environment variable becomes effective. Install Jekyll and Bundler using `gem install jekyll bundler`
4. Check if Jekyll has been installed properly: `jekyll -v`

That’s it, you’re ready to use Jekyll!

## Running Jekyll and Static pages
1. Create a new Jekyll site at `./myblog`.
```jekyll new myblog```
2. Change into your new directory.
```cd myblog```
3. Build the site and make it available on a local server.
```bundle exec jekyll serve```
4. Browse to [http://localhost:4000](http://localhost:4000)

> If you are using Ruby version 3.0.0 or higher, step 5 may fail. You may fix it by adding `webrick` to your dependencies: `bundle add webrick`