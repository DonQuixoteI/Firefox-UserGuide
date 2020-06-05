# user.js

## Index

- [Network](#network)
  - [Network Connectivity Service](#network-connectivity-service)
  - [Captive Portal Detection](#captive-portal-detection)
  - [Cookie](#cookie)
  - [HTTP Alternative Services](#http-alternative-services)
  - [IPv6 Name Lookups](#ipv6-name-lookups)
  - [Offline Status](#offline-status)
  - [Prefetching](#prefetching)
  - [Proxy](#proxy)
  - [Send Referer](#send-referer)
  - [SPDY](#spdy)
- [Reports to Mozilla and Data Collection](#reports-to-mozilla-and-data-collection)
  - [Crash Report](#crash-report)
  - [Health Report](#health-report)
  - [SSL Error Report](#ssl-error-report)
  - [Telemetry](#telemetry)
    - [Ping Centre](#ping-centre)
    - [Shield Studies](#shield-studies)
    - [Devtools Telemetry](#devtools-telemetry)
- [Safe Browsing](#safe-browsing)
- [Tracking Protection](#tracking-protection)
- [Updating](#updating)
  - [Extensions](#extensions-update)
  - [Search Engines](#search-engines-update)
  - [Web Apps](#web-apps-update)
  - [What is New](#what-is-new)
- [WebRTC](#webrtc)
  - [Gecko Media Plugins](#gecko-media-plugins)
  - [Get User Media](#get-user-media)
- [Digital Rights Management](#digital-rights-management)
- [Encrypted Media Extension](#encrypted-media-extension)
- [Extensions](#extensions)
  - [Extension Blocklist](#extension-blocklist)
  - [Extension Signing](#extension-signing)
  - [Get Add-ons Discovery Pane](#get-add-ons-discovery-pane)
  - [Legacy Extensions](#legacy-extensions)
  - [Web Compatibility Reporter](#web-compatibility-reporter)
  - [Personalized Extension Recommendations](#personalized-extension-recommendations)
  - [Extension Abuse Reporting](#extension-abuse-reporting)
- [Firefox Account](#firefox-account)
- [Home Page](#home-page)
  - [Messages on Home Page](#messages-on-home-page)
- [Tabs](#tabs)
  - [New Tab](#new-tab)
  - [Last Tab](#last-tab)
- [Onboarding](#onboarding)
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
  - [HTMLCanvasElement](#htmlcanvaselement)
  - [Network Information API](#network-information-api)
  - [Notification API](#notification-api)
  - [Push API](#push-api)
  - [Sensor API](#sensor-api)
  - [Vibration API](#vibration-api)
  - [WebGL API](#webgl-api)
  - [Web Speech API](#web-speech-api)
  - [WebVR API](#webvr-api)
- [Web Channel](#web-channel)
- [Accessibility Service](#accessibility-service)
- [Auto Play](#auto-play)
  - [Animated Image](#animated-image)
  - [Media](#media)
- [Bookmarks](#bookmarks)
- [Cache](#cache)
- [Clear History](#clear-history)
- [Closing Last Tab](#closing-last-tab)
- [Developer Tools](#developer-tools)
  - [WebIDE](#webide)
- [DOM](#dom)
  - [Clipboard](#clipboard)
  - [Context Menu](#context-menu)
  - [Device Name](#device-name)
  - [Storage](#storage)
  - [Window](#window)
- [Download Manager](#download-manager)
- [Fingerprinting](#fingerprinting)
  - [OS Locale](#os-locale)
- [Fonts](#fonts)
  - [Document Fonts](#document-fonts)
  - [SVG Fonts](#svg-fonts)
  - [Fonts with Incorrect Underline Offsets](#fonts-with-incorrect-underline-offsets)
- [Forms](#forms)
- [Animation](#animation)
  - [Fullscreen Animation](#fullscreen-animation)
  - [Reduced Motion](#reduced-motion)
- [Location Bar](#location-bar)
  - [Domain Guessing](#domain-guessing)
  - [Keyword Service](#keyword-service)
- [Mozilla Websites](#mozilla-websites)
- [Offline Data](#offline-data)
- [Passwords](#passwords)
- [PDF Viewer](#pdf-viewer)
- [Plugins](#plugins)
- [Popup Windows](#popup-windows)
- [Reader Mode](#reader-mode)
- [Screen Casting](#screen-casting)
- [Screen Resolution](#screen-resolution)
- [Search Suggestions](#search-suggestions)
- [Security](#security)
  - [Digital Certificates](#digital-certificates)
  - [First-Party Isolation](#first-party-isolation)
  - [Punycode Phishing](#punycode-phishing)
  - [SSL](#ssl)
- [Session Store](#session-store)
- [Smooth Scrolling](#smooth-scrolling)
- [Startup](#startup)
  - [Check Default Browser](#check-default-browser)
  - [Rights](#rights)
  - [Slow Startup](#slow-startup)
  - [Startup Page](#startup-page)
- [Thumbnails](#thumbnails)
- [UI Tour](#ui-tour)
- [Video Buffering](#video-buffering)
- [View Source](#view-source)
- [Warning on about config](#warning-on-about-config)


![Win][Windows Logo] - Mozilla Firefox 77.x (Windows),
![Debian][Debian Logo] - Firefox 77.x (Debian),
![Tor Browser][Tor Browser Logo] - Tor Browser 9.0.x (Firefox 68.x-esr),
![Android][Android Logo] - Mozilla Firefox 68.x (Android)

[Debian Logo]: img/Debian.svg

[Tor Browser Logo]: img/TorBrowser.png

[Windows Logo]: img/Windows.svg

[Android Logo]: img/Android.svg

## Network

[Mozilla networking preferences - MDN](https://developer.mozilla.org/en-US/docs/Mozilla/Preferences/Mozilla_networking_preferences)

### Network Connectivity Service

```js
user_pref("network.connectivity-service.enabled", false);
```

Default:
`true`
  ![Win][Windows Logo]
  ![Debian][Debian Logo]
  ![Android][Android Logo],
n/a
  ![Tor Browser][Tor Browser Logo].
  ([FF65+](https://bugzilla.mozilla.org/1460537))


### Captive Portal Detection

[Handling Captive Portals in Firefox](https://github.com/vtsatskin/FX-Captive-Portals-Design)

```js
user_pref("network.captive-portal-service.enabled", false);
```

Default:
`true`
  ![Win][Windows Logo]
  ![Debian][Debian Logo],
`false`
  ![Tor Browser][Tor Browser Logo]
  ![Android][Android Logo]
(FF52+). [[Tor Bug #21790](https://trac.torproject.org/projects/tor/ticket/21790)]


```js
user_pref("captivedetect.canonicalURL", "");
```

Default:
"http://detectportal.firefox.com/success.txt"
  ![Win][Windows Logo]
  ![Debian][Debian Logo]
  ![Tor Browser][Tor Browser Logo]
  ![Android][Android Logo]


### Cookie

```js
user_pref("network.cookie.cookieBehavior", 1);
```

Default:
`0`
  ![Win][Windows Logo]
  ![Debian][Debian Logo]
  ![Android][Android Logo],
`1`
  ![Tor Browser][Tor Browser Logo]

`0` - allow all cookies,
`1` - allow only from the originating server,
`2` - disallow all,
`3` - allow 3rd party if it already set a cookie,
`4` - reject trackers ([FF64+](https://github.com/mozilla/price-wise/issues/183)).

[mozillaZine](http://kb.mozillazine.org/Network.cookie.cookieBehavior)

This also controls access to 3rd party Web Storage, IndexedDB, Cache API and Service Worker Cache
[[fxsitecompat.com](https://www.fxsitecompat.com/en-CA/docs/2015/web-storage-indexeddb-cache-api-now-obey-third-party-cookies-preference/)].

WARNING: Blocking 3rd-party cookies breaks a number of payment gateways.


### HTTP Alternative Services

[RFC 7838 - HTTP Alternative Services](https://tools.ietf.org/html/rfc7838)

```js
user_pref("network.http.altsvc.enabled", false);
user_pref("network.http.altsvc.oe", false);
```

Default:
`true`
  ![Win][Windows Logo]
  ![Debian][Debian Logo]
  ![Tor Browser][Tor Browser Logo]
  ![Android][Android Logo]

[#16673: Isolate/Disable HTTP Alternative-Services - Tor Bug Tracker](https://trac.torproject.org/projects/tor/ticket/16673)


### IPv6 Name Lookups

[network.dns.disableIPv6 - mozillaZine](http://kb.mozillazine.org/Network.dns.disableIPv6)

```js
user_pref("network.dns.disableIPv6", true);
```

Default:
`false`
  ![Win][Windows Logo]
  ![Debian][Debian Logo]
  ![Tor Browser][Tor Browser Logo]
  ![Android][Android Logo].
[wiki.archlinux.de](https://wiki.archlinux.de/title/Firefox)


### Offline Status

[Online and offline events | MDN](https://developer.mozilla.org/en-US/docs/Online_and_offline_events)

```js
user_pref("network.manage-offline-status", false);
```

Default:
`true`
  ![Win][Windows Logo]
  ![Debian][Debian Logo]
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
  ![Win][Windows Logo]
  ![Debian][Debian Logo]
  ![Tor Browser][Tor Browser Logo]
  ![Android][Android Logo]

Link prefetching is a browser mechanism, which utilizes browser idle time to download or prefetch documents that the user might visit in the near future [[MDN](https://developer.mozilla.org/en-US/docs/Web/HTTP/Link_prefetching_FAQ)]. `false` disables link prefetching [[mozillaZine](http://kb.mozillazine.org/Network.prefetch-next)].


```js
user_pref("network.dns.disablePrefetch", true);
```

Default:
`false`
  ![Win][Windows Logo]
  ![Debian][Debian Logo]
  ![Android][Android Logo],
`true`
  ![Tor Browser][Tor Browser Logo]

[X-DNS-Prefetch-Control | MDN](https://developer.mozilla.org/en-US/docs/Web/HTTP/Headers/X-DNS-Prefetch-Control)

[Network.dns.disablePrefetch - mozillaZine](http://kb.mozillazine.org/Network.dns.disablePrefetch)


```js
user_pref("network.dns.disablePrefetchFromHTTPS", true);
```

Default:
`true`
  ![Win][Windows Logo]
  ![Debian][Debian Logo]
(FF70+),
n/a
  ![Tor Browser][Tor Browser Logo]
  ![Android][Android Logo]

By default, prefetching of embedded link hostnames is not performed on documents loaded over HTTPS [[MDN](https://developer.mozilla.org/en-US/docs/Web/HTTP/Headers/X-DNS-Prefetch-Control)].


```js
user_pref("network.predictor.enabled", false);
```

Default:
`true`
  ![Win][Windows Logo]
  ![Debian][Debian Logo]
  ![Android][Android Logo],
`false`
  ![Tor Browser][Tor Browser Logo]

The network predictor (formerly called '[seer](https://wiki.mozilla.org/Privacy/Reviews/Necko)') makes preemptive connections to resources in a page based on cached information. It can also do the same when the user hovers over a link. [[Tor](https://trac.torproject.org/projects/tor/ticket/16625)]

```js
user_pref("network.http.speculative-parallel-limit", 0);
```

Default:
`6`
  ![Win][Windows Logo]
  ![Debian][Debian Logo]
  ![Tor Browser][Tor Browser Logo]
  ![Android][Android Logo]
[[mozilla support](https://support.mozilla.org/en-US/kb/how-stop-firefox-making-automatic-connections#w_speculative-pre-connections)]


### Proxy

```js
user_pref("network.proxy.type", 0);
```

Default:
`5`
  ![Win][Windows Logo]
  ![Debian][Debian Logo]
  ![Android][Android Logo],
`1`
  ![Tor Browser][Tor Browser Logo].
[[mozillaZine](http://kb.mozillazine.org/Network.proxy.type)]


### Send Referer

```js
user_pref("network.http.sendRefererHeader", 2);
```

Default:
`2`
  ![Win][Windows Logo]
  ![Debian][Debian Logo]
  ![Tor Browser][Tor Browser Logo]
  ![Android][Android Logo]

0 - never send the referring URL,
1 - send only on clicked links,
2 - send for links and images
[[mozillaZine](http://kb.mozillazine.org/Network.http.sendRefererHeader)].


### [SPDY](https://en.wikipedia.org/wiki/SPDY)

```js
user_pref("network.http.spdy.enabled", false);
user_pref("network.http.spdy.enabled.deps", false);
user_pref("network.http.spdy.enabled.http2", false);
```

Default:
`true`
  ![Win][Windows Logo]
  ![Debian][Debian Logo]
  ![Tor Browser][Tor Browser Logo]
  ![Android][Android Logo]
[[ghacks-user.js](https://github.com/ghacksuserjs/ghacks-user.js/issues/107)]


## Reports to Mozilla and Data Collection

Firefox for Android, Firefox for iOS, Firefox Rocket and Firefox Focus collect data about installations and retention using a third-party tracking framework called Adjust and Leanplum [[mozilla support](https://support.mozilla.org/en-US/kb/send-usage-data-firefox-mobile-devices)].

[Mozilla Klar saugt Daten ab - deutschlandfunk.de](http://www.deutschlandfunk.de/anti-tracking-software-mozilla-klar-saugt-daten-ab.684.de.html?dram:article_id=378712) (in German)

[Firefox Focus: The 'Privacy Browser' with build in user tracking  | Born's Tech and Windows World](http://borncity.com/win/2017/02/12/firefox-focus-the-privacy-browser-with-build-in-user-tracking/)

[Firefox Focus privacy scandal - gHacks Tech News](http://www.ghacks.net/2017/02/12/firefox-focus-privacy-scandal/)

[Firefox/Data Collection - mozilla wiki](https://wiki.mozilla.org/Firefox/Data_Collection)

```js
user_pref("datareporting.policy.dataSubmissionEnabled", false);
```

Default:
`true`
  ![Win][Windows Logo]
  ![Android][Android Logo],
`false`
  ![Tor Browser][Tor Browser Logo],
`false` (locked via policies)
  ![Debian][Debian Logo]


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

Default:
"https://crash-stats.mozilla.com/report/index/"
  ![Win][Windows Logo]
  ![Debian][Debian Logo]
  ![Tor Browser][Tor Browser Logo]
  ![Android][Android Logo]

Set of libraries called `Breakpad` handles client-side crash reporting [[mozillaZine](http://kb.mozillazine.org/Breakpad.reportURL)].


```js
user_pref("dom.ipc.plugins.flash.subprocess.crashreporter.enabled", false);
```

Default:
`true`
  ![Win][Windows Logo]
  ![Debian][Debian Logo]
  ![Tor Browser][Tor Browser Logo]
  ![Android][Android Logo]

`false`: Do not send Flash crash reports [[ghacks.net](http://www.ghacks.net/2015/08/18/a-comprehensive-list-of-firefox-privacy-and-security-settings/)].

[[MDN](https://developer.mozilla.org/en-US/Firefox/Releases/43#Plugins)]: In preparation for future releases to switch over to multi-process content, NPAPI plugins can no longer be run in the same process as the page content. The preferences starting with `dom.ipc.plugins` are no longer used.


```js
user_pref("dom.ipc.plugins.reportCrashURL", false);
```

Default:
`true`
  ![Win][Windows Logo]
  ![Debian][Debian Logo]
  ![Tor Browser][Tor Browser Logo]
  ![Android][Android Logo]

`false`: Do not send the URL of the website where a plugin crashed [[ghacks.net](http://www.ghacks.net/2015/08/18/a-comprehensive-list-of-firefox-privacy-and-security-settings/)].


```js
user_pref("browser.tabs.crashReporting.sendReport", false);
```

Default:
`true`
  ![Win][Windows Logo]
  ![Debian][Debian Logo]
  ![Tor Browser][Tor Browser Logo],
n/a
  ![Android][Android Logo].
[[about:tabcrashed spec](https://people-mozilla.org/~mconley2/bugnotes/bug-1110511.html)]


```js
user_pref("browser.crashReports.unsubmittedCheck.enabled", false);
```

Default:
`true`
  ![Win][Windows Logo],
`false`
  ![Debian][Debian Logo]
  ![Tor Browser][Tor Browser Logo],
n/a
  ![Android][Android Logo]


### Health Report

[[mozilla](https://www.mozilla.org/en-US/privacy/firefox/#health-report)]: Firefox Health Report is designed to provide you with insights about your browser's stability and performance and with support tips should you experience issues, such as high crash rates or slow startup times. Mozilla collects and aggregates your data with that of other Firefox users and sends it back to your browser so you can see how your Firefox performance changes over time. This data includes, for example: device hardware, operating system, Firefox version, add-ons (count and type), timing of browser events, rendering, session restores, length of session, how old a profile is, count of crashes, and count of pages.

[[What is Firefox Health Report?](https://blog.mozilla.org/metrics/fhr-faq/)] [[What data are collected?](https://blog.mozilla.org/metrics/2012/09/21/firefox-health-report/)]

```js
user_pref("datareporting.healthreport.uploadEnabled", false);
```
Default:
`true`
  ![Win][Windows Logo],
`false`
  ![Debian][Debian Logo]
  ![Tor Browser][Tor Browser Logo],
n/a
  ![Android][Android Logo]


### SSL Error Report

[SSL Error Reporting - Mozilla Source Tree Docs](https://gecko.readthedocs.io/en/latest/browser/base/sslerrorreport/preferences.html)

```js
user_pref("security.ssl.errorReporting.enabled", false);
```

Default:
`true`
  ![Win][Windows Logo]
  ![Debian][Debian Logo]
  ![Android][Android Logo],
`false`
  ![Tor Browser][Tor Browser Logo]


```js
user_pref("security.ssl.errorReporting.url", "");
```

Default:
"https://incoming.telemetry.mozilla.org/submit/sslreports/"
  ![Win][Windows Logo]
  ![Debian][Debian Logo]
  ![Tor Browser][Tor Browser Logo]
  ![Android][Android Logo]


### Telemetry

> [[mozilla](https://www.mozilla.org/en-US/privacy/firefox/#telemetry)]:
> Telemetry is a feature in Firefox that sends Mozilla usage, performance, and responsiveness statistics about user interface features, memory, and hardware configuration. Your IP address is also collected as a part of a standard web log.

[Telemetry - Mozilla Source Tree Docs](https://firefox-source-docs.mozilla.org/toolkit/components/telemetry/telemetry/index.html)


```js
user_pref("toolkit.telemetry.unified", false);
```

Default:
`true`
  ![Win][Windows Logo]
  ![Debian][Debian Logo],
`false`
  ![Tor Browser][Tor Browser Logo]
  ![Android][Android Logo]

If `true`: Telemetry is always enabled and recording base data; Telemetry will send additional `main` pings [[Telemetry Preferences][telemetry-preferences]].

[telemetry-preferences]: https://firefox-source-docs.mozilla.org/toolkit/components/telemetry/telemetry/internals/preferences.html#id1


```js
user_pref("toolkit.telemetry.enabled", false);
```

Default:
locked `true`
  ![Win][Windows Logo],
  ![Debian][Debian Logo]
`true`
  ![Android][Android Logo],
`false` (locked)
  ![Tor Browser][Tor Browser Logo]

If `unified` is off, this controls whether the Telemetry module is enabled; if `unified` is on, this controls whether to record extended data [[Telemetry Preferences][telemetry-preferences]].


```js
user_pref("toolkit.telemetry.server", "");
```

Default:
"https://incoming.telemetry.mozilla.org"
  ![Win][Windows Logo]
  ![Debian][Debian Logo]
  ![Tor Browser][Tor Browser Logo]
  ![Android][Android Logo]

The server Telemetry pings are sent to [[Telemetry Preferences][telemetry-preferences]].


```js
user_pref("toolkit.telemetry.archive.enabled", false);
```

Default:
`true`
  ![Win][Windows Logo]
  ![Debian][Debian Logo]
  ![Tor Browser][Tor Browser Logo],
n/a
  ![Android][Android Logo]

[Telemetry Archiving - Mozilla Docs](https://firefox-source-docs.mozilla.org/toolkit/components/telemetry/telemetry/concepts/archiving.html)


```js
user_pref("toolkit.telemetry.bhrPing.enabled", false);
user_pref("toolkit.telemetry.firstShutdownPing.enabled", false);
user_pref("toolkit.telemetry.newProfilePing.enabled", false);
user_pref("toolkit.telemetry.shutdownPingSender.enabled", false);
user_pref("toolkit.telemetry.updatePing.enabled", false);
```

Default:
`true`
  ![Win][Windows Logo]
  ![Debian][Debian Logo]
  ![Tor Browser][Tor Browser Logo],
n/a
  ![Android][Android Logo]


```js
user_pref("toolkit.telemetry.reportingpolicy.firstRun", false);
```

Default:
n/a
  ![Win][Windows Logo]
  ![Debian][Debian Logo]
  ![Tor][Tor Browser Logo]
  ![Android][Android Logo]


```js
user_pref("toolkit.telemetry.hybridContent.enabled", false);
```

Default:
`true`
  ![Win][Windows Logo]
  ![Debian][Debian Logo]
  ![Tor Browser][Tor Browser Logo],
n/a
  ![Android][Android Logo]
([FF59+](https://bugzilla.mozilla.org/show_bug.cgi?id=1417473))

[Hybrid Content Telemetry - Mozilla Docs](https://firefox-source-docs.mozilla.org/toolkit/components/telemetry/telemetry/collection/hybrid-content.html)


#### Ping Centre

Ping Centre collects and sends your events and metrics to a staging server (metrics aggregator).

> [ping-centre](https://github.com/mozilla/ping-centre):
> The user does not need to specify the telemetry destination, i.e. the endpoint of the [Onyx](https://github.com/mozilla/onyx). Instead, the user just specifies the topic of the payload. In fact, Onyx merely exposes a single endpoint and multiplexes all the topics onto that endpoint. The [Infernyx](https://github.com/mozilla/infernyx) will demultiplex the inputs and process each topic separately.

[Bug 1403695: Send a generic health telemetry ping through Ping Centre for Activity Stream - Bugzilla](https://bugzilla.mozilla.org/show_bug.cgi?id=1403695)

```js
user_pref("browser.ping-centre.telemetry", false);
```

Default:
`true`
  ![Win][Windows Logo]
  ![Debian][Debian Logo]
  ![Tor Browser][Tor Browser Logo],
n/a
  ![Android][Android Logo]
([FF57+](https://bugzilla.mozilla.org/show_bug.cgi?id=1390249))


```js
user_pref("browser.ping-centre.production.endpoint", "");
```

Default:
`https://tiles.services.mozilla.com/v3/links/ping-centre`
  ![Win][Windows Logo]
  ![Debian][Debian Logo]
  ![Tor Browser][Tor Browser Logo],
n/a
  ![Android][Android Logo]


```js
user_pref("browser.ping-centre.staging.endpoint", "");
```

Default:
`https://onyx_tiles.stage.mozaws.net/v3/links/ping-centre`
  ![Win][Windows Logo]
  ![Debian][Debian Logo]
  ![Tor Browser][Tor Browser Logo],
n/a
  ![Android][Android Logo]

[Firefox Tuning zur Absicherung und Anonymisierung - Quantum Edition - kairaven.de](https://wiki.kairaven.de/open/app/firefoxquantum)


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
  ![Win][Windows Logo]
  ![Debian][Debian Logo]
  ![Tor Browser][Tor Browser Logo],
n/a
  ![Android][Android Logo]


Normandy is a collection of servers, workflows, and Firefox components that enables Mozilla to remote control Firefox clients ... [[readthedocs.io](https://normandy.readthedocs.io/)]

```js
user_pref("app.normandy.enabled", false);
```

Default:
`true`
  ![Win][Windows Logo]
  ![Debian][Debian Logo]
  ![Tor Browser][Tor Browser Logo],
n/a
  ![Android][Android Logo]


```js
user_pref("app.normandy.api_url", "");
```

Default:
`https://normandy.cdn.mozilla.net/api/v1`
  ![Win][Windows Logo]
  ![Debian][Debian Logo]
  ![Tor Browser][Tor Browser Logo],
n/a
  ![Android][Android Logo]


#### Devtools Telemetry

```js
lockPref("devtools.onboarding.telemetry.logged", false);
```

Default:
`false`
  ![Win][Windows Logo]
  ![Debian][Debian Logo]
  ![Tor Browser][Tor Browser Logo],
n/a
  ![Android][Android Logo]

Firefox auto-resets to `true` on start
[[ghacks.net comment](https://www.ghacks.net/2018/03/10/firefox-60-ships-with-windows-group-policy-support/#comment-4365175)].


## Safe Browsing

The Safe Browsing feature in Firefox has been renamed to Phishing Protection, but it's still known as Safe Browsing internally [[mozilla wiki](https://wiki.mozilla.org/Phishing_Protection)].

```js
user_pref("browser.safebrowsing.blockedURIs.enabled", false);
```

Default:
`true`
  ![Win][Windows Logo]
  ![Debian][Debian Logo]
  ![Android][Android Logo],
`false`
  ![Tor Browser][Tor Browser Logo]


```js
user_pref("browser.safebrowsing.phishing.enabled", false);
```

Default:
`true`
  ![Win][Windows Logo]
  ![Debian][Debian Logo]
  ![Android][Android Logo],
`false`
  ![Tor Browser][Tor Browser Logo]
([FF50+](https://bugzilla.mozilla.org/show_bug.cgi?id=1025965))


```js
user_pref("browser.safebrowsing.malware.enabled", false);
```

Default:
`true`
  ![Win][Windows Logo]
  ![Debian][Debian Logo]
  ![Android][Android Logo],
`false`
  ![Tor Browser][Tor Browser Logo]

`false`: do not download malware blacklists and do not check user downloads
[[mozillaZine](http://kb.mozillazine.org/Browser.safebrowsing.malware.enabled)].
[[mozilla support](https://support.mozilla.org/en-US/kb/how-does-phishing-and-malware-protection-work "How does built-in Phishing and Malware Protection")]


```js
user_pref("browser.safebrowsing.downloads.enabled", false);
```
Default:
`true`
  ![Win][Windows Logo]
  ![Debian][Debian Logo],
`false`
  ![Tor Browser][Tor Browser Logo]
  ![Android][Android Logo]

It enables/disables application reputation checks for downloaded files [[mozilla wiki](https://wiki.mozilla.org/Security/Application_Reputation "Application Reputation")].
`true` does only the local checks against a blacklist and a whitelist, as long as `browser.safebrowsing.downloads.remote.enabled` is disabled [[pyllyukko](https://github.com/pyllyukko/user.js/pull/65)].


```js
user_pref("browser.safebrowsing.downloads.remote.enabled", false);
```

Default:
`true`
  ![Win][Windows Logo]
  ![Debian][Debian Logo]
  ![Android][Android Logo],
`false`
  ![Tor Browser][Tor Browser Logo]

`false` disables application reputation remote lookups, but leaves other Safebrowsing malware protection intact [[mozilla wiki](https://wiki.mozilla.org/Security/Features/Application_Reputation_Design_Doc#How_to_turn_off_this_feature "Application Reputation Design Doc")].

[[GOV.UK](https://www.gov.uk/government/publications/browser-security-guidance-mozilla-firefox/browser-security-guidance-mozilla-firefox#enterprise-considerations "Browser Security Guidance: Mozilla Firefox - GOV.UK")]:
Firefox uses Google's Safe Browsing service that aims to protect against phishing websites and malicious downloads. It works by sending hashes of some visited website addresses to Google. If Google reports that the page is unsafe, the page or file will not be downloaded or displayed to protect the user against malware and data theft. Google states that it cannot derive the full website addresses from the information submitted as it only sends a partial URL fingerprint. Full website addresses are only sent if an organisation chooses to configure Chrome to send usage statistics to Google. Safe Browsing can be disabled entirely if the trade-off between privacy and security is not acceptable.


```js
user_pref("browser.safebrowsing.downloads.remote.block_potentially_unwanted", false);
user_pref("browser.safebrowsing.downloads.remote.block_uncommon", false);
user_pref("browser.safebrowsing.downloads.remote.block_dangerous", false);
user_pref("browser.safebrowsing.downloads.remote.block_dangerous_host", false);
```

Default:
`true`
  ![Win][Windows Logo]
  ![Debian][Debian Logo]
  ![Tor Browser][Tor Browser Logo]
  ![Android][Android Logo]


```js
user_pref("browser.safebrowsing.provider.google.reportURL", "");
user_pref("browser.safebrowsing.provider.google.reportMalwareMistakeURL", "");
user_pref("browser.safebrowsing.provider.google.reportPhishMistakeURL", "");
user_pref("browser.safebrowsing.provider.google4.dataSharingURL", "");
user_pref("browser.safebrowsing.provider.google4.reportMalwareMistakeURL", "");
user_pref("browser.safebrowsing.provider.google4.reportPhishMistakeURL", "");
user_pref("browser.safebrowsing.provider.google4.reportURL", "");
user_pref("browser.safebrowsing.reportPhishURL", "");
```

Default:
(various URLs)
  ![Windows][Windows Logo]
  ![Debian][Debian Logo]
  ![Tor Browser][Tor Browser Logo]
  ![Android][Android Logo]


```js
user_pref("browser.safebrowsing.downloads.remote.url", "");
```

Default:
"https://sb-ssl.google.com/safebrowsing/clientreport/download?key=%GOOGLE_SAFEBROWSING_API_KEY%"
""
  ![Windows][Windows Logo]
  ![Debian][Debian Logo]
  ![Android][Android Logo],
"(_empty string_)"
  ![Tor Browser][Tor Browser Logo]


```js
user_pref("browser.safebrowsing.provider.google.gethashURL", "");
```

Default:
"https://safebrowsing.google.com/safebrowsing/gethash?client=SAFEBROWSING_ID&appver=%MAJOR_VERSION%&pver=2.2"
  ![Windows][Windows Logo]
  ![Debian][Debian Logo]
  ![Android][Android Logo],
"(_empty string_)"
  ![Tor Browser][Tor Browser Logo]


```js
user_pref("browser.safebrowsing.provider.google.updateURL", "");
```

Default:
"https://safebrowsing.google.com/safebrowsing/downloads?client=SAFEBROWSING_ID&appver=%MAJOR_VERSION%&pver=2.2&key=%GOOGLE_SAFEBROWSING_API_KEY%"
  ![Windows][Windows Logo]
  ![Debian][Debian Logo]
  ![Android][Android Logo],
"(_empty string_)"
  ![Tor Browser][Tor Browser Logo]


```js
user_pref("browser.safebrowsing.provider.google4.gethashURL", "");
```

Default:
"https://safebrowsing.googleapis.com/v4/fullHashes:find?$ct=application/x-protobuf&key=%GOOGLE_SAFEBROWSING_API_KEY%&$httpMethod=POST"
  ![Windows][Windows Logo]
  ![Debian][Debian Logo]
  ![Android][Android Logo],
"(_empty string_)"
  ![Tor Browser][Tor Browser Logo]


```js
user_pref("browser.safebrowsing.provider.google4.updateURL", "");
```

Default:
"https://safebrowsing.googleapis.com/v4/threatListUpdates:fetch?$ct=application/x-protobuf&key=%GOOGLE_SAFEBROWSING_API_KEY%&$httpMethod=POST"
  ![Windows][Windows Logo]
  ![Debian][Debian Logo]
  ![Android][Android Logo],
"(_empty string_)"
  ![Tor Browser][Tor Browser Logo]


```js
user_pref("browser.safebrowsing.provider.mozilla.gethashURL", "");
```

Default:
"https://shavar.services.mozilla.com/gethash?client=SAFEBROWSING_ID&appver=%MAJOR_VERSION%&pver=2.2"
  ![Win][Windows Logo]
  ![Debian][Debian Logo]
  ![Android][Android Logo],
"(_empty string_)"
  ![Tor Browser][Tor Browser Logo]


```js
user_pref("browser.safebrowsing.provider.mozilla.updateURL", "");
```

Default:
"https://shavar.services.mozilla.com/downloads?client=SAFEBROWSING_ID&appver=%MAJOR_VERSION%&pver=2.2"
  ![Win][Windows Logo]
  ![Debian][Debian Logo]
  ![Android][Android Logo],
"(_empty string_)"
  ![Tor Browser][Tor Browser Logo]

"(_empty string_)" prevents background connections to Mozilla.


## Tracking Protection

[[mozilla wiki](https://wiki.mozilla.org/Security/Tracking_protection)] [[mozilla support](https://support.mozilla.org/en-US/kb/tracking-protection-firefox)]

```js
user_pref("privacy.trackingprotection.enabled", false);
```

Default:
`false`
  ![Win][Windows Logo]
  ![Debian][Debian Logo]
  ![Tor Browser][Tor Browser Logo]
  ![Android][Android Logo]


```js
user_pref("privacy.trackingprotection.pbmode.enabled", false);
```

Default:
`true`
  ![Win][Windows Logo]
  ![Debian][Debian Logo]
  ![Android][Android Logo],
`false`
  ![Tor Browser][Tor Browser Logo]


## Updating

[[Disable Updater - MDN](https://developer.mozilla.org/en-US/docs/Mozilla/Firefox/Enterprise_deployment#Example_configuration_file)]

```js
user_pref("app.update.enabled", false);
```

Default:
`true`
  ![Win][Windows Logo]
  ![Tor Browser][Tor Browser Logo],
`false`
  ![Android][Android Logo],
n/a
    ![Debian][Debian Logo].
[[mozillaZine](http://kb.mozillazine.org/App.update.enabled)]


```js
user_pref("app.update.auto", false);
```

Default:
`true`
  ![Win][Windows Logo]
  ![Debian][Debian Logo]
  ![Tor Browser][Tor Browser Logo],
n/a
  ![Android][Android Logo].
[[mozillaZine](http://kb.mozillazine.org/App.update.auto)]


```js
user_pref("app.update.service.enabled", false);
```

Default:
`true`
  ![Win][Windows Logo],
n/a
  ![Debian][Debian Logo]
  ![Tor Browser][Tor Browser Logo]
  ![Android][Android Logo].
[[Windows Service Silent Update - mozilla wiki](https://wiki.mozilla.org/Windows_Service_Silent_Update)]


```js
user_pref("app.update.BITS.enabled", false);
```

Default:
`true`
  ![Win][Windows Logo],
n/a
  ![Debian][Debian Logo]
  ![Tor Browser][Tor Browser Logo]
  ![Android][Android Logo]
([FF68+](https://github.com/earthlng/FFprefs-diffs/blob/master/diffs/6x/diff-v67.0-vs-v68.0.log.js))
[[Background Intelligent Transfer Service - ghacks.net](https://www.ghacks.net/2019/06/24/firefox-will-use-bits-on-windows-for-updates-going-forward/)]


### Extensions Update

[[Mozilla Add-ons Blog](https://blog.mozilla.org/addons/how-to-opt-out-of-add-on-metadata-updates/)]: Firefox asks the [Mozilla Add-ons gallery](https://addons.mozilla.org/) for information about the add-ons you have installed once a day. This involves sending the identifiers of each add-on you have installed to Mozilla, as well as information on how long it last took Firefox to start up. Opting out of this daily ping will stop Firefox from sending the add-ons you have installed and most recent start-up time to Mozilla, and will also stop displaying updated metadata for your add-ons and discontinue personalized recommendations if they were displayed in the Get Add-ons pane of the Add-ons Manager. To opt out, set `extensions.getAddons.cache.enabled` to `false`.

```js
user_pref("extensions.getAddons.cache.enabled", false);
```

Default:
`true`
  ![Win][Windows Logo]
  ![Debian][Debian Logo]
  ![Android][Android Logo],
`false`
  ![Tor Browser][Tor Browser Logo]


```js
user_pref("extensions.update.enabled", false);
```

Default:
`true`
  ![Win][Windows Logo]
  ![Tor Browser][Tor Browser Logo]
  ![Android][Android Logo],
`false` (locked via policies)
  ![Debian][Debian Logo].
[[mozillaZine](http://kb.mozillazine.org/About:config_entries#Extensions.)]


```js
user_pref("extensions.update.autoUpdateDefault", false);
```

Default:
`true`
  ![Win][Windows Logo]
  ![Debian][Debian Logo]
  ![Tor Browser][Tor Browser Logo],
n/a
  ![Android][Android Logo].
[[mozilla support](https://support.mozilla.org/en-US/questions/952162 "Difference between extensions.update.autoUpdateDefault and extensions.update.enabled")]


```js
user_pref("extensions.autoupdate.enabled", false);
```

Default:
n/a
  ![Win][Windows Logo]
  ![Debian][Debian Logo]
  ![Tor Browser][Tor Browser Logo],
`true`
  ![Android][Android Logo].
[[Blog](http://starkravingfinkle.org/blog/2010/05/updating-add-ons-in-firefox-mobile-1-1/ "Updating Add-ons in Firefox Mobile 1.1")]


```js
user_pref("extensions.systemAddon.update.enabled", false);
```

Default:
`true`
  ![Win][Windows Logo]
  ![Debian][Debian Logo],
`false`
  ![Android][Android Logo],
n/a
  ![Tor Browser][Tor Browser Logo]
  (FF62+)


```js
user_pref("extensions.systemAddon.update.url", "");
```

Default:
"https://aus5.mozilla.org/update/3/SystemAddons/%VERSION%/%BUILD_ID%/%BUILD_TARGET%/%LOCALE%/%CHANNEL%/%OS_VERSION%/%DISTRIBUTION%/%DISTRIBUTION_VERSION%/update.xml"
  ![Win][Windows Logo]
  ![Debian][Debian Logo],
"(_empty string_)"
  ![Tor Browser][Tor Browser Logo],
`n/a`
  ![Android][Android Logo]
  (FF44+)


### Search Engines Update

```js
user_pref("browser.search.update", false);
```

Default:
`true`
  ![Win][Windows Logo]
  ![Debian][Debian Logo],
`false`
  ![Tor Browser][Tor Browser Logo]
  ![Android][Android Logo]

`false`: do not automatically check for updates to search plugins [[mozillaZine](http://kb.mozillazine.org/About:config_entries#Browser.)].


### Web Apps Update

[[Web Application - Wikipedia](https://en.wikipedia.org/wiki/Web_application)] [[MDN](https://developer.mozilla.org/en-US/Apps)]

```js
user_pref("app.update.autodownload", "never");
```
Default:
n/a
  ![Win][Windows Logo]
  ![Debian][Debian Logo]
  ![Tor Browser][Tor Browser Logo],
"wifi"
  ![Android][Android Logo].
[Bug 805431](https://bugzilla.mozilla.org/show_bug.cgi?id=805431)


```js
user_pref("app.update.url.android", "");
```

Default:
n/a
  ![Win][Windows Logo]
  ![Debian][Debian Logo]
  ![Tor Browser][Tor Browser Logo],
"https://aus5.mozilla.org/update/4/%PRODUCT%/%VERSION%/%BUILD_ID%/%BUILD_TARGET%/%LOCALE%/%CHANNEL%/%OS_VERSION%/%DISTRIBUTION%/%DISTRIBUTION_VERSION%/%MOZ_VERSION%/update.xml")
  ![Android][Android Logo]


### What is New

```js
user_pref("browser.messaging-system.whatsNewPanel.enabled", false);
```

Default:
`true`
  ![Windows][Windows Logo]
  ![Debian][Debian Logo],
n/a
  ![Tor Browser][Tor Browser Logo]
  ![Android][Android Logo]
(FF70+)



## WebRTC

[[MDN](https://developer.mozilla.org/en-US/docs/Web/Guide/API/WebRTC)]: WebRTC (Web Real Time Communications) is a technology that enables audio/video streaming and data sharing between browser clients (peers). WebRTC provides the ability to share application data and perform teleconferencing peer to peer, without the need to install plug-ins or third-party software.

```js
user_pref("media.navigator.enabled", false);
```

Default:
`true`
  ![Win][Windows Logo]
  ![Debian][Debian Logo]
  ![Android][Android Logo],
`false`
  ![Tor Browser][Tor Browser Logo].
[[mozilla wiki](https://wiki.mozilla.org/Media/getUserMedia)]


```js
user_pref("media.navigator.video.enabled", false);
```

Default:
`true`
  ![Win][Windows Logo]
  ![Debian][Debian Logo]
  ![Android][Android Logo],
n/a
  ![Tor Browser][Tor Browser Logo]
([FF28+](https://bugzilla.mozilla.org/show_bug.cgi?id=947429))


```js
user_pref("media.peerconnection.enabled", false);
```

Default:
`true`
  ![Win][Windows Logo]
  ![Debian][Debian Logo]
  ![Android][Android Logo],
`false`
  ![Tor Browser][Tor Browser Logo].
[[mozilla wiki](https://wiki.mozilla.org/Media/getUserMedia)]


```js
user_pref("media.peerconnection.ice.default_address_only", true);
user_pref("media.peerconnection.ice.no_host", true);
```

Default:
`false`
  ![Win][Windows Logo]
  ![Debian][Debian Logo]
  ![Android][Android Logo],
n/a
  ![Tor Browser][Tor Browser Logo].
[[mozilla wiki](https://wiki.mozilla.org/Media/WebRTC/Privacy)]


```js
user_pref("media.peerconnection.use_document_iceservers", false);
```

Default:
`true`
  ![Win][Windows Logo]
  ![Debian][Debian Logo]
  ![Android][Android Logo],
n/a
  ![Tor Browser][Tor Browser Logo].
[[mozilla wiki](https://wiki.mozilla.org/Media/WebRTC/Privacy)]


```js
user_pref("media.peerconnection.turn.disable", true);
```

Default:
`false`
  ![Win][Windows Logo]
  ![Debian][Debian Logo]
  ![Android][Android Logo],
n/a
  ![Tor Browser][Tor Browser Logo].
[[privacytools.io](https://www.privacytools.io/#webrtc)]


```js
user_pref("media.peerconnection.video.enabled", false);
```

Default:
`true`
  ![Win][Windows Logo]
  ![Debian][Debian Logo]
  ![Android][Android Logo],
n/a
  ![Tor Browser][Tor Browser Logo].
[[privacytools.io](https://www.privacytools.io/#webrtc)]


```js
user_pref("media.peerconnection.identity.enabled", false);
```

Default:
`true`
  ![Win][Windows Logo]
  ![Debian][Debian Logo]
  ![Android][Android Logo],
n/a
  ![Tor Browser][Tor Browser Logo].
[[kairaven.de](https://wiki.kairaven.de/open/app/firefoxquantum)]


```js
user_pref("media.peerconnection.identity.timeout", 1);
```

Default:
`10000`
  ![Win][Windows Logo]
  ![Debian][Debian Logo]
  ![Android][Android Logo],
n/a
  ![Tor Browser][Tor Browser Logo].
[[privacytools.io](https://www.privacytools.io/#webrtc)]


```js
user_pref("media.ondevicechange.enabled", true);
```

Default:
`true`
  ![Win][Windows Logo]
  ![Debian][Debian Logo]
  ![Tor Browser][Tor Browser Logo]
  ![Android][Android Logo] (FF52+)

Change is not needed if `privacy.resistFingerprinting` is `true` [[ghacks](https://github.com/ghacksuserjs/ghacks-user.js/blob/master/user.js)].
[MDN#1](https://developer.mozilla.org/en-US/docs/Web/API/MediaDevices/ondevicechange),
[MDN#2](https://developer.mozilla.org/en-US/docs/Web/Events/devicechange)


WebRTC Leak Tests:

- [privacytools.io](https://www.privacytools.io/webrtc.html)
- [diafygi.github.io](https://diafygi.github.io/webrtc-ips/)
- [browserleaks.com](https://www.browserleaks.com/webrtc)


### Gecko Media Plugins

Gecko Media Plugins (GMPs) is a special purpose extension point for authorised 3rd party codecs and EME (Encrypted Media Extensions) CDMs (Content Decryption Modules) [[mozilla wiki](https://wiki.mozilla.org/GeckoMediaPlugins)].

```js
user_pref("media.gmp-provider.enabled", false);
```

Default:
`true`
  ![Win][Windows Logo]
  ![Debian][Debian Logo]
  ![Android][Android Logo],
`false`
  ![Tor Browser][Tor Browser Logo]

`false` removes OpenH264 codec from the Plugins list.

The OpenH264 codec is not distributed with Firefox but gets downloaded at the first start of Firefox. In case you want to prohibit that, you will have to set the `media.gmp-gmpopenh264.enabled` and `media.gmp-gmpopenh264.autoupdate` to `false`  [[mozilla support](https://support.mozilla.org/en-US/kb/how-stop-firefox-making-automatic-connections#w_openh264-codec)].


```js
user_pref("media.gmp-gmpopenh264.enabled", false);
```
Default:
`true`
  ![Debian][Debian Logo],
n/a
  ![Win][Windows Logo]
  ![Android][Android Logo],
n/a (hidden pref)
  ![Tor Browser][Tor Browser Logo]


```js
user_pref("media.gmp-gmpopenh264.autoupdate", false);
```
Default:
n/a
  ![Win][Windows Logo]
  ![Debian][Debian Logo]
  ![Android][Android Logo],
n/a (hidden pref)
  ![Tor Browser][Tor Browser Logo]

The installed codec is stored in `<Profile>/gmp-gmpopenh264/` and can be deleted.


```js
user_pref("media.gmp-manager.updateEnabled", false);
```

Default:
n/a (hidden)
  ![Win][Windows Logo]
  ![Debian][Debian Logo],
n/a
  ![Android][Android Logo],
`false`
  ![Tor Browser][Tor Browser Logo]

`false`: disable GMP downloads via local fallback [[Tor Browser](https://www.torproject.org/projects/torbrowser/design/)].


```js
user_pref("media.gmp-manager.url", "data:text/plain,");
```

Default:
"https://aus5.mozilla.org/update/3/GMP/%VERSION%/%BUILD_ID%/%BUILD_TARGET%/%LOCALE%/%CHANNEL%/%OS_VERSION%/%DISTRIBUTION%/%DISTRIBUTION_VERSION%/update.xml"
  ![Win][Windows Logo]
  ![Debian][Debian Logo]
  ![Tor Browser][Tor Browser Logo]
  ![Android][Android Logo]


```js
user_pref("media.gmp-manager.url.override", "data:text/plain,");
```

Default:
n/a (hidden)
  ![Win][Windows Logo]
  ![Debian][Debian Logo]
  ![Android][Android Logo],
"data:text/plain,"
  ![Tor Browser][Tor Browser Logo]


```js
user_pref("media.gmp.trial-create.enabled", false);
```

Default:
`true`
  ![Win][Windows Logo]
  ![Debian][Debian Logo]
  ![Tor Browser][Tor Browser Logo],
n/a
  ![Android][Android Logo]

Whether we should run a test-pattern through EME GMPs before assuming they'll decode H.264 [[DXR](https://dxr.mozilla.org/mozilla-central/source/browser/app/profile/firefox.js)].


### Get User Media

```js
user_pref("media.getusermedia.screensharing.enabled", false);
```

Default:
`true`
  ![Win][Windows Logo]
  ![Debian][Debian Logo]
  ![Tor Browser][Tor Browser Logo],
n/a
  ![Android][Android Logo]


```js
user_pref("media.getusermedia.audiocapture.enabled", false);
```

Default:
`false`
  ![Win][Windows Logo]
  ![Debian][Debian Logo]
  ![Tor Browser][Tor Browser Logo]
  ![Android][Android Logo]

[Capture local camera and microphone streams with getUserMedia - now enabled in Firefox - Mozilla Blog](https://blog.mozilla.org/futurereleases/2013/01/12/capture-local-camera-and-microphone-streams-with-getusermedia-now-enabled-in-firefox/)

[Media/getUserMedia - mozilla wiki](https://wiki.mozilla.org/Media/getUserMedia)

[MediaDevices.getUserMedia() - MDN](https://developer.mozilla.org/en-US/docs/Web/API/MediaDevices/getUserMedia)


## Digital Rights Management

[Watch DRM content on Firefox - Mozilla Support](https://support.mozilla.org/en-US/kb/enable-drm)

```js
user_pref("media.gmp-widevinecdm.visible", false);
user_pref("media.gmp-widevinecdm.enabled", false);
```

Default:
`true`
  ![Win][Windows Logo]
  ![Debian][Debian Logo],
`false`
  ![Tor Browser][Tor Browser Logo],
n/a
  ![Android][Android Logo]


## Encrypted Media Extension

[[What is EME?](https://hsivonen.fi/eme/)] [[Mozilla Hacks](https://hacks.mozilla.org/2014/05/reconciling-mozillas-mission-and-w3c-eme/)] [[W3C](https://w3c.github.io/encrypted-media/)]

```js
user_pref("media.eme.enabled", false);
```

Default:
 `true`
  ![Win][Windows Logo],
`false`
  ![Debian][Debian Logo]
  ![Tor Browser][Tor Browser Logo],
n/a
  ![Android][Android Logo].
[DXR](https://dxr.mozilla.org/mozilla-central/search?q=media.eme.enabled)


```js
user_pref("browser.eme.ui.enabled", false);
```

Default:
`true`
  ![Win][Windows Logo]
  ![Debian][Debian Logo],
`false`
  ![Tor Browser][Tor Browser Logo],
n/a
  ![Android][Android Logo]


## Extensions

### Extension Blocklist

Blocklisting is the ability to disable errant add-ons, plugins, and other third-party software [[Mozilla Wiki](https://wiki.mozilla.org/Blocklisting)].

```js
user_pref("extensions.blocklist.enabled", true);
```

Default:
`true`
  ![Win][Windows Logo]
  ![Debian][Debian Logo]
  ![Tor Browser][Tor Browser Logo]
  ![Android][Android Logo]

Firefox periodically retrieves a list of blocked addons and certificates from the Mozilla server.
`true`: Retrieve a blocklist, restrict extension installation and disable them if blocklisted extensions or plugins are already installed [[mozillaZine](http://kb.mozillazine.org/Extensions.blocklist.enabled)].

```js
user_pref("extensions.blocklist.url", "https://blocklist.addons.mozilla.org/v1/blocklist/3/%APP_ID%/%APP_VERSION%/");
```
Default:
"https://blocklist.addons.mozilla.org/v1/blocklist/3/%APP_ID%/%APP_VERSION%/%PRODUCT%/%BUILD_ID%/%BUILD_TARGET%/%LOCALE%/%CHANNEL%/%OS_VERSION%/%DISTRIBUTION%/%DISTRIBUTION_VERSION%/%PING_COUNT%/%TOTAL_PING_COUNT%/%DAYS_SINCE_LAST_PING%/"
  ![Win][Windows Logo]
  ![Debian][Debian Logo]
  ![Tor Browser][Tor Browser Logo]
  ![Android][Android Logo]

[Tor Bug #16931: Sanitize the add-on blocklist update URL](https://trac.torproject.org/projects/tor/ticket/16931)


### Extension Signing

```js
user_pref("xpinstall.signatures.required", false);
```
Default:
`true`
  ![Win][Windows Logo]
  ![Debian][Debian Logo]
  ![Tor Browser][Tor Browser Logo]
  ![Android][Android Logo].
[mozilla wiki](https://wiki.mozilla.org/Addons/Extension_Signing)


### Get Add-ons Discovery Pane

```js
user_pref("extensions.getAddons.showPane", false);
```

Default:
n/a (hidden)
  ![Win][Windows Logo]
  ![Debian][Debian Logo],
n/a
  ![Android][Android Logo],
`false`
  ![Tor Browser][Tor Browser Logo]

`false`: disable about:addons' Get Add-ons panel (uses Google-Analytics)
[[ghacks-user.js](https://github.com/ghacksuserjs/ghacks-user.js/blob/master/user.js)].


```js
user_pref("extensions.webservice.discoverURL", "");
```

Default:
"https://services.addons.mozilla.org/%LOCALE%/firefox/discovery/pane/%VERSION%/%OS%/%COMPATIBILITY_MODE%"
  ![Win][Windows Logo],
  ![Debian][Debian Logo]
  ![Tor Browser][Tor Browser Logo],
n/a
  ![Android][Android Logo].
[Techdows](http://techdows.com/2016/08/firefox-48-disable-add-on-discovery-pane.html)


### Legacy Extensions

```js
user_pref("extensions.legacy.exceptions", "(long list)");
```

The preference just controls how things are presented in the UI, it doesn't actually change what is allowed to load/run [[1360777](https://bugzilla.mozilla.org/show_bug.cgi?id=1360777)].


### Web Compatibility Reporter

```js
user_pref("extensions.webcompat-reporter.enabled", false);
```

Default:
`true`
  ![Win][Windows Logo],
`false`
  ![Debian][Debian Logo]
  ![Tor Browser][Tor Browser Logo]
  ![Android][Android Logo]

Browser extension that allows users to click on a button in the browser to report a site compatibility issue [[webcompat](https://github.com/webcompat/webcompat-reporter-extensions)].


### Personalized Extension Recommendations

Firefox might occasionally recommend extensions based on other extensions you’ve installed, profile preferences, hardware, and usage statistics [[Mozilla Support](https://support.mozilla.org/en-US/kb/personalized-extension-recommendations)].

```js
user_pref("browser.discovery.enabled", false);
```

Default:
`true`
  ![Win][Windows Logo]
  ![Debian][Debian Logo],
n/a
  ![Tor Browser][Tor Browser Logo]
  ![Android][Android Logo].
(FF65+)

This preference has no effect when [Health Report](#health-report) is disabled and can be changed via Preferences -> Privacy & Security -> Firefox Data Collection and Use -> Allow Firefox to make personalized extension recommendations.


```js
user_pref("extensions.getAddons.discovery.api_url", "");
```

Default:
"https://services.addons.mozilla.org/api/v4/discovery/?lang=%LOCALE%"
  ![Win][Windows Logo]
  ![Debian][Debian Logo],
n/a
  ![Tor Browser][Tor Browser Logo]
  ![Android][Android Logo]
(FF68+)

```js
user_pref("extensions.htmlaboutaddons.discover.enabled", false);
```

Default:
`true`
  ![Win][Windows Logo]
  ![Debian][Debian Logo],
n/a
  ![Tor Browser][Tor Browser Logo]
  ![Android][Android Logo]
(FF68+)


```js
user_pref("extensions.htmlaboutaddons.recommendations.enabled", false);
```

Default:
`true`
  ![Win][Windows Logo]
  ![Debian][Debian Logo]
  ![Android][Android Logo],
n/a
  ![Tor Browser][Tor Browser Logo]
(FF68+)


### Extension Abuse Reporting


```js
user_pref("extensions.abuseReport.enabled", false);
```

Default:
`true`
  ![Win][Windows Logo]
  ![Debian][Debian Logo]
  ![Android][Android Logo],
n/a
  ![Tor Browser][Tor Browser Logo]
([FF68+](https://bugzilla.mozilla.org/show_bug.cgi?id=1544928))


## Firefox Account

[Firefox Accounts - Mozilla | MDN](https://developer.mozilla.org/en-US/docs/Mozilla/Tech/Firefox_Accounts)

```js
user_pref("identity.fxaccounts.enabled", false);
```

Default:
`true`
  ![Win][Windows Logo],
`false`
  ![Tor Browser][Tor Browser Logo],
n/a
  ![Debian][Debian Logo]
  ![Android][Android Logo]
(FF60+). [ghacks.net](https://www.ghacks.net/2018/02/28/firefox-60-disable-firefox-sync-integration/)


## Home Page

```js
user_pref("browser.startup.homepage", "about:blank");
```

Default:
"about:home"
  ![Win][Windows Logo]
  ![Debian][Debian Logo],
"about:tor"
  ![Tor Browser][Tor Browser Logo],
n/a
  ![Android][Android Logo]

[[mozilla wiki](https://wiki.mozilla.org/Firefox/Projects/Firefox_Start/Snippet_Service)]:
`about:home` fetches content from the production snippets service once every 24 hours. If content is available, it gets is stashed in local storage for the page and displayed from there until the next fetch. If no content is available, the browser has a built-in default set of snippets for display.


```js
user_pref("browser.startup.homepage_override.mstone", "ignore");
```

Default:
n/a (hidden)
  ![Win][Windows Logo]
  ![Debian][Debian Logo]
  ![Tor Browser][Tor Browser Logo]
  ![Android][Android Logo]

This preference is examined during browser start up. If its value differs from the browser's current milestone, then Firefox connects and fetches content from Mozilla snippets server. `ignore`: the browser's homepage will not be overridden after updates [[mozillaZine](http://kb.mozillazine.org/Browser.startup.homepage_override.mstone)]. _Note_: Firefox for Android overrides this user preference and set it to actual Firefox version?!


```js
user_pref("browser.aboutHomeSnippets.updateUrl", "https://127.0.0.1");
```

Default:
"https://snippets.cdn.mozilla.net/%STARTPAGE_VERSION%/%NAME%/%VERSION%/%APPBUILDID%/%BUILD_TARGET%/%LOCALE%/%CHANNEL%/%OS_VERSION%/%DISTRIBUTION%/%DISTRIBUTION_VERSION%/"
  ![Tor Browser][Tor Browser Logo],
n/a
  ![Win][Windows Logo]
  ![Debian][Debian Logo]
  ![Android][Android Logo].
([-FF67](https://bugzilla.mozilla.org/show_bug.cgi?id=1540939))
[[mozilla wiki](https://wiki.mozilla.org/Firefox/Projects/Firefox_Start/Snippet_Service)]


```js
user_pref("startup.homepage_override_url", "");
```

Default:
"https://www.mozilla.org/projects/firefox/%VERSION%/whatsnew/?oldversion=%OLD_VERSION%"
  ![Win][Windows Logo],
"(_empty string_)"
  ![Debian][Debian Logo],
"https://blog.torproject.org/category/tags/tor-browser"
  ![Tor Browser][Tor Browser Logo],
n/a
  ![Android][Android Logo]

"(_empty string_)" disables What is New Page after updates.


```js
user_pref("startup.homepage_welcome_url", "about:blank");
```

Default:
`https://www.mozilla.org/projects/firefox/%VERSION%/firstrun/`
  ![Win][Windows Logo]
  ![Debian][Debian Logo],
"(_empty string_)"
 ![Tor Browser][Tor Browser Logo],
n/a
  ![Android][Android Logo]


### Messages on Home Page

[How to stop Firefox messages on home screen?](https://support.mozilla.org/en-US/questions/1035229)

```js
user_pref("browser.snippets.enabled", false);
user_pref("browser.snippets.syncPromo.enabled", false);
```

Default:
n/a (hidden)
  ![Win][Windows Logo]
  ![Debian][Debian Logo]
  ![Tor Browser][Tor Browser Logo],
`true`
  ![Android][Android Logo]


```js
user_pref("browser.snippets.firstrunHomepage.enabled", false);
```

Default:
n/a (hidden)
  ![Win][Windows Logo]
  ![Debian][Debian Logo]
  ![Tor Browser][Tor Browser Logo],
`true`
  ![Android][Android Logo]


```js
user_pref("browser.snippets.updateUrl", "http://127.0.0.1");
```

Default:
n/a
  ![Win][Windows Logo]
  ![Debian][Debian Logo]
  ![Tor Browser][Tor Browser Logo],
"https://snippets.cdn.mozilla.net/json/%SNIPPETS_VERSION%/%NAME%/%VERSION%/%APPBUILDID%/%BUILD_TARGET%/%LOCALE%/%CHANNEL%/%OS_VERSION%/%DISTRIBUTION%/%DISTRIBUTION_VERSION%/"
  ![Android][Android Logo]


```js
user_pref("browser.snippets.statsUrl", "http://127.0.0.1");
```

Default:
n/a
  ![Win][Windows Logo]
  ![Debian][Debian Logo]
  ![Tor Browser][Tor Browser Logo],
"https://snippets-stats.mozilla.org/mobile"
  ![Android][Android Logo]

```js
user_pref("browser.snippets.geoUrl", "http://127.0.0.1");
```

Default:
n/a
  ![Win][Windows Logo]
  ![Debian][Debian Logo]
  ![Tor Browser][Tor Browser Logo],
"https://location.services.mozilla.com/v1/country?key=fff72d56-b040-4205-9a11-82feda9d83a3"
  ![Android][Android Logo]


## Tabs

### New Tab

```js
user_pref("browser.newtabpage.introShown", true);
```

Default:
`false`
  ![Win][Windows Logo]
  ![Debian][Debian Logo],
n/a
  ![Tor Browser][Tor Browser Logo]
  ![Android][Android Logo]


```js
user_pref("browser.newtabpage.enabled", false);
```

Default:
`true`
  ![Win][Windows Logo]
  ![Debian][Debian Logo]
  ![Tor Browser][Tor Browser Logo],
n/a
  ![Android][Android Logo]

Setting `enabled` and `enhanced` to `false` disables top and suggested sites (equivalent to blank page).


```js
user_pref("browser.newtabpage.enhanced", false);
```

Default:
`true`
  ![Win][Windows Logo]
  ![Debian][Debian Logo],
n/a
  ![Tor Browser][Tor Browser Logo]
  ![Android][Android Logo]


```js
user_pref("browser.newtabpage.directory.source", "data:text/plain,{}");
```

Default:
"https://tiles.services.mozilla.com/v3/links/fetch/%LOCALE%/%CHANNEL%"
  ![Win][Windows Logo],
n/a
  ![Debian][Debian Logo]
  ![Tor Browser][Tor Browser Logo]
  ![Android][Android Logo]
([-FF59?](https://github.com/earthlng/FFprefs-diffs/blob/38cf35c43c8479111dd3bc5e534386d8d746ee12/diffs/ESR/diff-v52.9.0esr-vs-v60.0esr.log.js)).
[Mozilla Source Tree Docs](https://media.readthedocs.org/pdf/gecko/latest/gecko.pdf)


```js
user_pref("browser.newtab.preload", false);
```

Default:
`true`
  ![Win][Windows Logo]
  ![Debian][Debian Logo]
  ![Tor Browser][Tor Browser Logo],
n/a
  ![Android][Android Logo]


```js
user_pref("browser.tabs.loadInBackground", false);
```

Default:
`true`
  ![Win][Windows Logo]
  ![Debian][Debian Logo]
  ![Tor Browser][Tor Browser Logo],
n/a
  ![Android][Android Logo]

`false`:  Open link in a new tab and automatically switch into that tab. [[mozillaZine](http://kb.mozillazine.org/About:config_entries#Browser.)]


```js
user_pref("browser.library.activity-stream.enabled", false);
```

Default:
`true`
  ![Win][Windows Logo]
  ![Debian][Debian Logo]
  ![Tor Browser][Tor Browser Logo],
n/a
  ![Android][Android Logo]


```js
user_pref("browser.newtabpage.activity-stream.feeds.discoverystreamfeed", false);
user_pref("browser.newtabpage.activity-stream.feeds.section.highlights", false);
user_pref("browser.newtabpage.activity-stream.feeds.section.topstories", false);
user_pref("browser.newtabpage.activity-stream.feeds.snippets", false);
user_pref("browser.newtabpage.activity-stream.feeds.telemetry", false);
user_pref("browser.newtabpage.activity-stream.feeds.topsites", false);
user_pref("browser.newtabpage.activity-stream.showSearch", false);
user_pref("browser.newtabpage.activity-stream.showSponsored", false);
user_pref("browser.newtabpage.activity-stream.section.highlights.includePocket", false);
user_pref("browser.newtabpage.activity-stream.telemetry", false);
```

Default:
`true`
  ![Win][Windows Logo]
  ![Debian][Debian Logo],
n/a
  ![Tor Browser][Tor Browser Logo]
  ![Android][Android Logo]

[Activity Stream - Mozilla Wiki](https://wiki.mozilla.org/Firefox/Activity_Stream)

[Activity Stream 1.0 - Mozilla Wiki](https://wiki.mozilla.org/Firefox/Activity_Stream_1.0)


```js
user_pref("browser.newtabpage.activity-stream.migrationExpired", true);
```

Default:
`false`
  ![Win][Windows Logo]
  ![Debian][Debian Logo],
n/a
  ![Tor Browser][Tor Browser Logo]
  ![Android][Android Logo]


```js
user_pref("browser.newtabpage.activity-stream.disableSnippets", true);
```

Default:
n/a
  ![Win][Windows Logo]
  ![Debian][Debian Logo]
  ![Tor Browser][Tor Browser Logo]
  ![Android][Android Logo]
([-FF67](https://bugzilla.mozilla.org/show_bug.cgi?id=1540939))


```js
user_pref("browser.newtabpage.activity-stream.telemetry.ping.endpoint", "");
```

Default:
`https://tiles.services.mozilla.com/v4/links/activity-stream`
  ![Debian][Debian Logo],
n/a
  ![Tor Browser][Tor Browser Logo]
  ![Android][Android Logo]


```js
user_pref("browser.newtabpage.activity-stream.asrouter.providers.snippets", "");
```

Default:
`{"id":"snippets","enabled":true,"type":"remote","url":"https://snippets.cdn.mozilla.net/%STARTPAGE_VERSION%/%NAME%/%VERSION%/%APPBUILDID%/%BUILD_TARGET%/%LOCALE%/%CHANNEL%/%OS_VERSION%/%DISTRIBUTION%/%DISTRIBUTION_VERSION%/","updateCycleInMs":14400000}`
  ![Debian][Debian Logo],
n/a
  ![Tor Browser][Tor Browser Logo]
  ![Android][Android Logo]


__Old/Obsolete__

[[-FF59](https://bugzilla.mozilla.org/show_bug.cgi?id=1433324)] `browser.newtabpage.activity-stream.enabled`

[[-FF60](https://github.com/earthlng/FFprefs-diffs/blob/5562958cb9eed5818e382313c0594565a2bd0def/diffs/6x/diff-v60.0-vs-v61.0.log.js)] `browser.newtabpage.activity-stream.section.topstories.collapsed`

[[-FF60](https://github.com/earthlng/FFprefs-diffs/blob/5562958cb9eed5818e382313c0594565a2bd0def/diffs/6x/diff-v60.0-vs-v61.0.log.js)] `browser.newtabpage.activity-stream.showTopSites`

[[-FF62](https://github.com/earthlng/FFprefs-diffs/blob/fd1c9edb566ea06e66760236f4040cd576463571/diffs/6x/diff-v62.0-vs-v63.0.log.js)] `browser.newtabpage.activity-stream.section.topstories.showDisclaimer`


### Last Tab

```js
user_pref("browser.tabs.closeWindowWithLastTab", false);
```

Default:
`true`
  ![Win][Windows Logo]
  ![Debian][Debian Logo]
  ![Tor Browser][Tor Browser Logo],
n/a
  ![Android][Android Logo]

`false`: do not close browser with closing last tab.


## Onboarding

[[ghacks-user.js](https://github.com/ghacksuserjs/ghacks-user.js/blob/master/user.js)]: [Onboarding](https://wiki.mozilla.org/Firefox/Onboarding) is an interactive tour/setup for new installs/profiles and features. Every time `about:home` or `about:newtab` is opened, the onboarding overlay is injected into that page. Onboarding uses Google Analytics [[1](https://github.com/mozilla/onboard/commit/db4d6c8726c89a5d6a241c1b1065827b525c5baf)], and leaks `resource://URIs` [[2](https://bugzilla.mozilla.org/show_bug.cgi?id=863246#c154)].

```js
user_pref("browser.onboarding.enabled", false);
```

Default:
`true`
  ![Win][Windows Logo]
  ![Tor Browser][Tor Browser Logo],
n/a
  ![Debian][Debian Logo]
  ![Android][Android Logo]
(FF55-[FF63](https://github.com/earthlng/FFprefs-diffs/blob/fa12137da87451c1037116c24bcf4892c413e9f3/diffs/6x/diff-v63.0-vs-v64.0.log.js))


## Pocket

[[mozilla support](https://support.mozilla.org/en-US/kb/save-web-pages-later-pocket-firefox)] [[ghacks.net](http://www.ghacks.net/2015/05/14/how-to-disable-pocket-in-firefox/)]

```js
user_pref("extensions.pocket.enabled", false);
```

Default:
`true`
  ![Win][Windows Logo]
  ![Debian][Debian Logo]
  ![Tor Browser][Tor Browser Logo],
n/a
  ![Android][Android Logo]

`browser.pocket.enabled` was replaced by `extensions.pocket.enabled` in FF46 [[Bug 1215694](https://bugzilla.mozilla.org/show_bug.cgi?id=1215694)].

[How do I delete Pocket? - Mozilla Support Forum](https://support.mozilla.org/en-US/questions/1087570)


```js
user_pref("browser.pocket.api", "");
```

Default:
"(_empty string_)"
  ![Tor Browser][Tor Browser Logo]
([-FF45](https://bugzilla.mozilla.org/show_bug.cgi?id=1215694))


```js
user_pref("browser.pocket.site", "");
```

Default:
"(_empty string_)"
  ![Tor Browser][Tor Browser Logo]
([-FF45](https://bugzilla.mozilla.org/show_bug.cgi?id=1215694))


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
  ![Win][Windows Logo]
  ![Debian][Debian Logo]
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
  ![Win][Windows Logo]
  ![Debian][Debian Logo]
  ![Android][Android Logo],
`false`
  ![Tor Browser][Tor Browser Logo]
([FF35+](https://bugzilla.mozilla.org/show_bug.cgi?id=1002855))


[User Timing - W3C](https://www.w3.org/TR/2013/REC-user-timing-20131212/)

```js
user_pref("dom.enable_user_timing", false);
```

Default:
`false`
  ![Tor Browser][Tor Browser Logo]
([FF38](https://bugzilla.mozilla.org/show_bug.cgi?id=782751)-[FF54](https://bugzilla.mozilla.org/show_bug.cgi?id=1344669))


### Video Stats

```js
user_pref("media.video_stats.enabled", false);
```

Default:
`true`
  ![Win][Windows Logo]
  ![Debian][Debian Logo]
  ![Android][Android Logo],
`false`
  ![Tor Browser][Tor Browser Logo]
([FF25+](https://bugzilla.mozilla.org/show_bug.cgi?id=654550))

`true` provides web applications with information about video playback statistics such as the framerate [[ghacks.net](http://www.ghacks.net/overview-firefox-aboutconfig-security-privacy-preferences/)].


## Web API

WebAPI allows Web apps and content to access device hardware (such as battery status or the device vibration hardware), as well as access to data stored on the device (such as the calendar or contacts list) [[MDN](https://developer.mozilla.org/en-US/docs/WebAPI)].
[[WebAPI - MozillaWiki](https://wiki.mozilla.org/WebAPI)]

### Battery API

[[BatteryManager - MDN](https://developer.mozilla.org/en-US/docs/Web/API/BatteryManager)]

```js
user_pref("dom.battery.enabled", false);
```

Default:
`true`
  ![Win][Windows Logo]
  ![Debian][Debian Logo]
  ![Tor Browser][Tor Browser Logo]
  ![Android][Android Logo].
[[TechCrunch](https://techcrunch.com/2015/08/04/battery-attributes-can-be-used-to-track-web-users/)]


### Beacon API

[[Wikipedia](https://en.wikipedia.org/wiki/Web_beacon)]: A web beacon is an object embedded in a web page or email, which unobtrusively (usually invisibly) allows checking that a user has accessed the content. Common uses are email tracking and page tagging for web analytics.

[[MDN](https://developer.mozilla.org/en-US/docs/Web/API/Beacon_API)]: Example use cases of the Beacon API are logging activity and sending analytics data to the server.

```js
user_pref("beacon.enabled", false);
```

Default:
`true`
  ![Win][Windows Logo]
  ![Debian][Debian Logo]
  ![Tor Browser][Tor Browser Logo]
  ![Android][Android Logo]


### Camera API

[Camera API - MDN](https://developer.mozilla.org/en-US/docs/Mozilla/B2G_OS/API/Camera_API)

```js
user_pref("device.camera.enabled", false);
```

Default:
n/a
  ![Win][Windows Logo]
  ![Debian][Debian Logo]
  ![Tor Browser][Tor Browser Logo],
`true`
  ![Android][Android Logo]


### CSS Font Loading API

[CSS Font Loading API - MDN](https://developer.mozilla.org/en-US/docs/Web/API/CSSFontLoading_API)

```js
user_pref("layout.css.font-loading-api.enabled", false);
```

Default:
`true`
  ![Win][Windows Logo]
  ![Debian][Debian Logo]
  ![Tor Browser][Tor Browser Logo]
  ![Android][Android Logo]


### Device Storage API

```js
user_pref("device.storage.enabled", false);
```

Default:
`false`
  ![Debian][Debian Logo]
  ![Tor Browser][Tor Browser Logo]
  ![Win][Windows Logo],
`true`
  ![Android][Android Logo].
[[mozilla wiki](https://wiki.mozilla.org/WebAPI/DeviceStorageAPI#Security.2FPrivacy_considerations)]

[Device Storage API - Mozilla | MDN](https://developer.mozilla.org/en-US/docs/Mozilla/B2G_OS/API/Device_Storage_API)


### Gamepad API

[[MDN](https://developer.mozilla.org/en-US/docs/Web/API/Gamepad_API/Using_the_Gamepad_API)] [[W3C](https://www.w3.org/TR/gamepad/)]

```js
user_pref("dom.gamepad.enabled", false);
```

Default:
`true`
  ![Win][Windows Logo]
  ![Debian][Debian Logo]
  ![Android][Android Logo],
`false`
  ![Tor Browser][Tor Browser Logo]


### Geolocation API

[Geolocation - Web APIs | MDN](https://developer.mozilla.org/en-US/docs/Web/API/Geolocation)

```js
user_pref("geo.enabled", false);
```

Default:
`true`
  ![Win][Windows Logo]
  ![Debian][Debian Logo]
  ![Android][Android Logo],
`false`
  ![Tor Browser][Tor Browser Logo].
[[mozilla](https://www.mozilla.org/en-US/firefox/geolocation/)]


```js
user_pref("geo.wifi.logging.enabled", false);
```

Default:
n/a
  ![Win][Windows Logo]
  ![Debian][Debian Logo]
  ![Tor Browser][Tor Browser Logo]
  ![Android][Android Logo]
(hidden)


```js
user_pref("geo.wifi.xhr.timeout", 1);
```

Default:
`60000`
  ![Win][Windows Logo]
  ![Debian][Debian Logo]
  ![Tor Browser][Tor Browser Logo]
  ![Android][Android Logo]


```js
user_pref("geo.wifi.uri", "");
```

Default:
"https://www.googleapis.com/geolocation/v1/geolocate?key=%GOOGLE_API_KEY%"
  ![Win][Windows Logo]
  ![Debian][Debian Logo],
"(_empty string_)"
  ![Tor Browser][Tor Browser Logo],
n/a
  ![Android][Android Logo]

The information around you (mac addresses, signal strengths, SSIDs and etc.) is transmitted to Google Location Services in order to locate you [[stackoverflow](http://stackoverflow.com/a/5134619)].

[Geolocation Test](http://html5demos.com/geo)


#### Geolocation-Based Search

[[mozilla-central](https://dxr.mozilla.org/mozilla-central/source/layout/tools/reftest/reftest-preferences.js#58)]: Tell the search service we are running in the US:

```js
user_pref("browser.search.countryCode", "US");
user_pref("browser.search.region", "US");
```

Default:
n/a (hidden)
  ![Win][Windows Logo]
  ![Debian][Debian Logo]
  ![Android][Android Logo],
"US"
  ![Tor Browser][Tor Browser Logo].
[[Tor Bug #16254](https://trac.torproject.org/projects/tor/ticket/16254)]


```js
user_pref("browser.search.isUS", true);
```

Default:
n/a (hidden)
  ![Win][Windows Logo]
  ![Debian][Debian Logo]
  ![Tor Browser][Tor Browser Logo]
  ![Android][Android Logo]


```js
user_pref("browser.search.geoSpecificDefaults", false);
```

Default:
`true`
  ![Win][Windows Logo]
  ![Debian][Debian Logo]
  ![Android][Android Logo],
`false`
  ![Tor Browser][Tor Browser Logo].
[[ghacks](http://www.ghacks.net/2015/08/18/a-comprehensive-list-of-firefox-privacy-and-security-settings/)]


```js
user_pref("browser.search.geoSpecificDefaults.url", "");
```

Default:
"https://search.services.mozilla.com/1/%APP%/%VERSION%/%CHANNEL%/%LOCALE%/%REGION%/%DISTRIBUTION%/%DISTRIBUTION_VERSION%"
  ![Win][Windows Logo]
  ![Debian][Debian Logo]
  ![Tor Browser][Tor Browser Logo]
  ![Android][Android Logo]


```js
user_pref("browser.search.geoip.timeout", 1);
```

Default:
`3000`
  ![Win][Windows Logo]
  ![Debian][Debian Logo]
  ![Tor Browser][Tor Browser Logo]
  ![Android][Android Logo].
[[Raven Wiki](https://wiki.kairaven.de/open/app/firefox)]


```js
user_pref("browser.search.geoip.url", "");
```

Default:
"https://location.services.mozilla.com/v1/country?key=%MOZILLA_API_KEY%"
  ![Win][Windows Logo]
  ![Debian][Debian Logo]
  ![Android][Android Logo],
"(_empty string_)"
  ![Tor Browser][Tor Browser Logo].
[[mozilla support](https://support.mozilla.org/en-US/kb/how-stop-firefox-making-automatic-connections#w_geolocation-for-default-search-engine)]


### HTMLCanvasElement

[HTMLCanvasElement.captureStream() - MDN](https://developer.mozilla.org/en-US/docs/Web/API/HTMLCanvasElement/captureStream)

[Canvas PeerConnection Demo](https://mozilla.github.io/webrtc-landing/canvas_demo.html)

```js
user_pref("canvas.capturestream.enabled", false);
```

Default:
`true`
  ![Win][Windows Logo]
  ![Debian][Debian Logo]
  ![Tor Browser][Tor Browser Logo]
  ![Android][Android Logo]
(FF41+)


### Network Information API

[[Network Information API - MDN](https://developer.mozilla.org/en-US/docs/Web/API/Network_Information_API)]

```js
user_pref("dom.netinfo.enabled", false);
```

Default:
`false`
  ![Win][Windows Logo]
  ![Debian][Debian Logo]
  ![Tor Browser][Tor Browser Logo],
`true`
  ![Android][Android Logo].
[[wicg.io](https://wicg.github.io/netinfo/)]


### Notification API

[[Notifications API - MDN](https://developer.mozilla.org/en-US/docs/Web/API/Notifications_API)] [[Notification - MDN](https://developer.mozilla.org/en-US/docs/Web/API/notification)]

```js
user_pref("dom.webnotifications.enabled", false);
user_pref("dom.webnotifications.serviceworker.enabled", false);
```

Default:
`true`
  ![Win][Windows Logo]
  ![Debian][Debian Logo]
  ![Tor Browser][Tor Browser Logo]
  ![Android][Android Logo].
[[Mozilla Support Forum](https://support.mozilla.org/en-US/questions/1140700)]


## Push API

The Push API gives web applications the ability to receive messages pushed to them from a server, whether or not the web app is in the foreground [[MDN](https://developer.mozilla.org/docs/Web/API/Push_API)].

[Mozilla Wiki](https://wiki.mozilla.org/Firefox/Push_Notifications),
[Mozilla Hacks](https://hacks.mozilla.org/2016/01/web-push-arrives-in-firefox-44/)


```js
user_pref("dom.push.enabled", false);
```

Default:
`true`
  ![Win][Windows Logo]
  ![Debian][Debian Logo]
  ![Android][Android Logo],
`false`
  ![Tor Browser][Tor Browser Logo]


```js
user_pref("dom.push.connection.enabled", false);
```

Default:
`true`
  ![Win][Windows Logo]
  ![Debian][Debian Logo]
  ![Tor Browser][Tor Browser Logo]
  ![Android][Android Logo]


```js
user_pref("dom.push.serverURL", "");
```

Default:
"wss://push.services.mozilla.com/"
  ![Win][Windows Logo]
  ![Debian][Debian Logo],
"(_empty string_)"
  ![Tor Browser][Tor Browser Logo],
"https://updates.push.services.mozilla.com/v1/gcm/..."
  ![Android][Android Logo]


### Sensor API

[[Sensor API - mozilla wiki](https://wiki.mozilla.org/Sensor_API)]

```js
user_pref("device.sensors.enabled", false);
```

Default:
`true`
  ![Win][Windows Logo]
  ![Debian][Debian Logo]
  ![Android][Android Logo],
`false`
  ![Tor Browser][Tor Browser Logo].
[[Tor Bug #15758](https://trac.torproject.org/projects/tor/ticket/15758)]


### Vibration API

[[MDN](https://developer.mozilla.org/en-US/docs/Web/API/Vibration_API)] [[W3C](https://w3c.github.io/vibration/)]

```js
user_pref("dom.vibrator.enabled", false);
```

Default:
`true`
  ![Win][Windows Logo]
  ![Debian][Debian Logo]
  ![Tor Browser][Tor Browser Logo]
  ![Android][Android Logo]


## WebGL API

[The WebGL API: 2D and 3D graphics for the web - MDN](https://developer.mozilla.org/en-US/docs/Web/API/WebGL_API)

```js
user_pref("webgl.disabled", true);
```

Default:
`false`
  ![Win][Windows Logo]
  ![Debian][Debian Logo]
  ![Tor Browser][Tor Browser Logo]
  ![Android][Android Logo]

[Is WebGL a security concern? - Security Stack Exchange](https://security.stackexchange.com/questions/13799/is-webgl-a-security-concern)

<hr align="left" width="30%"/>

[WEBGL debug renderer info - MDN](https://developer.mozilla.org/en-US/docs/Web/API/WEBGL_debug_renderer_info)

```js
user_pref("webgl.enable-debug-renderer-info", false);
```

Default:
`true`
  ![Win][Windows Logo]
  ![Debian][Debian Logo]
  ![Tor Browser][Tor Browser Logo]
  ![Android][Android Logo]

[Bug 1171228: Expose WEBGL_debug_renderer_info extension to Web content - Bugzilla](https://bugzilla.mozilla.org/show_bug.cgi?id=1171228)


### [Web Speech API](https://developer.mozilla.org/en-US/docs/Web/API/Web_Speech_API)

```js
user_pref("media.webspeech.synth.enabled", false);
```

Default:
`true`
  ![Win][Windows Logo]
  ![Debian][Debian Logo],
`false`
  ![Tor Browser][Tor Browser Logo]
  ![Android][Android Logo]
([FF45+](https://bugzilla.mozilla.org/show_bug.cgi?id=1003439))


## [WebVR API](https://developer.mozilla.org/en-US/docs/Web/API/WebVR_API)

```js
user_pref("dom.vr.process.enabled", false);
```

Default:
`true`
  ![Win][Windows Logo],
`false`
  ![Debian][Debian Logo]
  ![Android][Android Logo],
n/a
  ![Tor Browser][Tor Browser Logo]
([FF68+](https://github.com/earthlng/FFprefs-diffs/blob/master/diffs/6x/diff-v67.0-vs-v68.0.log.js))


## Web Channel

[WebChannel.jsm - MDN](https://developer.mozilla.org/en-US/docs/Mozilla/JavaScript_code_modules/WebChannel.jsm)

```js
user_pref("webchannel.allowObject.urlWhitelist", "");
```

Default:
"https://content.cdn.mozilla.net https://input.mozilla.org https://support.mozilla.org https://install.mozilla.org"
  ![Win][Windows Logo]
  ![Debian][Debian Logo]
  ![Tor Browser][Tor Browser Logo]
  ![Android][Android Logo]

Space separated list of URLS that are allowed to send objects (instead of only strings) through webchannels [[DXR](https://dxr.mozilla.org/mozilla-central/source/browser/app/profile/firefox.js)].


## Accessibility Service

Firefox Accessibility Service is a technology built into Firefox that provides 3rd party applications running on the same device the ability to inspect, monitor, visualize, and alter web page content hosted within Firefox [[Mozilla Support](https://support.mozilla.org/en-US/kb/accessibility-services)].

```js
user_pref("accessibility.force_disabled", 1);
```

Default:
`0`
  ![Win][Windows Logo]
  ![Debian][Debian Logo]
  ![Tor Browser][Tor Browser Logo]
  ![Android][Android Logo]
(FF57+)


## Auto Play

### Animated Image

```js
user_pref("image.animation_mode", "none");
```

Default:
"normal"
  ![Win][Windows Logo]
  ![Debian][Debian Logo]
  ![Tor Browser][Tor Browser Logo]
  ![Android][Android Logo]

`none`: animated images will never play [[mozillaZine](http://kb.mozillazine.org/Firefox_:_Tips_:_Animated_Images)].


### Media

```js
user_pref("media.autoplay.default", 1);
```

Default:
`1`
  ![Win][Windows Logo]
  ![Debian][Debian Logo]
  ![Android][Android Logo],
n/a
  ![Tor Browser][Tor Browser Logo].
(FF65+)

`0`: autoplay is allowed;
`1`: autoplay is blocked
[[MDN web docs](https://developer.mozilla.org/en-US/docs/Web/Media/Autoplay_guide#Browser_configuration_options)].


```js
user_pref("media.autoplay.enabled.user-gestures-needed", false);
```

Default:
`true`
  ![Win][Windows Logo]
  ![Debian][Debian Logo]
  ![Android][Android Logo],
n/a
  ![Tor Browser][Tor Browser Logo].
(FF66+)

`false`: detection of user gestures is not allowed to override the setting of `media.autoplay.default`
[[MDN web docs](https://developer.mozilla.org/en-US/docs/Web/Media/Autoplay_guide#Browser_configuration_options)].


```js
user_pref("media.autoplay.allow-muted", false);
```

Default:
`true`
  ![Win][Windows Logo]
  ![Debian][Debian Logo]
  ![Android][Android Logo],
n/a
  ![Tor Browser][Tor Browser Logo].
  (FF65+).


## Bookmarks

```js
user_pref("browser.bookmarks.max_backups", 2);
```

Default:
`15`
  ![Win][Windows Logo]
  ![Debian][Debian Logo]
  ![Tor Browser][Tor Browser Logo],
`5`
  ![Android][Android Logo].
[[mozillazine](http://kb.mozillazine.org/Browser.bookmarks.max_backups)]


## Cache

```js
user_pref("browser.cache.disk.parent_directory", "R:\TEMP\FirefoxCache");
```
Default:
  n/a.
[[mozillaZine](http://kb.mozillazine.org/Browser.cache.disk.parent_directory)]

To use RAM disk for caching is good for systems with big enough RAM.


## Clear History

```js
user_pref("privacy.cpd.offlineApps", true);
```

Default:
`false`
  ![Win][Windows Logo]
  ![Debian][Debian Logo]
  ![Tor Browser][Tor Browser Logo],
n/a
  ![Android][Android Logo]

`true`: Automatically select "Offline Website Data" in the list of history items to clear.


```js
user_pref("privacy.sanitize.timeSpan", 0);
```

Default:
`1`
  ![Win][Windows Logo]
  ![Debian][Debian Logo]
  ![Tor Browser][Tor Browser Logo],
n/a
  ![Android][Android Logo]

What default should we use for the time span in the sanitizer: `0` - clear everything, `1` - last hour [[DXR](https://dxr.mozilla.org/mozilla-central/source/browser/app/profile/firefox.js)].


## Closing Last Tab

```js
user_pref("browser.tabs.closeWindowWithLastTab", false);
```

Default:
`true`
  ![Debian][Debian Logo]
  ![Tor Browser][Tor Browser Logo]

`false` prevents Firefox from exiting when you close the last Tab.


## Developer Tools

### WebIDE

[WebIDE - MDN](https://developer.mozilla.org/en-US/docs/Tools/WebIDE)

[16222: Review networking code for Firefox 38 | Tor Trac](https://trac.torproject.org/projects/tor/ticket/16222)

```js
user_pref("devtools.webide.enabled", false);
```

Default:
`false`
  ![Tor Browser][Tor Browser Logo],
n/a
  ![Win][Windows Logo]
  ![Debian][Debian Logo]
  ![Android][Android Logo]
(-FF70)


```js
user_pref("devtools.webide.autoinstallADBHelper", false);
```

Default:
`true`
  ![Win][Windows Logo],
`false`
  ![Debian][Debian Logo]
  ![Tor Browser][Tor Browser Logo],
n/a
  ![Android][Android Logo]


```js
user_pref("devtools.webide.autoinstallFxdtAdapters", false);
```

Default:
`false`
  ![Tor Browser][Tor Browser Logo]
([-FF56](https://bugzilla.mozilla.org/show_bug.cgi?id=1393497))


## DOM

### Clipboard

```js
user_pref("dom.allow_cut_copy", true);
```

Default:
`true`
  ![Win][Windows Logo]
  ![Debian][Debian Logo]
  ![Android][Android Logo],
n/a (hidden)
  ![Tor Browser][Tor Browser Logo].
[[reddit](https://www.reddit.com/r/firefox/comments/5upj7a/disable_js_access_to_clipboard/)]
[[Bug 1170911](https://bugzilla.mozilla.org/show_bug.cgi?id=1170911)]

WARNING: `false` makes impossible to get a link to issue comment in github repositories.


```js
user_pref("dom.event.clipboardevents.enabled", false);
```

Default:
`true`
  ![Win][Windows Logo]
  ![Debian][Debian Logo]
  ![Tor Browser][Tor Browser Logo]
  ![Android][Android Logo]

`false`: Do not let websites to get notifications if the user copies, pastes, or cuts something from a web page, and do not let them know which part of the page has been selected [[MDN](https://developer.mozilla.org/en-US/docs/Mozilla/Preferences/Preference_reference/dom.event.clipboardevents.enabled)].


### Context Menu

[][DOM Entries - mozillaZine]

[DOM entries - mozillaZine]: http://kb.mozillazine.org/About:config_entries#DOM.

```js
user_pref("dom.event.contextmenu.enabled", false);
```

Default:
`true`
  ![Win][Windows Logo]
  ![Debian][Debian Logo]
  ![Tor Browser][Tor Browser Logo]
  ![Android][Android Logo]

`false`: Webpages will not be able to affect the context menu event [[DOM Entries - mozillaZine]].


### Device Name

```js
user_pref("dom.presentation.device.name", "dummy-device");
```

Default:
n/a
  ![Win][Windows Logo]
  ![Debian][Debian Logo]
  ![Tor Browser][Tor Browser Logo]
  ![Android][Android Logo]

_Note_: Firefox for Android sets name of your device. [[Bug 1265275]](https://bugzilla.mozilla.org/show_bug.cgi?id=1265275)


### Storage

```js
user_pref("dom.storage.enabled", true);
```

Default:
`true`
  ![Win][Windows Logo]
  ![Debian][Debian Logo]
  ![Tor Browser][Tor Browser Logo]
  ![Android][Android Logo]

`false` may break some sites.

[Web Storage - Wikipedia](https://en.wikipedia.org/wiki/Web_storage)

[Web Storage API - MDN](https://developer.mozilla.org/en-US/docs/Web/API/Web_Storage_API)


### Window

```js
user_pref("dom.disable_window_move_resize", true);
```

Default:
`false`
  ![Win][Windows Logo]
  ![Debian][Debian Logo]
  ![Tor Browser][Tor Browser Logo],
`true`
  ![Android][Android Logo]

`true`: Windows may not be moved or resized [[DOM Entries - mozillaZine]].


```js
user_pref("dom.disable_window_open_feature.close", true);
```

Default:
`false`
  ![Win][Windows Logo]
  ![Debian][Debian Logo]
  ![Tor Browser][Tor Browser Logo]
  ![Android][Android Logo]

`true`: Prevent close button from being disabled [[DOM Entries - mozillaZine]].


```js
user_pref("dom.disable_window_open_feature.location", true);
```

Default:
`true`
  ![Win][Windows Logo]
  ![Debian][Debian Logo]
  ![Tor Browser][Tor Browser Logo],
`false`
  ![Android][Android Logo]

`true`: Prevent popups from hiding the Location Bar [[mozillaZine](http://kb.mozillazine.org/Dom.disable_window_open_feature.location)].


```js
user_pref("dom.disable_window_open_feature.menubar", true);
```

Default:
`false`
  ![Win][Windows Logo]
  ![Debian][Debian Logo]
  ![Tor Browser][Tor Browser Logo]
  ![Android][Android Logo]

`true`: Prevent menubar from being hidden [[DOM Entries - mozillaZine]].


```js
user_pref("dom.disable_window_open_feature.minimizable", true);
```

Default:
`false`
  ![Win][Windows Logo]
  ![Debian][Debian Logo]
  ![Tor Browser][Tor Browser Logo]
  ![Android][Android Logo]

`true`: Prevent popup window minimization from being disabled [[DOM Entries - mozillaZine]].


```js
user_pref("dom.disable_window_open_feature.personalbar", true);
```

Default:
`false`
  ![Win][Windows Logo]
  ![Debian][Debian Logo]
  ![Tor Browser][Tor Browser Logo]
  ![Android][Android Logo]

`true`: Prevent bookmarks toolbar from being hidden [[DOM Entries - mozillaZine]].


```js
user_pref("dom.disable_window_open_feature.toolbar", true);
```

Default:
`false`
  ![Win][Windows Logo]
  ![Debian][Debian Logo]
  ![Tor Browser][Tor Browser Logo]
  ![Android][Android Logo]

`true`: Prevent navigation toolbar from being hidden [[DOM Entries - mozillaZine]].


## Download Manager

```js
user_pref("browser.helperApps.deleteTempFileOnExit", true);
```

Default:
`true`
  ![Win][Windows Logo]
  ![Debian][Debian Logo]
  ![Tor Browser][Tor Browser Logo],
`false`
  ![Android][Android Logo].
[[mozillaZine](http://kb.mozillazine.org/About:config_entries#Browser.)]


```js
user_pref("browser.download.folderList", 2);
```

Default:
`1`
  ![Win][Windows Logo]
  ![Debian][Debian Logo]
  ![Tor Browser][Tor Browser Logo]
  ![Android][Android Logo]

`1`: system default folder,
`2`: custom (user defined) folder. [[MDN](https://developer.mozilla.org/en-US/docs/Download_Manager_preferences)]

```js
user_pref("browser.download.useDownloadDir", false);
```

Default:
`true`
  ![Win][Windows Logo]
  ![Debian][Debian Logo]
  ![Android][Android Logo],
`false`
  ![Tor Browser][Tor Browser Logo]

`false`: Always ask where to download. [[MDN](https://developer.mozilla.org/en-US/docs/Download_Manager_preferences)]


## Fingerprinting

```js
user_pref("privacy.resistFingerprinting", true);
```

Default:
`false`
  ![Win][Windows Logo]
  ![Debian][Debian Logo]
  ![Android][Android Logo],
`true`
  ![Tor Browser][Tor Browser Logo]

[Security/Fingerprinting | mozilla wiki](https://wiki.mozilla.org/Security/Fingerprinting)

[Bug 418986: window.screen and CSS media queries provide a large amount of identifiable information (Tor 2875) | Bugzilla](https://bugzilla.mozilla.org/show_bug.cgi?id=418986)


[Bug 1333933: Disable/spoof fingerprintable features when privacy.resistFingerprinting = true | Bugzilla](https://bugzilla.mozilla.org/show_bug.cgi?id=1333933)

[meta: tor uplift: privacy.resistFingerprinting #7 | ghacks-user.js](https://github.com/ghacksuserjs/ghacks-user.js/issues/7)


### OS Locale

```js
user_pref("javascript.use_us_english_locale", true);
```

Default:
n/a (hidden)
  ![Win][Windows Logo]
  ![Debian][Debian Logo]
  ![Tor Browser][Tor Browser Logo]
  ![Android][Android Logo]

An anti-fingerprinting patch from Tor Browser was added to Firefox 46 to force using en-US date format regardless of the OS locale [[Bug 867501](https://bugzilla.mozilla.org/show_bug.cgi?id=867501)].


## Fonts

### Document Fonts

```js
user_pref("browser.display.use_document_fonts", 0);
```

Default:
`1`
  ![Win][Windows Logo]
  ![Debian][Debian Logo]
  ![Tor Browser][Tor Browser Logo]
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

Default:
`true`
  ![Win][Windows Logo]
  ![Debian][Debian Logo]
  ![Tor Browser][Tor Browser Logo]
  ![Android][Android Logo]


### Fonts with Incorrect Underline Offsets

```js
user_pref("font.blacklist.underline_offset", "");
```

Default:
"(_list of fonts_)"
  ![Win][Windows Logo]
  ![Debian][Debian Logo]
  ![Tor Browser][Tor Browser Logo]
  ![Android][Android Logo].
[[mozillaZine](http://kb.mozillazine.org/Font.blacklist.underline_offset)]

Any of these fonts on your system can be enumerated for fingerprinting [[ghacks-user.js](https://github.com/ghacksuserjs/ghacks-user.js/blob/master/user.js)].


## Forms

```js
user_pref("browser.formfill.enable", false);
```

Default:
`true`
  ![Win][Windows Logo]
  ![Debian][Debian Logo]
  ![Android][Android Logo],
`false`
  ![Tor Browser][Tor Browser Logo]

`false`: Do not save information entered in web page forms and the Search Bar [[mozillaZine](http://kb.mozillazine.org/About:config_entries#Browser.)].


```js
user_pref("browser.formfill.expire_days", 0);
```

Default:
`180`
  ![Win][Windows Logo]
  ![Debian][Debian Logo]
  ![Tor Browser][Tor Browser Logo]
  ![Android][Android Logo]


```js
user_pref("extensions.formautofill.available", "off");
```

Default:
`on`
  ![Win][Windows Logo],
`detect`
  ![Debian][Debian Logo]
  ![Tor Browser][Tor Browser Logo],
n/a
  ![Android][Android Logo]

```js
user_pref("extensions.formautofill.addresses.enabled", false);
user_pref("extensions.formautofill.creditCards.enabled", false);
user_pref("extensions.formautofill.heuristics.enabled", false);
```

Default:
`true`
  ![Win][Windows Logo]
  ![Debian][Debian Logo]
  ![Tor Browser][Tor Browser Logo],
n/a
  ![Android][Android Logo]

[Form Autofill - mozilla wiki](https://wiki.mozilla.org/Firefox/Features/Form_Autofill)

```js
user_pref("extensions.formautofill.creditCards.available", false);
```

Default:
`true`
  ![Win][Windows Logo],
`false`
  ![Debian][Debian Logo]
  ![Tor Browser][Tor Browser Logo],
n/a
  ![Android][Android Logo]


### Animation


### Fullscreen Animation

```js
user_pref("toolkit.cosmeticAnimations.enabled", false);
```

Default:
`true`
  ![Debian][Debian Logo]
  ![Tor Browser][Tor Browser Logo]
  ![Android][Android Logo]


```js
user_pref("full-screen-api.warning.delay", 0);
```

Default:
`500`
  ![Win][Windows Logo]
  ![Debian][Debian Logo]
  ![Tor Browser][Tor Browser Logo]
  ![Android][Android Logo]

[Fullscreen API - MDN](https://developer.mozilla.org/en-US/docs/Web/API/Fullscreen_API)


```js
user_pref("full-screen-api.warning.timeout", 0);
```

Default:
`3000`
  ![Win][Windows Logo]
  ![Debian][Debian Logo]
  ![Tor Browser][Tor Browser Logo]
  ![Android][Android Logo]


### Reduced Motion

```js
user_pref("ui.prefersReducedMotion", 1);
```

Default:
n/a (hidden)
  ![Win][Windows Logo]
  ![Debian][Debian Logo]
  ![Tor Browser][Tor Browser Logo]
  ![Android][Android Logo]

`1`: minimize the amount of non-essential motion
[[MDN](https://developer.mozilla.org/en-US/docs/Web/CSS/@media/prefers-reduced-motion)].


## Location Bar

```js
user_pref("browser.urlbar.searchSuggestionsChoice", false);
```

Default:
`true`
  ![Win][Windows Logo]
  ![Debian][Debian Logo],
n/a
  ![Tor Browser][Tor Browser Logo]
  ![Android][Android Logo]


```js
user_pref("browser.urlbar.suggest.history", false);
user_pref("browser.urlbar.suggest.openpage", false);
```

Default:
`true`
  ![Win][Windows Logo]
  ![Debian][Debian Logo]
  ![Tor Browser][Tor Browser Logo],
n/a
  ![Android][Android Logo]


```js
user_pref("browser.urlbar.suggest.searches", false);
```

Default:
`true`
  ![Win][Windows Logo]
  ![Tor Browser][Tor Browser Logo],
`false`
  ![Debian][Debian Logo],
n/a
  ![Android][Android Logo]


```js
user_pref("browser.urlbar.clickSelectsAll", true);
```

Default:
`true`
  ![Win][Windows Logo],
`false`
  ![Debian][Debian Logo]
  ![Tor Browser][Tor Browser Logo]
  ![Android][Android Logo]


### Domain Guessing

Domain Guessing intercepts the DNS "hostname not found" error, and resends the
request to a guessed hostname that might use the correct domain [[Domain Guessing - Mozilla Archive](http://www-archive.mozilla.org/docs/end-user/domain-guessing.html)].

```js
user_pref("browser.fixup.alternate.enabled", false);
```

Default:
`true`
  ![Win][Windows Logo]
  ![Debian][Debian Logo]
  ![Android][Android Logo],
`false`
  ![Tor Browser][Tor Browser Logo]

`false`: Disable location bar domain guessing.


### Keyword Service

[[mozillaZine](http://kb.mozillazine.org/Keyword.enabled)]: When entering information in the Location Bar, Mozilla attempts to convert the information into a usable URI. For example, "mozilla.org" is automatically converted to "http://mozilla.org/". When Mozilla is unable to discern what URL the user wanted, the information that was entered may be submitted to an Internet Keywords service. This preference determines whether or not to use Internet Keywords.

```js
user_pref("keyword.enabled", false);
```

Default:
`true`
  ![Win][Windows Logo]
  ![Debian][Debian Logo]
  ![Tor Browser][Tor Browser Logo]
  ![Android][Android Logo]

`false`: Do not use Internet Keywords and display an error message indicating the entered information is not a valid URL.

---

```js
user_pref("browser.urlbar.speculativeConnect.enabled", false);
```

Default:
`true`
  ![Win][Windows Logo]
  ![Debian][Debian Logo]
  ![Tor Browser][Tor Browser Logo],
n/a
  ![Android][Android Logo]
(FF57+)

[Bug 1348275: speculatively connect to web server(s) on autocomplete when typing in awesomebar - Bugzilla](https://bugzilla.mozilla.org/show_bug.cgi?id=1348275)


```js
user_pref("browser.urlbar.trimURLs", false);
```

Default:
`true`
  ![Win][Windows Logo]
  ![Debian][Debian Logo]
  ![Tor Browser][Tor Browser Logo]
  ![Android][Android Logo]
(FF7+)

`false` - all parts of the url are shown
[[MDN](https://developer.mozilla.org/en-US/docs/Mozilla/Preferences/Preference_reference/browser.urlbar.trimURLs)].


## Mozilla Websites

The WebExtensions do not work on Mozilla websites by default [[ghacks.net](https://www.ghacks.net/2017/10/27/how-to-enable-firefox-webextensions-on-mozilla-websites/)].


```js
user_pref("privacy.resistFingerprinting.block_mozAddonManager", true);
```

Default:
n/a (hidden)
  ![Win][Windows Logo]
  ![Debian][Debian Logo]
  ![Android][Android Logo],
`true`
  ![Tor Browser][Tor Browser Logo]


```js
user_pref("extensions.webextensions.restrictedDomains", "");
```

Default:
"accounts-static.cdn.mozilla.net,accounts.firefox.com,addons.cdn.mozilla.net,addons.mozilla.org,api.accounts.firefox.com,content.cdn.mozilla.net,discovery.addons.mozilla.org,input.mozilla.org,install.mozilla.org,oauth.accounts.firefox.com,profile.accounts.firefox.com,support.mozilla.org,sync.services.mozilla.com"
  ![Win][Windows Logo]
  ![Debian][Debian Logo]
  ![Android][Android Logo],
"(empty string)"
  ![Tor Browser][Tor Browser Logo]


## Offline Data

```js
user_pref("offline-apps.allow_by_default", false);
```

Default:
`true`
  ![Tor Browser][Tor Browser Logo],
n/a
  ![Win][Windows Logo]
  ![Debian][Debian Logo]
  ![Android][Android Logo]
(-FF70)

[Firefox not honoring "Offline Web Content And User Data" settings - Mozilla Support Forum](https://support.mozilla.org/questions/1098540)


## Passwords

[Password Manager - mozillaZine](http://kb.mozillazine.org/Password_Manager)

[Master Password - mozilla support](https://support.mozilla.org/en-US/kb/use-master-password-protect-stored-logins)

```js
user_pref("signon.rememberSignons", false);
```

Default:
`true`
  ![Win][Windows Logo]
  ![Debian][Debian Logo]
  ![Android][Android Logo],
`false`
  ![Tor Browser][Tor Browser Logo]

`false`: Disable the Password Manager [[mozillaZine](http://kb.mozillazine.org/About:config_entries#Signon.)].


```js
user_pref("signon.autofillForms", false);
```

Default:
`true`
  ![Win][Windows Logo]
  ![Debian][Debian Logo]
  ![Android][Android Logo],
`false`
  ![Tor Browser][Tor Browser Logo]

`false`: Do not automatically fill sign-in forms with known usernames and passwords [[mozillaZine](http://kb.mozillazine.org/Signon.autofillForms)].


```js
user_pref("signon.storeWhenAutocompleteOff", false);
```

Default:
`true`
  ![Win][Windows Logo]
  ![Debian][Debian Logo]
  ![Tor Browser][Tor Browser Logo]
  ![Android][Android Logo]

`false`: Do not ignore [`autocomplete=off` form feature](http://www.w3schools.com/tags/att_input_autocomplete.asp) that some websites use to prevent password storing or automatic fill out into sign-on forms, in other words, Firefox Password Manager (if it is enabled) will be not used on that websites. [[Mozilla Bugzilla](https://bugzilla.mozilla.org/show_bug.cgi?id=956906)]


```js
user_pref("signon.formlessCapture.enabled", false);
```

Default:
`true`
  ![Win][Windows Logo]
  ![Debian][Debian Logo]
  ![Tor Browser][Tor Browser Logo]
  ![Android][Android Logo]
(FF51+)

`false`: disable formless login capture for Password Manager.


## PDF Viewer

```js
user_pref("pdfjs.disabled", true);
```

Default:
`false`
  ![Win][Windows Logo]
  ![Debian][Debian Logo]
  ![Tor Browser][Tor Browser Logo],
n/a
  ![Android][Android Logo]. [[mozilla pdf.js FAQ](https://github.com/mozilla/pdf.js/wiki/Frequently-Asked-Questions)] [[mozilla support](https://support.mozilla.org/en-US/kb/view-pdf-files-firefox-without-downloading-them)]


## Plugins

```js
user_pref("plugin.scan.plid.all", false);
```

Default:
`true`
  ![Win][Windows Logo],
n/a
  ![Debian][Debian Logo]
  ![Tor Browser][Tor Browser Logo]
  ![Android][Android Logo]

`false`: Disable all Mozilla plugins specified in the Windows registry `HKLM\Software\MozillaPlugins\` [[mozillaZine](http://kb.mozillazine.org/Plugin_scanning)].


```js
user_pref("plugin.default.state", 0);
```

Default:
`1`
  ![Win][Windows Logo]
  ![Debian][Debian Logo]
  ![Tor Browser][Tor Browser Logo],
`2`
  ![Android][Android Logo]

`0` - never activate, `1` - ask to activate, `2` - active.

```js
user_pref("plugin.defaultXpi.state", 0);
```

Default:
`2`
  ![Win][Windows Logo]
  ![Debian][Debian Logo]
  ![Tor Browser][Tor Browser Logo],
n/a
  ![Android][Android Logo]

`2` - Plugins bundled in XPIs are enabled by default
[[DXR](https://dxr.mozilla.org/mozilla-central/source/browser/app/profile/firefox.js)].


## Popup Windows

```js
user_pref("browser.link.open_newwindow.restriction", 0);
```

Default:
`2`
  ![Win][Windows Logo]
  ![Debian][Debian Logo],
`0`
  ![Tor Browser][Tor Browser Logo]
  ![Android][Android Logo]

`0`: Force all new windows opened by JavaScript into tabs [[mozillaZine](http://kb.mozillazine.org/About:config_entries#Browser.), [Tor Bug #9881](https://trac.torproject.org/projects/tor/ticket/9881)]. [Test](https://people.torproject.org/~gk/misc/entire_desktop.html)


```js
user_pref("dom.popup_maximum", 3);
```

Default:
`20`
  ![Win][Windows Logo]
  ![Debian][Debian Logo]
  ![Tor Browser][Tor Browser Logo]
  ![Android][Android Logo].
[mozillaZine](http://kb.mozillazine.org/Dom.popup_maximum)


## Reader Mode

```js
user_pref("reader.parse-on-load.enabled", false);
```

Default:
`true`
  ![Win][Windows Logo]
  ![Debian][Debian Logo]
  ![Tor Browser][Tor Browser Logo]
  ![Android][Android Logo]
[[ghacks.net](http://www.ghacks.net/2015/02/07/mozilla-starts-to-push-reader-mode-to-desktop-firefox/)]


## Screen Casting

Firefox contains a "Send Video To Device" feature to send HTML5 video content to a Roku, Chromecast or similar device in the same network. In order to discover and pair with such a device, Firefox will send SSDP packages to the local network (multicast address 239.255.255.250:1900) [[mozilla support](https://support.mozilla.org/en-US/kb/how-stop-firefox-making-automatic-connections#w_send-video-to-device)].

```js
user_pref("browser.casting.enabled", false);
```

Default:
`true`
  ![Android][Android Logo],
n/a
  ![Debian][Debian Logo]
  ![Tor Browser][Tor Browser Logo]
  ![Win][Windows Logo]
([-FF56](https://bugzilla.mozilla.org/show_bug.cgi?id=1393582))


## Screen Resolution

```js
user_pref("layout.css.devPixelsPerPx", "1.5");
```

Default (string):
`-1.0`
  ![Win][Windows Logo]
  ![Debian][Debian Logo]
  ![Tor Browser][Tor Browser Logo]
  ![Android][Android Logo]

Firefox uses 96 dpi by default. The fonts are too small to read in the case of high-resolution displays.
`1.5` sets dpi to 144.

>_Warning_: The pref breaks YouTube. The video will be shown only after the change of window size.

[Configure the DPI value - ArchWiki](https://wiki.archlinux.org/index.php/Firefox/Tweaks#Configure_the_DPI_value)


## Search Suggestions

```js
user_pref("browser.search.suggest.enabled", false);
```

Default:
`true`
  ![Win][Windows Logo]
  ![Debian][Debian Logo],
`false`
  ![Tor Browser][Tor Browser Logo]
  ![Android][Android Logo]

`false`: Do not offer "search suggestions" of similar search queries as a user enters a query in the Search Bar. [[mozillaZine](http://kb.mozillazine.org/Browser.search.suggest.enabled)]


## Security

### Digital Certificates

```js
user_pref("security.OCSP.enabled", 0);
```

Default:
`1`
  ![Win][Windows Logo]
  ![Debian][Debian Logo]
  ![Tor Browser][Tor Browser Logo],
`2`
  ![Android][Android Logo]

`0` - disabled, `1` - enabled, `2` - enabled for [EV certificates](https://en.wikipedia.org/wiki/Extended_Validation_Certificate) only.

[OCSP - privacy-handbuch.de](https://www.privacy-handbuch.de/handbuch_21r.htm) in German

[Online Certificate Status Protocol - Wikipedia](https://en.wikipedia.org/wiki/Online_Certificate_Status_Protocol)


### First-Party Isolation

```js
user_pref("privacy.firstparty.isolate", true);
```

Default:
`false`
  ![Win][Windows Logo]
  ![Debian][Debian Logo]
  ![Android][Android Logo],
`true`
  ![Tor Browser][Tor Browser Logo]
([FF51+](https://bugzilla.mozilla.org/show_bug.cgi?id=1260931))

`true` may  break cross-domain logins and site functionality.

[Bug 1299996: META: Support Tor first-party isolation - Bugzilla](https://bugzilla.mozilla.org/show_bug.cgi?id=1299996)

[Security/FirstPartyIsolation - mozilla wiki](https://wiki.mozilla.org/Security/FirstPartyIsolation#First_Party_Isolation_-_FIXED)

[meta: tor uplift: privacy.firstparty.isolate #8 - ghacks-user.js](https://github.com/ghacksuserjs/ghacks-user.js/issues/8)


### Punycode Phishing

```js
user_pref("network.IDN_show_punycode", true);
```

Default:
`false`
  ![Win][Windows Logo]
  ![Debian][Debian Logo]
  ![Tor Browser][Tor Browser Logo]
  ![Android][Android Logo]

[Internationalized Domain Name (IDN) homograph attack - wikipedia](https://en.wikipedia.org/wiki/IDN_homograph_attack)

[IDN Display Algorithm - mozilla wiki](https://wiki.mozilla.org/IDN_Display_Algorithm)

[Punycode Phishing Attacks - thehackernews.com](https://thehackernews.com/2017/04/unicode-Punycode-phishing-attack.html)


### SSL

```js
user_pref("security.ssl.treat_unsafe_negotiation_as_broken", true);
```

Default:
`false`
  ![Win][Windows Logo]
  ![Debian][Debian Logo]
  ![Tor Browser][Tor Browser Logo]
  ![Android][Android Logo].
[[mozilla wiki](https://wiki.mozilla.org/Security:Renegotiation#security.ssl.treat_unsafe_negotiation_as_broken)]


## Session Store

[Firefox is eating your SSD - here is how to fix it](https://www.servethehome.com/firefox-is-eating-your-ssd-here-is-how-to-fix-it/)

```js
user_pref("browser.sessionstore.interval", 1800000);
```

Default:
`15000`
  ![Win][Windows Logo]
  ![Debian][Debian Logo]
  ![Tor Browser][Tor Browser Logo],
`10000`
  ![Android][Android Logo]

The preference controls how often information about the current session is saved to the profile.


```js
user_pref("browser.sessionstore.privacy_level", 2);
```

Default:
`0`
  ![Win][Windows Logo]
  ![Debian][Debian Logo]
  ![Android][Android Logo],
`2`
  ![Tor Browser][Tor Browser Logo]

`0`: store extra session data for any site,
`1`: store extra session data for unencrypted (non-HTTPS) sites only,
`2`: never store extra session data. [[mozillaZine](http://kb.mozillazine.org/Browser.sessionstore.privacy_level)]


## Smooth Scrolling

```js
user_pref("general.smoothScroll", false);
```

Default: 
`true`
  ![Win][Windows Logo]
  ![Debian][Debian Logo]
  ![Tor Browser][Tor Browser Logo],
n/a
  ![Android][Android Logo]


## Startup

### Check Default Browser

```js
user_pref("browser.shell.checkDefaultBrowser", false);
```

Default:
`true`
  ![Win][Windows Logo],
`false`
  ![Debian][Debian Logo]
  ![Tor Browser][Tor Browser Logo],
n/a
  ![Android][Android Logo]

`false`:  Do not check on startup if Firefox is set as default browser [[mozillaZine](http://kb.mozillazine.org/About:config_entries#Browser.)].


### Rights

[Bug 462254 - Bugzilla](https://bugzilla.mozilla.org/show_bug.cgi?id=462254)

```js
user_pref("browser.rights.3.shown", true);
```

Default:
`false`
  ![Win][Windows Logo],
`true`
  ![Tor Browser][Tor Browser Logo],
n/a
  ![Debian][Debian Logo]
  ![Android][Android Logo]
([-FF61](https://github.com/earthlng/FFprefs-diffs/blob/65df04dd48f975073bfbb9fc48ceeb344e51ae33/diffs/6x/diff-v61.0-vs-v62.0.log.js))

### Slow Startup

```js
user_pref("browser.slowStartup.samples", "0");
```

Default (string):
n/a (hidden)
  ![Win][Windows Logo]
  ![Debian][Debian Logo],
`0`
  ![Tor Browser][Tor Browser Logo],
n/a
  ![Android][Android Logo]

Firefox determines whether or not the browser is slow to start up by storing information about browser startup times to disk. `0` prevents this information from being stored [[Tor Bug #13346](https://trac.torproject.org/projects/tor/ticket/13346)].

```js
user_pref("browser.slowStartup.maxSamples", 0);
```

Default:
`5`
  ![Win][Windows Logo]
  ![Debian][Debian Logo],
`0`
  ![Tor Browser][Tor Browser Logo],
n/a
  ![Android][Android Logo].
[Tor Bug #13346](https://trac.torproject.org/projects/tor/ticket/13346)

```js
user_pref("browser.slowStartup.notificationDisabled", true);
```

Default:
`false`
  ![Win][Windows Logo]
  ![Debian][Debian Logo],
`true`
  ![Tor Browser][Tor Browser Logo],
n/a
  ![Android][Android Logo].
[Tor Bug #13346](https://trac.torproject.org/projects/tor/ticket/13346)


### Startup Page

```js
user_pref("browser.startup.page", 0);
```

Default:
`1`
  ![Win][Windows Logo]
  ![Debian][Debian Logo]
  ![Tor Browser][Tor Browser Logo],
n/a
  ![Android][Android Logo]

`0` - blank page, `1` - home page, `2` - last visited page, `3` - resume previous session.
It can be changed in Options/Startup/When Firefox starts.


## Thumbnails

```js
user_pref("browser.pagethumbnails.capturing_disabled", true);
```

Default:
n/a (hidden)
  ![Win][Windows Logo]
  ![Debian][Debian Logo]
  ![Tor Browser][Tor Browser Logo]
  ![Android][Android Logo]

`true`: Do not create screenshots of visited pages which will be shown if the web page is shown in the grid of the "New Tab Page" [[MDN](https://developer.mozilla.org/en-US/docs/Mozilla/Preferences/Preference_reference/browser.pagethumbnails.capturing_disabled)]. The preference is available in the desktop versions of Firefox only.


## UI Tour

The UITour API provides ways for pages on trusted domains to safely interact with the browser UI and request it to perform actions such as opening menus and showing highlights over the browser chrome - for the purposes of interactive tours [[Mozilla Source Tree Docs](https://firefox-source-docs.mozilla.org/browser/browser/UITelemetry.html)].

```js
user_pref("browser.uitour.enabled", false);
```

Default:
`true`
  ![Win][Windows Logo]
  ![Debian][Debian Logo]
  ![Tor Browser][Tor Browser Logo],
n/a
  ![Android][Android Logo]

[Mozilla.UITour - Mozilla Documentation](https://bedrock.readthedocs.io/en/latest/uitour.html)


```js
user_pref("browser.uitour.url", "");
```

Default:
"https://www.mozilla.org/%LOCALE%/firefox/%VERSION%/tour/"
  ![Win][Windows Logo]
  ![Debian][Debian Logo]
  ![Tor Browser][Tor Browser Logo],
n/a
  ![Android][Android Logo]


## Video Buffering

```js
user_pref("media.mediasource.enabled", true);
```

Default:
`true`
  ![Win][Windows Logo]
  ![Debian][Debian Logo]
  ![Tor Browser][Tor Browser Logo]
  ![Android][Android Logo]

WARNING: Setting to `false` results in lost support of "Media Source Extensions" and "MSE & H.264" in [YouTube HTML5 Video Player](https://www.youtube.com/html5) and some YouTube videos can not be played anymore.

[How to enforce full video buffering on YouTube - ghacks.net](http://www.ghacks.net/2016/08/31/how-to-enforce-full-video-buffering-on-youtube/)


## View Source

```js
user_pref("view_source.tab", false);
```

Default:
`true`
  ![Win][Windows Logo]
  ![Debian][Debian Logo],
n/a
  ![Tor Browser][Tor Browser Logo]
  ![Android][Android Logo]
([-FF59?](https://github.com/earthlng/FFprefs-diffs/blob/38cf35c43c8479111dd3bc5e534386d8d746ee12/diffs/ESR/diff-v52.9.0esr-vs-v60.0esr.log.js), [FF68+](https://github.com/earthlng/FFprefs-diffs/blob/master/diffs/6x/diff-v67.0-vs-v68.0.log.js))

`false`: open page source in a new window.


## Warning on about config

```js
user_pref("general.warnOnAboutConfig", false);
```

Default:
`true`
  ![Tor Browser][Tor Browser Logo]
  ![Android][Android Logo],
n/a
  ![Win][Windows Logo]
  ![Debian][Debian Logo]
(-FF70)

```js
user_pref("browser.aboutConfig.showWarning", false);
```

Default:
`true`
  ![Win][Windows Logo]
  ![Debian][Debian Logo]
(FF71+)

`false`: display configuration screen (`about:config`) without a warning [[mozillaZine](http://kb.mozillazine.org/General.warnOnAboutConfig)].
