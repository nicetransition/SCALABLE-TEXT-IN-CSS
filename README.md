# Scalable Text in CSS with Maximum and Minimum Sizes
Scale font-size property based on viewport width using only CSS. The following CSS units will work: em, rem, px, ch, cm, mm, in, pt, pc.

## MIXINS
Mixins have up to four values that need to be passed:

* `context-width`: The identified width that is used as the scaling point.
* `base-font-size`: The base font-size. When the viewport is equal to context-width's width, the calculated font-size will be equal to base-font-size. base-font-size has to be a smaller value than limit-font-size-max and has to be a larger value than limit-font-size-min.
* `limit-font-size-min`: The minimal size that is intended for font-size. The scaling effect will not allow the font to be smaller than the limit-font-size-min. limit-font-size-min has to be a smaller value than base-font-size.
* `limit-font-size-max`: The maximum size that is intended for font-size. The scaling effect will not allow the font to be larger than the limit-font-size-max. limit-font-size-max has to be a larger value than base-font-size.


### `scaleFont()`
Scales font "up" as browser gets wider with a maximum set font-size and scales font "down" as browser gets thinner with a minimum set font-size.

```
	@include scaleFont(context-width, base-font-size, limit-font-size-min, limit-font-size-max);
```

```
	.selector-name { // apply to any selector

		@include scaleFont(62.5rem, 4rem, 1.875rem, 6.25rem);
		// 4 required arguments:
		// 62.5rem: context-width
		// 4rem: base-font-size
		// 1.875rem: limit-font-size-min
		// 6.25rem: limit-font-size-max
	}
```


### `scaleFontUp()`
Scales font "up" as browser gets wider with a maximum set font-size.
````
	@include scaleFontUp(context-width, base-font-size, limit-font-size-max);
	
````
````
	.selector-name { // apply to any selector

		@include scaleFontUp(62.5rem, 4rem, 6.25rem);
		// 3 required arguments:
		// 62.5rem: context-width
		// 4rem: base-font-size
		// 6.25rem: limit-font-size-max
	}
````


### `scaleFontDown()`
Scales font "down" as browser gets thinner with a minimum set font-size.
````
	@include scaleFontDown(context-width, base-font-size, limit-font-size-min);
````

````
.selector-name { // apply to any selector

	@include scaleFontDown(62.5rem, 4rem,  1.875rem);
	// 3 required arguments:
	// 62.5rem: context-width
	// 4rem: base-font-size
	// 1.875rem: limit-font-size-min
}
````