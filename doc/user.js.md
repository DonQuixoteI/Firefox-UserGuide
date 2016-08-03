# user.js

## Index

- [Browser Cache](#browser-cache)
- [Extension Signing](#extension-signing)

![Android][Android Logo] - Firefox for Android,
![Debian][Debian Logo] - Firefox for Debian Stable,
![Windows][Windows Logo] - Firefox ESR for MS Windows

[Android Logo]: img/Android.png

[Debian Logo]: img/Debian.png

[Windows Logo]: img/Windows.png

## Browser Cache

```js
user_pref("browser.cache.disk.parent_directory", "R:\TEMP\FirefoxCache");
```
Default: n/a

To use RAM disk for caching is good for systems with big enough RAM.

[mozillaZine](http://kb.mozillazine.org/Browser.cache.disk.parent_directory)

## Extension Signing

```js
user_pref("xpinstall.signatures.required", false);
```
Default: `true` ![Windows][Windows Logo] ![Debian][Debian Logo] ![Android][Android Logo]

[MozillaWiki](https://wiki.mozilla.org/Addons/Extension_Signing)
