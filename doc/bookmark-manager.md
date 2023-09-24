# Bookmark Manager

- [Default Folder](#default-folder)
- [Custom Queries](#custom-queries)

## Default Folder

To set `Bookmark Toolbar` as a default folder in Librewolf (Linux),
add following into `$HOME/.librewolf/librewolf.overrides.cfg`

```js
try {
 let {classes:Cc, interfaces:Ci, manager:Cm, utils:Cu} = Components;
 var Services = globalThis.Services || ChromeUtils.import("resource://gre/modules/Services.jsm").Services;

 function ConfigJS() { Services.obs.addObserver(this, 'chrome-document-global-created', false); }
 ConfigJS.prototype = {
  observe: function (aSubject) { aSubject.addEventListener('DOMContentLoaded', this, {once: true}); },
  handleEvent: function (aEvent) {
   let document = aEvent.originalTarget;
   let window = document.defaultView;
   let location = window.location;
   if (/^(chrome:(?!\/\/(global\/content\/commonDialog|browser\/content\/webext-panels)\.x?html)|about:(?!blank))/i.test(location.href)) {
    if (window._gBrowser) {
      let showPlaces = ["AllBookmarks","BookmarksMenu","BookmarksToolbar","OtherBookmarks"][2];
      elm = document.getElementById("Browser:ShowAllBookmarks");
      if (elm) {
       elm.setAttribute("oncommand", "PlacesCommandHook.showPlacesOrganizer('"+showPlaces+"')");
      }
    }
   }
  }
 };
 if (!Services.appinfo.inSafeMode) { new ConfigJS(); }
} catch(e) {Cu.reportError(e);}
```

[Mozilla Firefox - Manage Bookmarks - Default Folder | Firefox Support Forum | Mozilla Support](https://support.mozilla.org/en-US/questions/1373437)


## Custom Queries

To list 500 most recently added bookmarks, create a bookmark:

Name: Recently Added  
URL: `place:sort=12&maxResults=500&queryType=1`  

An other useful query could be:

Name: Recently Modified  
URL: `place:sort=14&maxResults=500&queryType=1`

Name: Oldest Modified  
URL: `place:sort=13&maxResults=500&queryType=1`

[Places query URIs - Mozilla | MDN](https://developer.mozilla.org.cach3.com/en/Places_query_URIs)

The URLs of that bookmarks are not shown by Firefox Bookmark Manager. The extension [Bookmark Commander](https://addons.mozilla.org/en-US/firefox/addon/bookmarks-commander/) is able to show/edit them.
