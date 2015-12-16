# jobim

`jobim` is a Clojurescript presentation library, meant for building
simple presentations quickly, out of pure data. It's currently usable
alpha software that should evolve as I make presentations and my needs
change.

The core abstraction of `jobim` is the Slide protocol. `jobim` provides
a few slides to you by default, but anything that implements the protocol
can be rendered. This allows you to create your own custom

Here is what an example presentation can look like.

```clojure
(ns examples.intro
  (:require [jobim.core :as jobim
             :refer [slide-show default-style ->Title
                     ->CaptionedPic ->ClojureCode ->Picture]
             :refer-macros [defshow clojure-code]]
            [cljs.test :refer-macros [deftest is testing run-tests]]))

(defclj code-slide 40
  (def a (+ 1 2))
  (def b (+ a 3))
  (defn c [d] (+ a b d))
  (c 10))

(defshow intro-to-clojure
  default-style
  (->Title
   "Unit Testing In Clojure"
   "Built for the Recurse Center by Sal Becker as a demonstration of Jobim")
  (->CaptionedPic
   "jobim.png"
   "I started naming all my libraries after Brazilian things.")
  code-slide
  (->Picture "meme.png"))
```

One of the coolest features of `jobim` is that it allows you to include
Clojure code as a quoted form, allowing you to use ACTUAL code inside
code examples.

Jobim allows you to write test driven presentations, and to build up certainty that your slides mean what you think they means. Run tests lives, and do live reload, effortlessly!

![jobim live reloading and retesting](https://pbs.twimg.com/media/CWOuIJFUkAIcbY1.png:large)

## Feature Wishlist

* Package management stuff
* A psuedocode macro for stuff you're not testing
* A lein plugin for blazing fast development
* A built in REPL
* Features for more languages

## Setup

Setup information coming as the project achieves more stability. For now,
checkout the examples directory to see running code. A presentation should
be buildable as long as you copy all HTML, CSS, and you run cljsbuild on
some sort of presentation to get it running.

More specific information coming soon.

## License

Copyright © 2015 Salomao Becker 

Distributed under the Eclipse Public License either version 1.0 or (at your option) any later version.
