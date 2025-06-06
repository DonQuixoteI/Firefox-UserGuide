# Policies

- [How to Apply Policies](#how-to-apply-policies)
- [Favorite Policies](#favorite-policies)
  - [DisableAppUpdate](#disableappupdate)
  - [DisableBuiltinPDFViewer](#disablebuiltinpdfviewer)
  - [DisableDefaultBrowserAgent](#disabledefaultbrowseragent)
  - [DisableFeedbackCommands](#disablefeedbackcommands)
  - [DisableFirefoxAccounts](#disablefirefoxaccounts)
  - [DisableFirefoxStudies](#disablefirefoxstudies)
  - [DisablePocket](#disablepocket)
  - [DisableSystemAddonUpdate](#disablesystemaddonupdate)
  - [DisableTelemetry](#disabletelemetry)
  - [DNSOverHTTPS](#dnsoverhttps)
  - [DontCheckDefaultBrowser](#dontcheckdefaultbrowser)
  - [ExtensionUpdate](#extensionupdate)
- [View Policies](#view-policies)
- [References](#references)


## How to Apply Policies

In Debian, create or edit `/usr/share/firefox/distribution/policies.json`. [Here](../policies.json) is an example.

## Favorite Policies

### DisableAppUpdate

`true`:
Turn off application updates.

Preferences Affected:
n/a

### DisableBuiltinPDFViewer

`true`:
Disable built in PDF viewer. PDF files are downloaded and sent externally.

Preferences Affected:
`pdfjs.disabled`

### DisableDefaultBrowserAgent

`true`:
Prevent the default browser agent from taking any actions (Windows only, FF75+, FF68.7esr+).

Preferences Affected:
n/a

[How to Disable Firefox Default Browser Agent in Firefox 75 - winaero.com](https://winaero.com/blog/how-to-disable-firefox-default-browser-agent-in-firefox-75/)

### DisableFeedbackCommands

`true`:
Disable menus for reporting sites (Submit Feedback, Report Deceptive Site).

Preferences Affected:
n/a

### DisableFirefoxAccounts

`true`:
Disable Firefox Accounts integration (Sync).

Preferences Affected:
`identity.fxaccounts.enabled`

### DisableFirefoxStudies

`true`:
Disable Firefox studies (Shield).

Preferences Affected:
n/a

### DisablePocket

`true`:
Remove Pocket in the Firefox UI. It does not remove it from the new tab page.

Preferences Affected:
`extensions.pocket.enabled`

### DisableSystemAddonUpdate

`true`:
Prevent system add-ons from being installed or update.

Preferences Affected:
n/a

### DisableTelemetry

`true`:
Prevent upload of telemetry data.

Preferences Affected:
`datareporting.healthreport.uploadEnabled`,
`datareporting.policy.dataSubmissionEnabled`

### DNSOverHTTPS

`Enabled`: `false`,
`Locked`: `true`
-- do not use DNS over HTTPS and prevent changing DNS over HTTPS preferences.

Preferences Affected: `network.trr.mode`, `network.trr.uri`

[Mozilla is becoming evil - be careful with Firefox - unixsheikh.com](https://unixsheikh.com/articles/mozilla-is-becoming-evil-be-careful-with-firefox.html)

### DontCheckDefaultBrowser

`true`:
Don't check if Firefox is the default browser at startup.

Preferences Affected:
`browser.shell.checkDefaultBrowser`

### ExtensionUpdate

`false`: Disable automatic extension updates.

Preferences Affected:
`extensions.update.enabled`

## GPO and policies.json

GPO always overrides settings in `policies.json`. GPO applies settings to all Firefox installations. `policies.json` applies settings to a specific Firefox installation.

## View Policies

If policies were applied you will see at the top of Firefox Preferencies the information link "_Your browser is being managed by your organization_", just click on the link. Or, type `about:policies` in the address bar.

## References

[GitHub - mozilla/policy-templates: Policy Templates for Firefox](https://github.com/mozilla/policy-templates)

