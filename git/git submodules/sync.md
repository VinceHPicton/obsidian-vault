 sync --recursive -- <path>...
           Synchronizes submodules' remote URL configuration setting to the value specified in .gitmodules. It will only affect those submodules which already have a URL entry in .git/config (that is the case when they are initialized
           or freshly added). This is useful when submodule URLs change upstream and you need to update your local repositories accordingly.

           git submodule sync synchronizes all submodules while git submodule sync -- A synchronizes submodule "A" only.

           If --recursive is specified, this command will recurse into the registered submodules, and sync any nested submodules within.