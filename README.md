# toggle-fn-os-x

As a programmer I program in IDEs and surf the web on a daily basis. IDEs often uses the F1, F2, etc. keys to provide additional keyboard shortcuts, however those keys also function as multimedia keys and backlight controls which is handy while not programming. This has resulted me in frequently toggling the _Use all F1, F2, etc. keys as standard function keys_ checkbox in the keyboard preferences, which is extremely tedious. As a result I have created this to speed up the process.

_**tl;dr;**_ toggling fn keys through preferences is tedious, this app will do it for you

## Screenshot
![Screenshot](https://github.com/leoxiong/toggle-fn-os-x/blob/master/screenshot.png)

## Instructions
1. Open _AppleScript Editor_.
2. Past the following code.
```applescript
tell application "System Preferences"
	set current pane to pane "com.apple.preference.keyboard"
	tell application "System Events"
		tell process "System Preferences"
			click checkbox 1 of tab group 1 of window 1
			set state to get value of checkbox 1 of tab group 1 of window 1
		end tell
	end tell
end tell
quit application "System Preferences"
set state to item (((state is 0) as integer) + 1) of {"Fn modifier key disabled. F keys are standard function keys.", "Fn modifier key enabled. F keys are multimedia keys."}
display notification state with title "Toggle fn"
```
3. Save script with the name as _Toggle fn_ in the _Applications_ location as with _Application_ as the file format.
4. Go to the _Security & Privacy_ preferences, _Privacy_ tab, and select _Accessibility_ on the left. Then click the _+_ button and browse to _~/Applications/Toggle fn_. This allows the app to modify system preferences.
5. Launch app by searching _Toggle fn_ from Spotlight or using other means (eg. shortcut keys by creating a service).

## Todo
- Do not steal focus when launched!
