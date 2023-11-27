# Gazou OCR

Gazou is a Japanese and Chinese OCR application written in C++. It utilizes image processing, and other parameters to improve the accuracy. All contributions are welcome.

## Installation

## Building from source

### Dependencies

These dependencies will need to be installed by your system's package manager:

- Qt5 >= 5.10
- Tesseract >= 4.0.0
- Leptonica >= 1.70

Optional dependencies:

- Qt5X11Extras >= 5.10 (for GUI)

### Install

```sh
git clone --recursive https://github.com/kamui-fin/gazou.git
cd gazou
mkdir build
cd build
cmake .. -DGUI=OFF
sudo make install
```

- `jpn`: Japanese
- `chi_sim`: Simplified Chinese
- `chi_trad`: Traditional Chinese

## CLI

Gazou also has a command line mode, and this can be useful for integrating it with bash scripts.
To get the resulting text copied to your clipboard, you can use `xclip`, `wl-copy`, or any clipboard utility you prefer.
Available options include:

```
Usage: gazou [options] imagePath
Launches GUI if no options are provided.

Options:
  -p, --prevscan             Run the OCR on the same coordinates of the
                             previous scan
  -l, --language <language>  Specify OCR language, defaults to jpn. Options:
                             jpn, chi_sim, chi_trad
  -v, --vertical             Switch orientation to vertical. Without this,
                             gazou expects horizontal text.
  --version                  Fetch the version information of gazou
  --help                     View this help menu

Arguments:
  imagePath                  Source image file to OCR
```

### Piping from stdin

You can also run gazou by pipeing an image into the CLI:

```
cat img.png | gazou
```

### Hyprland

To make gazou work with hyprland, simply add these lines to your ~/.config/hypr/hyprland.conf
```
bind = ALT,A,exec, hyprshot -m region -r | gazou | wl-copy 
bind = ALT,D,exec, hyprshot -m region -r | gazou -v | wl-copy
```
