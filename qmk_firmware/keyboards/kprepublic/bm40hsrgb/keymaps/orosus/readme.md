# orosus keymap for bm40hsrgb

## Steps

### Install and set it up (once)
$ python3 -m pip install --user qmk
$ qmk setup

### Compile (every time)
$ cd /home/orosus/qmk_firmware/kprepublic/keyboards/bm40hsrgb/keymaps/orosus
$ qmk compile -kb bm40hsrgb -km orosus

### Put keyboard in RESET mode (Raise+Lower+Q) and Flash (every time)
$ qmk flash -kb bm40hsrgb -km orosus

