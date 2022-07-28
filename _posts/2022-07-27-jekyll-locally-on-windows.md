---
layout: post
title: Jekyll Locally On Windows
description: Running Jekyll Locally for running github-pages on Windows
---

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
* Create a new Jekyll site at `./myblog`.
```jekyll new myblog```

~~~PowerShell
    PS > jekyll new myblog
    Running bundle install in C:/tools/myblog...
      Bundler: Fetching gem metadata from https://rubygems.org/............
      Bundler: Resolving dependencies...
      Bundler: Using bundler 2.3.18
      Bundler: Using public_suffix 4.0.7
      Bundler: Using colorator 1.1.0
      Bundler: Using concurrent-ruby 1.1.10
      Bundler: Using eventmachine 1.2.7
      Bundler: Using http_parser.rb 0.8.0
      Bundler: Using ffi 1.15.5 (x64-mingw-ucrt)
      Bundler: Using forwardable-extended 2.6.0
      Bundler: Using rb-fsevent 0.11.1
      Bundler: Using rexml 3.2.5
      Bundler: Using liquid 4.0.3
      Bundler: Using mercenary 0.4.0
      Bundler: Using rouge 3.29.0
      Bundler: Using safe_yaml 1.0.5
      Bundler: Using unicode-display_width 1.8.0
      Bundler: Using addressable 2.8.0
      Bundler: Using i18n 1.12.0
      Bundler: Fetching thread_safe 0.3.6
      Bundler: Fetching wdm 0.1.1
      Bundler: Using kramdown 2.4.0
      Bundler: Using em-websocket 0.5.3
      Bundler: Using terminal-table 2.0.0
      Bundler: Using sassc 2.4.0
      Bundler: Using rb-inotify 0.10.1
      Bundler: Using kramdown-parser-gfm 1.1.0
      Bundler: Using pathutil 0.16.2
      Bundler: Using jekyll-sass-converter 2.2.0
      Bundler: Using listen 3.7.1
      Bundler: Using jekyll-watch 2.2.1
      Bundler: Using jekyll 4.2.2
      Bundler: Fetching jekyll-seo-tag 2.8.0
      Bundler: Fetching jekyll-feed 0.16.0
      Bundler: Installing jekyll-feed 0.16.0
      Bundler: Installing wdm 0.1.1 with native extensions
      Bundler: Installing jekyll-seo-tag 2.8.0
      Bundler: Installing thread_safe 0.3.6
      Bundler: Fetching minima 2.5.1
      Bundler: Fetching tzinfo 1.2.10
      Bundler: Installing minima 2.5.1
      Bundler: Installing tzinfo 1.2.10
      Bundler: Fetching tzinfo-data 1.2022.1
      Bundler: Installing tzinfo-data 1.2022.1
      Bundler: Bundle complete! 7 Gemfile dependencies, 35 gems now installed.
      Bundler: Use `bundle info [gemname]` to see where a bundled gem is installed.
    New jekyll site installed in C:/tools/myblog.
~~~

* Change into your new directory.
```cd myblog```

~~~PowerShell
    PS > cd ./myblog/
    PS > dir

            Directory: C:\tools\myblog


    Mode                LastWriteTime         Length Name
    ----                -------------         ------ ----
    d----        27/07/2022     18:26                  _posts
    -a---        27/07/2022     18:26           2080   _config.yml
    -a---        27/07/2022     18:26             56   .gitignore
    -a---        27/07/2022     18:26            419   404.html
    -a---        27/07/2022     18:26            539   about.markdown
    -a---        27/07/2022     18:26           1337   Gemfile
    -a---        27/07/2022     18:26           2047   Gemfile.lock
    -a---        27/07/2022     18:26            175   index.markdown
~~~

* Build the site and make it available on a local server.
```bundle exec jekyll serve```

~~~PowerShell
    PS > bundle exec jekyll serve
    Configuration file: C:/tools/myblog/_config.yml
                Source: C:/tools/myblog
        Destination: C:/tools/myblog/_site
    Incremental build: disabled. Enable with --incremental
        Generating...
        Jekyll Feed: Generating feed for posts
                        done in 1.486 seconds.
    Auto-regeneration: enabled for 'C:/tools/myblog'
                        ------------------------------------------------
        Jekyll 4.2.2   Please append `--trace` to the `serve` command
                        for any additional information or backtrace.
                        ------------------------------------------------
    C:/tools/ruby31/lib/ruby/gems/3.1.0/gems/jekyll-4.2.2/lib/jekyll/commands/serve/servlet.rb:3:in `require': cannot load such file -- webrick (LoadError)
            from C:/tools/ruby31/lib/ruby/gems/3.1.0/gems/jekyll-4.2.2/lib/jekyll/commands/serve/servlet.rb:3:in `<top (required)>'
            from C:/tools/ruby31/lib/ruby/gems/3.1.0/gems/jekyll-4.2.2/lib/jekyll/commands/serve.rb:179:in `require_relative'
            from C:/tools/ruby31/lib/ruby/gems/3.1.0/gems/jekyll-4.2.2/lib/jekyll/commands/serve.rb:179:in `setup'
            from C:/tools/ruby31/lib/ruby/gems/3.1.0/gems/jekyll-4.2.2/lib/jekyll/commands/serve.rb:100:in `process'
            from C:/tools/ruby31/lib/ruby/gems/3.1.0/gems/jekyll-4.2.2/lib/jekyll/command.rb:91:in `block in process_with_graceful_fail'
            from C:/tools/ruby31/lib/ruby/gems/3.1.0/gems/jekyll-4.2.2/lib/jekyll/command.rb:91:in `each'
            from C:/tools/ruby31/lib/ruby/gems/3.1.0/gems/jekyll-4.2.2/lib/jekyll/command.rb:91:in `process_with_graceful_fail'
            from C:/tools/ruby31/lib/ruby/gems/3.1.0/gems/jekyll-4.2.2/lib/jekyll/commands/serve.rb:86:in `block (2 levels) in init_with_program'
            from C:/tools/ruby31/lib/ruby/gems/3.1.0/gems/mercenary-0.4.0/lib/mercenary/command.rb:221:in `block in execute'
            from C:/tools/ruby31/lib/ruby/gems/3.1.0/gems/mercenary-0.4.0/lib/mercenary/command.rb:221:in `each'
            from C:/tools/ruby31/lib/ruby/gems/3.1.0/gems/mercenary-0.4.0/lib/mercenary/command.rb:221:in `execute'
            from C:/tools/ruby31/lib/ruby/gems/3.1.0/gems/mercenary-0.4.0/lib/mercenary/program.rb:44:in `go'
            from C:/tools/ruby31/lib/ruby/gems/3.1.0/gems/mercenary-0.4.0/lib/mercenary.rb:21:in `program'
            from C:/tools/ruby31/lib/ruby/gems/3.1.0/gems/jekyll-4.2.2/exe/jekyll:15:in `<top (required)>'
            from C:/tools/ruby31/bin/jekyll:32:in `load'
            from C:/tools/ruby31/bin/jekyll:32:in `<main>'
~~~

> If you are using Ruby version 3.0.0 or higher, step 5 may fail. You may fix it by adding `webrick` to your dependencies: `bundle add webrick`
~~~PowerShell
    PS > bundle add webrick
    Fetching gem metadata from https://rubygems.org/...........
    Resolving dependencies...
    Fetching gem metadata from https://rubygems.org/...........
    Resolving dependencies...
    Using bundler 2.3.18
    Using public_suffix 4.0.7
    Using colorator 1.1.0
    Using concurrent-ruby 1.1.10
    Using eventmachine 1.2.7
    Using http_parser.rb 0.8.0
    Using ffi 1.15.5 (x64-mingw-ucrt)
    Using forwardable-extended 2.6.0
    Using rb-fsevent 0.11.1
    Using rexml 3.2.5
    Using liquid 4.0.3
    Using mercenary 0.4.0
    Using rouge 3.29.0
    Using safe_yaml 1.0.5
    Using unicode-display_width 1.8.0
    Using thread_safe 0.3.6
    Using wdm 0.1.1
    Using addressable 2.8.0
    Using em-websocket 0.5.3
    Using i18n 1.12.0
    Using sassc 2.4.0
    Using rb-inotify 0.10.1
    Using kramdown 2.4.0
    Using pathutil 0.16.2
    Using terminal-table 2.0.0
    Fetching webrick 1.7.0
    Using tzinfo 1.2.10
    Using jekyll-sass-converter 2.2.0
    Using listen 3.7.1
    Using kramdown-parser-gfm 1.1.0
    Using tzinfo-data 1.2022.1
    Using jekyll-watch 2.2.1
    Using jekyll 4.2.2
    Using jekyll-feed 0.16.0
    Using jekyll-seo-tag 2.8.0
    Using minima 2.5.1
    Installing webrick 1.7.0
~~~


* Browse to [http://localhost:4000](http://localhost:4000)

> If there some Dependency error

~~~PowerShell
Dependency Error: Yikes! It looks like you don't have jekyll-paginate or one of its dependencies installed. In order to use Jekyll as currently configured, you'll need to install this gem. If you've run Jekyll with `bundle exec`, ensure that you have included the jekyll-paginate gem in your Gemfile as well. The full error message from Ruby is: 'cannot load such file -- jekyll-paginate' If you run into trouble, you can find helpful resources at https://jekyllrb.com/help/!
C:/tools/ruby31/lib/ruby/gems/3.1.0/gems/jekyll-4.2.2/lib/jekyll/external.rb:73:in `rescue in block in require_with_graceful_fail': jekyll-paginate (Jekyll::Errors::MissingDependencyException)
C:/tools/ruby31/lib/ruby/gems/3.1.0/gems/jekyll-4.2.2/lib/jekyll/external.rb:73:in `rescue in block in require_with_graceful_fail': jekyll-paginate (Jekyll::Errors::MissingDependencyException)
        from C:/tools/ruby31/lib/ruby/gems/3.1.0/gems/jekyll-4.2.2/lib/jekyll/external.rb:58:in `block in require_with_graceful_fail'
        from C:/tools/ruby31/lib/ruby/gems/3.1.0/gems/jekyll-4.2.2/lib/jekyll/external.rb:57:in `each'
        from C:/tools/ruby31/lib/ruby/gems/3.1.0/gems/jekyll-4.2.2/lib/jekyll/external.rb:57:in `require_with_graceful_fail'
        from C:/tools/ruby31/lib/ruby/gems/3.1.0/gems/jekyll-4.2.2/lib/jekyll/plugin_manager.rb:30:in `require_gems'
        from C:/tools/ruby31/lib/ruby/gems/3.1.0/gems/jekyll-4.2.2/lib/jekyll/plugin_manager.rb:22:in `conscientious_require'
        from C:/tools/ruby31/lib/ruby/gems/3.1.0/gems/jekyll-4.2.2/lib/jekyll/site.rb:131:in `setup'
        from C:/tools/ruby31/lib/ruby/gems/3.1.0/gems/jekyll-4.2.2/lib/jekyll/site.rb:36:in `initialize'
        from C:/tools/ruby31/lib/ruby/gems/3.1.0/gems/jekyll-4.2.2/lib/jekyll/commands/build.rb:30:in `new'
        from C:/tools/ruby31/lib/ruby/gems/3.1.0/gems/jekyll-4.2.2/lib/jekyll/commands/build.rb:30:in `process'
        from C:/tools/ruby31/lib/ruby/gems/3.1.0/gems/jekyll-4.2.2/lib/jekyll/command.rb:91:in `block in process_with_graceful_fail'
        from C:/tools/ruby31/lib/ruby/gems/3.1.0/gems/jekyll-4.2.2/lib/jekyll/command.rb:91:in `each'
        from C:/tools/ruby31/lib/ruby/gems/3.1.0/gems/jekyll-4.2.2/lib/jekyll/command.rb:91:in `process_with_graceful_fail'
        from C:/tools/ruby31/lib/ruby/gems/3.1.0/gems/jekyll-4.2.2/lib/jekyll/commands/serve.rb:86:in `block (2 levels) in init_with_program'
        from C:/tools/ruby31/lib/ruby/gems/3.1.0/gems/mercenary-0.4.0/lib/mercenary/command.rb:221:in `block in execute'        from C:/tools/ruby31/lib/ruby/gems/3.1.0/gems/mercenary-0.4.0/lib/mercenary/command.rb:221:in `each'
        from C:/tools/ruby31/lib/ruby/gems/3.1.0/gems/mercenary-0.4.0/lib/mercenary/command.rb:221:in `execute'
        from C:/tools/ruby31/lib/ruby/gems/3.1.0/gems/mercenary-0.4.0/lib/mercenary/program.rb:44:in `go'
        from C:/tools/ruby31/lib/ruby/gems/3.1.0/gems/mercenary-0.4.0/lib/mercenary.rb:21:in `program'
        from C:/tools/ruby31/lib/ruby/gems/3.1.0/gems/jekyll-4.2.2/exe/jekyll:15:in `<top (required)>'
        from C:/tools/ruby31/bin/jekyll:32:in `load'
        from C:/tools/ruby31/bin/jekyll:32:in `<main>'
<internal:C:/tools/ruby31/lib/ruby/3.1.0/rubygems/core_ext/kernel_require.rb>:85:in `require': cannot load such file -- jekyll-paginate (LoadError)
        from <internal:C:/tools/ruby31/lib/ruby/3.1.0/rubygems/core_ext/kernel_require.rb>:85:in `require'
        from C:/tools/ruby31/lib/ruby/gems/3.1.0/gems/jekyll-4.2.2/lib/jekyll/external.rb:60:in `block in require_with_graceful_fail'
        from C:/tools/ruby31/lib/ruby/gems/3.1.0/gems/jekyll-4.2.2/lib/jekyll/external.rb:57:in `each'
        from C:/tools/ruby31/lib/ruby/gems/3.1.0/gems/jekyll-4.2.2/lib/jekyll/external.rb:57:in `require_with_graceful_fail'
        from C:/tools/ruby31/lib/ruby/gems/3.1.0/gems/jekyll-4.2.2/lib/jekyll/plugin_manager.rb:30:in `require_gems'
        from C:/tools/ruby31/lib/ruby/gems/3.1.0/gems/jekyll-4.2.2/lib/jekyll/plugin_manager.rb:22:in `conscientious_require'
        from C:/tools/ruby31/lib/ruby/gems/3.1.0/gems/jekyll-4.2.2/lib/jekyll/site.rb:131:in `setup'
        from C:/tools/ruby31/lib/ruby/gems/3.1.0/gems/jekyll-4.2.2/lib/jekyll/site.rb:36:in `initialize'
        from C:/tools/ruby31/lib/ruby/gems/3.1.0/gems/jekyll-4.2.2/lib/jekyll/commands/build.rb:30:in `new'
        from C:/tools/ruby31/lib/ruby/gems/3.1.0/gems/jekyll-4.2.2/lib/jekyll/commands/build.rb:30:in `process'
        from C:/tools/ruby31/lib/ruby/gems/3.1.0/gems/jekyll-4.2.2/lib/jekyll/command.rb:91:in `block in process_with_graceful_fail'
        from C:/tools/ruby31/lib/ruby/gems/3.1.0/gems/jekyll-4.2.2/lib/jekyll/command.rb:91:in `each'
        from C:/tools/ruby31/lib/ruby/gems/3.1.0/gems/jekyll-4.2.2/lib/jekyll/command.rb:91:in `process_with_graceful_fail'
        from C:/tools/ruby31/lib/ruby/gems/3.1.0/gems/jekyll-4.2.2/lib/jekyll/commands/serve.rb:86:in `block (2 levels) in init_with_program'
        from C:/tools/ruby31/lib/ruby/gems/3.1.0/gems/mercenary-0.4.0/lib/mercenary/command.rb:221:in `block in execute'        from C:/tools/ruby31/lib/ruby/gems/3.1.0/gems/mercenary-0.4.0/lib/mercenary/command.rb:221:in `each'
        from C:/tools/ruby31/lib/ruby/gems/3.1.0/gems/mercenary-0.4.0/lib/mercenary/command.rb:221:in `execute'
        from C:/tools/ruby31/lib/ruby/gems/3.1.0/gems/mercenary-0.4.0/lib/mercenary/program.rb:44:in `go'
        from C:/tools/ruby31/lib/ruby/gems/3.1.0/gems/mercenary-0.4.0/lib/mercenary.rb:21:in `program'
        from C:/tools/ruby31/lib/ruby/gems/3.1.0/gems/jekyll-4.2.2/exe/jekyll:15:in `<top (required)>'
        from C:/tools/ruby31/bin/jekyll:32:in `load'
        from C:/tools/ruby31/bin/jekyll:32:in `<main>'
~~~

> Just install depedency correctly to running jekyll `gem install REQ_DEPEDENCY`

~~~PowerShell
    PS > gem install jekyll-paginate
    Fetching jekyll-paginate-1.1.0.gem
    Successfully installed jekyll-paginate-1.1.0
    Parsing documentation for jekyll-paginate-1.1.0
    Installing ri documentation for jekyll-paginate-1.1.0
    Done installing documentation for jekyll-paginate after 0 seconds
    1 gem installed

    PS > gem install jekyll-email-protect
    Fetching jekyll-email-protect-1.1.0.gem
    Successfully installed jekyll-email-protect-1.1.0
    Parsing documentation for jekyll-email-protect-1.1.0
    Installing ri documentation for jekyll-email-protect-1.1.0
    Done installing documentation for jekyll-email-protect after 0 seconds
    1 gem installed

    PS > gem install jekyll-target-blank
    Fetching nokogiri-1.13.8-x64-mingw-ucrt.gem
    Fetching jekyll-target-blank-2.0.0.gem
    Successfully installed nokogiri-1.13.8-x64-mingw-ucrt
    Successfully installed jekyll-target-blank-2.0.0
    Parsing documentation for nokogiri-1.13.8-x64-mingw-ucrt
    Installing ri documentation for nokogiri-1.13.8-x64-mingw-ucrt
    Parsing documentation for jekyll-target-blank-2.0.0
    Installing ri documentation for jekyll-target-blank-2.0.0
    Done installing documentation for nokogiri, jekyll-target-blank after 2 seconds
    2 gems installed
~~~

### Running Github-Pages Locally on Windows
1. Download the source files and unzip to whereever directory you want to make changes locally.
2. Open a terminal inside the source folder and use `jekyll serve --incremental --trace`.
3. Open browser and access trough [http://localhost:4000/](http://localhost:4000/) to make it available on a local server and test these changes.

The `--incremental` flag ensures that any changes you make are reflected in your browser in real time and the `--trace` option might be useful for debugging if things break while you are changing the source files.

Once you have personalised and tested the site, you can create a new repo, upload these files and host your website from the repo.

