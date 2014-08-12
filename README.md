alfred-workflow-mockup
======================

Template webpage to demo your amazing workflows.

## summary
Through a very straightforward script (see json script in `script_example.js`), this framework allows you to demo how your workflows work thanks to an **Alfred mockup**, a simple **OSX notifications** system and a **key modifiers** display.

[> See demo here](http://sheraff.github.io/alfred-workflow-mockup/)

![Screen shot of mockup](screen_shot.gif)

## how to script
The script is a simple array of states, each described by a json string. All elements are optional and have a default state (either hidden of placeholders). Here’s a list of possible elements:
- `duration`: duration of the state in milliseconds.
```
// Example
"duration": 1000
```

- `keypress`: emits a *pressed key* display of the specified string (similar to the *volume up* or *volume down* notifications on OSX) at the beginning of the state. The display fades out in 1 second.
```
// Example
`"keypress": “⇥”`
```

- `notification`: emits an *osx notification* (similar to all the notifications you can see on the top right corner of your screen under OSX) at the beginning of the state. The notification enters, stills, and pans out in 4 seconds. Sub-elements are:
-- `title`: the main text of the notification
-- `sub`: the secondary text, written smaller and in grey.
```
// Example
"notification": {
	"title": "Le Coucou (1980)",
	"sub": "Download started..."
}
```

- `alfred`: describes the composition of the alfred mockup. Remove to hide Alfred. Sub-elements are:
-- `title`: the query typed in alfred
-- `icon`: main icon of the current workflow (this is similar to when alfred is called with a hotkey). Leave empty to default to Alfred’s icon.
-- `list`: an array of json strings to describe the results shown in alfred. Each element is composed of:
--- `title`: Main text of the result
--- `sub`: Secondary text of the result
--- `icon`: small icon for the result, leave empty to default to the main icon defined before.
--- `selected`: boolean to indicate the selected result. If no result is described as selected, the first result is selected.
```
// Example
"alfred": {
	"title": "coucou0",
	"icon": "imgs/icon.png",
	"list": [{
		"title": "Le Coucou (1980)",
		"sub": "Video (Movie), 800Mb, Seed: 10, Leech: 20",
		"icon": "imgs/icon.png",
		"selected": true
	}, {
		"title": "Vol au dessus d'un nid de coucou.French DVDRip [Sheraff]",
		"icon": "imgs/icon.png"
	}]
}
```
