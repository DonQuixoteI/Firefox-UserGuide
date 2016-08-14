# user.js

## Index

- [Beacon](#beacon)
- [Browser Cache](#browser-cache)
- [Reports to Mozilla](#reports-to-mozilla)
  - [Crash Report](#crash-report)
  - [Health Report](#health-report)
  - [Telemetry](#telemetry)
    - [Experiments](#experiments)
- [Safe Browsing](#safe-browsing)
- [Updating](#updating)
- [WebRTC](#webrtc)
- [Auto-Play Animated Image](#auto-play-animated-image)
- [Auto-Play Videos](#auto-play-videos)
- [Extension Signing](#extension-signing)
- [Firefox Chat](#firefox-chat)
- [Home Page](#home-page)
  - [Messages on Home Page](#messages-on-home-page)

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

## Updating

```js
user_pref("app.update.enabled", false);
```

Default: `true` ![Windows][Windows Logo], `false` ![Debian][Debian Logo] ![Android][Android Logo].
[[mozillaZine](http://kb.mozillazine.org/App.update.enabled)]

```js
user_pref("browser.search.update", false);
```

Default: `true` ![Windows][Windows Logo] ![Debian][Debian Logo], `false` ![Android][Android Logo]

`false`: do not automatically check for updates to search plugins [[mozillaZine](http://kb.mozillazine.org/About:config_entries#Browser.)].

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

```js
user_pref("app.update.autodownload", "disabled");
```
Default: n/a ![Windows][Windows Logo] ![Debian][Debian Logo], "wifi" ![Android][Android Logo]

```js
user_pref("lightweightThemes.update.enabled", false);
```

Default: `true` ![Windows][Windows Logo] ![Debian][Debian Logo], `false` ![Android][Android Logo]. [[mozillaZine](http://kb.mozillazine.org/Themes#Lightweight_theme)]

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

## Extension Signing

```js
user_pref("xpinstall.signatures.required", false);
```
Default: `true` ![Windows][Windows Logo] ![Debian][Debian Logo] ![Android][Android Logo]

[[mozilla wiki](https://wiki.mozilla.org/Addons/Extension_Signing)]

## Firefox Chat

```js
user_pref("loop.enabled", false);
```

Default: `false` ![Debian][Debian Logo], n/a ![Windows][Windows Logo] ![Android][Android Logo]

Firefox Hello (code name Loop) is video and voice chat feature built into the browser.
[[mozilla wiki](https://wiki.mozilla.org/Loop)]

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
