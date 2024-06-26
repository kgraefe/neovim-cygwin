# neovim-cygwin

This a recipe to build and package [neovim][1] for [Cygwin][2]. The recipe is
based on the [recipe in cascent's old neovim port][3].


## Looking for a maintainer

I stopped maintaining the Cygwin port of neovim and its dependencies. My
personal goal has always been to get the same experience in Cygwin and Linux
since I'm constantly switching between those two.  While the editor itself
seemed to work fine, a lot of plugins did not and plugins are a vital part of
the neovim experience. However, the time I've been willing to invest has been
exhausted. Therefore I decided to ditch Windows entirely and thus I do not use
Cygwin anymore.

I pushed the scripts I used to generate the Cygwin packages overlay server
directory structure to [Github][neovim-cygwin-package-overlay] in case someone
else wants to pick it up. The generated directory must be served via a normal
HTTP / HTTPS server. I will also keep my server running for another 6 months
(until at least 2024-11-01) to help people explore the current state.

[neovim-cygwin-package-overlay]: https://github.com/kgraefe/neovim-cygwin-package-overlay

## Installation

If things go well I am willing to maintain neovim and its dependencies on the
Cygwin repository. Until then I host the binary packages on a Cygwin package
overlay server at [cygwin.paktolos.net][12] which can be used to install them
with the Cygwin setup tool.

## Building from source

Dependencies:
- pkg-config (from Cygwin)
- cmake (from Cygwin)
- ninja (from Cygwin)
- libuv-devel (from Cygwin)
- libtree-sitter{0,-devel} (from Cygwin)
- libiconv-devel (from Cygwin)
- libintl-devel (from Cygwin)
- gettext-devel (from Cygwin)
- [libmsgpackc{2,-devel}][4]
- [libluv{1,-devel}][5]
- [luajit{,-devel}][6]
- [luajit-lpeg][7]
- [luajit-mpack][8]
- [libunibilium{4,-devel}][9]
- [libtermkey{1,-devel}][10]
- [libvterm{0,-devel}][11]

To build the package install the dependencies and run the following command:
```sh
cygport neovim.cygport download prepare compile install package
```

To install the package you can extract it into the root directory:
```sh
eval "$(cygport neovim.cygport vars PVR)"
tar -C / -xjvf neovim-$PVR.x86_64/dist/neovim/neovim-$PVR.tar.xz
```

[1]: https://neovim.io/
[2]: http://www.cygwin.com/
[3]: https://github.com/cascent/neovim-cygwin/blob/09277e3f76981189a2f15d1dbc2f5a4ab4b6c86f/neovim/neovim.cygport
[4]: https://github.com/kgraefe/msgpack-c-cygwin
[5]: https://github.com/kgraefe/libluv-cygwin
[6]: https://github.com/kgraefe/luajit-cygwin
[7]: https://github.com/kgraefe/luajit-lpeg-cygwin
[8]: https://github.com/kgraefe/luajit-mpack-cygwin
[9]: https://github.com/kgraefe/unibilium-cygwin
[10]: https://github.com/kgraefe/libtermkey-cygwin
[11]: https://github.com/kgraefe/libvterm-cygwin
[12]: https://cygwin.paktolos.net/
