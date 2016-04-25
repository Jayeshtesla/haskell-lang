haskell-lang
============

[![Build Status](https://travis-ci.org/haskell-lang/haskell-lang.svg?branch=master)](https://travis-ci.org/haskell-lang/haskell-lang)

haskell-lang.org web site.

## Editing pages

If you're just here to contribute a content change, read this section.

All pages that are produced by markdown
[are here](https://github.com/haskell-lang/haskell-lang/tree/master/static/markdown). To
contribute changes simply fork this repo and open a pull request. It
will be merged and redeployed in short order.

If you want to edit a page which has some custom code in it, you'll
want to see the next sections for building and running
instructions. Maybe also take a look at [architecture](#architecture).

If you want to include Haskell code samples in markdown, use:

    ``` haskell
    main = putStrLn "Hello, World!"
    ```

If you want to include Haskell code samples in Haskell code pages,
use:

``` haskell
haskellPre "main = print 123"
haskellCode "peyton `simon` jones"
```

Pre for `<pre>` block, code for `<code>` span snippet.


## Building

Clone the repo:

    $ git clone git@github.com:haskell-lang/haskell-lang.git

Install dependencies and build:

    $ stack build

Done!

### Note on text-icu

If `text-icu` fails to build, you'll want to install the icu dev libraries. The appropriate include/lib directories are configured in the `stack.yaml` already.

#### Mac OS X

```
brew install icu4c
```

#### Ubuntu/Debian

```
$ sudo apt-get install libicu-dev
```


## Running

It runs at: http://localhost:1990/

Manually running the binary:

    $ stack exec haskell-lang

Running from inside GHCi:

    > :l DevelMain
    > DevelMain.update

Run this every time you want to update the web handler in-place, as in
[this demo](https://github.com/chrisdone/ghci-reload-demo).

If you use Emacs, you can just bind it to a key:

``` lisp
(define-key html-mode-map [f12] 'haskell-process-reload-devel-main)
```

Just hit f12 to recompile and restart.

## Architecture

It uses Yesod and an MVC organization.

* HL.Model.* -- [models](https://github.com/haskell-lang/haskell-lang/tree/master/src/HL/Model)
* HL.View.* -- [views](https://github.com/haskell-lang/haskell-lang/tree/master/src/HL/View)
* HL.Controller.* -- [controllers](https://github.com/haskell-lang/haskell-lang/tree/master/src/HL/Controller)

Templates are written in
[Lucid](https://github.com/chrisdone/lucid). There is presently no
database.

## Style

We generally use
[this style](https://github.com/chrisdone/haskell-style-guide)
for this project. You don't have to use this style, we can reformat patches as
they come in.
