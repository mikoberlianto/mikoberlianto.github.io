---
layout: post
title: Jekyll Secara Lokal Di Windows
description: Running Jekyll Locally for running github-pages on Windows
---

Jekyll adalah generator situs statis. Dibutuhkan teks yang ditulis dalam bahasa markup favorit Anda dan menggunakan tata letak untuk membuat situs web statis. Anda dapat mengubah tampilan dan nuansa situs, URL, data yang ditampilkan di halaman, dan banyak lagi.

# Instalasi
Jekyll adalah [Ruby Gem](https://jekyllrb.com/docs/ruby-101/#gems) yang dapat diinstal pada sebagian besar sistem.

Persyaratan
* [Ruby](https://www.ruby-lang.org/en/downloads/) versi **2.5.0** atau lebih tinggi, termasuk semua header pengembangan (periksa versi Ruby Anda menggunakan `ruby -v`)
* [RubyGems](https://rubygems.org/pages/download) (periksa versi Permata Anda menggunakan `gem -v`)
* [GCC](https://gcc.gnu.org/install/) dan [Make](https://www.gnu.org/software/make/) (periksa versi menggunakan `gcc -v`, `g++ -v`, dan `make -v`)

## Jekyll di Windows
Meskipun Windows bukan platform yang didukung secara resmi, windows dapat digunakan untuk menjalankan Jekyll dengan tweak yang tepat.

### Menginstal Ruby, Gem dan Jekyll
Cara termudah untuk menginstal Ruby dan Jekyll adalah dengan menggunakan [RubyInstaller](https://rubyinstaller.org/) untuk Windows.

RubyInstaller adalah penginstal berbasis Windows mandiri yang mencakup bahasa Ruby, lingkungan eksekusi, dokumentasi penting, dan banyak lagi.

Kami hanya membahas RubyInstaller-2.4 dan yang lebih baru di sini. Versi yang lebih lama perlu menginstal [Devkit secara manual](https://github.com/oneclick/rubyinstaller/wiki/Development-Kit).

1. Unduh dan instal versi **Ruby+Devkit** dari [RubyInstaller Downloads](https://rubyinstaller.org/downloads/). Gunakan opsi default untuk instalasi.
2. Jalankan `ridk install` langkah pada tahap terakhir dari wizard instalasi. Ini diperlukan untuk menginstal permata dengan ekstensi asli. Anda dapat menemukan informasi tambahan mengenai hal ini di [Dokumentasi RubyInstaller](https://github.com/oneclick/rubyinstaller2#using-the-installer-on-a-target-system). Dari opsi pilih `MSYS2 and MINGW development tool chain`.
3. Buka jendela prompt perintah baru dari menu mulai, sehingga perubahan pada `PATH` variabel lingkungan menjadi efektif. Instal Jekyll dan Bundler menggunakan `gem install jekyll bundler`
4. Periksa apakah Jekyll telah diinstal dengan benar: `jekyll -v`

Itu saja, Anda siap menggunakan Jekyll!

## Menjalankan halaman Jekyll dan Statis
* Buat situs Jekyll baru di `./myblog`.
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

* Ubah ke direktori baru Anda. `cd myblog`

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

* Bangun situs dan buat tersedia di server lokal. `bundle exec jekyll serve`

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

> Jika Anda menggunakan Ruby versi 3.0.0 atau lebih tinggi, langkah 5 mungkin gagal. Anda dapat memperbaikinya dengan menambahkan `webrick` ke dependensi Anda: `bundle add webrick`

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


* Telusuri ke [http://localhost:4000](http://localhost:4000)

> Jika ada beberapa kesalahan Dependensi

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

> Cukup instal depedency dengan benar untuk menjalankan jekyll `gem install REQ_DEPEDENCY`

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

### Menjalankan Github-Pages Secara Lokal di Windows
1. Unduh file sumber dan unzip ke direktori mana pun yang Anda inginkan untuk membuat perubahan secara lokal.
2. Buka terminal di dalam folder sumber dan gunakan file `jekyll serve --incremental --trace`.
3. Buka browser dan akses melalui [http://localhost:4000/](http://localhost:4000/) untuk membuatnya tersedia di server lokal dan uji perubahan ini.

Bendera `--incremental` memastikan bahwa setiap perubahan yang Anda buat tercermin di browser Anda secara real time dan opsi `--trace` ini mungkin berguna untuk debugging jika ada yang rusak saat Anda mengubah file sumber.

Setelah Anda mempersonalisasi dan menguji situs, Anda dapat membuat repo baru, mengunggah file-file ini, dan meng-host situs web Anda dari repo.

