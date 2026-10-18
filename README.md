# Shield Size Planner

A one-page web app for planning LARP shields. Pick a shape and a size class, adjust the dimensions, and see the outline redraw on a 1-inch grid. When you're happy with it, print a full-size pattern to trace onto foam.

**Use it here:** https://rmwphd.github.io/shield-planner/

## What it does

- Sizes seven shapes: heater, kite, teardrop, round, oval, coffin, and rectangle.
- Targets a size class. Pick Max Small, Max Medium, Max Large, or a custom area. The dimension marked **Auto** is solved for you.
- Rounds solved dimensions down to the nearest 1/16 inch, so cutting to the number keeps you at or under the limit.
- Lets you aim a little under the max with an optional safety margin (0.5% to 5%).
- Handles edge padding. Enter your padding thickness to see the core cut line and the finished edge together.
- Checks a finished shield. Enter its dimensions and it tells you which class it falls in.
- Prints a full-size pattern, tiled across US Letter or A4 paper.
- Works on phones, needs no account, and sends no data anywhere.

## Size classes

Face area is the area of the shield's largest flat projection. Width, height, and area are all measured on the finished shield, including edge padding.

| Class  | Face area |
|--------|-----------|
| Small  | 36 in² to 3 ft² (432 in²) |
| Medium | over 3 ft² to 5 ft² (720 in²) |
| Large  | over 5 ft² to 8 ft² (1152 in²) |

If your group uses different limits, change the `LIM` values near the top of the script in `index.html`.

## Shapes

Every shape has width and height. Some have one to three extra sliders.

| Shape | Extra controls |
|-------|----------------|
| Heater | Straight sides (share of height before the curve to the point) |
| Kite | Top curve depth (where the rounded top meets the straight sides) |
| Teardrop | None. The sides are straight and tangent to a round top. |
| Round | Diameter only |
| Oval | None |
| Coffin | Shoulder position, top edge width, bottom edge width |
| Rectangle | Corner radius |

Some limits keep every shape buildable:

- No shield can be more than 11 times as tall as it is wide, or the reverse.
- A heater must be at least half as tall as it is wide, so it keeps a clean point.
- A teardrop must be at least 5% taller than it is wide.

## Printing a pattern

1. Set your shape, size, and edge padding.
2. Under **Full-size pattern**, choose your paper size and which lines to print.
3. Tap **Print full-size pattern**.
4. In the print dialog, set the scale to **100%** or **Actual size**, and turn **Fit to page** off.
5. Measure the 2-inch square on the cover sheet before you cut anything. If it isn't exactly 2 inches, your printer is scaling the page.
6. Lay the pages out by the page map on the cover sheet. Each page overlaps its neighbors by 1/2 inch along the gray bands. Line up the grid and tape.

Printing works on the hosted page and from the file opened in any browser. It does not work inside the Claude preview.

## Host your own copy

The whole app is one file, `index.html`. It has no build step and no dependencies to install.

**Using GitHub, no terminal needed:**

1. Click **Fork** at the top of this page.
2. In your fork, go to **Settings → Pages**.
3. Under "Build and deployment," choose **Deploy from a branch**, then `main` and `/ (root)`. Click **Save**.
4. After a minute or two, your copy is live at `https://YOUR-USERNAME.github.io/shield-planner/`.

**Without GitHub:** download `index.html` and drag it onto [Netlify Drop](https://app.netlify.com/drop), or open it directly in a browser.

## How the math works

Each shape is drawn as a fine-grained outline, and its area is computed from that outline. Results match the exact formula for each shape to within 0.02%, and any error reads slightly low. The Auto dimension is found by searching for the value that hits the target, then rounded down to 1/16 inch. The padded core is an exact inward offset of the finished outline.

## Credits

Built by Reed with help from Claude.
