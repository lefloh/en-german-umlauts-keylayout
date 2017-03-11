# English keyboard layout with german umlauts

English keyboard layout and keyBindings with german umlauts for MacOS.

## Keyboard layout

```sh
cp -r en-german-umlauts.bundle ~/Library/Keyboard\ Layouts/
```

This installs a full keyboard layout for current user.
This layout maps german vocals like `alt + a` to `ä`, `alt + s` to `ß` and `alt + e` to `€`.
You have to enable it in `System Preferences -> Keyboard -> Input Sources -> English -> English German Umlauts`.

MacOS won't accept this keyboard layout as default.
In my case some applications are using it, others not.
This can be fixed on MacOS Sierra with following steps:

* Double-check if English with German Umlauts is currently selected.
* `vim ~/Library/Preferences/com.apple.HIToolbox.plist`
* Remove the default fallback from `AppleEnabledInputSources`.
  If there is an `AppleDefaultAsciiInputSource` key, remove it.
* `sudo reboot`  

It's important to follow these steps exactly.
MacOS will instantly restore the plist file if you switch to another application
with default keyboard after editing the file or if you don't reboot with `sudo`.
More information on [Ask Different][ask-different].

I suggest using [Ukelele][ukelele] if you want to create a custom keyboard layout on your own.

## KeyBindings

This is an alternative if you want to easily remap keys on your own without
creating a full keyboard layout.
Unfortunately you can't remap dead keys so `alt + a` is mapped to `ä` but for
`ü` you have to type `alt + u` and `u`.

```sh
# Backup if already present
$ cp ~/Library/KeyBindings/DefaultKeyBinding.dict ~/Library/KeyBindings/DefaultKeyBinding.dict.orig
$ cp DefaultKeyBinding.dict ~/Library/KeyBindings/
```

MacOS will also accept this file written in plist syntax.

More information in [Text System Defaults and Key Bindings][keybindings] and [OS X Notes][osx-notes].

 [ask-different]: http://apple.stackexchange.com/questions/44921
 [ukelele]: http://scripts.sil.org/cms/scripts/page.php?site_id=nrsi&id=ukelele
 [keybindings]: https://developer.apple.com/library/content/documentation/Cocoa/Conceptual/EventOverview/TextDefaultsBindings/TextDefaultsBindings.html
 [osx-notes]: http://osxnotes.net/keybindings.html
