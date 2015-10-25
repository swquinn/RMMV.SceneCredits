rmmv-scenecredits
=================

> **NOTE:** This plugin is a work-in-progress and the plugin as well as the
> documentation is likely to change dramatically over the next few weeks.

This plugin is intended to be a flexible plugin for interpreting how to display
credits, ultimately targeting any number of credit sequences.

## Proposed Credits Group Structure

```
{
  "id":1,
  "x": 0,
  "y": 0,
  "align": "left" | "center" | "right",
  "width": null | <number> | <expr>,
  "transition", "fade",
  "speed": 500,
  "duration": 500,
  "items": [
    { "type": "label", "text": "Director", "offsetX": 10, "offsetY": 10, "fontSize": 28 },
    { "type": "label", "text": "Sean Quinn", "offsetX": 150, "offsetY": 12, "fontSize": 20 }
  ]
}
```

The credits data, at present, exists in a monolithic `Credits.json` data file under `MyProject/data`

* ___id___ -- The primary-key identifier of the credit entry.
* ___align___ (values: `left`, `center`, `right`) -- How the credit block should be aligned, the alignment will affect the horizontal (`x`) and vertical (`y`) positioning of a credit block's components. **Default value:** `left`.
* ___width___ (values: `null`, `<number>`, `<expr>`) -- How wide the credit block is, supports expressions, e.g. `"Graphics.Width / 2"`. **Default value:** `null`.
* ___x___ -- The horizontal positioning of the credit block. **Default value:** 0.
* ___y___ -- The vertical positioning of the credit block. **Default value:** 0.
* ___transition___ (values: `null`, `fade`) -- The transition used to render the credit block.
* ___speed___ (values: `<number>`) -- How quickly the credit block transitions in (and out).
* ___duration___ (values: `<number>`) -- The length of time that the credit block is displayed for, before being removed. Credit blocks are displayed synchronously.
* ___items___ -- The individual items within the credit block (see _Credit Items_ below for more details).

### Credit Items

There are three credit item types:

* ___Images.___ These credit item types render an image on to the scene.
* ___Labels.___ These credit item types render text on to the scene.
* ___Events.___ These credit item types invoke an event.
