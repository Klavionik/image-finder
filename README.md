# Similar Images Finder
A CLI utility to find similar/duplicate images using perceptual hashing algorithm. Built 
upon ImageHash library.

## Install
The recommended way to install this package is using [pipx](https://pypa.github.io/pipx). 
The utility and its dependencies will be installed in an isolated virtual environment 
and made available from the terminal.

```shell
$ pipx install git+https://github.com/Klavionik/image-finder.git
```

Another way is to install it via `pip`, but you'll need to activate the venv every time
to run `findimg` command.

```shell
$ python -m venv venv && source venv/bin/activate
$ pip install git+https://github.com/Klavionik/image-finder.git
```

## Usage
```
usage: findimg [-h] [-s SENSITIVITY] [-d DISTANCE] [-e EXCLUDE] [--debug] reference top

positional arguments:
  reference             Path to the reference image.
  top                   Path to the top search directory.

options:
  -h, --help            show this help message and exit
  -s SENSITIVITY, --sensitivity SENSITIVITY
                        Hashing sensitivity (2 - 8). Defaults to 7.
  -d DISTANCE, --distance DISTANCE
                        Max. Hamming distance. Defaults to 0.
  -e EXCLUDE, --exclude EXCLUDE
                        Directories to exclude from search (a comma-separated list).
  --debug               Output debug messages

Find images similar to a given reference image using a perceptual hashing algorithm.
May work even if the search target (or the reference) if cropped, resized, rotated,
color-manipulated etc.

Example:
    Find images similar to ref.png inside /home/user directory.
    $ findimg /home/user/ref.png /home/user

    Find images similar to ref.png inside /home/user directory, excluding "excludeme" and "skipthis" directories.
    $ findimg --exclude excludeme,skipthis /home/user/reference.png /home/user
```