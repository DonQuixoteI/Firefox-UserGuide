# Locking Preferences

[Locking preferences - mozillaZine](http://kb.mozillazine.org/Locking_preferences)

Create an ANSI encoded file `config.js` in your your [installation directory](http://kb.mozillazine.org/Installation_directory), and make the first line start with double forward slashes and desired preferences.

(_Firefox Installation Directory_)`/config.js`:

```js
//
lockPref("network.proxy.type", 0);
```

Create an other lock loading file `config-prefs.js` in the installation subdirectory.

(_Firefox Installation Directory_)`/defaults/pref/config-prefs.js`:

```js
//
pref("general.config.obscure_value", 0);
pref("general.config.filename", "config.js");
```

Restart Firefox and (optionally) check if the status of prefs in `about:config` have been changed to `locked` (appear in _italic_).
