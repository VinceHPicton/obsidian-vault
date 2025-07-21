Submodules don’t follow branches — they follow specific commit SHAs.

Setting `git config submodule.recurse true` will cause command `git submodule update --init --recursive` to always run on a clone or pull

