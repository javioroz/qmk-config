# qmk-config
Configuration for my plank keyboard (BM40)

## QMK firmware install on linux
rerrequisitos: python y python-pip

```
sudo apt install -y git python3-pip
```

Install the QMK CLI by running:

```
python3 -m pip install --user qmk
```

After installing QMK you can set it up with this command:

```
qmk setup
```

It's possible, that you will get an error saying something like: bash: qmk: command not found. Run this as your user:

```
echo 'PATH="$HOME/.local/bin:$PATH"' >> $HOME/.bashrc && source $HOME/.bashrc
qmk setup
```

Now that your QMK build environment is set up, you can build a firmware for your keyboard. Start by trying to build the keyboard's default keymap. You should be able to do that with a command in this format:

```
qmk compile -kb <keyboard> -km default
```

Replace "keyboard" with your keyboard name. Mine is: bm40hsrgb

When it is done you should have a lot of output that ends similar to this:

```
Linking: .build/bm40hsrgb_default.elf                                                               [OK]
Creating load file for flashing: .build/bm40hsrgb_default.hex                                       [OK]
Copying bm40hsrgb_default.hex to qmk_firmware folder                                                [OK]
Checking file size of bm40hsrgb_default.hex                                                         [OK]
 * The firmware size is fine - 25898/28672 (90%, 2774 bytes free)
```

You can configure your build environment to set the defaults and make working with QMK less tedious. Let's do that now!

Most people new to QMK only have 1 keyboard. You can set this keyboard as your default with the qmk config command. For example, to set your default keyboard to clueboard/66/rev4:

```
qmk config user.keyboard=bm40hsrgb
```

You can also set your default keymap name. Most people use their GitHub username here.

```
qmk config user.keymap=<github_username>
```

To create your own keymap you'll want to create a copy of the default keymap. If you configured your build environment in the last step you can do that easily with the QMK CLI:

```
qmk new-keymap
```

Look at the output from that command, you should see something like this:

```
Ψ orosus keymap directory created in: /home/orosus/qmk_firmware/keyboards/bm40hsrgb/keymaps/orosus
```

This is the location of your new keymap.c file.

```
cd /home/orosus/qmk_firmware/keyboards/bm40hsrgb/keymaps/orosus_km
```

Open your keymap.c file in your text editor and edit the layouts and layers.

See keycodes  here [https://beta.docs.qmk.fm/using-qmk/simple-keycodes/keycodes_basic](https://beta.docs.qmk.fm/using-qmk/simple-keycodes/keycodes_basic)

Or it also can be configured usin QMK config online:

And downloading the JSON file. In this case, you can convert this JSON file to a keymap.c using this command:

```
qmk json2c filename.json
```

## How to flash keyboard the first time
Go to the path where the default keyboard is saved:
```bash
$ cd /home/<user>/qmk_firmware/keyboards/krepublic/bm40hsrgb/keymaps/orosus_km
$ qmk compile
```
Flash the keyboard, for that put the keyboard in RESET mode (Raise+Lower+Q) and run:
```bash
$ qmk flash
## or if you haven't configured any keyboard before:
$ qmk flash -kb <my_keyboard> -km <my_keymap>
## e.g.:
$ qmk flash -kb bm40hsrgb -km orosus_km
``` 

