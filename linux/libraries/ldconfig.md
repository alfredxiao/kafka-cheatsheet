This is for managing the library cache. it is automatically run when we use package manager, but for any applications you are developing yourself, you’ll have to manually run the `ldconfig` command.

# Procedures for developing new library
1. testing:
  * export `LD_LIBRARY_PATH` to include a path to your library file
2. installation:
  * add your library file to `/usr/lib*` directory tree
  * create a library config file within `/etc/ld.so.conf.d/` and points to library file location
    - this `/etc/ld.so.conf.d/` is loaded as indicated by `/etc/ld.so.conf` with below line
    - `include /etc/ld.so.conf.d/*.conf`
3. config
  * run `ldconfig` to update library cache such that a linker/loader can find dynamic libraries in the updated library cache
    * the cache is stored as `/etc/ld.so.cache` binary file

# Listing file cache
* `ldconfig -v` Scans all the directories, and prints the directory name, and all the links that are created under it.
* `ldconfig -p` to print current cache (`/etc/ld.so.cache`)

# Process a directory
- `ldconfig -n /path/to/dir`
