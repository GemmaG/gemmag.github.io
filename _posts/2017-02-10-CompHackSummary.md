---
layout: post
title: OCaml Compiler Hacking Feb 2017 - Activity Summaries
tags: ocamllabs events community hackathon
---

Thanks to everyone who joined us for a relaxed but productive evening of [OCaml compiler hacking](https://ocamllabs.github.io/compiler-hacking/) on Tuesday 7th February. We focussed on fixing bugs and tidying up documentation during this session, and we had a high proportion of people who are relatively new to OCaml getting stuck into the internals.

<div>
<img style="float:right; -webkit-transform:rotate(90deg); transform:rotate(90deg);" src="/images/FebCHPembroke.JPG" alt="Olivier, Maxime, David and Fred talk all things compiler" width="200" />
</div>

### Compiler Projects

* Mark Shinwell focussed on the next version of [Flambda](https://blogs.janestreet.com/flambda/).

* Olivier Nicole and Maxime Lesourd continued with their work on a [signatured open command](https://github.com/ocamllabs/compiler-hacking/wiki/Things-to-work-on#signatured-open-command). They didn't quite manage to finish it, but spent some time thinking of the best way to implement it [here](https://github.com/OlivierNicole/ocaml/commits/signatured_open).

### Bug Fixing

* Tadeu Zagallo from [Uber](https://www.uber.com/en-GB/cities/london/) [returned](http://reynard.io/2016/11/16/CompHack.html) with increased OCaml knowledge and found a fix for [printing exceptions that happen within custom printers installed in the OCaml toplevel](https://caml.inria.fr/mantis/view.php?id=7060) (which are currently being swallowed). A PR will be on the way soon for review.

* Marek Bernát from [Metail](http://metail.com/) joined us for the first time to learn more about OCaml, and perused some Mantis bugs. He worked on finding a fix for [expressions ignored by the toplevel and compiler](https://caml.inria.fr/mantis/view.php?id=6604) and prepared a change that issues warnings when the line directive is found in inappropriate positions or with inappropriate arguments. A PR will be incoming soon - this is great progress for a first session, with little prior understanding of the OCaml compiler!

### Documentation

* Dhruv Makwana worked on updating our [compiler documentation](https://github.com/ocamllabs/ocaml-internals/wiki) by starting writing up about the [Parse Tree](https://github.com/ocamllabs/ocaml-internals/wiki/The-Parse-Tree-%28AST%29), and completing the [Source Code](https://github.com/ocamllabs/ocaml-internals/wiki/Source-code) section.

### Other projects

* Frederic Bour worked on some [Merlin](https://github.com/ocaml/merlin) fixes, specifically:
  - Emacs mode rewrite fixes:
    - To do syntax highlighting, merlin-mode checks if tuareg-mode or caml-mode are enabled and use the same mode for highlighting information reported to the user. Mode detection was broken, hence no more colors in Merlin interactions. This is fixed.
    - A simple heuristic determines whether information should be reported in mini-buffer or in a split window: 8 lines or less go into the mini-buffer, anything bigger goes into its own window. Except this check was mostly ignored and everything went to minibuffer.
  - General OCaml-Merlin fixes:
    - When completing an identifier, Merlin didn't put parentheses around operators (e.g when completing `Monad.(>>=)`. Now it checks whether the completion is a qualified operator and add parentheses accordingly.

He also managed to finally track a tricky regression he'd been chasing for some time: When asking for the signature of a module alias or when asking for the type of an expression, Merlin would just refuse to load a module. It turned out to be related to the printing of types in the compiler(!). short-path is a feature that finds the shortest alias that refer to a given type. This is mostly useful with large libraries, such as Core or Async, where canonical names of types can be very long. Previous versions of the compiler would load new modules to look for shorter names, causing [inconsistent behaviors](https://caml.inria.fr/mantis/view.php?id=7134), (depending on modules that are not directly used by the current file).
So a new feature, `Env.without_cmis` prevent the compiler from loading new modules when in "printing mode". This broke Merlin which roughly works this way: read input file, set the printing environment to where the user cursor is, then process the query. So any query requiring the use of new modules would fail. That's no longer the case thanks to `Env.with_cmis` when a module is really needed.

* Christian Lindig and I talked about his plans to use some [OPAM](https://github.com/ocaml/opam) features in his next project at Citrix - Thomas Gazagnaire will follow up.

* Takayuki Imada continued with delving into [MirageOS performance](https://github.com/TImada), specifically looking at if and how server-side virtualisation might be a factor.

* Ciaran Lawlor and Matt Harrison were busy with their Part II projects and preparing for presentations next week. Ciaran is working on incremental parsing under the supervision of Stephen Dolan, whilst Matt's project aims to provide secure, user-controlled sharing of personal data. Matt is supervised by KC Sivaramakrishnan and is linked with the [Databox](http://www.databoxproject.uk/) project.
