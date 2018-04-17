# Linez

Linez is CLI data visualizer.

## Quick usage example

Write your own script, that generates some raw data. You can go to linez-examples (link) repo to get usage examples.

After, send output of your script to linez, like this:
```bash
$ ./yourscript.sh | linez OPTIONS
```

Output will be similar to this:

![Imgur](http://i.imgur.com/fFz5iXD.png)

or this:

![Imgur](http://i.imgur.com/Mb2e6Wx.png)

## Example scripts

You can get example script, here: linez-examples (link).

## Options

`--linecount` - sets lines count that must be displayed at frame, default 1

`--maxlength` - sets maximum line length, default 40

`--linewidth` - sets line width, default 1

`--sepwidth` - sets separator width, default 1, can be zero

`--mode` - sets drawing mode (v for vertical and h for horizontal)

`--scale` - by default, linez accepts values from 0.0 to 1.0, but with scale you can set maximal value, more that 1.0, as example 80 for cpu temperature

`--cut` - with cut you can set minimal value, more than 0, as example 30 for cpu temperature

`--smoothness C` - lesser values is more smooth updating, from 0.0 to 1.0, default 0.5

`--print` - print (original unscaled, uncutted) values for each line before drawing line

`--header` - show header with given text (horizontal mode only)

`--auto-linelength` - setting line length depend on terminal size and update it if terminal size changes

`--auto-scale-cut` - setting scale and cut automaticaly, depend on input

`--noupdate-colors` - disabling colors scaling for auto-scale-cut option, enable this if you think, that colorizing is wrong

`--auto-linewidth` - setting linewidth automaticaly (and update it), depend on terminal size

`--colors` - colors for line, that can be one color (red, green, blue, etc.) or dictionary (green:0.33,yellow:0.66,red)

`--colormode` - colorize line by `sections` (default) or `full`

## Colors

### Single color

Just use `--colors COLOR` and put something like `green`, `red` or `blue` instead of `COLOR`.

### Multiple colors

For multiple colors, use dictionary like this `--colors COLOR1:BOUND1,COLOR2:BOUND2,COLOR3`, as example `--colors green:0.1,yellow:0.5,red`. Note, that spaces isn't allowed here.

This is mean:
* Use `green` color for values < 0.1
* Use `yellow` color for values < 0.5 (but > 0.1)
* Use `red` color for all other values (> 0.5)

For example to colorize cpu temperature output by scheme 40 < 55 < 70 to green, yellow and red colors, use `--colors green:40,yellow:55,red:70`.
