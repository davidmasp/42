# Terminals

## Mouse paste (windows)

(Improvement point)

In Windows, the paste button in the mouse should be the right click button.
Main reason is that is complicated to do the middle-click in the
trackpad of a laptop.

How to do it in:

### Putty

When you are loaded in a Session, go to:

```txt
Window > Selection > Control use of mouse
```

There, select `Compromise`.


#### How to use `crtl+arrow` in putty

In linux when you press control and arrow in the terminal it goes the full
word instead of changing character by character.

To enable this features in bash you can create a file named `~/.inputrc` 
with the following components:

```
"\eOD": backward-word
"\eOC": forward-word
```

Credit [here](https://superuser.com/a/103097/767632)

I still didn't manage to make it work in the tmux server with PuTTy


### Git bash

Open a git bash window and right-click the top of the window, there select
options:

```txt
1) Mouse (left menu) > Right mouse button -> Paste
2) Mouse (left menu) > Middle mouse button -> Extend
```

### Ubuntu WSL

Should already work as default.

## Appearance

Unifying looks can be challenging. Can differ between platforms and it can
be very taste dependant. You should take these choices as guides, not defaults.

### Accepted list of color schemes

* [base 16 unikitty](https://github.com/joshwlewis/base16-unikitty)

### Forbidden list of color schemes



### Ubuntu WSL

Right click in the terminal and go to defaults.

* Cursor Size: Large
* Font
  * Size: 16
  * Lucida Sans Typewritter
* Colors
  * Opacity: 90%
  * Screen background: `#2e2a31`
