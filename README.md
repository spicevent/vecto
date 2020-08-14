# Vecto

A small but efficient tool to generate custom SVG, WEBP, PNG and JPG from SVG source files (useful for logos, icons, …)

This tool uses Vue.js (version 2) from [unpkg.com](https://unpkg.com/vue).

[Demo here](https://intranet.spicevent.com/services/vecto/)

## Installation

Just clone this repository in a folder :)

You will get some example SVG and color palettes when cloning the app. Let's see how to customize it in the next chapter.

## Configuration

First, put all your SVG files into `svg` folder.

The configuration of the application is located in `vecto.json`. Let's look at what's inside this example:

```
{
	"palettes": [
		{
			"name": "Social",
			"width": 5,
			"colors": [
				{"code": "#3b5998", "name": "Facebook"},
				{"code": "#1da1f2", "name": "Twitter"},
				{"code": "#e1306c", "name": "Instagram"},
				{"code": "#ff0000", "name": "YouTube"},
				{"code": "#6441a5", "name": "Twitch"}
			]
		}
	],
	"svg": [
		"logo",
		"logo_colour",
		"logo_text"
	]
}
```

### Properties

* `palettes`: allows you to configure some color palettes, so you can easily use color presets you frequently use. This variable is an array of objects. Where you can set these variables:
	* `name`: the name of the palette
	* `width`: how many colors you want to display on a row. This parameter is useful to display beautiful palettes grouped by colors tint or contrast for example
	* `colors`: array of color presets. You can set these variables:
		* `code`: the code of the color. Use any CSS format (#rrggbb, rgba(), hsv(), …)
		* `name`: the name of the color preset
* `svg`: an array of filenames without the `.svg` suffix. It must matches the files inside the `svg` folder

## How to use the dynamic color generation?

SVG files may be standard SVG files, but **Vecto** allows you to use custom properties, so you can dynamically choose the color of your SVG before generate it as image files.

On any SVG element, use the CSS custom property notation with a default value:
```
<svg>
	<!-- … -->
	<path fill="var(--foo, #000000)">
		<!-- … -->
	</path>
	<!-- … -->
</svg>
```

**Vecto** will parse the SVG and look for some `var()` declarations. Then, the application will list all the variables and let you choose the color by yourself.
