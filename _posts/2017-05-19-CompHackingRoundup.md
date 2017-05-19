---
layout: post
title: OCaml Compiler Hacking May 2017 - Activity Summaries
tags: ocamllabs events community hackathon
---

Thanks to everyone who joined us for OCaml Compiler Hacking in the (incredibly warm!) Old Library at Pembroke College this week.

Prior to the event, we attempted a temporary update of the ["Things to Work On"](https://github.com/ocamllabs/compiler-hacking/wiki/Things-to-work-on) wiki page, and added some projects needing attention (thank you to Mark Shinwell, David Allsopp and Anil Madhavapeddy). We will go through the list in more detail this month and update the remaining items. If you have any suggestions for compiler projects, please join the discussion on the [mailing list](http://lists.ocaml.org/listinfo/cam-compiler-hacking), or in the [OCaml Discourse Forum](https://discuss.ocaml.org/t/ocaml-compiler-hacking-event/140).

### Newcomers

Christian Lindig brought some of his team from Citrix to discuss OCaml and Opam with the compiler developers from OCaml Labs and Jane Street. XenServer is Citrix's virtualisation platform based on Xen and CentOS. Christian described how their internal set-up at Citrix means they still need to rely on RPM in some areas, but how switching some projects over to Opam has improved their workflow, and overall has been a huge success. The toolstack layer of the XenServer platform is implemented in OCaml, with code available as Opam packages in their [own Opam repository](https://github.com/xapi-project/xs-opam). Other code is available as RPM packages which are released as open source, but are not part of the repository.

Fred is new to OCaml, and spent time reading through the "Getting Started" page, and started looking at the [CAML-DEBUG-SOCKET documentation](https://caml.inria.fr/mantis/view.php?id=6504) item in the Mantis [Junior Jobs](https://caml.inria.fr/mantis/view_all_bug_page.php) list. It's always a great opportunity to work with newcomers to the language, and Fred commented, "The atmosphere there made it a great learning environment for a beginner like me, and so I'm afraid I was getting constantly distracted by new topics I was hearing about and asking questions and pretty much going on every possible tangent that my curiosity led me".

Gabor and Marcello started working on cleaning up their [own Opam packages](https://github.com/xapi-project/xs-opam) in the [main Opam repository](https://github.com/ocaml/opam) and [submitted a PR](https://github.com/ocaml/opam-repository/pull/9206) to remove the relevant outdated packages. Another PR is likely to follow, to update packages used by other members of the OCaml community to their most recent versions.

Edwin isn't new to the OCaml compiler - last year he wrote a [tool](https://github.com/ocaml/ocaml/pull/916) to update the compiler documentation - but decided to dive into OCaml Multicore by tackling an issue to enable the `Domain.join` primitive, and submitted a [PR](https://github.com/ocamllabs/ocaml-multicore/pull/130) for the implementation.

### Compiler Projects

KC and Mark spent some time working on DWARF support for handlers in Multicore, an issue which is scheduled for [Multicore Alpha](https://github.com/ocamllabs/ocaml-multicore/projects/1#card-2897910). They had some initial success and have a prototype implementation which backtraces through the handler stack. This builds on [previous work](http://ocamllabs.io/doc/dwarf-debugging.html) that enabled the native-code OCaml compiler to emit DWARF debugging information.

Stephen and Jeremy spent most of the evening discussing a workshop submission based on subtyping witnesses, and the "hairy bits of OCaml typechecking" related to [PR#556](https://github.com/ocaml/ocaml/pull/556) and [#1142](https://github.com/ocaml/ocaml/pull/1142).

### Bug Fixing

David and Mark worked on closing PRs, including one to tidy up and fix parsing by [ocamlyacc code](https://github.com/ocaml/ocaml/pull/1012) - In David's words "ocamlyacc is due to be retired soon in favour of using Menhir directly in the compiler codebase, but it's still nice for the old dear to get a little love before put out to pasture". Some of the GitHub PRs merged that evening had subsequent issues with Inria's CI, so David followed them up on Wednesday morning.

Mark also started looking at [PR#1063](https://github.com/ocaml/ocaml/pull/1063) to fix dynlinking, but it looks like it will require further investigation since an important part of functionality is currently missing.

### Other projects

Liang continued to increase the flexibility of the OCaml numerical library, [Owl](https://github.com/ryanrhymes/owl), by extending the Algorithmic Differentiation module ([Algodiff](https://github.com/ryanrhymes/owl/wiki/Tutorial:-Algorithmic-Differentiation)) to support N-dimensional array. The AD module calculates the exact derivative of a given function, and is especially useful for fast prototyping in machine learning research. Owl has quite a few users now, and it's great to see contributions from them, and see development influenced by them.

Taka continued work on benchmarking MirageOS performance by writing a script to deploy multiple pairs of unikernels to conduct parallel throughput measurements using [iperf](https://github.com/TImada/mirage_iperf) automatically. He and KC also discussed the idea of doing batched I/O operations using effect handlers to minimise the context switching between VM and Dom0.
