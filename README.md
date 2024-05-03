# neovim-cygwin

This a recipe to build and package [neovim][1] for [Cygwin][2]. The recipe is
based on the [recipe in cascent's old neovim port][3].

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
