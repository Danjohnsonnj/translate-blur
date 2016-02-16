# translate-blur
There has historically been an issue in which text vertically or center aligned via

`position: absolute; left: 50%; transform: translateX(-50%);`, `position: absolute; top: 50%; transform: translateY(-50%);`, or `position: absolute; left: 50%; top: 50%; transform: translate(-50%, -50%);`

resulted in text that was rendered blurry on devices with a pixel ratio of 1. This would be seen when the positioning context containing element is an odd pixel value in the width and/or height (depending on vertical or horizontal centering), resulting in a fractional pixel value for the positioned element's top or left (again, depending on the axis for centering).

This is an exploration to confirm the various improvements in recent browser versions.

It seems that this behavior has been improved in recent browser releases. Specifically I am seeing the following on a Macbook running OS X 10.10.5:

* _Chrome 48.0.2564.103_
    The text seems to only move on whole pixels, producing a "bouncing" effect, particularly noticeable on the headline when   changing the window height.
    >The "button" vertical edges remain sharp on resize, but the horizontal edges will alternate between crisp and blurred on the window height resize, exhibiting the issue as it was observed in the past.

* _Safari 9.0.3 (10601.4.4)_
  The text seems to behave as in the Chrome description above.
  The "button" edges all remain sharp regardless of window dimensions.

* _Firefox 43.0.4_
  The text seems to behave as in the Chrome description above.
  The "button" edges behave like Safari above.
