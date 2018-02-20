# user.js

## Index

- [Network](#network)
  - [Cookie](#cookie)
  - [HTTP Alternative Services](#http-alternative-services)
  - [Offline Status](#offline-status)
  - [Prefetching](#prefetching)
  - [Proxy](#proxy)
  - [Send Referer](#send-referer)
- [Reports to Mozilla and Data Collecting Company](#reports-to-mozilla-and-data-collecting-company)
  - [Crash Report](#crash-report)
  - [Health Report](#health-report)
  - [SSL Error Report](#ssl-error-report)
  - [Telemetry](#telemetry)
    - [Shield Studies](#shield-studies)
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
- [Extensions](#extensions)
  - [Extension Blocklist](#extension-blocklist)
  - [Extension Signing](#extension-signing)
  - [Get Add-ons Discovery Pane](#get-add-ons-discovery-pane)
- [Firefox Account](#firefox-account)
- [Firefox Chat](#firefox-chat)
- [Mozilla Social](#mozilla-social)
- [Home Page](#home-page)
  - [Messages on Home Page](#messages-on-home-page)
- [New Tab](#new-tab)
- [Pocket](#pocket)
- [Statistics](#statistics)
  - [Timing](#timing)
  - [Video Stats](#video-stats)
- [WebAPI](#web-api)
  - [Battery API](#battery-api)
  - [Beacon API](#beacon-api)
  - [Camera API](#camera-api)
  - [CSS Font Loading API](#css-font-loading-api)
  - [Device Storage API](#device-storage-api)
  - [Gamepad API](#gamepad-api)
  - [Geolocation API](#geolocation-api)
    - [Geolocation-Based Search](#geolocation-based-search)
  - [Keyboard API](#keyboard-api)
  - [Network Information API](#network-information-api)
  - [Notification API](#notification-api)
  - [Sensor API](#sensor-api)
  - [Vibration API](#vibration-api)
- [Auto Play](#auto-play)
  - [Animated Image](#animated-image)
  - [Videos](#videos)
- [Bookmarks](#bookmarks)
- [Cache](#cache)
- [Developer Tools](#developer-tools)
  - [WebIDE](#webide)
- [DOM](#dom)
  - [Clipboard](#clipboard)
  - [Context Menu](#context-menu)
  - [Device Name](#device-name)
  - [Popup Windows](#popup-windows)
  - [Storage](#storage)
  - [Window](#window)
- [Download Manager](#download-manager)
- [Fingerprinting](#fingerprinting)
- [Fonts](#fonts)
  - [Document Fonts](#document-fonts)
  - [SVG Fonts](#svg-fonts)
- [Forms](#forms)
- [Fullscreen Animation](#fullscreen-animation)
- [Location Bar](#location-bar)
  - [Domain Guessing](#domain-guessing)
  - [Keyword Service](#keyword-service)
- [Passwords](#passwords)
- [PDF Viewer](#pdf-viewer)
- [Reader Mode](#reader-mode)
- [Search Suggestions](#search-suggestions)
- [Security](#security)
  - [First-Party Isolation](#first-party-isolation)
  - [Punycode Phishing](#punycode-phishing)
  - [SSL](#ssl)
  - [XPConnect](#xpconnect)
- [Session Store](#session-store)
- [Startup](#startup)
  - [Check Default Browser](#check-default-browser)
  - [Rights](#rights)
  - [Slow Startup](#slow-startup)
- [Thumbnails](#thumbnails)
- [Video Buffering](#video-buffering)
- [View Source](#view-source)
- [WebGL](#webgl)


![Windows][Windows Logo] - Firefox 45.x (MS Windows),
![Debian][Debian Logo] - Firefox 45.x (Debian Stable),
![Android][Android Logo] - IceCat 45.x (Android),
![Tor Browser][Tor Browser Logo] - Tor Browser 6.5.x (Firefox 45.x),
![Basilisk][Basilisk Logo] - Basilisk (Firefox 55.x)
![NightlyWin][Nightly Firefox Windows Logo] - Firefox Nightly (Firefox 60.x, Windows)
![NightlyAndroid][Nightly Firefox Android Logo] - Firefox Nightly (Firefox 60.x, Android)

[Android Logo]: img/Android.png

[Debian Logo]: img/Debian.png

[Tor Browser Logo]: img/TorBrowser.png

[Basilisk Logo]: img/Basilisk.png

[Windows Logo]: img/Windows.png

[Nightly Firefox Windows Logo]: img/FF-Nightly-Win.png

[Nightly Firefox Android Logo]: img/FF-Nightly-Android.png

## Network

[Mozilla networking preferences - MDN](https://developer.mozilla.org/en-US/docs/Mozilla/Preferences/Mozilla_networking_preferences)

### Cookie

```js
user_pref("network.cookie.cookieBehavior", 1);
```

Default:
`0`
  ![Windows][Windows Logo]
  ![Debian][Debian Logo],
`1`
  ![Tor Browser][Tor Browser Logo]
  ![Basilisk][Basilisk Logo]
  ![Android][Android Logo]

0 - allow all cookies,
1 - allow cookie only from the originating server [[mozillaZine](http://kb.mozillazine.org/Network.cookie.cookieBehavior)].

### HTTP Alternative Services

[RFC 7838 - HTTP Alternative Services](https://tools.ietf.org/html/rfc7838)

```js
user_pref("network.http.altsvc.enabled", false);
user_pref("network.http.altsvc.oe", false);
```

Default:
`true`
  ![Windows][Windows Logo]
  ![Debian][Debian Logo]
  ![Basilisk][Basilisk Logo]
  ![Android][Android Logo],
`false`
  ![Tor Browser][Tor Browser Logo]

[#16673: Isolate/Disable HTTP Alternative-Services – Tor Bug Tracker](https://trac.torproject.org/projects/tor/ticket/16673)

### Offline Status

[Online and offline events | MDN](https://developer.mozilla.org/en-US/docs/Online_and_offline_events)

```js
user_pref("network.manage-offline-status", false);
```

Default:
`true`
  ![Windows][Windows Logo]
  ![Debian][Debian Logo]
  ![Basilisk][Basilisk Logo]
  ![Android][Android Logo],
`false`
  ![Tor Browser][Tor Browser Logo]

[#18945: Disable monitoring the connected state of Tor Browser users | Tor Bug Tracker](https://trac.torproject.org/projects/tor/ticket/18945)


### Prefetching

```js
user_pref("network.prefetch-next", false);
```

Default:
`true`
  ![Windows][Windows Logo]
  ![Debian][Debian Logo]
  ![Tor Browser][Tor Browser Logo]
  ![Basilisk][Basilisk Logo],
`false`
  ![Android][Android Logo]

Link prefetching is a browser mechanism, which utilizes browser idle time to download or prefetch documents that the user might visit in the near future [[MDN](https://developer.mozilla.org/en-US/docs/Web/HTTP/Link_prefetching_FAQ)]. `false` disables link prefetching [[mozillaZine](http://kb.mozillazine.org/Network.prefetch-next)].


```js
user_pref("network.dns.disablePrefetch", true);
```

Default:
`false`
  ![Windows][Windows Logo]
  ![Debian][Debian Logo]
  ![Basilisk][Basilisk Logo],
`true`
  ![Tor Browser][Tor Browser Logo]
  ![Android][Android Logo]

[X-DNS-Prefetch-Control | MDN](https://developer.mozilla.org/en-US/docs/Web/HTTP/Headers/X-DNS-Prefetch-Control)

[Network.dns.disablePrefetch - mozillaZine](http://kb.mozillazine.org/Network.dns.disablePrefetch)


```js
user_pref("network.dns.disablePrefetchFromHTTPS", true);
```

Default:
n/a
  ![Windows][Windows Logo]
  ![Debian][Debian Logo]
  ![Tor Browser][Tor Browser Logo]
  ![Basilisk][Basilisk Logo]
  ![Android][Android Logo]

By default, prefetching of embedded link hostnames is not performed on documents loaded over HTTPS [[MDN](https://developer.mozilla.org/en-US/docs/Web/HTTP/Headers/X-DNS-Prefetch-Control)].


```js
user_pref("network.predictor.enabled", false);
```

Default: `true` ![Windows][Windows Logo] ![Debian][Debian Logo] ![Basilisk][Basilisk Logo] ![Android][Android Logo], `false` ![Tor Browser][Tor Browser Logo]

The network predictor (formerly called '[seer](https://wiki.mozilla.org/Privacy/Reviews/Necko)') makes preemptive connections to resources in a page based on cached information. It can also do the same when the user hovers over a link. [[Tor](https://trac.torproject.org/projects/tor/ticket/16625)]

```js
user_pref("network.http.speculative-parallel-limit", 0);
```

Default: `6` ![Windows][Windows Logo] ![Debian][Debian Logo] ![Basilisk][Basilisk Logo], `0` ![Tor Browser][Tor Browser Logo] ![Android][Android Logo]. [[mozilla support](https://support.mozilla.org/en-US/kb/how-stop-firefox-making-automatic-connections#w_speculative-pre-connections)]

### Proxy

```js
user_pref("network.proxy.type", 0);
```

Default: `5` ![Windows][Windows Logo] ![Debian][Debian Logo] ![Basilisk][Basilisk Logo] ![Android][Android Logo], `1` ![Tor Browser][Tor Browser Logo]. [[mozillaZine](http://kb.mozillazine.org/Network.proxy.type)]

### Send Referer

```js
user_pref("network.http.sendRefererHeader", 0);
```

Default: 2 ![Windows][Windows Logo] ![Debian][Debian Logo] ![Tor Browser][Tor Browser Logo] ![Basilisk][Basilisk Logo] ![Android][Android Logo]

0 - never send the referring URL,
1 - send only on clicked links,
2 - send for links and images [[mozillaZine](http://kb.mozillazine.org/Network.http.sendRefererHeader)].

```js
user_pref("network.http.sendSecureXSiteReferrer", false);
```

Default: `true` ![Windows][Windows Logo] ![Debian][Debian Logo] ![Tor Browser][Tor Browser Logo] ![Android][Android Logo], n/a ![Basilisk][Basilisk Logo]. [[mozillaZine](http://kb.mozillazine.org/Network.http.sendSecureXSiteReferrer)]

## Reports to Mozilla and Data Collecting Company

Firefox for Android, Firefox for iOS, Firefox Focus and Firefox Klar collect and send data to the German company adjust GmbH [[mozilla support](https://support.mozilla.org/t5/Protect-your-privacy/Send-anonymous-usage-data-from-Firefox-on-mobile-devices/ta-p/37739)].

[Mozilla Klar saugt Daten ab - deutschlandfunk.de](http://www.deutschlandfunk.de/anti-tracking-software-mozilla-klar-saugt-daten-ab.684.de.html?dram:article_id=378712) (in German)

[Firefox Focus: The 'Privacy Browser' with build in user tracking  | Born's Tech and Windows World](http://borncity.com/win/2017/02/12/firefox-focus-the-privacy-browser-with-build-in-user-tracking/)

[Firefox Focus privacy scandal - gHacks Tech News](http://www.ghacks.net/2017/02/12/firefox-focus-privacy-scandal/)

```js
user_pref("datareporting.policy.dataSubmissionEnabled", false);
```

Default:
`true`
  ![Windows][Windows Logo]
  ![Debian][Debian Logo],
`false`
  ![Tor Browser][Tor Browser Logo]
  ![Android][Android Logo],
n/a
  ![Basilisk][Basilisk Logo]

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

Default: "https://crash-stats.mozilla.com/report/index/" ![Windows][Windows Logo] ![Debian][Debian Logo] ![Tor Browser][Tor Browser Logo] ![Basilisk][Basilisk Logo] ![Android][Android Logo]

Set of libraries called `Breakpad` handles client-side crash reporting [[mozillaZine](http://kb.mozillazine.org/Breakpad.reportURL)].

```js
user_pref("dom.ipc.plugins.flash.subprocess.crashreporter.enabled", false);
```

Default: `true` ![Windows][Windows Logo] ![Debian][Debian Logo] ![Tor Browser][Tor Browser Logo] ![Basilisk][Basilisk Logo], `false` ![Android][Android Logo]

`false`: Do not send Flash crash reports [[ghacks.net](http://www.ghacks.net/2015/08/18/a-comprehensive-list-of-firefox-privacy-and-security-settings/)].

[[MDN](https://developer.mozilla.org/en-US/Firefox/Releases/43#Plugins)]: In preparation for future releases to switch over to multi-process content, NPAPI plugins can no longer be run in the same process as the page content. The preferences starting with `dom.ipc.plugins` are no longer used.

```js
user_pref("dom.ipc.plugins.reportCrashURL", false);
```

Default: `true` ![Windows][Windows Logo] ![Debian][Debian Logo] ![Tor Browser][Tor Browser Logo] ![Basilisk][Basilisk Logo] ![Android][Android Logo]

`false`: Do not send the URL of the website where a plugin crashed [[ghacks.net](http://www.ghacks.net/2015/08/18/a-comprehensive-list-of-firefox-privacy-and-security-settings/)].

```js
user_pref("browser.tabs.crashReporting.sendReport", false);
```

Default: `true` ![Windows][Windows Logo] ![Debian][Debian Logo] ![Tor Browser][Tor Browser Logo] ![Basilisk][Basilisk Logo], n/a ![Android][Android Logo]. [[about:tabcrashed spec](https://people-mozilla.org/~mconley2/bugnotes/bug-1110511.html)]

### Health Report

[[mozilla](https://www.mozilla.org/en-US/privacy/firefox/#health-report)]: Firefox Health Report is designed to provide you with insights about your browser's stability and performance and with support tips should you experience issues, such as high crash rates or slow startup times. Mozilla collects and aggregates your data with that of other Firefox users and sends it back to your browser so you can see how your Firefox performance changes over time. This data includes, for example: device hardware, operating system, Firefox version, add-ons (count and type), timing of browser events, rendering, session restores, length of session, how old a profile is, count of crashes, and count of pages.

[[What is Firefox Health Report?](https://blog.mozilla.org/metrics/fhr-faq/)] [[What data are collected?](https://blog.mozilla.org/metrics/2012/09/21/firefox-health-report/)]

```js
user_pref("datareporting.healthreport.uploadEnabled", false);
```
Default: `true` ![Windows][Windows Logo], `false` ![Debian][Debian Logo] ![Tor Browser][Tor Browser Logo], n/a ![Basilisk][Basilisk Logo] ![Android][Android Logo]

```js
user_pref("datareporting.healthreport.service.enabled", false);
```

Default: `true` ![Windows][Windows Logo] ![Debian][Debian Logo], `false` ![Tor Browser][Tor Browser Logo], n/a ![Basilisk][Basilisk Logo] ![Android][Android Logo]

```js
user_pref("datareporting.healthreport.documentServerURI", "");
```

Default: "https://fhr.data.mozilla.com/" ![Windows][Windows Logo] ![Debian][Debian Logo] ![Tor Browser][Tor Browser Logo], n/a ![Basilisk][Basilisk Logo] ![Android][Android Logo]

```js
user_pref("datareporting.healthreport.about.reportUrl", "");
```

Default: "https://fhr.cdn.mozilla.net/%LOCALE%/v4/" ![Windows][Windows Logo] ![Debian][Debian Logo], "data:text/plain," ![Tor Browser][Tor Browser Logo], "127.0.0.1" ![Android][Android Logo], n/a ![Basilisk][Basilisk Logo]

```js
user_pref("datareporting.healthreport.about.reportUrlUnified", "");
```

Default: "https://fhr.cdn.mozilla.net/%LOCALE%/v4/" ![Windows][Windows Logo] ![Debian][Debian Logo], "data:text/plain," ![Tor Browser][Tor Browser Logo], n/a ![Basilisk][Basilisk Logo] ![Android][Android Logo]

```js
user_pref("datareporting.healthreport.logging.consoleEnabled", false);
```

Default: `true` ![Windows][Windows Logo] ![Debian][Debian Logo] ![Tor Browser][Tor Browser Logo], n/a ![Basilisk][Basilisk Logo] ![Android][Android Logo]

### SSL Error Report

[SSL Error Reporting - Mozilla Source Tree Docs](https://gecko.readthedocs.io/en/latest/browser/base/sslerrorreport/preferences.html)

```js
user_pref("security.ssl.errorReporting.enabled", false);
```

Default: `true` ![Windows][Windows Logo] ![Debian][Debian Logo] ![Tor Browser][Tor Browser Logo] ![Basilisk][Basilisk Logo] ![Android][Android Logo]

```js
user_pref("security.ssl.errorReporting.url", "");
```

Default: "https://data.mozilla.com/submit/sslreports" ![Windows][Windows Logo] ![Debian][Debian Logo] ![Tor Browser][Tor Browser Logo] ![Android][Android Logo], "https://incoming.telemetry.mozilla.org/submit/sslreports/" ![Basilisk][Basilisk Logo]

### Telemetry

> [[mozilla](https://www.mozilla.org/en-US/privacy/firefox/#telemetry)]:
> Telemetry is a feature in Firefox that sends Mozilla usage, performance, and responsiveness statistics about user interface features, memory, and hardware configuration. Your IP address is also collected as a part of a standard web log.

[Docs/Telemetry/Internals/Preferences - Mozilla Source Tree Docs](https://firefox-source-docs.mozilla.org/toolkit/components/telemetry/telemetry/internals/preferences.html)


```js
user_pref("toolkit.telemetry.unified", false);
```

Default: `true` ![Windows][Windows Logo] ![Debian][Debian Logo] ![Basilisk][Basilisk Logo], `false` ![Tor Browser][Tor Browser Logo] ![Android][Android Logo]

If `true`: Telemetry is always enabled and recording base data; Telemetry will send additional `main` pings [[Mozilla Source Tree Docs][telemetry-preferences]].

[telemetry-preferences]: https://gecko.readthedocs.io/en/latest/toolkit/components/telemetry/telemetry/preferences.html#id1

```js
user_pref("toolkit.telemetry.enabled", false);
```

Default: `false` ![Windows][Windows Logo] ![Debian][Debian Logo] ![Tor Browser][Tor Browser Logo] ![Basilisk][Basilisk Logo] ![Android][Android Logo]

If `unified` is off, this controls whether the Telemetry module is enabled; if `unified` is on, this controls whether to record extended data [[Mozilla Source Tree Docs][telemetry-preferences]].

```js
user_pref("toolkit.telemetry.server", "");
```

Default: "https://incoming.telemetry.mozilla.org" ![Windows][Windows Logo] ![Debian][Debian Logo] ![Tor Browser][Tor Browser Logo] ![Basilisk][Basilisk Logo] ![Android][Android Logo]

The server Telemetry pings are sent to [[Mozilla Source Tree Docs][telemetry-preferences]].


#### Shield Studies

[About SHIELD Studies - Firefox Help](https://support.mozilla.org/en-US/kb/shield)

[Firefox/Shield - MozillaWiki](https://wiki.mozilla.org/Firefox/Shield)

[Bug 1370801: Add Shield Opt-out Preference - Bugzilla](https://bugzilla.mozilla.org/show_bug.cgi?id=1370801)

[Mozilla creates Shield study rules to avoid another Mr.Robot disaster - ghacks.net](https://www.ghacks.net/2018/01/31/mozilla-creates-shield-study-rules-to-avoid-another-mr-robot-disaster/)

```js
user_pref("app.shield.optoutstudies.enabled", false);
```

Default:
`true`
  ![NightlyWin][Nightly Firefox Windows Logo],
n/a
  ![NightlyAndroid][Nightly Firefox Android Logo]


[Issue #319: Block Firefox Shield Recipe Client - pyllyukko/user.js](https://github.com/pyllyukko/user.js/issues/319)

```js
user_pref("extensions.shield-recipe-client.enabled", false);
```

Default:
`true`
  ![NightlyWin][Nightly Firefox Windows Logo],
n/a
  ![NightlyAndroid][Nightly Firefox Android Logo]

```js
user_pref("extensions.shield-recipe-client.api_url", "");
```

Default:
`"https://normandy.cdn.mozilla.net/api/v1"`
  ![NightlyWin][Nightly Firefox Windows Logo],
n/a
  ![NightlyAndroid][Nightly Firefox Android Logo]


#### Experiments

Experiments are available to anyone who has Telemetry enabled [[mozilla wiki](https://wiki.mozilla.org/Telemetry/Experiments)].

```js
user_pref("experiments.supported", false);
```

Default: `true` ![Windows][Windows Logo] ![Debian][Debian Logo] ![Tor Browser][Tor Browser Logo], `false` ![Basilisk][Basilisk Logo], n/a ![Android][Android Logo]

```js
user_pref("experiments.enabled", false);
```

Default: `true` ![Windows][Windows Logo] ![Debian][Debian Logo], `false` ![Tor Browser][Tor Browser Logo] ![Basilisk][Basilisk Logo], n/a ![Android][Android Logo]

```js
user_pref("experiments.manifest.uri", "");
```

Default: "https://telemetry-experiment.cdn.mozilla.net/manifest/v1/firefox/%VERSION%/%CHANNEL%" ![Windows][Windows Logo] ![Debian][Debian Logo] ![Tor Browser][Tor Browser Logo] ![Basilisk][Basilisk Logo], n/a ![Android][Android Logo]

```js
user_pref("experiments.activeExperiment", false);
```

Default: `true` ![Windows][Windows Logo] ![Debian][Debian Logo], n/a ![Tor Browser][Tor Browser Logo] ![Basilisk][Basilisk Logo] ![Android][Android Logo]. [[mozilla wiki](https://wiki.mozilla.org/QA/Telemetry/AboutPreferences "QA/Telemetry/AboutPreferences")]

```js
user_pref("network.allow-experiments", false);
```

Default: `true` ![Windows][Windows Logo] ![Debian][Debian Logo] ![Tor Browser][Tor Browser Logo] ![Basilisk][Basilisk Logo] ![Android][Android Logo].

`true` grants permission for mozilla to silently "opt a user's browser" into participating in A/B tests, user behavior profiling tests, etc. [[Tor](https://trac.torproject.org/projects/tor/ticket/13170)].

### User Rating Feedback

```js
user_pref("browser.selfsupport.enabled", false);
```

Default: n/a ![Windows][Windows Logo] ![Debian][Debian Logo] ![Basilisk][Basilisk Logo] ![Android][Android Logo], `false` ![Tor Browser][Tor Browser Logo]. [[Tor Bug #18738](https://trac.torproject.org/projects/tor/ticket/18738)]

```js
user_pref("browser.selfsupport.url", "");
```

Default: `https://self-repair.mozilla.org/%LOCALE%/repair` ![Windows][Windows Logo] ![Debian][Debian Logo], "(_empty string_)" ![Tor Browser][Tor Browser Logo] ![Basilisk][Basilisk Logo] ![Android][Android Logo]. [[mozilla wiki](https://wiki.mozilla.org/Advocacy/heartbeat)]

## Safe Browsing

The Safe Browsing feature in Firefox has been renamed to Phishing Protection, but it's still known as Safe Browsing internally [[mozilla wiki](https://wiki.mozilla.org/Phishing_Protection)].

```js
user_pref("browser.safebrowsing.enabled", false);
```

Default: `true` ![Windows][Windows Logo] ![Debian][Debian Logo], `false` ![Tor Browser][Tor Browser Logo] ![Android][Android Logo], replaced by `browser.safebrowsing.phishing.enabled` and set to `false` ![Basilisk][Basilisk Logo].
[[mozillaZine](http://kb.mozillazine.org/Browser.safebrowsing.enabled)]

```js
user_pref("browser.safebrowsing.malware.enabled", false);
```

Default: `true` ![Windows][Windows Logo] ![Debian][Debian Logo], `false` ![Tor Browser][Tor Browser Logo] ![Basilisk][Basilisk Logo] ![Android][Android Logo].

`false`: do not download malware blacklists and do not check user downloads [[mozillaZine](http://kb.mozillazine.org/Browser.safebrowsing.malware.enabled)]. [[mozilla support](https://support.mozilla.org/en-US/kb/how-does-phishing-and-malware-protection-work "How does built-in Phishing and Malware Protection")]

```js
user_pref("browser.safebrowsing.downloads.enabled", false);
```
Default:
`true`
  ![Windows][Windows Logo]
  ![Debian][Debian Logo]
  ![Tor Browser][Tor Browser Logo],
`false`
  ![Basilisk][Basilisk Logo]
  ![Android][Android Logo]

It enables/disables application reputation checks for downloaded files [[mozilla wiki](https://wiki.mozilla.org/Security/Application_Reputation "Application Reputation")].
`true` does only the local checks against a blacklist and a whitelist, as long as `browser.safebrowsing.downloads.remote.enabled` is disabled [[pyllyukko](https://github.com/pyllyukko/user.js/pull/65)].


```js
user_pref("browser.safebrowsing.downloads.remote.enabled", false);
```

Default: `true` ![Windows][Windows Logo] ![Debian][Debian Logo] ![Tor Browser][Tor Browser Logo], `false` ![Basilisk][Basilisk Logo] ![Android][Android Logo]

`false` disables application reputation remote lookups, but leaves other Safebrowsing malware protection intact [[mozilla wiki](https://wiki.mozilla.org/Security/Features/Application_Reputation_Design_Doc#How_to_turn_off_this_feature "Application Reputation Design Doc")].

[[GOV.UK](https://www.gov.uk/government/publications/browser-security-guidance-mozilla-firefox/browser-security-guidance-mozilla-firefox#enterprise-considerations "Browser Security Guidance: Mozilla Firefox - GOV.UK")]: Firefox uses Google's Safe Browsing service that aims to protect against phishing websites and malicious downloads. It works by sending hashes of some visited website addresses to Google. If Google reports that the page is unsafe, the page or file will not be downloaded or displayed to protect the user against malware and data theft. Google states that it cannot derive the full website addresses from the information submitted as it only sends a partial URL fingerprint. Full website addresses are only sent if an organisation chooses to configure Chrome to send usage statistics to Google. Safe Browsing can be disabled entirely if the trade-off between privacy and security is not acceptable.

```js
user_pref("privacy.trackingprotection.enabled", false);
```

Default: `false` ![Windows][Windows Logo] ![Debian][Debian Logo] ![Tor Browser][Tor Browser Logo] ![Basilisk][Basilisk Logo] ![Android][Android Logo] [[mozilla wiki](https://wiki.mozilla.org/Security/Tracking_protection)] [[mozilla support](https://support.mozilla.org/en-US/kb/tracking-protection-firefox)]

## Screen Casting

Firefox contains a "Send Video To Device" feature to send HTML5 video content to a Roku, Chromecast or similar device in the same network. In order to discover and pair with such a device, Firefox will send SSDP packages to the local network (multicast address 239.255.255.250:1900) [[mozilla support](https://support.mozilla.org/en-US/kb/how-stop-firefox-making-automatic-connections#w_send-video-to-device)].

```js
user_pref("browser.casting.enabled", false);
```

Default:
`false`
  ![Windows][Windows Logo]
  ![Debian][Debian Logo]
  ![Tor Browser][Tor Browser Logo]
  ![Basilisk][Basilisk Logo]
  ![Android][Android Logo]
([-FF56](https://bugzilla.mozilla.org/show_bug.cgi?id=1393582))


## Updating

[[Disable Updater - MDN](https://developer.mozilla.org/en-US/docs/Mozilla/Firefox/Enterprise_deployment#Example_configuration_file)]

```js
user_pref("app.update.enabled", false);
```

Default: `true` ![Windows][Windows Logo] ![Tor Browser][Tor Browser Logo] ![Basilisk][Basilisk Logo], `false` ![Debian][Debian Logo] ![Android][Android Logo]. [[mozillaZine](http://kb.mozillazine.org/App.update.enabled)]

```js
user_pref("app.update.auto", false);
```

Default: `true` ![Windows][Windows Logo] ![Debian][Debian Logo] ![Tor Browser][Tor Browser Logo] ![Basilisk][Basilisk Logo], n/a ![Android][Android Logo]. [[mozillaZine](http://kb.mozillazine.org/App.update.auto)]

```js
user_pref("app.update.service.enabled", false);
```

Default: `true` ![Windows][Windows Logo], n/a ![Debian][Debian Logo] ![Tor Browser][Tor Browser Logo] ![Basilisk][Basilisk Logo] ![Android][Android Logo]. [[Windows Service Silent Update - mozilla wiki](https://wiki.mozilla.org/Windows_Service_Silent_Update)]

### Extensions Update

[[Mozilla Add-ons Blog](https://blog.mozilla.org/addons/how-to-opt-out-of-add-on-metadata-updates/)]: Firefox asks the [Mozilla Add-ons gallery](https://addons.mozilla.org/) for information about the add-ons you have installed once a day. This involves sending the identifiers of each add-on you have installed to Mozilla, as well as information on how long it last took Firefox to start up. Opting out of this daily ping will stop Firefox from sending the add-ons you have installed and most recent start-up time to Mozilla, and will also stop displaying updated metadata for your add-ons and discontinue personalized recommendations if they were displayed in the Get Add-ons pane of the Add-ons Manager. To opt out, set `extensions.getAddons.cache.enabled` to `false`.

```js
user_pref("extensions.getAddons.cache.enabled", false);
```

Default: `true` ![Windows][Windows Logo] ![Debian][Debian Logo] ![Android][Android Logo], `false` ![Tor Browser][Tor Browser Logo] ![Basilisk][Basilisk Logo]

```js
user_pref("extensions.update.enabled", false);
```

Default: `true` ![Windows][Windows Logo] ![Debian][Debian Logo] ![Tor Browser][Tor Browser Logo] ![Basilisk][Basilisk Logo] ![Android][Android Logo]. [[mozillaZine](http://kb.mozillazine.org/About:config_entries#Extensions.)]

```js
user_pref("extensions.update.autoUpdateDefault", false);
```

Default: `true` ![Windows][Windows Logo] ![Debian][Debian Logo] ![Tor Browser][Tor Browser Logo], n/a ![Android][Android Logo]. [[mozilla support](https://support.mozilla.org/en-US/questions/952162 "Difference between extensions.update.autoUpdateDefault and extensions.update.enabled")]

```js
user_pref("extensions.autoupdate.enabled", false);
```

Default: n/a ![Windows][Windows Logo] ![Debian][Debian Logo] ![Tor Browser][Tor Browser Logo] ![Basilisk][Basilisk Logo], `true` ![Android][Android Logo]. [[Blog](http://starkravingfinkle.org/blog/2010/05/updating-add-ons-in-firefox-mobile-1-1/ "Updating Add-ons in Firefox Mobile 1.1")]

### Search Engines Update

```js
user_pref("browser.search.update", false);
```

Default: `true` ![Windows][Windows Logo] ![Debian][Debian Logo] ![Basilisk][Basilisk Logo], `false` ![Tor Browser][Tor Browser Logo] ![Android][Android Logo]

`false`: do not automatically check for updates to search plugins [[mozillaZine](http://kb.mozillazine.org/About:config_entries#Browser.)].

### Themes Update

```js
user_pref("lightweightThemes.update.enabled", false);
```

Default: `true` ![Windows][Windows Logo] ![Debian][Debian Logo] ![Tor Browser][Tor Browser Logo] ![Basilisk][Basilisk Logo], `false` ![Android][Android Logo]. [[mozillaZine](http://kb.mozillazine.org/Themes#Lightweight_theme)]

### Web Apps Update

[[Web Application - Wikipedia](https://en.wikipedia.org/wiki/Web_application)] [[MDN](https://developer.mozilla.org/en-US/Apps)]

```js
user_pref("app.update.autodownload", "disabled");
```
Default: n/a ![Windows][Windows Logo] ![Debian][Debian Logo] ![Tor Browser][Tor Browser Logo] ![Basilisk][Basilisk Logo], "wifi" ![Android][Android Logo]

```js
user_pref("app.update.url.android", "");
```

Default: n/a ![Windows][Windows Logo] ![Debian][Debian Logo] ![Tor Browser][Tor Browser Logo] ![Basilisk][Basilisk Logo], "https://aus5.mozilla.org/update/4/%PRODUCT%/%VERSION%/%BUILD_ID%/%BUILD_TARGET%/%LOCALE%/%CHANNEL%/%OS_VERSION%/%DISTRIBUTION%/%DISTRIBUTION_VERSION%/%MOZ_VERSION%/update.xml") ![Android][Android Logo]

## WebRTC

[[MDN](https://developer.mozilla.org/en-US/docs/Web/Guide/API/WebRTC)]: WebRTC (Web Real Time Communications) is a technology that enables audio/video streaming and data sharing between browser clients (peers). WebRTC provides the ability to share application data and perform teleconferencing peer to peer, without the need to install plug-ins or third-party software.

```js
user_pref("media.navigator.enabled", false);
```

Default: `true` ![Windows][Windows Logo] ![Debian][Debian Logo] ![Basilisk][Basilisk Logo] ![Android][Android Logo], `false` ![Tor Browser][Tor Browser Logo]. [[mozilla wiki](https://wiki.mozilla.org/Media/getUserMedia)]

```js
user_pref("media.peerconnection.enabled", false);
```

Default: `true` ![Windows][Windows Logo] ![Debian][Debian Logo] ![Basilisk][Basilisk Logo], `false` ![Tor Browser][Tor Browser Logo] ![Android][Android Logo]. [[mozilla wiki](https://wiki.mozilla.org/Media/getUserMedia)]

WebRTC Leak Tests:

- [privacytools.io](https://www.privacytools.io/webrtc.html)
- [diafygi.github.io](https://diafygi.github.io/webrtc-ips/)
- [browserleaks.com](https://www.browserleaks.com/webrtc)

### Gecko Media Plugins

Gecko Media Plugins (GMPs) is a special purpose extension point for authorised 3rd party codecs and EME (Encrypted Media Extensions) CDMs (Content Decryption Modules) [[mozilla wiki](https://wiki.mozilla.org/GeckoMediaPlugins)].

```js
user_pref("media.gmp-provider.enabled", false);
```

Default: `true` ![Windows][Windows Logo] ![Debian][Debian Logo] ![Basilisk][Basilisk Logo], `false` ![Tor Browser][Tor Browser Logo] ![Android][Android Logo]

`false` removes OpenH264 codec from the Plugins list.

The OpenH264 codec is not distributed with Firefox but gets downloaded at the first start of Firefox. In case you want to prohibit that, you will have to set the `media.gmp-gmpopenh264.enabled` and `media.gmp-gmpopenh264.autoupdate` to `false`  [[mozilla support](https://support.mozilla.org/en-US/kb/how-stop-firefox-making-automatic-connections#w_openh264-codec)].

```js
user_pref("media.gmp-gmpopenh264.enabled", false);
```
Default: n/a (hidden pref) ![Windows][Windows Logo] ![Tor Browser][Tor Browser Logo] ![Basilisk][Basilisk Logo] ![Android][Android Logo], `false` ![Debian][Debian Logo]

```js
user_pref("media.gmp-gmpopenh264.autoupdate", false);
```
Default: n/a (hidden pref) ![Windows][Windows Logo] ![Debian][Debian Logo] ![Tor Browser][Tor Browser Logo] ![Basilisk][Basilisk Logo] ![Android][Android Logo]

The installed codec is stored in `<Profile>/gmp-gmpopenh264/` and can be deleted.

```js
user_pref("media.gmp-manager.url", "http://127.0.0.1/");
```

Default: "https://aus5.mozilla.org/update/3/GMP/%VERSION%/%BUILD_ID%/%BUILD_TARGET%/%LOCALE%/%CHANNEL%/%OS_VERSION%/%DISTRIBUTION%/%DISTRIBUTION_VERSION%/update.xml" ![Windows][Windows Logo] ![Debian][Debian Logo] ![Tor Browser][Tor Browser Logo] ![Basilisk][Basilisk Logo], "http://127.0.0.1/" ![Android][Android Logo]

```js
user_pref("media.gmp-manager.url.override", "data:text/plain,");
```

Default: n/a ![Windows][Windows Logo] ![Basilisk][Basilisk Logo], "data:text/plain," ![Debian][Debian Logo] ![Tor Browser][Tor Browser Logo] ![Android][Android Logo]

```js
user_pref("media.gmp-manager.cert.checkAttributes", false);
user_pref("media.gmp-manager.cert.requireBuiltIn", false);
```

Default: `true` ![Windows][Windows Logo] ![Debian][Debian Logo] ![Tor Browser][Tor Browser Logo] ![Basilisk][Basilisk Logo] ![Android][Android Logo]

## Encrypted Media Extension

[[What is EME?](https://hsivonen.fi/eme/)] [[Mozilla Hacks](https://hacks.mozilla.org/2014/05/reconciling-mozillas-mission-and-w3c-eme/)] [[W3C](https://w3c.github.io/encrypted-media/)]

```js
user_pref("media.eme.enabled", false);
```

Default: `true` ![Windows][Windows Logo] ![Debian][Debian Logo], `false` ![Tor Browser][Tor Browser Logo] ![Basilisk][Basilisk Logo], n/a ![Android][Android Logo]

```js
user_pref("media.eme.apiVisible", false);
```

Default: `true` ![Windows][Windows Logo] ![Debian][Debian Logo] ![Basilisk][Basilisk Logo], `false` ![Tor Browser][Tor Browser Logo], n/a ![Android][Android Logo]

```js
user_pref("browser.eme.ui.enabled", false);
```

Default: `true` ![Windows][Windows Logo] ![Basilisk][Basilisk Logo], `false` ![Debian][Debian Logo] ![Tor Browser][Tor Browser Logo], n/a ![Android][Android Logo]

```js
user_pref("media.gmp-eme-adobe.enabled", false);
```

Default: `true` ![Windows][Windows Logo], `false` ![Tor Browser][Tor Browser Logo], n/a ![Debian][Debian Logo] ![Basilisk][Basilisk Logo] ![Android][Android Logo]

## Extensions

### Extension Blocklist

Blocklisting is the ability to disable errant add-ons, plugins, and other third-party software [[MozillaWiki](https://wiki.mozilla.org/Blocklisting)].

```js
user_pref("extensions.blocklist.enabled", false);
```

Default: `true` ![Windows][Windows Logo] ![Debian][Debian Logo] ![Tor Browser][Tor Browser Logo] ![Basilisk][Basilisk Logo], `false` ![Android][Android Logo]

Firefox periodically retrieves a blocklist from the Mozilla server. `false`: Do not retrieve a blocklist and do not restrict extension installation [[mozillaZine](http://kb.mozillazine.org/Extensions.blocklist.enabled)].

```js
user_pref("extensions.blocklist.url", "https://blocklist.addons.mozilla.org/blocklist/3/%APP_ID%/%APP_VERSION%/");
```
Default:
"https://blocklist.addons.mozilla.org/blocklist/3/%APP_ID%/%APP_VERSION%/%PRODUCT%/%BUILD_ID%/%BUILD_TARGET%/%LOCALE%/%CHANNEL%/%OS_VERSION%/%DISTRIBUTION%/%DISTRIBUTION_VERSION%/%PING_COUNT%/%TOTAL_PING_COUNT%/%DAYS_SINCE_LAST_PING%/" ![Windows][Windows Logo] ![Debian][Debian Logo] ![Tor Browser][Tor Browser Logo] ![Android][Android Logo],
"https://blocklist.basilisk-browser.org/blocklist/%APP_ID%/%APP_VERSION%/%PRODUCT%/%BUILD_ID%/%BUILD_TARGET%/%LOCALE%/%CHANNEL%/%OS_VERSION%/" ![Basilisk][Basilisk Logo]


[[Tor Bug #16931](https://trac.torproject.org/projects/tor/ticket/16931)]

### Extension Signing

```js
user_pref("xpinstall.signatures.required", false);
```
Default: `true` ![Windows][Windows Logo] ![Debian][Debian Logo] ![Tor Browser][Tor Browser Logo], `false` ![Basilisk][Basilisk Logo] ![Android][Android Logo]. [[mozilla wiki](https://wiki.mozilla.org/Addons/Extension_Signing)]

### Get Add-ons Discovery Pane

```js
user_pref("extensions.webservice.discoverURL", "http://127.0.0.1");
```

Default: "https://services.addons.mozilla.org/%LOCALE%/firefox/discovery/pane/%VERSION%/%OS%/%COMPATIBILITY_MODE%" ![Windows][Windows Logo] ![Debian][Debian Logo] ![Tor Browser][Tor Browser Logo] ![Basilisk][Basilisk Logo], n/a ![Android][Android Logo]. [[Techdows](http://techdows.com/2016/08/firefox-48-disable-add-on-discovery-pane.html)]

## Firefox Account

[Firefox Accounts - Mozilla | MDN](https://developer.mozilla.org/en-US/docs/Mozilla/Tech/Firefox_Accounts)

```js
user_pref("identity.fxaccounts.auth.uri", "");
```

Default: "https://api.accounts.firefox.com/v1" ![Windows][Windows Logo] ![Debian][Debian Logo] ![Tor Browser][Tor Browser Logo] ![Basilisk][Basilisk Logo] ![Android][Android Logo]

```js
user_pref("identity.fxaccounts.remote.force_auth.uri", "");
```

Default: "https://accounts.firefox.com/force_auth?service=sync&context=fx_desktop_v2" ![Windows][Windows Logo] ![Debian][Debian Logo] ![Tor Browser][Tor Browser Logo] ![Basilisk][Basilisk Logo], n/a ![Android][Android Logo]

```js
user_pref("identity.fxaccounts.remote.signin.uri", "");
```

Default: "https://accounts.firefox.com/signin?service=sync&context=fx_desktop_v2" ![Windows][Windows Logo] ![Debian][Debian Logo] ![Tor Browser][Tor Browser Logo] ![Basilisk][Basilisk Logo], n/a ![Android][Android Logo]

```js
user_pref("identity.fxaccounts.remote.signup.uri", "");
```

Default: "https://accounts.firefox.com/signup?service=sync&context=fx_desktop_v2" ![Windows][Windows Logo] ![Debian][Debian Logo] ![Tor Browser][Tor Browser Logo] ![Basilisk][Basilisk Logo], n/a ![Android][Android Logo]

```js
user_pref("identity.fxaccounts.settings.uri", "");
```

Default: "https://accounts.firefox.com/settings" ![Windows][Windows Logo] ![Debian][Debian Logo] ![Tor Browser][Tor Browser Logo] ![Basilisk][Basilisk Logo], n/a ![Android][Android Logo]

```js
user_pref("services.sync.engine.addons", false);
user_pref("services.sync.engine.prefs", false);
user_pref("services.sync.engine.tabs", false);
```

Default: `true` ![Windows][Windows Logo] ![Debian][Debian Logo] ![Basilisk][Basilisk Logo], `false` ![Tor Browser][Tor Browser Logo], n/a ![Android][Android Logo]

```js
user_pref("services.sync.engine.bookmarks", false);
user_pref("services.sync.engine.history", false);
user_pref("services.sync.engine.passwords", false);
```

Default: `true` ![Windows][Windows Logo] ![Debian][Debian Logo] ![Tor Browser][Tor Browser Logo] ![Basilisk][Basilisk Logo], n/a ![Android][Android Logo]

```js
user_pref("services.sync.serverURL", "");
```

Default: "https://auth.services.mozilla.com/" ![Windows][Windows Logo] ![Debian][Debian Logo] ![Basilisk][Basilisk Logo], n/a ![Android][Android Logo]

## Firefox Chat

```js
user_pref("loop.enabled", false);
```

Default: `false` ![Debian][Debian Logo], n/a ![Windows][Windows Logo] ![Tor Browser][Tor Browser Logo] ![Basilisk][Basilisk Logo] ![Android][Android Logo]

Firefox Hello (code name Loop) is video and voice chat feature built into the browser.
[[mozilla wiki](https://wiki.mozilla.org/Loop)]

## Mozilla Social

[Social API](https://developer.mozilla.org/en-US/docs/Mozilla/Projects/Social_API)

```js
user_pref("social.directories", "");
```

Default: "https://activations.cdn.mozilla.net" ![Windows][Windows Logo] ![Debian][Debian Logo] ![Tor Browser][Tor Browser Logo], " " ![Android][Android Logo], n/a ![Basilisk][Basilisk Logo]

```js
user_pref("social.remote-install.enabled", false);
```

Default: `true` ![Windows][Windows Logo] ![Debian][Debian Logo] ![Tor Browser][Tor Browser Logo], `false` ![Android][Android Logo], n/a ![Basilisk][Basilisk Logo]

```js
user_pref("social.shareDirectory", "");
```

Default: "https://activations.cdn.mozilla.net/sharePanel.html" ![Windows][Windows Logo] ![Debian][Debian Logo] ![Tor Browser][Tor Browser Logo], n/a ![Basilisk][Basilisk Logo] ![Android][Android Logo]

```js
user_pref("social.share.activationPanelEnabled", false);
```

Default: `true` ![Windows][Windows Logo] ![Debian][Debian Logo] ![Tor Browser][Tor Browser Logo], n/a ![Basilisk][Basilisk Logo] ![Android][Android Logo]

```js
user_pref("social.toast-notifications.enabled", false);
```

Default: `true` ![Windows][Windows Logo] ![Debian][Debian Logo] ![Tor Browser][Tor Browser Logo], `false` ![Android][Android Logo], n/a ![Basilisk][Basilisk Logo]

```js
user_pref("social.whitelist", "");
```

Default: "https://mozsocial.cliqz.com" ![Windows][Windows Logo] ![Debian][Debian Logo] ![Tor Browser][Tor Browser Logo] ![Android][Android Logo], n/a ![Basilisk][Basilisk Logo]

## Home Page

```js
user_pref("browser.startup.homepage", "about:blank");
```

Default: "about:home" ![Windows][Windows Logo] ![Debian][Debian Logo] ![Tor Browser][Tor Browser Logo] ![Basilisk][Basilisk Logo], n/a ![Android][Android Logo]

[[mozilla wiki](https://wiki.mozilla.org/Firefox/Projects/Firefox_Start/Snippet_Service)]:
`about:home` fetches content from the production snippets service once every 24 hours. If content is available, it gets is stashed in local storage for the page and displayed from there until the next fetch. If no content is available, the browser has a built-in default set of snippets for display.

```js
user_pref("browser.startup.homepage_override.mstone", "ignore");
```

Default: n/a ![Windows][Windows Logo] ![Debian][Debian Logo] ![Tor Browser][Tor Browser Logo] ![Basilisk][Basilisk Logo] ![Android][Android Logo]

This preference is examined during browser start up. If its value differs from the browser's current milestone, then Firefox connects and fetches content from Mozilla snippets server. `ignore`: the browser's homepage will not be overridden after updates [[mozillaZine](http://kb.mozillazine.org/Browser.startup.homepage_override.mstone)]. _Note_: Firefox for Android overrides this user preference and set it to actual Firefox version?!

```js
user_pref("browser.aboutHomeSnippets.updateUrl", "https://127.0.0.1");
```

Default: "https://snippets.cdn.mozilla.net/%STARTPAGE_VERSION%/%NAME%/%VERSION%/%APPBUILDID%/%BUILD_TARGET%/%LOCALE%/%CHANNEL%/%OS_VERSION%/%DISTRIBUTION%/%DISTRIBUTION_VERSION%/" ![Windows][Windows Logo] ![Debian][Debian Logo] ![Tor Browser][Tor Browser Logo] ![Basilisk][Basilisk Logo], n/a ![Android][Android Logo]. [[mozilla wiki](https://wiki.mozilla.org/Firefox/Projects/Firefox_Start/Snippet_Service)]

### Messages on Home Page

[How to stop Firefox messages on home screen?](https://support.mozilla.org/en-US/questions/1035229)

```js
user_pref("browser.snippets.enabled", false);
user_pref("browser.snippets.syncPromo.enabled", false);
```

Default: n/a ![Windows][Windows Logo] ![Debian][Debian Logo] ![Tor Browser][Tor Browser Logo] ![Basilisk][Basilisk Logo], `false` ![Android][Android Logo]

```js
user_pref("browser.snippets.firstrunHomepage.enabled", false);
```

Default: n/a ![Windows][Windows Logo] ![Debian][Debian Logo] ![Tor Browser][Tor Browser Logo] ![Basilisk][Basilisk Logo], `true` ![Android][Android Logo]

```js
user_pref("browser.snippets.updateUrl", "http://127.0.0.1");
```

Default: n/a ![Windows][Windows Logo] ![Debian][Debian Logo] ![Tor Browser][Tor Browser Logo] ![Basilisk][Basilisk Logo], "http://127.0.0.1" ![Android][Android Logo]

```js
user_pref("browser.snippets.statsUrl", "http://127.0.0.1");
```

Default: n/a ![Windows][Windows Logo] ![Debian][Debian Logo] ![Tor Browser][Tor Browser Logo] ![Basilisk][Basilisk Logo], "http://127.0.0.1" ![Android][Android Logo]

```js
user_pref("browser.snippets.geoUrl", "http://127.0.0.1");
```

Default: n/a ![Windows][Windows Logo] ![Debian][Debian Logo] ![Tor Browser][Tor Browser Logo] ![Basilisk][Basilisk Logo], "http://127.0.0.1" ![Android][Android Logo]

## New Tab

```js
user_pref("browser.newtabpage.introShown", true);
```

Default: `false` ![Windows][Windows Logo] ![Debian][Debian Logo] ![Basilisk][Basilisk Logo], `true` ![Tor Browser][Tor Browser Logo], n/a ![Android][Android Logo]

```js
user_pref("browser.newtabpage.enabled", false);
user_pref("browser.newtabpage.enhanced", false);
```

Default: `true` ![Windows][Windows Logo] ![Debian][Debian Logo] ![Tor Browser][Tor Browser Logo] ![Basilisk][Basilisk Logo], n/a ![Android][Android Logo]

Setting `enabled` and `enhanced` to `false` disables top and suggested sites (equivalent to blank page).

```js
user_pref("browser.newtabpage.directory.source", "data:application/json,{}");
```

Default: "https://tiles.services.mozilla.com/v3/links/fetch/%LOCALE%/%CHANNEL%" ![Windows][Windows Logo] ![Debian][Debian Logo] ![Basilisk][Basilisk Logo], "data:text/plain," ![Tor Browser][Tor Browser Logo], n/a ![Android][Android Logo]. [[Mozilla Source Tree Docs](http://gecko.readthedocs.io/en/latest/browser/browser/DirectoryLinksProvider.html#browser-newtabpage-directory-source)]

```js
user_pref("browser.newtabpage.directory.ping", "");
```

Default: "https://tiles.services.mozilla.com/v3/links/" ![Windows][Windows Logo] ![Debian][Debian Logo] ![Basilisk][Basilisk Logo], "data:text/plain," ![Tor Browser][Tor Browser Logo], n/a ![Android][Android Logo]. [[Mozilla Source Tree Docs](http://gecko.readthedocs.io/en/latest/browser/browser/DirectoryLinksProvider.html#browser-newtabpage-directory-ping)]

```js
user_pref("browser.newtab.preload", false);
```

Default: `true` ![Windows][Windows Logo] ![Debian][Debian Logo] ![Tor Browser][Tor Browser Logo] ![Basilisk][Basilisk Logo], n/a ![Android][Android Logo]

```js
user_pref("browser.tabs.animate", false);
```

Default:
`true`
  ![Windows][Windows Logo]
  ![Debian][Debian Logo]
  ![Tor Browser][Tor Browser Logo]
  ![Basilisk][Basilisk Logo],
n/a
  ![Android][Android Logo].
([-FF54](https://bugzilla.mozilla.org/show_bug.cgi?id=1352069))

It was substituted by `toolkit.cosmeticAnimations.enabled` in FF55+.

[Tab animation | mozilla wiki](https://wiki.mozilla.org/Firefox/Projects/Tab_animation)

```js
user_pref("browser.tabs.loadInBackground", false);
```

Default: `true` ![Windows][Windows Logo] ![Debian][Debian Logo] ![Tor Browser][Tor Browser Logo] ![Basilisk][Basilisk Logo], n/a ![Android][Android Logo]

`false`:  Open link in a new tab and automatically switch into that tab. [[mozillaZine](http://kb.mozillazine.org/About:config_entries#Browser.)]

## Pocket

[[mozilla support](https://support.mozilla.org/en-US/kb/save-web-pages-later-pocket-firefox)] [[ghacks.net](http://www.ghacks.net/2015/05/14/how-to-disable-pocket-in-firefox/)]

```js
user_pref("browser.pocket.enabled", false);
```

Default: `true` ![Windows][Windows Logo] ![Debian][Debian Logo], `false` ![Tor Browser][Tor Browser Logo], n/a ![Android][Android Logo], replaced by `extensions.pocket.enabled` and set to `true` ![Basilisk][Basilisk Logo]. [[Mozilla Support Forum](https://support.mozilla.org/en-US/questions/1087570)]

```js
user_pref("browser.pocket.api", "");
```

Default: "api.getpocket.com" ![Windows][Windows Logo] ![Debian][Debian Logo], "" ![Tor Browser][Tor Browser Logo], n/a ![Basilisk][Basilisk Logo] ![Android][Android Logo]. [[Mozilla Support Forum](https://support.mozilla.org/en-US/questions/1087570)]

```js
user_pref("browser.pocket.site", "");
```

Default: "getpocket.com" ![Windows][Windows Logo] ![Debian][Debian Logo], "" ![Tor Browser][Tor Browser Logo], n/a ![Basilisk][Basilisk Logo] ![Android][Android Logo]. [[Mozilla Support Forum](https://support.mozilla.org/en-US/questions/1087570)]

```js
user_pref("browser.pocket.oAuthConsumerKey", "");
```

Default: "_your-consumer-key_" ![Windows][Windows Logo] ![Debian][Debian Logo] ![Tor Browser][Tor Browser Logo], n/a ![Basilisk][Basilisk Logo] ![Android][Android Logo]

## Statistics

### Timing

[NavigationTimingAPI - mozilla wiki](https://wiki.mozilla.org/Security/Reviews/Firefox/NavigationTimingAPI)

[Navigation Timing - W3C](http://www.w3.org/TR/2011/CR-navigation-timing-20110315/#nt-navigation-timing-interface)

[Performance API - MDN](https://developer.mozilla.org/en-US/docs/Web/API/Performance_API)

```js
user_pref("dom.enable_performance", false);
```

Default:
`true`
  ![Windows][Windows Logo]
  ![Debian][Debian Logo]
  ![Basilisk][Basilisk Logo]
  ![Android][Android Logo],
`false`
  ![Tor Browser][Tor Browser Logo]
([FF23+](https://bugzilla.mozilla.org/show_bug.cgi?id=870667))

`false`: Do not send start and end time of web page loading. [[forum.mozilla-russia.org](http://forum.mozilla-russia.org/viewtopic.php?pid=653380#p653380) (in Russian)]

[Resource Timing API - MDN](https://developer.mozilla.org/en-US/docs/Web/API/Resource_Timing_API)

```js
user_pref("dom.enable_resource_timing", false);
```

Default:
`true`
  ![Windows][Windows Logo]
  ![Debian][Debian Logo]
  ![Basilisk][Basilisk Logo]
  ![Android][Android Logo],
`false`
  ![Tor Browser][Tor Browser Logo]
([FF35+](https://bugzilla.mozilla.org/show_bug.cgi?id=1002855))


[User Timing - W3C](https://www.w3.org/TR/2013/REC-user-timing-20131212/)

```js
user_pref("dom.enable_user_timing", false);
```

Default:
`true`
  ![Windows][Windows Logo]
  ![Debian][Debian Logo]
  ![Basilisk][Basilisk Logo]
  ![Android][Android Logo],
`false`
  ![Tor Browser][Tor Browser Logo]
([FF38](https://bugzilla.mozilla.org/show_bug.cgi?id=782751)-[FF54](https://bugzilla.mozilla.org/show_bug.cgi?id=1344669))


```js
user_pref("dom.idle-observers-api.enabled", false);
```

Default:
`true`
  ![Windows][Windows Logo]
  ![Debian][Debian Logo]
  ![Tor Browser][Tor Browser Logo]
  ![Basilisk][Basilisk Logo]
  ![Android][Android Logo]
([-FF58](https://bugzilla.mozilla.org/show_bug.cgi?id=1416703))

### Video Stats

Provides web applications with information about video playback statistics such as the framerate [[ghacks.net](http://www.ghacks.net/overview-firefox-aboutconfig-security-privacy-preferences/)]

```js
user_pref("media.video_stats.enabled", false);
```

Default: `true` ![Windows][Windows Logo] ![Debian][Debian Logo] ![Basilisk][Basilisk Logo] ![Android][Android Logo], `false` ![Tor Browser][Tor Browser Logo] (FF25+)

[Bug 654550: Preference to disable video statistics | Bugzilla](https://bugzilla.mozilla.org/show_bug.cgi?id=654550)

## Web API

WebAPI allows Web apps and content to access device hardware (such as battery status or the device vibration hardware), as well as access to data stored on the device (such as the calendar or contacts list) [[MDN](https://developer.mozilla.org/en-US/docs/WebAPI)].
[[WebAPI - MozillaWiki](https://wiki.mozilla.org/WebAPI)]

### Battery API

[[BatteryManager - MDN](https://developer.mozilla.org/en-US/docs/Web/API/BatteryManager)]

```js
user_pref("dom.battery.enabled", false);
```

Default: `true` ![Windows][Windows Logo] ![Debian][Debian Logo] ![Basilisk][Basilisk Logo], `false` ![Tor Browser][Tor Browser Logo] ![Android][Android Logo].
[[TechCrunch](https://techcrunch.com/2015/08/04/battery-attributes-can-be-used-to-track-web-users/)]

### Beacon API

[[Wikipedia](https://en.wikipedia.org/wiki/Web_beacon)]: A web beacon is an object embedded in a web page or email, which unobtrusively (usually invisibly) allows checking that a user has accessed the content. Common uses are email tracking and page tagging for web analytics.

[[MDN](https://developer.mozilla.org/en-US/docs/Web/API/Beacon_API)]: Example use cases of the Beacon API are logging activity and sending analytics data to the server.

```js
user_pref("beacon.enabled", false);
```

Default: `true` ![Windows][Windows Logo] ![Debian][Debian Logo] ![Tor Browser][Tor Browser Logo] ![Basilisk][Basilisk Logo] ![Android][Android Logo]

### Camera API

[Camera API - MDN](https://developer.mozilla.org/en-US/docs/Mozilla/B2G_OS/API/Camera_API)

```js
user_pref("device.camera.enabled", false);
```

Default: n/a ![Windows][Windows Logo] ![Debian][Debian Logo] ![Tor Browser][Tor Browser Logo] ![Basilisk][Basilisk Logo], `true` ![Android][Android Logo]

```js
user_pref("camera.control.face_detection.enabled", false);
```

Default: `true` ![Windows][Windows Logo] ![Debian][Debian Logo] ![Tor Browser][Tor Browser Logo] ![Basilisk][Basilisk Logo], `false` ![Android][Android Logo]

### CSS Font Loading API

[CSS Font Loading API - MDN](https://developer.mozilla.org/en-US/docs/Web/API/CSSFontLoading_API)

```js
user_pref("layout.css.font-loading-api.enabled", false);
```

Default: `true` ![Windows][Windows Logo] ![Debian][Debian Logo] ![Tor Browser][Tor Browser Logo] ![Basilisk][Basilisk Logo] ![Android][Android Logo]

### Device Storage API

```js
user_pref("device.storage.enabled", false);
```

Default: `false` ![Windows][Windows Logo] ![Debian][Debian Logo] ![Tor Browser][Tor Browser Logo] ![Basilisk][Basilisk Logo], `true` ![Android][Android Logo]. [[mozilla wiki](https://wiki.mozilla.org/WebAPI/DeviceStorageAPI#Security.2FPrivacy_considerations)]

[Device Storage API - Mozilla | MDN](https://developer.mozilla.org/en-US/docs/Mozilla/B2G_OS/API/Device_Storage_API)

### Gamepad API

[[MDN](https://developer.mozilla.org/en-US/docs/Web/API/Gamepad_API/Using_the_Gamepad_API)] [[W3C](https://www.w3.org/TR/gamepad/)]

```js
user_pref("dom.gamepad.enabled", false);
```

Default: `true` ![Windows][Windows Logo] ![Debian][Debian Logo] ![Basilisk][Basilisk Logo] ![Android][Android Logo], `false` ![Tor Browser][Tor Browser Logo]

### Geolocation API

[Geolocation - Web APIs | MDN](https://developer.mozilla.org/en-US/docs/Web/API/Geolocation)

```js
user_pref("geo.enabled", false);
```

Default: `true` ![Windows][Windows Logo] ![Debian][Debian Logo] ![Basilisk][Basilisk Logo], `false` ![Tor Browser][Tor Browser Logo] ![Android][Android Logo]. [[mozilla](https://www.mozilla.org/en-US/firefox/geolocation/)]

```js
user_pref("geo.wifi.logging.enabled", false);
```

Default: n/a ![Windows][Windows Logo] ![Debian][Debian Logo] ![Tor Browser][Tor Browser Logo] ![Basilisk][Basilisk Logo] ![Android][Android Logo]

```js
user_pref("geo.wifi.xhr.timeout", 1);
```

Default: `60000` ![Windows][Windows Logo] ![Debian][Debian Logo] ![Tor Browser][Tor Browser Logo] ![Basilisk][Basilisk Logo] ![Android][Android Logo]

```js
user_pref("geo.wifi.uri", "https://127.0.0.1");
```

Default: "https://www.googleapis.com/geolocation/v1/geolocate?key=%GOOGLE_API_KEY%" ![Windows][Windows Logo] ![Debian][Debian Logo], "http://ip-api.com/json/?fields=lat,lon,status,message" ![Basilisk][Basilisk Logo], "(empty string)" ![Tor Browser][Tor Browser Logo], n/a ![Android][Android Logo]

The information around you (mac addresses, signal strengths, SSIDs and etc.) is transmitted to Google Location Services in order to locate you [[stackoverflow](http://stackoverflow.com/a/5134619)].

[Geolocation Test](http://html5demos.com/geo)

#### Geolocation-Based Search

[[mozilla-central](https://dxr.mozilla.org/mozilla-central/source/layout/tools/reftest/reftest-preferences.js#58)]: Tell the search service we are running in the US:

```js
user_pref("browser.search.countryCode", "US");
user_pref("browser.search.region", "US");
```

Default: n/a ![Windows][Windows Logo] ![Debian][Debian Logo] ![Basilisk][Basilisk Logo] ![Android][Android Logo], "US" ![Tor Browser][Tor Browser Logo]. [[Tor Bug #16254](https://trac.torproject.org/projects/tor/ticket/16254)]

```js
user_pref("browser.search.isUS", true);
```

Default: n/a ![Windows][Windows Logo] ![Debian][Debian Logo] ![Basilisk][Basilisk Logo] ![Tor Browser][Tor Browser Logo] ![Android][Android Logo]

```js
user_pref("browser.search.geoSpecificDefaults", false);
```

Default: `true` ![Windows][Windows Logo] ![Android][Android Logo], `false` ![Debian][Debian Logo] ![Tor Browser][Tor Browser Logo] ![Basilisk][Basilisk Logo]. [[ghacks](http://www.ghacks.net/2015/08/18/a-comprehensive-list-of-firefox-privacy-and-security-settings/)]

```js
user_pref("browser.search.geoSpecificDefaults.url", "");
```

Default: "https://search.services.mozilla.com/1/%APP%/%VERSION%/%CHANNEL%/%LOCALE%/%REGION%/%DISTRIBUTION%/%DISTRIBUTION_VERSION%" ![Windows][Windows Logo] ![Debian][Debian Logo] ![Tor Browser][Tor Browser Logo] ![Android][Android Logo], "(_empty string_)" ![Basilisk][Basilisk Logo]

```js
user_pref("browser.search.geoip.timeout", 1);
```

Default: `2000` ![Windows][Windows Logo] ![Debian][Debian Logo] ![Tor Browser][Tor Browser Logo] ![Basilisk][Basilisk Logo] ![Android][Android Logo]. [[Raven Wiki](https://wiki.kairaven.de/open/app/firefox)]

```js
user_pref("browser.search.geoip.url", "");
```

Default: "https://location.services.mozilla.com/v1/country?key=%MOZILLA_API_KEY%" ![Windows][Windows Logo] ![Debian][Debian Logo] ![Basilisk][Basilisk Logo] ![Android][Android Logo], "(_empty string_)" ![Tor Browser][Tor Browser Logo]. [[mozilla support](https://support.mozilla.org/en-US/kb/how-stop-firefox-making-automatic-connections#w_geolocation-for-default-search-engine)]

### Keyboard API

[KeyboardEvent.code - MDN](https://developer.mozilla.org/en-US/docs/Web/API/KeyboardEvent/code)

```js
user_pref("dom.keyboardevent.code.enabled", false);
```

Default:
`true`
  ![Windows][Windows Logo]
  ![Debian][Debian Logo]
  ![Tor Browser][Tor Browser Logo]
  ![Basilisk][Basilisk Logo]
  ![Android][Android Logo]
([-FF54](https://bugzilla.mozilla.org/show_bug.cgi?id=1352949))

[Privacy-Handbuch.de](https://www.privacy-handbuch.de/handbuch_21v.htm) (in German)

### Network Information API

[[Network Information API - MDN](https://developer.mozilla.org/en-US/docs/Web/API/Network_Information_API)]

```js
user_pref("dom.netinfo.enabled", false);
```

Default: `false` ![Windows][Windows Logo] ![Debian][Debian Logo] ![Tor Browser][Tor Browser Logo] ![Basilisk][Basilisk Logo], `true` ![Android][Android Logo]. [[wicg.io](https://wicg.github.io/netinfo/)]

### Notification API

[[Notifications API - MDN](https://developer.mozilla.org/en-US/docs/Web/API/Notifications_API)] [[Notification - MDN](https://developer.mozilla.org/en-US/docs/Web/API/notification)]

```js
user_pref("dom.webnotifications.enabled", false);
```

Default:
`true`
  ![Windows][Windows Logo]
  ![Debian][Debian Logo]
  ![Tor Browser][Tor Browser Logo]
  ![Basilisk][Basilisk Logo]
  ![Android][Android Logo]

[Pull #111: Disable WebPush? - pyllyukko/user.js](https://github.com/pyllyukko/user.js/pull/111)


### Sensor API

[[Sensor API - mozilla wiki](https://wiki.mozilla.org/Sensor_API)]

```js
user_pref("device.sensors.enabled", false);
```

Default: `true` ![Windows][Windows Logo] ![Debian][Debian Logo] ![Basilisk][Basilisk Logo], `false` ![Tor Browser][Tor Browser Logo] ![Android][Android Logo].
[[Tor Bug #15758](https://trac.torproject.org/projects/tor/ticket/15758)]

### Vibration API

[[MDN](https://developer.mozilla.org/en-US/docs/Web/API/Vibration_API)] [[W3C](https://w3c.github.io/vibration/)]

```js
user_pref("dom.vibrator.enabled", false);
```

Default: `true` ![Windows][Windows Logo] ![Debian][Debian Logo] ![Tor Browser][Tor Browser Logo] ![Basilisk][Basilisk Logo] ![Android][Android Logo]

## Auto Play

### Animated Image

```js
user_pref("image.animation_mode", "none");
```

Default: "normal" ![Windows][Windows Logo] ![Debian][Debian Logo] ![Tor Browser][Tor Browser Logo] ![Basilisk][Basilisk Logo] ![Android][Android Logo]

`none`: animated images will never play [[mozillaZine](http://kb.mozillazine.org/Firefox_:_Tips_:_Animated_Images)].

### Videos

```js
user_pref("media.autoplay.enabled", false);
```

Default: `true` ![Windows][Windows Logo] ![Debian][Debian Logo] ![Tor Browser][Tor Browser Logo] ![Basilisk][Basilisk Logo] ![Android][Android Logo]. [[ghacks.net](http://www.ghacks.net/2016/05/06/how-to-stop-auto-playing-videos/)]

`false` may break video playback on various sites.

## Bookmarks

```js
user_pref("browser.bookmarks.max_backups", 2);
```

Default: `15` ![Windows][Windows Logo] ![Debian][Debian Logo] ![Tor Browser][Tor Browser Logo] ![Basilisk][Basilisk Logo], `5` ![Android][Android Logo]. [[mozillazine](http://kb.mozillazine.org/Browser.bookmarks.max_backups)]

## Cache

```js
user_pref("browser.cache.disk.parent_directory", "R:\TEMP\FirefoxCache");
```
Default: n/a. [[mozillaZine](http://kb.mozillazine.org/Browser.cache.disk.parent_directory)]

To use RAM disk for caching is good for systems with big enough RAM.

## Developer Tools

### WebIDE

[WebIDE - MDN](https://developer.mozilla.org/en-US/docs/Tools/WebIDE)

[16222: Review networking code for Firefox 38 | Tor Trac](https://trac.torproject.org/projects/tor/ticket/16222)

```js
user_pref("devtools.webide.enabled", false);
```

Default:
`true`
  ![Windows][Windows Logo]
  ![Debian][Debian Logo]
  ![Basilisk][Basilisk Logo],
`false`
  ![Tor Browser][Tor Browser Logo],
n/a
  ![Android][Android Logo]


```js
user_pref("devtools.webide.autoinstallADBHelper", false);
```

Default:
`true`
  ![Windows][Windows Logo]
  ![Basilisk][Basilisk Logo],
`false`
  ![Debian][Debian Logo]
  ![Tor Browser][Tor Browser Logo],
n/a
  ![Android][Android Logo]


```js
user_pref("devtools.webide.autoinstallFxdtAdapters", false);
```

Default:
`true`
  ![Windows][Windows Logo]
  ![Basilisk][Basilisk Logo],
`false`
  ![Debian][Debian Logo]
  ![Tor Browser][Tor Browser Logo],
n/a
  ![Android][Android Logo]
([-FF56](https://bugzilla.mozilla.org/show_bug.cgi?id=1393497))


## DOM

### Clipboard

```js
user_pref("dom.allow_cut_copy", false);
```

Default: n/a ![Windows][Windows Logo] ![Debian][Debian Logo] ![Tor Browser][Tor Browser Logo] ![Basilisk][Basilisk Logo] ![Android][Android Logo]. [[reddit](https://www.reddit.com/r/firefox/comments/5upj7a/disable_js_access_to_clipboard/)] [[Bug 1170911](https://bugzilla.mozilla.org/show_bug.cgi?id=1170911)]

```js
user_pref("dom.event.clipboardevents.enabled", false);
```

Default: `true` ![Windows][Windows Logo] ![Debian][Debian Logo] ![Tor Browser][Tor Browser Logo] ![Basilisk][Basilisk Logo], `false` ![Android][Android Logo]

`false`: Do not let websites to get notifications if the user copies, pastes, or cuts something from a web page, and do not let them know which part of the page has been selected [[MDN](https://developer.mozilla.org/en-US/docs/Mozilla/Preferences/Preference_reference/dom.event.clipboardevents.enabled)].

### Context Menu

[][DOM Entries - mozillaZine]

[DOM entries - mozillaZine]: http://kb.mozillazine.org/About:config_entries#DOM.

```js
user_pref("dom.event.contextmenu.enabled", false);
```

Default: `true` ![Windows][Windows Logo] ![Debian][Debian Logo] ![Tor Browser][Tor Browser Logo] ![Basilisk][Basilisk Logo] ![Android][Android Logo]

`false`: Webpages will not be able to affect the context menu event [[DOM Entries - mozillaZine]].

### Device Name

```js
user_pref("dom.presentation.device.name", "dummy-device");
```

Default: n/a ![Windows][Windows Logo] ![Debian][Debian Logo] ![Tor Browser][Tor Browser Logo] ![Basilisk][Basilisk Logo] ![Android][Android Logo]

_Note_: Firefox for Android sets name of your device. [[Bug 1265275]](https://bugzilla.mozilla.org/show_bug.cgi?id=1265275)

### Popup Windows

```js
user_pref("dom.popup_maximum", 3);
```

Default: 20 ![Windows][Windows Logo] ![Debian][Debian Logo] ![Tor Browser][Tor Browser Logo] ![Basilisk][Basilisk Logo] ![Android][Android Logo]. [[mozillaZine](http://kb.mozillazine.org/Dom.popup_maximum)]

### Storage

```js
user_pref("dom.storage.enabled", true);
```

Default: `true` ![Windows][Windows Logo] ![Debian][Debian Logo] ![Tor Browser][Tor Browser Logo] ![Basilisk][Basilisk Logo] ![Android][Android Logo].

`false` may break some sites.

[Web Storage - Wikipedia](https://en.wikipedia.org/wiki/Web_storage)

[Web Storage API - MDN](https://developer.mozilla.org/en-US/docs/Web/API/Web_Storage_API)

### Window

```js
user_pref("dom.disable_window_move_resize", true);
```

Default: `false` ![Windows][Windows Logo] ![Debian][Debian Logo] ![Tor Browser][Tor Browser Logo] ![Basilisk][Basilisk Logo], `true` ![Android][Android Logo]

`true`: Windows may not be moved or resized [[DOM Entries - mozillaZine]].

```js
user_pref("dom.disable_window_open_feature.close", true);
```

Default: `false` ![Windows][Windows Logo] ![Debian][Debian Logo] ![Tor Browser][Tor Browser Logo] ![Basilisk][Basilisk Logo] ![Android][Android Logo]

`true`: Prevent close button from being disabled [[DOM Entries - mozillaZine]].

```js
user_pref("dom.disable_window_open_feature.location", true);
```

Default: `true` ![Windows][Windows Logo] ![Debian][Debian Logo] ![Tor Browser][Tor Browser Logo] ![Basilisk][Basilisk Logo], `false` ![Android][Android Logo]

`true`: Prevent popups from hiding the Location Bar [[mozillaZine](http://kb.mozillazine.org/Dom.disable_window_open_feature.location)].

```js
user_pref("dom.disable_window_open_feature.menubar", true);
```

Default: `false` ![Windows][Windows Logo] ![Debian][Debian Logo] ![Tor Browser][Tor Browser Logo] ![Basilisk][Basilisk Logo] ![Android][Android Logo]

`true`: Prevent menubar from being hidden [[DOM Entries - mozillaZine]].

```js
user_pref("dom.disable_window_open_feature.minimizable", true);
```

Default: `false` ![Windows][Windows Logo] ![Debian][Debian Logo] ![Tor Browser][Tor Browser Logo] ![Basilisk][Basilisk Logo] ![Android][Android Logo]

`true`: Prevent popup window minimization from being disabled [[DOM Entries - mozillaZine]].

```js
user_pref("dom.disable_window_open_feature.personalbar", true);
```

Default: `false` ![Windows][Windows Logo] ![Debian][Debian Logo] ![Tor Browser][Tor Browser Logo] ![Basilisk][Basilisk Logo] ![Android][Android Logo]

`true`: Prevent bookmarks toolbar from being hidden [[DOM Entries - mozillaZine]].

```js
user_pref("dom.disable_window_open_feature.toolbar", true);
```

Default: `false` ![Windows][Windows Logo] ![Debian][Debian Logo] ![Tor Browser][Tor Browser Logo] ![Basilisk][Basilisk Logo] ![Android][Android Logo]

`true`: Prevent navigation toolbar from being hidden [[DOM Entries - mozillaZine]].

## Download Manager

```js
user_pref("browser.helperApps.deleteTempFileOnExit", true);
```

Default: `true` ![Windows][Windows Logo] ![Debian][Debian Logo] ![Tor Browser][Tor Browser Logo] ![Basilisk][Basilisk Logo], `false` ![Android][Android Logo]. [[mozillaZine](http://kb.mozillazine.org/About:config_entries#Browser.)]

```js
user_pref("browser.download.folderList", 2);
```

Default: `1` ![Windows][Windows Logo] ![Debian][Debian Logo] ![Tor Browser][Tor Browser Logo] ![Basilisk][Basilisk Logo] ![Android][Android Logo]

`1`: system default folder,
`2`: custom (user defined) folder. [[MDN](https://developer.mozilla.org/en-US/docs/Download_Manager_preferences)]

```js
user_pref("browser.download.useDownloadDir", false);
```

Default: `true` ![Windows][Windows Logo] ![Debian][Debian Logo] ![Basilisk][Basilisk Logo] ![Android][Android Logo], `false` ![Tor Browser][Tor Browser Logo].

`false`: Always ask where to download. [[MDN](https://developer.mozilla.org/en-US/docs/Download_Manager_preferences)]


## Fingerprinting

```js
user_pref("privacy.resistFingerprinting", true);
```

Default:
`false`
  ![NightlyWin][Nightly Firefox Windows Logo]
  ![NightlyAndroid][Nightly Firefox Android Logo]

[Security/Fingerprinting | mozilla wiki](https://wiki.mozilla.org/Security/Fingerprinting)

[Bug 418986: window.screen and CSS media queries provide a large amount of identifiable information (Tor 2875) | Bugzilla](https://bugzilla.mozilla.org/show_bug.cgi?id=418986)


[Bug 1333933: Disable/spoof fingerprintable features when privacy.resistFingerprinting = true | Bugzilla](https://bugzilla.mozilla.org/show_bug.cgi?id=1333933)

[meta: tor uplift: privacy.resistFingerprinting #7 | ghacks-user.js](https://github.com/ghacksuserjs/ghacks-user.js/issues/7)

## Fonts

### Document Fonts

```js
user_pref("browser.display.use_document_fonts", 0);
```

Default:
`1`
  ![Windows][Windows Logo]
  ![Debian][Debian Logo]
  ![Tor Browser][Tor Browser Logo]
  ![Basilisk][Basilisk Logo]
  ![Android][Android Logo]

`0` - never use document's fonts, `1` - allow documents to specify fonts to use [[mozillazine](http://kb.mozillazine.org/About:config_entries#Browser.)].

[[ghacks](https://github.com/ghacksuserjs/ghacks-user.js/blob/master/user.js)]: Disallowing document fonts drastically reduces font enumeration which is a high entropy fingerprinting vector. WARNING: Disabling fonts can uglify the web a fair bit.

[Font Fingerprinting - Fonts Detection - BrowserLeaks.com](https://browserleaks.com/fonts)

[Issue #120: Font fingerprinting - pyllyukko/user.js](https://github.com/pyllyukko/user.js/issues/120)

### SVG Fonts

[SVG OpenType Fonts](https://wiki.mozilla.org/SVGOpenTypeFonts)

```js
user_pref("gfx.font_rendering.opentype_svg.enabled", false);
```

Default: `true` ![Windows][Windows Logo] ![Debian][Debian Logo] ![Tor Browser][Tor Browser Logo] ![Basilisk][Basilisk Logo] ![Android][Android Logo]

## Forms

```js
user_pref("browser.formfill.enable", false);
```

Default: `true` ![Windows][Windows Logo] ![Debian][Debian Logo] ![Basilisk][Basilisk Logo] ![Android][Android Logo], `false` ![Tor Browser][Tor Browser Logo]

`false`: Do not save information entered in web page forms and the Search Bar [[mozillaZine](http://kb.mozillazine.org/About:config_entries#Browser.)].

```js
user_pref("browser.formfill.expire_days", 0);
```

Default: 180 ![Windows][Windows Logo] ![Debian][Debian Logo] ![Tor Browser][Tor Browser Logo] ![Basilisk][Basilisk Logo] ![Android][Android Logo]

```js
user_pref("browser.formfill.saveHttpsForms", false);
```

Default: `true` ![Basilisk][Basilisk Logo]. [[Bug 1361220 - Mozilla Bugzilla](https://bugzilla.mozilla.org/show_bug.cgi?id=1361220)]

## Fullscreen Animation

```js
user_pref("browser.fullscreen.animate", false);
```

Default:
`true`
  ![Windows][Windows Logo]
  ![Debian][Debian Logo]
  ![Tor Browser][Tor Browser Logo]
  ![Basilisk][Basilisk Logo],
n/a
  ![Android][Android Logo]
([-FF54](https://bugzilla.mozilla.org/show_bug.cgi?id=1352069))

It was substituted by `toolkit.cosmeticAnimations.enabled` in FF55+.

```js
user_pref("full-screen-api.warning.delay", 0);
user_pref("full-screen-api.warning.timeout", 0);
```

Default: `1` ![Basilisk][Basilisk Logo]. [Fullscreen API - MDN](https://developer.mozilla.org/en-US/docs/Web/API/Fullscreen_API)

## Location Bar

### Domain Guessing

Domain Guessing intercepts the DNS "hostname not found" error, and resends the
request to a guessed hostname that might use the correct domain [[Domain Guessing - Mozilla Archive](http://www-archive.mozilla.org/docs/end-user/domain-guessing.html)].

```js
user_pref("browser.fixup.alternate.enabled", false);
```

Default: `true` ![Windows][Windows Logo] ![Debian][Debian Logo] ![Basilisk][Basilisk Logo] ![Android][Android Logo], `false` ![Tor Browser][Tor Browser Logo]

`false`: Disable location bar domain guessing.

### Keyword Service

[[mozillaZine](http://kb.mozillazine.org/Keyword.enabled)]: When entering information in the Location Bar, Mozilla attempts to convert the information into a usable URI. For example, "mozilla.org" is automatically converted to "http://mozilla.org/". When Mozilla is unable to discern what URL the user wanted, the information that was entered may be submitted to an Internet Keywords service. This preference determines whether or not to use Internet Keywords.

```js
user_pref("keyword.enabled", false);
```

Default: `true` ![Windows][Windows Logo] ![Debian][Debian Logo] ![Tor Browser][Tor Browser Logo] ![Basilisk][Basilisk Logo] ![Android][Android Logo]

`false`: Do not use Internet Keywords and display an error message indicating the entered information is not a valid URL.

## Passwords

[Password Manager - mozillaZine](http://kb.mozillazine.org/Password_Manager)

[Master Password - mozilla support](https://support.mozilla.org/en-US/kb/use-master-password-protect-stored-logins)

```js
user_pref("signon.rememberSignons", false);
```

Default: `true` ![Windows][Windows Logo] ![Debian][Debian Logo] ![Basilisk][Basilisk Logo] ![Android][Android Logo], `false` ![Tor Browser][Tor Browser Logo]

`false`: Disable the Password Manager [[mozillaZine](http://kb.mozillazine.org/About:config_entries#Signon.)].

```js
user_pref("signon.autofillForms", false);
```

Default: `true` ![Windows][Windows Logo] ![Debian][Debian Logo] ![Basilisk][Basilisk Logo] ![Android][Android Logo], `false` ![Tor Browser][Tor Browser Logo]

`false`: Do not automatically fill sign-in forms with known usernames and passwords [[mozillaZine](http://kb.mozillazine.org/Signon.autofillForms)].

```js
user_pref("signon.storeWhenAutocompleteOff", false);
```

Default: `true` ![Windows][Windows Logo] ![Debian][Debian Logo] ![Tor Browser][Tor Browser Logo] ![Basilisk][Basilisk Logo] ![Android][Android Logo]

`false`: Do not ignore [`autocomplete=off` form feature](http://www.w3schools.com/tags/att_input_autocomplete.asp) that some websites use to prevent password storing or automatic fill out into sign-on forms, in other words, Firefox Password Manager (if it is enabled) will be not used on that websites. [[Mozilla Bugzilla](https://bugzilla.mozilla.org/show_bug.cgi?id=956906)]

```js
user_pref("signon.formlessCapture.enabled", false);
```

Default:
`true`
  ![NightlyWin][Nightly Firefox Windows Logo]
  ![NightlyAndroid][Nightly Firefox Android Logo]
(FF51+)

`false`: disable formless login capture for Password Manager.


## PDF Viewer

```js
user_pref("pdfjs.disabled", true);
```

Default: `false` ![Windows][Windows Logo] ![Debian][Debian Logo] ![Tor Browser][Tor Browser Logo] ![Basilisk][Basilisk Logo], n/a ![Android][Android Logo]. [[mozilla pdf.js FAQ](https://github.com/mozilla/pdf.js/wiki/Frequently-Asked-Questions)] [[mozilla support](https://support.mozilla.org/en-US/kb/view-pdf-files-firefox-without-downloading-them)]

## Reader Mode

```js
user_pref("reader.parse-on-load.enabled", false);
```

Default: `true` ![Windows][Windows Logo] ![Debian][Debian Logo] ![Basilisk][Basilisk Logo] ![Android][Android Logo], `false` ![Tor Browser][Tor Browser Logo]. [[ghacks.net](http://www.ghacks.net/2015/02/07/mozilla-starts-to-push-reader-mode-to-desktop-firefox/)]

## Search Suggestions

```js
user_pref("browser.search.suggest.enabled", false);
```

Default: `true` ![Windows][Windows Logo] ![Debian][Debian Logo] ![Basilisk][Basilisk Logo], `false` ![Tor Browser][Tor Browser Logo] ![Android][Android Logo]

`false`: Do not offer "search suggestions" of similar search queries as a user enters a query in the Search Bar. [[mozillaZine](http://kb.mozillazine.org/Browser.search.suggest.enabled)]

## Security

### First-Party Isolation

```js
user_pref("privacy.firstparty.isolate", true);
```

Default:
`false`
  ![NightlyWin][Nightly Firefox Windows Logo]
  ![NightlyAndroid][Nightly Firefox Android Logo]
([FF51+](https://bugzilla.mozilla.org/show_bug.cgi?id=1260931))

`true` may  break cross-domain logins and site functionality.

[Bug 1299996: META: Support Tor first-party isolation - Bugzilla](https://bugzilla.mozilla.org/show_bug.cgi?id=1299996)

[Security/FirstPartyIsolation - mozilla wiki](https://wiki.mozilla.org/Security/FirstPartyIsolation#First_Party_Isolation_-_FIXED)

[meta: tor uplift: privacy.firstparty.isolate #8 - ghacks-user.js](https://github.com/ghacksuserjs/ghacks-user.js/issues/8)


### Punycode Phishing

```js
user_pref("network.IDN_show_punycode", true);
```

Default: `false` ![Basilisk][Basilisk Logo]

[Internationalized Domain Name (IDN) homograph attack - wikipedia](https://en.wikipedia.org/wiki/IDN_homograph_attack)

[IDN Display Algorithm - mozilla wiki](https://wiki.mozilla.org/IDN_Display_Algorithm)

[Punycode Phishing Attacks - thehackernews.com](https://thehackernews.com/2017/04/unicode-Punycode-phishing-attack.html)


### SSL

```js
user_pref("security.ssl.treat_unsafe_negotiation_as_broken", true);
```

Default: `false` ![Windows][Windows Logo] ![Debian][Debian Logo] ![Tor Browser][Tor Browser Logo] ![Basilisk][Basilisk Logo], `true` ![Android][Android Logo]. [[mozilla wiki](https://wiki.mozilla.org/Security:Renegotiation#security.ssl.treat_unsafe_negotiation_as_broken)]

### XPConnect

[[MDN](https://developer.mozilla.org/en-US/docs/Mozilla/Tech/XPCOM/Language_bindings/XPConnect)]: XPConnect is a bridge between [JavaScript](https://developer.mozilla.org/en-US/docs/Web/JavaScript) and [XPCOM](https://developer.mozilla.org/en-US/docs/Mozilla/Tech/XPCOM). With XPConnect, you can use XPCOM components from JavaScript code, and interact with JavaScript objects from within XPCOM components. XPConnect is part of Firefox and is actively used in [XUL](https://developer.mozilla.org/en-US/docs/Mozilla/Tech/XUL) applications.

```js
user_pref("security.xpconnect.plugin.unrestricted", false);
```

Default: `true` ![Windows][Windows Logo] ![Debian][Debian Logo] ![Tor Browser][Tor Browser Logo] ![Basilisk][Basilisk Logo] ![Android][Android Logo]

## Session Store

[Firefox is eating your SSD - here is how to fix it](https://www.servethehome.com/firefox-is-eating-your-ssd-here-is-how-to-fix-it/)

```js
user_pref("browser.sessionstore.interval", 1800000);
```

Default: 15000 ![Windows][Windows Logo] ![Debian][Debian Logo] ![Tor Browser][Tor Browser Logo] ![Basilisk][Basilisk Logo], 10000 ![Android][Android Logo]

The preference controls how often information about the current session is saved to the profile.

```js
user_pref("browser.sessionstore.privacy_level", 2);
```

Default: 0 ![Windows][Windows Logo] ![Debian][Debian Logo] ![Basilisk][Basilisk Logo] ![Android][Android Logo], `2` ![Tor Browser][Tor Browser Logo]

`0`: store extra session data for any site,
`1`: store extra session data for unencrypted (non-HTTPS) sites only,
`2`: never store extra session data. [[mozillaZine](http://kb.mozillazine.org/Browser.sessionstore.privacy_level)]

## Startup

### Check Default Browser

```js
user_pref("browser.shell.checkDefaultBrowser", false);
```

Default: `true` ![Windows][Windows Logo], `false` ![Debian][Debian Logo] ![Tor Browser][Tor Browser Logo] ![Basilisk][Basilisk Logo], n/a ![Android][Android Logo]

`false`:  Do not check on startup if Firefox is set as default browser [[mozillaZine](http://kb.mozillazine.org/About:config_entries#Browser.)].

### Rights

[Bug 462254 - Bugzilla](https://bugzilla.mozilla.org/show_bug.cgi?id=462254)

```js
user_pref("browser.rights.3.shown", true);
```

Default: `false` ![Windows][Windows Logo] ![Debian][Debian Logo], `true` ![Tor Browser][Tor Browser Logo] ![Basilisk][Basilisk Logo], n/a ![Android][Android Logo]

### Slow Startup

```js
user_pref("browser.slowStartup.notificationDisabled", true);
```

Default: `false` ![Windows][Windows Logo] ![Debian][Debian Logo], `true` ![Tor Browser][Tor Browser Logo] ![Basilisk][Basilisk Logo] ![Android][Android Logo].

`false` disables "Slow startup" warnings [[Tor Bug #13346](https://trac.torproject.org/projects/tor/ticket/13346)].

```js
user_pref("browser.slowStartup.maxSamples", 0);
```

Default: `5` ![Windows][Windows Logo] ![Debian][Debian Logo] ![Basilisk][Basilisk Logo], `0` ![Tor Browser][Tor Browser Logo], n/a ![Android][Android Logo]

Firefox determines whether or not the browser is slow to start up by storing information about browser startup times to disk. `0` prevents this information from being stored [[Tor Bug #13346](https://trac.torproject.org/projects/tor/ticket/13346)].

## Thumbnails

```js
user_pref("browser.pagethumbnails.capturing_disabled", true);
```

Default: n/a (hidden preference) ![Windows][Windows Logo] ![Debian][Debian Logo] ![Tor Browser][Tor Browser Logo] ![Basilisk][Basilisk Logo] ![Android][Android Logo]

`true`: Do not create screenshots of visited pages which will be shown if the web page is shown in the grid of the "New Tab Page" [[MDN](https://developer.mozilla.org/en-US/docs/Mozilla/Preferences/Preference_reference/browser.pagethumbnails.capturing_disabled)]. The preference is available in the desktop versions of Firefox only.

## Video Buffering

```js
user_pref("media.mediasource.enabled", true);
```

Default: `true` ![Windows][Windows Logo] ![Debian][Debian Logo] ![Tor Browser][Tor Browser Logo] ![Basilisk][Basilisk Logo] ![Android][Android Logo]

WARNING: Setting to `false` results in lost support of "Media Source Extensions" and "MSE & H.264" in [YouTube HTML5 Video Player](https://www.youtube.com/html5) and some YouTube videos can not be played anymore.

[How to enforce full video buffering on YouTube - ghacks.net](http://www.ghacks.net/2016/08/31/how-to-enforce-full-video-buffering-on-youtube/)


## View Source

```js
user_pref("view_source.tab", false);
```

Default:
`true`
  ![NightlyWin][Nightly Firefox Windows Logo],
n/a
  ![NightlyAndroid][Nightly Firefox Android Logo]

`false`: open page source in a new window.


## WebGL

[[MDN](https://developer.mozilla.org/en-US/docs/Web/API/WebGL_API)] [[Security.StackExchange](https://security.stackexchange.com/questions/13799/is-webgl-a-security-concern)]

```js
user_pref("webgl.disabled", true);
```

Default: `false` ![Windows][Windows Logo] ![Debian][Debian Logo] ![Tor Browser][Tor Browser Logo] ![Basilisk][Basilisk Logo] ![Android][Android Logo]
