# MMM

A web browser written entirely in OCaml, using Tk for its GUI.

MMM was written originally by Francois Rouaix (INRIA Rocquencourt,
projet Cristal) and last released in 1997.

It was forked by Yoann Padioleau in 2024 who took over its maintenance
and modernized the codebase (see `changes.txt` and `authors.txt`).

The old website was https://caml.inria.fr/pub/old_caml_site/~rouaix/mmm/

## Building

### Prerequisites

OCaml 4.14+ (via opam >= 2.1), gcc, git, curl, pkg-config.

On Ubuntu/Debian:
```bash
apt-get install build-essential pkg-config opam curl
```

### Quick start

```bash
git clone --recurse-submodules https://github.com/aryx/mmm
cd mmm
./configure
# Build the vendored Tk bindings:
cd external/ocamltk && ./configure --with-config=./site.config && make && make opt && make install && cd ../..
make
```

### Docker

A reference build using Ubuntu is provided:

```bash
docker build -t mmm .
```

## Usage

```bash
./mmm <url>
```

## Inspiration

MMM is part of [Principia Softwarica](https://github.com/aryx/principia-softwarica),
a series of literate-programming books that explain with full details the source
code of all the essential programs used by a programmer (kernel, shell, compiler,
editor, browser, etc.). The programs chosen for Principia must be small and
elegant enough to explain completely -- MMM, at around 30,000 lines, fits that
criterion while covering all the essential concepts of a web browser: URL
parsing, HTTP protocol, HTML lexing/parsing, CSS layout, incremental rendering,
and even an OCaml applet system.

Other web browsers that were considered as alternatives for the book:

- **[Nexus](https://en.wikipedia.org/wiki/WorldWideWeb)** -- Tim Berners-Lee's original browser (~8,000 LOC in Objective-C). Historically important but too primitive.
- **[Mosaic](https://en.wikipedia.org/wiki/Mosaic_(web_browser))** -- The browser that popularized the Web by adding inline images. At 130,000 LOC, too large compared to MMM's 30,000.
- **[Gecko/Firefox](https://firefox-source-docs.mozilla.org/)** -- Descendant of Mosaic/Netscape. Far too large for a literate programming treatment.
- **[WebKit/Blink](https://webkit.org/)** -- Started from scratch by KDE (KHTML), now used by Safari and Chrome. Also far too large.
- **[NetSurf](https://www.netsurf-browser.org/)** -- A small independent C browser with clean subprojects (Hubbub, LibCSS, LibDOM). A reasonable candidate but still C.
- **[Servo](https://servo.org/)** -- Mozilla's experimental browser in Rust. Interesting architecture but already a large codebase.
