
### `scaleFont()`
Scales font "up" as browser gets wider with a maximum set font-size and scales font "down" as browser gets thinner with a minimum set font-size.

```
	@include scale(context, base-size, limit-size-min, limit-size-max, property, width);
```

```
	.selector-name { // apply to any selector

		@include scale(62.5rem, 4rem, 1.875rem, 6.25rem, font-size, true);

		// 4 required arguments*:
		// 62.5rem: context
		// 4rem: base-size
		// 1.875rem: limit-size-min
		// 6.25rem: limit-size-max
		// *All values need to be the same unit type
		// 2 optional arguments:
		// font-size: property (can be any CSS property that uses unit values; `font-size` is default)
		// true: width (if `false`, scales based on viewport height; if `true`, scales based on viewport width; `true` is default)

	}
```


### `scaleUp()`
Scales font "up" as browser gets wider with a maximum set font-size or any CSS property.

````
	@include scaleUp(context-width, base-size, limit-size-max, property, width);
````

````
	.selector-name { // apply to any selector

		@include scaleUp(62.5rem, 4rem, 6.25rem, font-size, true);

		// 3 required arguments*:
		// 62.5rem: context-width
		// 4rem: base-font-size
		// 6.25rem: limit-font-size-max
		// *All values need to be the same unit type
		// 2 optional arguments:
		// font-size: property (can be any CSS property that uses unit values; `font-size` is default)
		// true: width (if `false`, scales based on viewport height; if `true`, scales based on viewport width; `true` is default)

	}
````


### `scaleDown()`
Scales font "down" as browser gets thinner with a minimum set font-size or any CSS property.

````
	@include scaleDown(context, base-size, limit-size-min, property, width);
````

````
	.selector-name { // apply to any selector

		@include scaleFontDown(62.5rem, 4rem,  1.875rem, font-size, true);

		// 3 required arguments*:
		// 62.5rem: context-width
		// 4rem: base-font-size
		// 1.875rem: limit-font-size-min
		// *All values need to be the same unit type
		// 2 optional arguments:
		// font-size: property (can be any CSS property that uses unit values; `font-size` is default)
		// true: width (if `false`, scales based on viewport height; if `true`, scales based on viewport width; `true` is default)
		
	}
````
