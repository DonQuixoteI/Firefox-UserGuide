# Profiles

## New Instance of Firefox with another Profile

To use Firefox with two different profiles ("Profile1" and "Profile2") isolated from each other at the same time:

`firefox -P "Profile1" -no-remote`

`firefox -P "Profile2" -no-remote`

[mozillaZine](http://kb.mozillazine.org/Opening_a_new_instance_of_Firefox_with_another_profile)

## Safe Mode

Safe Mode temporarily turns off hardware acceleration, resets some settings, and disables add-ons (extensions and themes)
[[Mozilla Support](https://support.mozilla.org/en-US/kb/troubleshoot-firefox-issues-using-safe-mode)].

`firefox -P "Profile1" -no-remote -safe-mode`
