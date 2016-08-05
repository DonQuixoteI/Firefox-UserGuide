# user.js

## Index

- [Browser Cache](#browser-cache)
- [Reports to Mozilla](#reports-to-mozilla)
  - [Crash Report](#crash-report)
  - [Health Report](#health-report)
  - [Telemetry](#telemetry)
    - [Experiments](#experiments)
- [Extension Signing](#extension-signing)
- [Firefox Chat](#firefox-chat)

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

[[mozilla](https://www.mozilla.org/en-US/privacy/firefox/#health-report)]: Firefox Health Report (FHR) is designed to provide you with insights about your browser's stability and performance and with support tips should you experience issues, such as high crash rates or slow startup times. Mozilla collects and aggregates your data with that of other Firefox users and sends it back to your browser so you can see how your Firefox performance changes over time. This data includes, for example: device hardware, operating system, Firefox version, add-ons (count and type), timing of browser events, rendering, session restores, length of session, how old a profile is, count of crashes, and count of pages.

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

If `true`: Telemetry is always enabled and recording base data; Telemetry will send additional `main` pings [[Mozilla Source Tree Docs][telemetry-preferencess]].

[telemetry-preferencess]: https://gecko.readthedocs.io/en/latest/toolkit/components/telemetry/telemetry/preferences.html#id1

```js
user_pref("toolkit.telemetry.enabled", false);
```

Default: `false` ![Windows][Windows Logo] ![Debian][Debian Logo] ![Android][Android Logo]

If `unified` is off, this controls whether the Telemetry module is enabled; if `unified` is on, this controls whether to record extended data [[Mozilla Source Tree Docs][telemetry-preferencess]].

```js
user_pref("toolkit.telemetry.server", "");
```

Default: "https://incoming.telemetry.mozilla.org" ![Windows][Windows Logo] ![Debian][Debian Logo] ![Android][Android Logo]

The server Telemetry pings are sent to [[Mozilla Source Tree Docs][telemetry-preferencess]].

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

[[MozillaWiki](https://wiki.mozilla.org/QA/Telemetry/AboutPreferences "QA/Telemetry/AboutPreferences")]

## Firefox Chat

```js
user_pref("loop.enabled", false);
```

Default: `false` ![Debian][Debian Logo], n/a ![Windows][Windows Logo] ![Android][Android Logo]

Firefox Hello (code name Loop) is video and voice chat feature built into the browser.

[[mozilla wiki](https://wiki.mozilla.org/Loop)]

## Extension Signing

```js
user_pref("xpinstall.signatures.required", false);
```
Default: `true` ![Windows][Windows Logo] ![Debian][Debian Logo] ![Android][Android Logo]

[MozillaWiki](https://wiki.mozilla.org/Addons/Extension_Signing)
