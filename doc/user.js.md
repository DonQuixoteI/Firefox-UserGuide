# user.js

## Index

- [Beacon](#beacon)
- [Browser Cache](#browser-cache)
- [Network](#network)
  - [Cookie](#cookie)
  - [Prefetching](#prefetching)
  - [Proxy](#proxy)
  - [Send Referer](#send-referer)
- [Reports to Mozilla](#reports-to-mozilla)
  - [Crash Report](#crash-report)
  - [Health Report](#health-report)
  - [Telemetry](#telemetry)
    - [Experiments](#experiments)
  - [User Rating Feedback](#user-rating-feedback)
- [Screen Casting](#screen-casting)
- [Safe Browsing](#safe-browsing)
- [Updating](#updating)
  - [Extensions](#extensions-update)
  - [Search Engines](#search-engines-update)
  - [Themes](#themes-update)
  - [Web Apps](#web-apps-update)
- [WebRTC](#webrtc)
  - [Gecko Media Plugins](#gecko-media-plugins)
- [Encrypted Media Extension](#encrypted-media-extension)
- [Auto-Play Animated Image](#auto-play-animated-image)
- [Auto-Play Videos](#auto-play-videos)
- [Extensions](#extensions)
  - [Extension Blocklist](#extension-blocklist)
  - [Extension Signing](#extension-signing)
- [Firefox Account](#firefox-account)
- [Firefox Chat](#firefox-chat)
- [Mozilla Social](#mozilla-social)
- [Hardware](#hardware)
  - [Battery API](#battery-api)
  - [Camera](#camera)
  - [Device Name](#device-name)
  - [Gamepad API](#gamepad-api)
  - [Keyboard API](#keyboard-api)
  - [Network Information API](#network-information-api)
  - [Sensor API](#sensor-api)
  - [Vibration API](#vibration-api)
- [Geolocation](#geolocation)
- [Home Page](#home-page)
  - [Messages on Home Page](#messages-on-home-page)
- [New Tab](#new-tab)
- [Passwords](#passwords)
- [Statistics](#statistics)
  - [Timing](#timing)
  - [Video Stats](#video-stats)
- [Thumbnails](#thumbnails)
- [DOM](#dom)
  - [Clipboard](#clipboard)
  - [Context Menu](#context-menu)
  - [Popup Windows](#popup-windows)
  - [Window](#window)

![Android][Android Logo] - Firefox for Android,
![Debian][Debian Logo] - Firefox for Debian Stable,
![Windows][Windows Logo] - Firefox ESR for MS Windows

[Android Logo]: img/Android.png

[Debian Logo]: img/Debian.png

[Windows Logo]: img/Windows.png

## Beacon

[[Wikipedia](https://en.wikipedia.org/wiki/Web_beacon)]: A web beacon is an object embedded in a web page or email, which unobtrusively (usually invisibly) allows checking that a user has accessed the content. Common uses are email tracking and page tagging for web analytics.

[[MDN](https://developer.mozilla.org/en-US/docs/Web/API/Beacon_API)]: Example use cases of the Beacon API are logging activity and sending analytics data to the server.

```js
user_pref("beacon.enabled", false);
```

Default: `true` ![Windows][Windows Logo] ![Debian][Debian Logo] ![Android][Android Logo]

[Test (Beacon) Performance API](http://mdn.github.io/web-performance/perf-api-support.html)

## Browser Cache

```js
user_pref("browser.cache.disk.parent_directory", "R:\TEMP\FirefoxCache");
```
Default: n/a.
[[mozillaZine](http://kb.mozillazine.org/Browser.cache.disk.parent_directory)]

To use RAM disk for caching is good for systems with big enough RAM.

## Network

[Mozilla networking preferences - MDN](https://developer.mozilla.org/en-US/docs/Mozilla/Preferences/Mozilla_networking_preferences)

### Cookie

```js
user_pref("network.cookie.cookieBehavior", 1);
```

Default: 0 ![Windows][Windows Logo] ![Debian][Debian Logo] ![Android][Android Logo]

0 - allow all cookies,
1 - allow cookie only from the originating server [[mozillaZine](http://kb.mozillazine.org/Network.cookie.cookieBehavior)].

### Prefetching

```js
user_pref("network.prefetch-next", false);
```

Default: `true` ![Windows][Windows Logo] ![Debian][Debian Logo] ![Android][Android Logo]

Link prefetching is a browser mechanism, which utilizes browser idle time to download or prefetch documents that the user might visit in the near future [[MDN](https://developer.mozilla.org/en-US/docs/Web/HTTP/Link_prefetching_FAQ)]. `false` disables link prefetching [[mozillaZine](http://kb.mozillazine.org/Network.prefetch-next)].

```js
user_pref("network.dns.disablePrefetch", true);
```

Default: `false` ![Windows][Windows Logo] ![Debian][Debian Logo] ![Android][Android Logo]. [[MDN](https://developer.mozilla.org/en-US/docs/Web/HTTP/Controlling_DNS_prefetching)] [[mozillaZine](http://kb.mozillazine.org/Network.dns.disablePrefetch)]

```js
user_pref("network.predictor.enabled", false);
```

Default: `true` ![Windows][Windows Logo] ![Debian][Debian Logo] ![Android][Android Logo]

The network predictor (formerly called '[seer](https://wiki.mozilla.org/Privacy/Reviews/Necko)') makes preemptive connections to resources in a page based on cached information. It can also do the same when the user hovers over a link. [[Tor](https://trac.torproject.org/projects/tor/ticket/16625)]

```js
user_pref("network.http.speculative-parallel-limit", 0);
```

Default: 6 ![Windows][Windows Logo] ![Debian][Debian Logo] ![Android][Android Logo]. [[mozilla support](https://support.mozilla.org/en-US/kb/how-stop-firefox-making-automatic-connections#w_speculative-pre-connections)]

### Proxy

```js
user_pref("network.proxy.type", 0);
```

Default: 5 ![Windows][Windows Logo] ![Debian][Debian Logo] ![Android][Android Logo]. [[mozillaZine](http://kb.mozillazine.org/Network.proxy.type)]

### Send Referer

```js
user_pref("network.http.sendRefererHeader", 0);
```

Default: 2 ![Windows][Windows Logo] ![Debian][Debian Logo] ![Android][Android Logo]

0 - never send the referring URL,
1 - send only on clicked links,
2 - send for links and images [[mozillaZine](http://kb.mozillazine.org/Network.http.sendRefererHeader)].

```js
user_pref("network.http.sendSecureXSiteReferrer", false);
```

Default: `true` ![Windows][Windows Logo] ![Debian][Debian Logo] ![Android][Android Logo]. [[mozillaZine](http://kb.mozillazine.org/Network.http.sendSecureXSiteReferrer)]

## Reports to Mozilla

```js
user_pref("datareporting.policy.dataSubmissionEnabled", false);
```

Default: `true` ![Windows][Windows Logo] ![Debian][Debian Logo] ![Android][Android Logo]

This is the data submission master kill switch. If disabled, no policy is shown or upload takes place, ever [[Mozilla Source Tree Docs](https://gecko.readthedocs.io/en/latest/toolkit/components/telemetry/telemetry/preferences.html#data-choices-notification)].

### Crash Report

[[mozilla](https://www.mozilla.org/en-US/privacy/firefox/#crash-reporter)]: You have the option to send Mozilla a crash report after Firefox crashes. This report contains technical information for us to improve Firefox including why Firefox crashed, the active URL at time of crash, and the state of computer memory during the crash. The crash report we receive may include personal information.

[[mozillaZine](http://kb.mozillazine.org/Breakpad#Can_I_disable_Crash_Reporter.3F)]: Mozilla Crash Reporter is enabled by default and there is no user interface to disable it. To disable, open the `application.ini` file in the [installation directory](http://kb.mozillazine.org/Installation_directory), find the entry

```
[Crash Reporter]
Enabled=1
```

and change the **1** to **0**.

```js
user_pref("breakpad.reportURL", "");
```

Default: "https://crash-stats.mozilla.com/report/index/" ![Windows][Windows Logo] ![Debian][Debian Logo] ![Android][Android Logo]

Set of libraries called `Breakpad` handles client-side crash reporting [[mozillaZine](http://kb.mozillazine.org/Breakpad.reportURL)].

### Health Report

[[mozilla](https://www.mozilla.org/en-US/privacy/firefox/#health-report)]: Firefox Health Report is designed to provide you with insights about your browser's stability and performance and with support tips should you experience issues, such as high crash rates or slow startup times. Mozilla collects and aggregates your data with that of other Firefox users and sends it back to your browser so you can see how your Firefox performance changes over time. This data includes, for example: device hardware, operating system, Firefox version, add-ons (count and type), timing of browser events, rendering, session restores, length of session, how old a profile is, count of crashes, and count of pages.

[[What is Firefox Health Report?](https://blog.mozilla.org/metrics/fhr-faq/)] [[What data are collected?](https://blog.mozilla.org/metrics/2012/09/21/firefox-health-report/)]

```js
user_pref("datareporting.healthreport.uploadEnabled", false);
```
Default: `true` ![Windows][Windows Logo], `false` ![Debian][Debian Logo], n/a ![Android][Android Logo]

```js
user_pref("datareporting.healthreport.service.enabled", false);
```

Default: `true` ![Windows][Windows Logo] ![Debian][Debian Logo], n/a ![Android][Android Logo]

```js
user_pref("datareporting.healthreport.documentServerURI", "");
```

Default: "https://fhr.data.mozilla.com/" ![Windows][Windows Logo] ![Debian][Debian Logo], n/a ![Android][Android Logo]

```js
user_pref("datareporting.healthreport.about.reportUrl", "");
```

Default: "https://fhr.cdn.mozilla.net/%LOCALE%/v4/" ![Windows][Windows Logo] ![Debian][Debian Logo], "https://fhr.cdn.mozilla.net/%LOCALE%/mobile/" ![Android][Android Logo]

```js
user_pref("datareporting.healthreport.about.reportUrlUnified", "");
```

Default: "https://fhr.cdn.mozilla.net/%LOCALE%/v4/" ![Windows][Windows Logo] ![Debian][Debian Logo], n/a ![Android][Android Logo]

```js
user_pref("datareporting.healthreport.logging.consoleEnabled", false);
```

Default: `true` ![Windows][Windows Logo] ![Debian][Debian Logo], n/a ![Android][Android Logo]

### Telemetry

[[mozilla](https://www.mozilla.org/en-US/privacy/firefox/#telemetry)]: Telemetry is a feature in Firefox that sends Mozilla usage, performance, and responsiveness statistics about user interface features, memory, and hardware configuration. Your IP address is also collected as a part of a standard web log.

```js
user_pref("toolkit.telemetry.unified", false);
```

Default: `true` ![Windows][Windows Logo] ![Debian][Debian Logo], `false` ![Android][Android Logo]

If `true`: Telemetry is always enabled and recording base data; Telemetry will send additional `main` pings [[Mozilla Source Tree Docs][telemetry-preferences]].

[telemetry-preferences]: https://gecko.readthedocs.io/en/latest/toolkit/components/telemetry/telemetry/preferences.html#id1

```js
user_pref("toolkit.telemetry.enabled", false);
```

Default: `false` ![Windows][Windows Logo] ![Debian][Debian Logo] ![Android][Android Logo]

If `unified` is off, this controls whether the Telemetry module is enabled; if `unified` is on, this controls whether to record extended data [[Mozilla Source Tree Docs][telemetry-preferences]].

```js
user_pref("toolkit.telemetry.server", "");
```

Default: "https://incoming.telemetry.mozilla.org" ![Windows][Windows Logo] ![Debian][Debian Logo] ![Android][Android Logo]

The server Telemetry pings are sent to [[Mozilla Source Tree Docs][telemetry-preferences]].

#### Experiments

Experiments are available to anyone who has Telemetry enabled [[mozilla wiki](https://wiki.mozilla.org/Telemetry/Experiments)].

```js
user_pref("experiments.supported", false);
```

Default: `true` ![Windows][Windows Logo] ![Debian][Debian Logo], n/a ![Android][Android Logo]

```js
user_pref("experiments.enabled", false);
```

Default: `true` ![Windows][Windows Logo] ![Debian][Debian Logo], n/a ![Android][Android Logo]

```js
user_pref("experiments.manifest.uri", "");
```

Default: "https://telemetry-experiment.cdn.mozilla.net/manifest/v1/firefox/%VERSION%/%CHANNEL%" ![Windows][Windows Logo] ![Debian][Debian Logo], n/a ![Android][Android Logo]

```js
user_pref("experiments.activeExperiment", false);
```

Default: `true` ![Windows][Windows Logo] ![Debian][Debian Logo], n/a ![Android][Android Logo]

[[mozilla wiki](https://wiki.mozilla.org/QA/Telemetry/AboutPreferences "QA/Telemetry/AboutPreferences")]

```js
user_pref("network.allow-experiments", false);
```

Default: `true` ![Windows][Windows Logo] ![Debian][Debian Logo] ![Android][Android Logo].

`true` grants permission for mozilla to silently "opt a user's browser" into participating in A/B tests, user behavior profiling tests, etc. [[Tor](https://trac.torproject.org/projects/tor/ticket/13170)].

### User Rating Feedback

[Firefox Heartbeat](https://wiki.mozilla.org/Advocacy/heartbeat)

```js
user_pref("browser.selfsupport.url", "");
```

Default: `https://self-repair.mozilla.org/%LOCALE%/repair` ![Windows][Windows Logo] ![Debian][Debian Logo], n/a ![Android][Android Logo]

## Safe Browsing

The Safe Browsing feature in Firefox has been renamed to Phishing Protection, but it's still known as Safe Browsing internally [[mozilla wiki](https://wiki.mozilla.org/Phishing_Protection)].

```js
user_pref("browser.safebrowsing.enabled", false);
```

Default: `true` ![Windows][Windows Logo] ![Debian][Debian Logo] ![Android][Android Logo].
[[mozillaZine](http://kb.mozillazine.org/Browser.safebrowsing.enabled)]

```js
user_pref("browser.safebrowsing.malware.enabled", false);
```

Default: `true` ![Windows][Windows Logo] ![Debian][Debian Logo] ![Android][Android Logo].

`false`: do not download malware blacklists and do not check user downloads [[mozillaZine](http://kb.mozillazine.org/Browser.safebrowsing.malware.enabled)]. [[mozilla support](https://support.mozilla.org/en-US/kb/how-does-phishing-and-malware-protection-work "How does built-in Phishing and Malware Protection")]

```js
user_pref("browser.safebrowsing.downloads.enabled", false);
```
Default: `true` ![Windows][Windows Logo] ![Debian][Debian Logo], `false` ![Android][Android Logo]

It enables/disables application reputation checks for downloaded files [[mozilla wiki](https://wiki.mozilla.org/Security/Application_Reputation "Application Reputation")].
`true` does only the local checks against a blacklist and a whitelist, as long as `browser.safebrowsing.downloads.remote.enabled` is disabled [[pyllyukko](https://github.com/pyllyukko/user.js/pull/65)].

```js
user_pref("browser.safebrowsing.downloads.remote.enabled", false);
```

Default: `true` ![Windows][Windows Logo] ![Debian][Debian Logo], `false` ![Android][Android Logo]

`false` disables application reputation remote lookups, but leaves other Safebrowsing malware protection intact [[mozilla wiki](https://wiki.mozilla.org/Security/Features/Application_Reputation_Design_Doc#How_to_turn_off_this_feature "Application Reputation Design Doc")].

[[GOV.UK](https://www.gov.uk/government/publications/browser-security-guidance-mozilla-firefox/browser-security-guidance-mozilla-firefox#enterprise-considerations "Browser Security Guidance: Mozilla Firefox - GOV.UK")]: Firefox uses Google's Safe Browsing service that aims to protect against phishing websites and malicious downloads. It works by sending hashes of some visited website addresses to Google. If Google reports that the page is unsafe, the page or file will not be downloaded or displayed to protect the user against malware and data theft. Google states that it cannot derive the full website addresses from the information submitted as it only sends a partial URL fingerprint. Full website addresses are only sent if an organisation chooses to configure Chrome to send usage statistics to Google. Safe Browsing can be disabled entirely if the trade-off between privacy and security is not acceptable.

```js
user_pref("privacy.trackingprotection.enabled", false);
```

Default: `false` ![Windows][Windows Logo] ![Debian][Debian Logo] ![Android][Android Logo] [[mozilla wiki](https://wiki.mozilla.org/Security/Tracking_protection)] [[mozilla support](https://support.mozilla.org/en-US/kb/tracking-protection-firefox)]

## Screen Casting

Firefox contains a "Send Video To Device" feature to send HTML5 video content to a Roku, Chromecast or similar device in the same network. In order to discover and pair with such a device, Firefox will send SSDP packages to the local network (multicast address 239.255.255.250:1900) [[mozilla support](https://support.mozilla.org/en-US/kb/how-stop-firefox-making-automatic-connections#w_send-video-to-device)].

```js
user_pref("browser.casting.enabled", false);
```

Default: `false` ![Windows][Windows Logo] ![Debian][Debian Logo], `true` ![Android][Android Logo]

## Updating

[[Disable Updater - MDN](https://developer.mozilla.org/en-US/docs/Mozilla/Firefox/Enterprise_deployment#Example_configuration_file)]

```js
user_pref("app.update.enabled", false);
```

Default: `true` ![Windows][Windows Logo], `false` ![Debian][Debian Logo] ![Android][Android Logo].
[[mozillaZine](http://kb.mozillazine.org/App.update.enabled)]

```js
user_pref("app.update.auto", false);
```

Default: `true` ![Windows][Windows Logo] ![Debian][Debian Logo], n/a ![Android][Android Logo]. [[mozillaZine](http://kb.mozillazine.org/App.update.auto)]

```js
user_pref("app.update.service.enabled", false);
```

Default: `true` ![Windows][Windows Logo], n/a ![Debian][Debian Logo] ![Android][Android Logo].
[[Windows Service Silent Update - mozilla wiki](https://wiki.mozilla.org/Windows_Service_Silent_Update)]

### Extensions Update

[[Mozilla Add-ons Blog](https://blog.mozilla.org/addons/how-to-opt-out-of-add-on-metadata-updates/)]: Firefox asks the [Mozilla Add-ons gallery](https://addons.mozilla.org/) for information about the add-ons you have installed once a day. This involves sending the identifiers of each add-on you have installed to Mozilla, as well as information on how long it last took Firefox to start up. Opting out of this daily ping will stop Firefox from sending the add-ons you have installed and most recent start-up time to Mozilla, and will also stop displaying updated metadata for your add-ons and discontinue personalized recommendations if they were displayed in the Get Add-ons pane of the Add-ons Manager. To opt out, set `extensions.getAddons.cache.enabled` to `false`.

```js
user_pref("extensions.getAddons.cache.enabled", false);
```

Default: `true` ![Windows][Windows Logo] ![Debian][Debian Logo] ![Android][Android Logo]

```js
user_pref("extensions.update.enabled", false);
```

Default: `true` ![Windows][Windows Logo] ![Debian][Debian Logo] ![Android][Android Logo]. [[mozillaZine](http://kb.mozillazine.org/About:config_entries#Extensions.)]

```js
user_pref("extensions.update.autoUpdateDefault", false);
```

Default: `true` ![Windows][Windows Logo] ![Debian][Debian Logo], n/a ![Android][Android Logo]. [[mozilla support](https://support.mozilla.org/en-US/questions/952162 "Difference between extensions.update.autoUpdateDefault and extensions.update.enabled")]

```js
user_pref("extensions.autoupdate.enabled", false);
```

Default: n/a ![Windows][Windows Logo] ![Debian][Debian Logo], `true` ![Android][Android Logo]. [[Blog](http://starkravingfinkle.org/blog/2010/05/updating-add-ons-in-firefox-mobile-1-1/ "Updating Add-ons in Firefox Mobile 1.1")]

### Search Engines Update

```js
user_pref("browser.search.update", false);
```

Default: `true` ![Windows][Windows Logo] ![Debian][Debian Logo], `false` ![Android][Android Logo]

`false`: do not automatically check for updates to search plugins [[mozillaZine](http://kb.mozillazine.org/About:config_entries#Browser.)].

### Themes Update

```js
user_pref("lightweightThemes.update.enabled", false);
```

Default: `true` ![Windows][Windows Logo] ![Debian][Debian Logo], `false` ![Android][Android Logo]. [[mozillaZine](http://kb.mozillazine.org/Themes#Lightweight_theme)]

### Web Apps Update

[[Web Application - Wikipedia](https://en.wikipedia.org/wiki/Web_application)]
[[MDN](https://developer.mozilla.org/en-US/Apps)]

```js
user_pref("app.update.autodownload", "disabled");
```
Default: n/a ![Windows][Windows Logo] ![Debian][Debian Logo], "wifi" ![Android][Android Logo]

```js
user_pref("app.update.url.android", "");
```

Default: n/a ![Windows][Windows Logo] ![Debian][Debian Logo], "https://aus5.mozilla.org/update/4/%PRODUCT%/%VERSION%/%BUILD_ID%/%BUILD_TARGET%/%LOCALE%/%CHANNEL%/%OS_VERSION%/%DISTRIBUTION%/%DISTRIBUTION_VERSION%/%MOZ_VERSION%/update.xml") ![Android][Android Logo]

## WebRTC

[[MDN](https://developer.mozilla.org/en-US/docs/Web/Guide/API/WebRTC)]: WebRTC (Web Real Time Communications) is a technology that enables audio/video streaming and data sharing between browser clients (peers). WebRTC provides the ability to share application data and perform teleconferencing peer to peer, without the need to install plug-ins or third-party software.

```js
user_pref("media.navigator.enabled", false);
user_pref("media.peerconnection.enabled", false);
```

Default: `true` ![Windows][Windows Logo] ![Debian][Debian Logo] ![Android][Android Logo]. [[mozilla wiki](https://wiki.mozilla.org/Media/getUserMedia)]

WebRTC Leak Tests:

- [privacytools.io](https://www.privacytools.io/webrtc.html)
- [diafygi.github.io](https://diafygi.github.io/webrtc-ips/)
- [browserleaks.com](https://www.browserleaks.com/webrtc)

### Gecko Media Plugins

Gecko Media Plugins (GMPs) is a special purpose extension point for authorised 3rd party codecs and EME (Encrypted Media Extensions) CDMs (Content Decryption Modules) [[mozilla wiki](https://wiki.mozilla.org/GeckoMediaPlugins)].

```js
user_pref("media.gmp-provider.enabled", false);
```

Default: `true` ![Windows][Windows Logo] ![Debian][Debian Logo] ![Android][Android Logo]

`false` removes OpenH264 codec from the Plugins list.

The OpenH264 codec is not distributed with Firefox but gets downloaded at the first start of Firefox. In case you want to prohibit that, you will have to set the `media.gmp-gmpopenh264.enabled` and `media.gmp-gmpopenh264.autoupdate` to `false`  [[mozilla support](https://support.mozilla.org/en-US/kb/how-stop-firefox-making-automatic-connections#w_openh264-codec)].

```js
user_pref("media.gmp-gmpopenh264.enabled", false);
```
Default: n/a (hidden pref) ![Windows][Windows Logo] ![Android][Android Logo], `false` ![Debian][Debian Logo]

```js
user_pref("media.gmp-gmpopenh264.autoupdate", false);
```
Default: n/a (hidden pref) ![Windows][Windows Logo] ![Debian][Debian Logo] ![Android][Android Logo]

The installed codec is stored in `<Profile>/gmp-gmpopenh264/` and can be deleted.

```js
user_pref("media.gmp-manager.url", "http://localhost/media-dummy/gmpmanager");
```

Default: "https://aus5.mozilla.org/update/3/GMP/%VERSION%/%BUILD_ID%/%BUILD_TARGET%/%LOCALE%/%CHANNEL%/%OS_VERSION%/%DISTRIBUTION%/%DISTRIBUTION_VERSION%/update.xml" ![Windows][Windows Logo] ![Debian][Debian Logo] ![Android][Android Logo]

```js
user_pref("media.gmp-manager.url.override", "http://localhost/dummy-gmp-manager.xml");
```

Default: n/a ![Windows][Windows Logo] ![Android][Android Logo], "data:text/plain," ![Debian][Debian Logo]

```js
user_pref("media.gmp-manager.cert.checkAttributes", false);
user_pref("media.gmp-manager.cert.requireBuiltIn", false);
```

Default: `true` ![Windows][Windows Logo] ![Debian][Debian Logo] ![Android][Android Logo]

## Encrypted Media Extension

[[What is EME?](https://hsivonen.fi/eme/)]
[[Mozilla Hacks](https://hacks.mozilla.org/2014/05/reconciling-mozillas-mission-and-w3c-eme/)]
[[W3C](https://w3c.github.io/encrypted-media/)]

```js
user_pref("media.eme.enabled", false);
user_pref("media.eme.apiVisible", false);
```

Default: `true` ![Windows][Windows Logo] ![Debian][Debian Logo], n/a ![Android][Android Logo]

```js
user_pref("browser.eme.ui.enabled", false);
```

Default: `true` ![Windows][Windows Logo], `false` ![Debian][Debian Logo], n/a ![Android][Android Logo]

```js
user_pref("media.gmp-eme-adobe.enabled", false);
```

Default: `true` ![Windows][Windows Logo], n/a ![Debian][Debian Logo] ![Android][Android Logo]

## Auto-Play Animated Image

```js
user_pref("image.animation_mode", "none");
```

Default: "normal" ![Windows][Windows Logo] ![Debian][Debian Logo] ![Android][Android Logo]

`none`: animated images will never play [[mozillaZine](http://kb.mozillazine.org/Firefox_:_Tips_:_Animated_Images)].

## Auto-Play Videos

```js
user_pref("media.autoplay.enabled", false);
```

Default: `true` ![Windows][Windows Logo] ![Debian][Debian Logo] ![Android][Android Logo]. [[ghacks.net](http://www.ghacks.net/2016/05/06/how-to-stop-auto-playing-videos/)]

## Extensions

### Extension Blocklist

```js
user_pref("extensions.blocklist.enabled", false);
```

Default: `true` ![Windows][Windows Logo] ![Debian][Debian Logo] ![Android][Android Logo]

Firefox periodically retrieves a blocklist from the Mozilla server. `false`: Do not retrieve a blocklist and do not restrict extension installation [[mozillaZine](http://kb.mozillazine.org/Extensions.blocklist.enabled)].

### Extension Signing

```js
user_pref("xpinstall.signatures.required", false);
```
Default: `true` ![Windows][Windows Logo] ![Debian][Debian Logo] ![Android][Android Logo]. [[mozilla wiki](https://wiki.mozilla.org/Addons/Extension_Signing)]

## Firefox Account

[Firefox Accounts - Mozilla | MDN](https://developer.mozilla.org/en-US/docs/Mozilla/Tech/Firefox_Accounts)

```js
user_pref("identity.fxaccounts.auth.uri", "");
```

Default: "https://api.accounts.firefox.com/v1" ![Windows][Windows Logo] ![Debian][Debian Logo] ![Android][Android Logo]

```js
user_pref("identity.fxaccounts.remote.force_auth.uri", "");
```

Default: "https://accounts.firefox.com/force_auth?service=sync&context=fx_desktop_v2" ![Windows][Windows Logo] ![Debian][Debian Logo], n/a ![Android][Android Logo]

```js
user_pref("identity.fxaccounts.remote.signin.uri", "");
```

Default: "https://accounts.firefox.com/signin?service=sync&context=fx_desktop_v2" ![Windows][Windows Logo] ![Debian][Debian Logo], n/a ![Android][Android Logo]

```js
user_pref("identity.fxaccounts.remote.signup.uri", "");
```

Default: "https://accounts.firefox.com/signup?service=sync&context=fx_desktop_v2" ![Windows][Windows Logo] ![Debian][Debian Logo], n/a ![Android][Android Logo]

```js
user_pref("identity.fxaccounts.settings.uri", "");
```

Default: "https://accounts.firefox.com/settings" ![Windows][Windows Logo] ![Debian][Debian Logo], n/a ![Android][Android Logo]

```js
user_pref("services.sync.engine.addons", false);
user_pref("services.sync.engine.bookmarks", false);
user_pref("services.sync.engine.history", false);
user_pref("services.sync.engine.passwords", false);
user_pref("services.sync.engine.prefs", false);
user_pref("services.sync.engine.tabs", false);
```

Default: `true` ![Windows][Windows Logo] ![Debian][Debian Logo], n/a ![Android][Android Logo]

```js
user_pref("services.sync.serverURL", "");
```

Default: "https://auth.services.mozilla.com/" ![Windows][Windows Logo] ![Debian][Debian Logo], n/a ![Android][Android Logo]

## Firefox Chat

```js
user_pref("loop.enabled", false);
```

Default: `false` ![Debian][Debian Logo], n/a ![Windows][Windows Logo] ![Android][Android Logo]

Firefox Hello (code name Loop) is video and voice chat feature built into the browser.
[[mozilla wiki](https://wiki.mozilla.org/Loop)]

## Mozilla Social

[Social API](https://developer.mozilla.org/en-US/docs/Mozilla/Projects/Social_API)

```js
user_pref("social.directories", "");
```

Default: "https://activations.cdn.mozilla.net" ![Windows][Windows Logo] ![Debian][Debian Logo] ![Android][Android Logo]

```js
user_pref("social.remote-install.enabled", false);
```

Default: `true` ![Windows][Windows Logo] ![Debian][Debian Logo] ![Android][Android Logo]

```js
user_pref("social.shareDirectory", "");
```

Default: "https://activations.cdn.mozilla.net/sharePanel.html" ![Windows][Windows Logo] ![Debian][Debian Logo], n/a ![Android][Android Logo]

```js
user_pref("social.share.activationPanelEnabled", false);
```

Default: `true` ![Windows][Windows Logo] ![Debian][Debian Logo], n/a ![Android][Android Logo]

```js
user_pref("social.toast-notifications.enabled", false);
```

Default: `true` ![Windows][Windows Logo] ![Debian][Debian Logo] ![Android][Android Logo]

```js
user_pref("social.whitelist", "");
```

Default: "https://mozsocial.cliqz.com" ![Windows][Windows Logo] ![Debian][Debian Logo] ![Android][Android Logo]

## Hardware

### Battery API

[[BatteryManager - MDN](https://developer.mozilla.org/en-US/docs/Web/API/BatteryManager)]

```js
user_pref("dom.battery.enabled", false);
```

Default: `true` ![Windows][Windows Logo] ![Debian][Debian Logo] ![Android][Android Logo].
[[TechCrunch](https://techcrunch.com/2015/08/04/battery-attributes-can-be-used-to-track-web-users/)]

### Camera

```js
user_pref("device.camera.enabled", false);
```

Default: n/a ![Windows][Windows Logo] ![Debian][Debian Logo], `true` ![Android][Android Logo]

```js
user_pref("camera.control.face_detection.enabled", false);
```

Default: `true` ![Windows][Windows Logo] ![Debian][Debian Logo] ![Android][Android Logo]

### Device Name

```js
user_pref("dom.presentation.device.name", "dummy-device");
```

Default: n/a ![Windows][Windows Logo] ![Debian][Debian Logo] ![Android][Android Logo]

_Note_: Firefox for Android sets name of your device. [[Bug 1265275]](https://bugzilla.mozilla.org/show_bug.cgi?id=1265275)

### Gamepad API

[[MDN](https://developer.mozilla.org/en-US/docs/Web/API/Gamepad_API/Using_the_Gamepad_API)] [[W3C](https://www.w3.org/TR/gamepad/)]

```js
user_pref("dom.gamepad.enabled", false);
```

Default: `true` ![Windows][Windows Logo] ![Debian][Debian Logo] ![Android][Android Logo]

### Keyboard API

[[KeyboardEvent.code - MDN](https://developer.mozilla.org/en-US/docs/Web/API/KeyboardEvent/code)]

```js
user_pref("dom.keyboardevent.code.enabled", false);
```

Default: `true` ![Windows][Windows Logo] ![Debian][Debian Logo] ![Android][Android Logo]. [[Privacy-Handbuch.de](https://www.privacy-handbuch.de/handbuch_21v.htm) (in German)]

### Network Information API

[[Network Information API - MDN](https://developer.mozilla.org/en-US/docs/Web/API/Network_Information_API)]

```js
user_pref("dom.netinfo.enabled", false);
```

Default: `false` ![Windows][Windows Logo] ![Debian][Debian Logo], `true` ![Android][Android Logo]. [[wicg.io](https://wicg.github.io/netinfo/)]

### Sensor API

[[Sensor API - mozilla wiki](https://wiki.mozilla.org/Sensor_API)]

```js
user_pref("device.sensors.enabled", false);
```

Default: `true` ![Windows][Windows Logo] ![Debian][Debian Logo] ![Android][Android Logo]

### Vibration API

[[Vibration API - W3C](https://w3c.github.io/vibration/)]

```js
user_pref("dom.vibrator.enabled", false);
```

Default: `true` ![Windows][Windows Logo] ![Debian][Debian Logo] ![Android][Android Logo]

## Geolocation

```js
user_pref("geo.enabled", false);
```

Default: `true` ![Windows][Windows Logo] ![Debian][Debian Logo] ![Android][Android Logo]. [[mozilla](https://www.mozilla.org/en-US/firefox/geolocation/)]

```js
user_pref("geo.wifi.uri", "https://127.0.0.1");
```

Default: "https://www.googleapis.com/geolocation/v1/geolocate?key=%GOOGLE_API_KEY%" ![Windows][Windows Logo] ![Debian][Debian Logo], n/a ![Android][Android Logo]

The information around you (mac addresses, signal strengths, SSIDs and etc.) is transmitted to Google Location Services in order to locate you [[stackoverflow](http://stackoverflow.com/a/5134619)].

[Geolocation Test](http://html5demos.com/geo)

```js
user_pref("browser.search.geoip.url", "");
```

Default: "https://location.services.mozilla.com/v1/country?key=%MOZILLA_API_KEY%" ![Windows][Windows Logo] ![Debian][Debian Logo] ![Android][Android Logo]. [[mozilla support](https://support.mozilla.org/en-US/kb/how-stop-firefox-making-automatic-connections#w_geolocation-for-default-search-engine)]

```js
user_pref("browser.search.geoSpecificDefaults", false);
```

Default: `true` ![Windows][Windows Logo] ![Android][Android Logo], `false` ![Debian][Debian Logo]. [[ghacks](http://www.ghacks.net/2015/08/18/a-comprehensive-list-of-firefox-privacy-and-security-settings/)]

## Home Page

```js
user_pref("browser.startup.homepage", "about:blank");
```

Default: "about:home" ![Windows][Windows Logo] ![Debian][Debian Logo], n/a ![Android][Android Logo]

[[mozilla wiki](https://wiki.mozilla.org/Firefox/Projects/Firefox_Start/Snippet_Service)]:
`about:home` fetches content from the production snippets service once every 24 hours. If content is available, it gets is stashed in local storage for the page and displayed from there until the next fetch. If no content is available, the browser has a built-in default set of snippets for display.

```js
user_pref("browser.startup.homepage_override.mstone", "ignore");
```

Default: n/a ![Windows][Windows Logo] ![Debian][Debian Logo] ![Android][Android Logo]

This preference is examined during browser start up. If its value differs from the browser's current milestone, then Firefox connects and fetches content from Mozilla snippets server. `ignore`: the browser's homepage will not be overridden after updates [[mozillaZine](http://kb.mozillazine.org/Browser.startup.homepage_override.mstone)]. _Note_: Firefox for Android overrides this user preference and set it to actual Firefox version?!

```js
user_pref("browser.aboutHomeSnippets.updateUrl", "https://127.0.0.1");
```

Default: "https://snippets.cdn.mozilla.net/%STARTPAGE_VERSION%/%NAME%/%VERSION%/%APPBUILDID%/%BUILD_TARGET%/%LOCALE%/%CHANNEL%/%OS_VERSION%/%DISTRIBUTION%/%DISTRIBUTION_VERSION%/"
![Windows][Windows Logo] ![Debian][Debian Logo],
n/a ![Android][Android Logo]. [[mozilla wiki](https://wiki.mozilla.org/Firefox/Projects/Firefox_Start/Snippet_Service)]

### Messages on Home Page

[How to stop Firefox messages on home screen?](https://support.mozilla.org/en-US/questions/1035229)

```js
user_pref("browser.snippets.enabled", false);
user_pref("browser.snippets.firstrunHomepage.enabled", false);
user_pref("browser.snippets.syncPromo.enabled", false);
```

Default: n/a ![Windows][Windows Logo] ![Debian][Debian Logo],
`true` ![Android][Android Logo]

```js
user_pref("browser.snippets.updateUrl", "https://127.0.0.1");
```

Default: n/a ![Windows][Windows Logo] ![Debian][Debian Logo],
"https://snippets.cdn.mozilla.net/json/%SNIPPETS_VERSION%/%NAME%/%VERSION%/%APPBUILDID%/%BUILD_TARGET%/%LOCALE%/%CHANNEL%/%OS_VERSION%/%DISTRIBUTION%/%DISTRIBUTION_VERSION%/" ![Android][Android Logo]

```js
user_pref("browser.snippets.statsUrl", "https://127.0.0.1");
```

Default: n/a ![Windows][Windows Logo] ![Debian][Debian Logo],
"https://snippets-stats.mozilla.org/mobile" ![Android][Android Logo]

```js
user_pref("browser.snippets.geoUrl", "https://127.0.0.1");
```

Default: n/a ![Windows][Windows Logo] ![Debian][Debian Logo],
"https://location.services.mozilla.com/v1/country?key=..." ![Android][Android Logo]

## New Tab

```js
user_pref("browser.newtabpage.introShown", true);
```

Default: `false` ![Windows][Windows Logo] ![Debian][Debian Logo], n/a ![Android][Android Logo]

```js
user_pref("browser.newtabpage.enabled", false);
user_pref("browser.newtabpage.enhanced", false);
```

Default: `true` ![Windows][Windows Logo] ![Debian][Debian Logo], n/a ![Android][Android Logo]

Setting `enabled` and `enhanced` to `false` disables top and suggested sites (equivalent to blank page).

```js
user_pref("browser.newtabpage.directory.source", "data:text/plain,{}");
```

Default: "https://tiles.services.mozilla.com/v3/links/fetch/%LOCALE%/%CHANNEL%" ![Windows][Windows Logo] ![Debian][Debian Logo], n/a ![Android][Android Logo]. [[Mozilla Source Tree Docs](http://gecko.readthedocs.io/en/latest/browser/browser/DirectoryLinksProvider.html#browser-newtabpage-directory-source)]

```js
user_pref("browser.newtabpage.directory.ping", "");
```

Default: "https://tiles.services.mozilla.com/v3/links/" ![Windows][Windows Logo] ![Debian][Debian Logo], n/a ![Android][Android Logo]. [[Mozilla Source Tree Docs](http://gecko.readthedocs.io/en/latest/browser/browser/DirectoryLinksProvider.html#browser-newtabpage-directory-ping)]

## Passwords

[[Password Manager - mozillaZine](http://kb.mozillazine.org/Password_Manager)]
[[Master Password - mozilla support](https://support.mozilla.org/en-US/kb/use-master-password-protect-stored-logins)]

```js
user_pref("signon.rememberSignons", false);
```

Default: `true` ![Windows][Windows Logo] ![Debian][Debian Logo] ![Android][Android Logo]

`false`: Disable the Password Manager [[mozillaZine](http://kb.mozillazine.org/About:config_entries#Signon.)].

```js
user_pref("signon.autofillForms", false);
```

Default: `true` ![Windows][Windows Logo] ![Debian][Debian Logo] ![Android][Android Logo]

`false`: Do not automatically fill sign-in forms with known usernames and passwords [[mozillaZine](http://kb.mozillazine.org/Signon.autofillForms)].

```js
user_pref("signon.storeWhenAutocompleteOff", false);
```

Default: `true` ![Windows][Windows Logo] ![Debian][Debian Logo] ![Android][Android Logo]

`false`: Do not ignore [`autocomplete=off` form feature](http://www.w3schools.com/tags/att_input_autocomplete.asp) that some websites use to prevent password storing or automatic fill out into sign-on forms, in other words, Firefox Password Manager (if it is enabled) will be not used on that websites. [[Mozilla Bugzilla](https://bugzilla.mozilla.org/show_bug.cgi?id=956906)]

## Statistics

### Timing

[[NavigationTimingAPI - mozilla wiki](https://wiki.mozilla.org/Security/Reviews/Firefox/NavigationTimingAPI)]
[[Navigation Timing - W3C](http://www.w3.org/TR/2011/CR-navigation-timing-20110315/#nt-navigation-timing-interface)]

```js
user_pref("dom.enable_performance", false);
```

Default: `true` ![Windows][Windows Logo] ![Debian][Debian Logo] ![Android][Android Logo]

`false`: Do not send start and end time of web page loading. [[forum.mozilla-russia.org](http://forum.mozilla-russia.org/viewtopic.php?pid=653380#p653380) (in Russian)]

```js
user_pref("dom.enable_resource_timing", false);
```

Default: `true` ![Windows][Windows Logo] ![Debian][Debian Logo] ![Android][Android Logo]

```js
user_pref("dom.enable_user_timing", false);
```

Default: `true` ![Windows][Windows Logo] ![Debian][Debian Logo] ![Android][Android Logo]. [[W3C](https://www.w3.org/TR/2013/REC-user-timing-20131212/)]

```js
user_pref("dom.idle-observers-api.enabled", false);
```

Default: `true` ![Windows][Windows Logo] ![Debian][Debian Logo] ![Android][Android Logo]

### Video Stats

Provides web applications with information about video playback statistics such as the framerate [[ghacks.net](http://www.ghacks.net/overview-firefox-aboutconfig-security-privacy-preferences/)]

```js
user_pref("media.video_stats.enabled", false);
```

Default: `true` ![Windows][Windows Logo] ![Debian][Debian Logo] ![Android][Android Logo]

## Thumbnails

```js
user_pref("browser.pagethumbnails.capturing_disabled", true);
```

Default: n/a (hidden preference) ![Windows][Windows Logo] ![Debian][Debian Logo] ![Android][Android Logo]

`true`: Do not create screenshots of visited pages which will be shown if the web page is shown in the grid of the "New Tab Page" [[MDN](https://developer.mozilla.org/en-US/docs/Mozilla/Preferences/Preference_reference/browser.pagethumbnails.capturing_disabled)]. The preference is available in the desktop versions of Firefox only.

## DOM

### Clipboard

```js
user_pref("dom.event.clipboardevents.enabled", false);
```

Default: `true` ![Windows][Windows Logo] ![Debian][Debian Logo] ![Android][Android Logo]

`false`: Do not let websites to get notifications if the user copies, pastes, or cuts something from a web page, and do not let them know which part of the page has been selected [[MDN](https://developer.mozilla.org/en-US/docs/Mozilla/Preferences/Preference_reference/dom.event.clipboardevents.enabled)].

### Context Menu

[][DOM Entries - mozillaZine]

[DOM entries - mozillaZine]: http://kb.mozillazine.org/About:config_entries#DOM.

```js
user_pref("dom.event.contextmenu.enabled", false);
```

Default: `true` ![Windows][Windows Logo] ![Debian][Debian Logo] ![Android][Android Logo]

`false`: Webpages will not be able to affect the context menu event [[DOM Entries - mozillaZine]].

### Popup Windows

```js
user_pref("dom.popup_maximum", 3);
```

Default: 20 ![Windows][Windows Logo] ![Debian][Debian Logo] ![Android][Android Logo]. [[mozillaZine](http://kb.mozillazine.org/Dom.popup_maximum)]

### Window

```js
user_pref("dom.disable_window_move_resize", true);
```

Default: `false` ![Windows][Windows Logo] ![Debian][Debian Logo], `true` ![Android][Android Logo]

`true`: Windows may not be moved or resized [[DOM Entries - mozillaZine]].

```js
user_pref("dom.disable_window_open_feature.close", true);
```

Default: `false` ![Windows][Windows Logo] ![Debian][Debian Logo] ![Android][Android Logo]

`true`: Prevent close button from being disabled [[DOM Entries - mozillaZine]].

```js
user_pref("dom.disable_window_open_feature.location", true);
```

Default: `true` ![Windows][Windows Logo] ![Debian][Debian Logo], `false` ![Android][Android Logo]

`true`: Prevent popups from hiding the Location Bar [[mozillaZine](http://kb.mozillazine.org/Dom.disable_window_open_feature.location)].

```js
user_pref("dom.disable_window_open_feature.menubar", true);
```

Default: `false` ![Windows][Windows Logo] ![Debian][Debian Logo] ![Android][Android Logo]

`true`: Prevent menubar from being hidden [[DOM Entries - mozillaZine]].

```js
user_pref("dom.disable_window_open_feature.minimizable", true);
```

Default: `false` ![Windows][Windows Logo] ![Debian][Debian Logo] ![Android][Android Logo]

`true`: Prevent popup window minimization from being disabled [[DOM Entries - mozillaZine]].

```js
user_pref("dom.disable_window_open_feature.personalbar", true);
```

Default: `false` ![Windows][Windows Logo] ![Debian][Debian Logo] ![Android][Android Logo]

`true`: Prevent bookmarks toolbar from being hidden [[DOM Entries - mozillaZine]].

```js
user_pref("dom.disable_window_open_feature.scrollbars", true);
```

Default: `false` ![Windows][Windows Logo] ![Debian][Debian Logo] ![Android][Android Logo]

`true`: Prevent scrollbars from being disabled [[DOM Entries - mozillaZine]].

```js
user_pref("dom.disable_window_open_feature.toolbar", true);
```

Default: `false` ![Windows][Windows Logo] ![Debian][Debian Logo] ![Android][Android Logo]

`true`: Prevent navigation toolbar from being hidden [[DOM Entries - mozillaZine]].
