-   [ggthemr](#ggthemr)
    -   [Installation](#installation)
    -   [Usage](#usage)
    -   [Further Development](#further-development)
    -   [Palettes](#palettes)
        -   [flat](#flat)
        -   [flat dark](#flat-dark)
        -   [camoflauge](#camoflauge)
        -   [chalk](#chalk)
        -   [copper](#copper)
        -   [dust](#dust)
        -   [earth](#earth)
        -   [fresh](#fresh)
        -   [grape](#grape)
        -   [grass](#grass)
        -   [greyscale](#greyscale)
        -   [light](#light)
        -   [lilac](#lilac)
        -   [pale](#pale)
        -   [sea](#sea)
        -   [sky](#sky)
        -   [solarized](#solarized)
    -   [Custom Palettes](#custom-palettes)
    -   [Layouts](#layouts)
        -   [Clean](#clean)
        -   [Clear (default)](#clear-default)
        -   [Minimal](#minimal)
        -   [Plain](#plain)
        -   [Scientific](#scientific)
    -   [Spacing](#spacing)
    -   [Type](#type)
    -   [Tweaking Themes](#tweaking-themes)
    -   [Plot Adjustments](#plot-adjustments)

<!-- README.md is generated from README.Rmd. Please edit that file -->
ggthemr
=======

Themes for ggplot2. The idea of this package is that you can just set the theme and then forget about it. You shouldn't have to change any of your existing code. There are several parts to a theme:

-   Colour palette for the background, axes, gridlines, text etc.
-   Layout of axes lines and gridlines.
-   Spacing around plot and between elements (i.e. axes titles to axes lines etc). You can set the spacing to determine how compact or spread out a plot is.
-   Text size.

There are a number of preset palettes and layouts, and methods to create your own colour schemes.

Installation
------------

This package is still under development and isn't too stable yet, but can be installed using [devtools](http://cran.r-project.org/web/packages/devtools/index.html).

``` r
devtools::install_github('cttobin/ggthemr')
```

Usage
-----

To just set the colour scheme:

``` r
ggthemr('dust')
```

That's it. Any ggplot you create from then on will have the theme applied. You can clear the theme and return to ggplot2's default using:

``` r
ggthemr_reset()
```

Further Development
-------------------

Features on the way:

-   More palettes and layouts.
-   Options to control fonts.
-   Ability to reset themes back to default.
-   Theme modifiers (so you can do things like `plot + no_legend()`, `plot + no_axes()` etc.).

Palettes
--------

The palette determines the colours of everything in a plot including the background, layers, gridlines, title text, axes lines, axes text and axes titles. The *swatch* is the the name given to the set of colours strictly used in styling the geoms/layer elements (e.g. the points in `geom_point()`, bars in `geom_bar()` etc.). At least six colours have been supplied in each palette's swatch.

There are a wide variety of themes in this package (and more on the way). Some of them serious business... others are delibrately stylish and might not be that good for use in proper publications.

### flat

[Base 16](https://github.com/chriskempson/base16)

![](README_files/figure-markdown_github/unnamed-chunk-5-1.png)

### flat dark

[Base 16](https://github.com/chriskempson/base16)

![](README_files/figure-markdown_github/unnamed-chunk-6-1.png)

### camoflauge

![](README_files/figure-markdown_github/unnamed-chunk-7-1.png)

### chalk

![](README_files/figure-markdown_github/unnamed-chunk-8-1.png)

### copper

![](README_files/figure-markdown_github/unnamed-chunk-9-1.png)

### dust

![](README_files/figure-markdown_github/unnamed-chunk-10-1.png)

### earth

![](README_files/figure-markdown_github/unnamed-chunk-11-1.png)

### fresh

![](README_files/figure-markdown_github/unnamed-chunk-12-1.png)

### grape

![](README_files/figure-markdown_github/unnamed-chunk-13-1.png)

### grass

![](README_files/figure-markdown_github/unnamed-chunk-14-1.png)

### greyscale

![](README_files/figure-markdown_github/unnamed-chunk-15-1.png)

### light

![](README_files/figure-markdown_github/unnamed-chunk-16-1.png)

### lilac

![](README_files/figure-markdown_github/unnamed-chunk-17-1.png)

### pale

![](README_files/figure-markdown_github/unnamed-chunk-18-1.png)

### sea

![](README_files/figure-markdown_github/unnamed-chunk-19-1.png)

### sky

![](README_files/figure-markdown_github/unnamed-chunk-20-1.png)

### solarized

![](README_files/figure-markdown_github/unnamed-chunk-21-1.png)

Custom Palettes
---------------

`define_palette()` lets you make your own themes that can be passed to `ggthemr()` just like any of the palettes above. Here's an example of a (probably ugly) palette using random colours:

``` r
# Random colours that aren't white.
set.seed(12345)
random_colours <- sample(colors()[-c(1, 253, 361)], 10L)

ugly <- define_palette(
  swatch = random_colours,
  gradient = c(lower = random_colours[1L], upper = random_colours[2L])
)

ggthemr(ugly)

example_plot + ggtitle(':(')
```

![](README_files/figure-markdown_github/unnamed-chunk-22-1.png)

You can define all elements of a palette using `define_palette()` including colours for the background, text, axes lines, swatch and gradients.

Layouts
-------

The layout of a theme controls the appearance and position of the axes, gridlines and text. Some folk prefer both major and minor gridlines, others prefer none or something in between.

### Clean

![](README_files/figure-markdown_github/unnamed-chunk-23-1.png)

### Clear (default)

![](README_files/figure-markdown_github/unnamed-chunk-24-1.png)

### Minimal

![](README_files/figure-markdown_github/unnamed-chunk-25-1.png)

### Plain

![](README_files/figure-markdown_github/unnamed-chunk-26-1.png)

### Scientific

![](README_files/figure-markdown_github/unnamed-chunk-27-1.png)

Spacing
-------

Plot margins and space between axes titles and lines etc. is controlled with the *spacing* parameter. Lower values will make plots more compact, higher values will give them more padding. Compare the plots below where the spacing has been set to 0, 1 and 2 respectively.

![](README_files/figure-markdown_github/unnamed-chunk-28-1.png)

![](README_files/figure-markdown_github/unnamed-chunk-29-1.png)

![](README_files/figure-markdown_github/unnamed-chunk-30-1.png)

Type
----

The *type* parameter can be set to either *inner* or *outer*. When *inner*, the background colour of a plot will not extend past the plot area. *outer* will colour the entire plot and background.

``` r
ggthemr('earth', type = 'inner')
example_plot
```

![](README_files/figure-markdown_github/unnamed-chunk-31-1.png)

``` r
ggthemr('earth', type = 'outer')
example_plot
```

![](README_files/figure-markdown_github/unnamed-chunk-32-1.png)

Tweaking Themes
---------------

Squinting at a chart? Low on printer ink? ggthemr includes some methods to tweak charts to make them lighter or darker. Here's a standard theme:

``` r
ggthemr('dust')
example_plot
```

![](README_files/figure-markdown_github/unnamed-chunk-33-1.png)

Maybe that plot comes out a bit pale looking when you print it. Here's how you can add a bit more contrast to the swatch:

``` r
darken_swatch(amount = 0.3)
example_plot
```

![](README_files/figure-markdown_github/unnamed-chunk-34-1.png)

The second parameter to `darken_swatch()` controls the degree to which the colours are made darker. Full list of methods with similar functionality:

-   `darken_swatch()` / `lighten_swatch()`: darker/lighter swatch colours.
-   `darken_gradient()` / `lighten_gradient()`: darker/lighter gradient colours.
-   `darken_palette()` / `lighten_palette()`: darker/lighter everything.

I'll add methods to darken/lighten the axes lines and text soon too.

Plot Adjustments
----------------

Most of the time you'll probably just want to set the theme and not worry about it. There may be times though where you'll want to make some small adjustment, or manually change what items appear as what colour in a plot.

``` r
ggthemr('dust')
mpg_plot <- ggplot(mpg[mpg$drv != '4', ], aes(factor(cyl), cty, fill = drv)) + 
  geom_boxplot() + labs(x = 'Cylinders', y = 'City MPG', fill = 'Drive Type') +
  theme(legend.position = 'bottom')
mpg_plot
```

![](README_files/figure-markdown_github/unnamed-chunk-35-1.png)

For some reason you decide you want to change those colours. Front-wheel drive vehicles should be orange. Rear-wheelers should be that red colour. You could change the order of the levels of your fill variable, but you shouldn't have to do that. You just want to switch those colours but you have no idea what they are. `swatch()` will give you the colours in the currently active ggthemr palette.

``` r
swatch()
```

    ## [1] "#555555" "#db735c" "#EFA86E" "#9A8A76" "#F3C57B" "#7A6752" "#2A91A2"
    ## [8] "#87F28A" "#6EDCEF"
    ## attr(,"class")
    ## [1] "ggthemr_swatch"

So you can manually swap the two colours around.

``` r
to_swap <- swatch()[2:3]
mpg_plot + scale_fill_manual(values = rev(to_swap))
```

![](README_files/figure-markdown_github/unnamed-chunk-37-1.png)

**Note:** the first colour in a swatch is a special one. It is reserved for outlining boxplots, text etc. So that's why the second and third colours were swapped.
