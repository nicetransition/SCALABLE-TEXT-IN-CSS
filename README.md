# Scalable Text in CSS with Maximum and Minimum Sizes
Scale font-size property based on viewport width using only CSS. The following CSS units will work: em, rem, px, ch, cm, mm, in, pt, pc.

* > [Demo on CodePen](http://codepen.io/kevinmack18/pen/OyRwKq?editors=110)


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


## Examples

### Scale Up & Down
**Sass**:
````
.u-scalable-1 {
	@include scaleFont(77.5rem, 4rem, 1.875rem, 6.250rem);
}
````
**Compiled CSS**:
````
@media screen and (max-width: 77.5rem) and (max-width: 36.32813rem) {
  .u-scalable-1 {
    font-size: 1.875rem;
  }
}

@media screen and (min-width: 77.5rem) and (min-width: 36.32813rem), screen and (max-width: 77.5rem) and (min-width: 36.32813rem) {
  .u-scalable-1 {
    font-size: 5.16129vw;
  }
}
@media screen and (min-width: 77.5rem) and (min-width: 121.09375rem) {
  .u-scalable-1 {
    font-size: 6.25rem;
  }
}
````

### Scale Up
**Sass**:
````
.u-scalable-2 {
	@include scaleFontUp(77.5rem, 3rem, 3.75rem);
}
````
**Compiled CSS**:
````
@media screen and (max-width: 77.5rem) {
  .u-scalable-2 {
    font-size: 3rem;
  }
}
@media screen and (min-width: 77.5rem) and (max-width: 96.875rem) {
  .u-scalable-2 {
    font-size: 3.87097vw;
  }
}
@media screen and (min-width: 77.5rem) and (min-width: 96.875rem) {
  .u-scalable-2 {
    font-size: 3.75rem;
  }
}
````

### Scale Down
**Sass**:
````
.u-scalable-3 {
	@include scaleFontDown(77.5rem, 3rem, 1.125rem);
}
````
**Compiled CSS**:
````
@media screen and (min-width: 77.5rem) {
  .u-scalable-3 {
    font-size: 3rem;
  }
}
@media screen and (max-width: 77.5rem) and (min-width: 29.0625rem) {
  .u-scalable-3 {
    font-size: 3.87097vw;
  }
}
@media screen and (max-width: 77.5rem) and (max-width: 29.0625rem) {
  .u-scalable-3 {
    font-size: 1.125rem;
  }
}
````