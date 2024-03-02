# enget
Shell script utility which can read specific variables (including **arrays** and **associative arrays**) from files
## How-to use
```sh
enget [::]varname [--from source] [--export] [--ensure] [-h]
```
You will typically use this script like this:
```sh
eval $(enget BREW_CACHE --export --ensure)
```
### varname syntax
- use `varname` for standard variable
- use `:varname` for arrays
- use `::varname` for associative arrays

### source options
- `[--from] system` reads/write `/etc/enget/.env` file
- `[--from] user` reads/write `$XDG_CONFIG_HOME/enget/.env` file
- `[--from] local` reads/write `.env` file in current directory

### other options
- `--export` is equivalent to appending `export` at the start of variable declaration (works for arrays and associative arrays as well using `declare -g`)
- `--ensure` will not read variable if `varname` is already present

## Prerequisites
- require `gawk` tool
- tested on `zsh` but should work on `bash` (>=v4) and other shells alike

### Development dependencies
- depend on [ko1nksm/getoptions](ko1nksm/getoptions) for parsing options

# .env syntax
## Standard variables
Simply add in a form of `VAR=str`.
## Array variables
Use `VAR=(item1 item2)` form. Also accept `\` to indicate multiple lines.
## Associative array variables
Use `VAR=([key1]=item1 [key2]=item2)` form. Same for `\` handling.

# Thoughts on future releases
- add enset script (definitely)
- read .yaml or .toml in addition to .env (maybe)