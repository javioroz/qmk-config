# orosus keymap for bm40hsrgb

## Steps

### Install and set it up (once)
$ python3 -m pip install --user qmk
$ qmk setup

### Go to folder
$ cd /home/orosus/qmk_firmware/keyboards/kprepublic/bm40hsrgb/keymaps/orosus
o
$ cd C:\Users\oroz\qmk_firmware\keyboards\kprepublic\bm40hsrgb\keymaps\orosus

### Compile (every time)
$ qmk compile -kb bm40hsrgb -km orosus

### Put keyboard in RESET mode (Raise+Lower+Q) and Flash (every time)
$ qmk flash -kb bm40hsrgb -km orosus

