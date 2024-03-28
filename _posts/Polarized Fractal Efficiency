---
layout: post
title:  "Polarized Fractal Efficiency"
date:   2021-11-21 10:09:10 +0000
categories: jekyll update
---
In finance, the Polarised Fractal Efficiency (PFE) indicator was developed byHans Hannula. This measure is becoming increasingly popular and is beingadopted in many financial models.
I often use it for stock price predictions in my models along with otherindicators. I explain the theory and usage of PFE below and also present thePython code for calculating it. Before looking at it, it might be helpful tounderstand what are fractals.

What are Fractals?
Fractal geometry describes systems in which increasing detail is revealed byincreasing magnification, and the newly revealed structure looks similar to whatone can see at lower magnification. Concepts of this type were defined as purelymathematical entities long ago by Poincare, Hausdorff and others. However itwas Mandelbrot who realised that many familiar structures in nature could bedescribed with these methods.

(Note: I have included the link to a Ted Talk by Mandelbrot at the end, forthose who are interested.)
Fractals are mathematical patterns that are characterized by self-similarity. If afractal pattern is zoomed into, the exact same pattern appears. Few popularexamples are the Sierpinski Gasket and the Koch Snowflake.
Fractals are also unique in that Fractal Dimension is not a whole number. As anexample, the length of a Koch Curve is infinite while the area is zero. Hence, thedimension of the fractal is greater than one and less than two. Fractaldimensions can also be understood as a measure for space-filing capacity of apattern.

Let us now see an example on how to find the dimensions of a fractal: KochCurve. Before that, consider a non-fractal object as shown and examine thepattern. If we magnify the line by a factor of r=2; its measure (length) increasesto 2. If we do the same thing to a square and a cube, the measure increases by afactor of 4 and 8 respectively. 
Note that the relation 'N = rD "> D' holds, where N is the number of pieces (similar to r=1), r is the scalingfactor and D is the dimension.

Thus D=log(N)log(r)
“>D=log(N)log(r)
Now, let us try to apply similarly to Koch Curve:


Scaling it by a factor of r=3, we get:

There are N=4 pieces of the final object similar to the object or r=1 as shown.Hence, Dimension is log(4)log(3)=1.6
“>log(4)log(3)=1.6

What is Polarised Fractal Effi ciency?
The Polarized Fractal Efficiency indicator is, in the essence, an exponentiallysmoothed ratio of the length of
two lines:
A straight line between today’s close and the close period days ago, and
A broken line connecting all Close points between today and period days ago.
The PFE generally indicates how trendy or overloaded a market is. In case thePFE reading is below zero, this suggests there is a bear trend. In case the PFEreading is above zero, this suggests there is a bull trend. The higher the value,the more efficient, ”trendier” the movement to the upside is. If the PFE readingis in proximity to zero, this means that market movement is choppy and lessefficient.
Usually a trader will enter at maximum efficiency, a level where the PFEappears to have reached a maximum in one direction or the other. The traderneeds to keep his/her position active all the way to the other extreme level.
However, as ever there are exceptions. When the PFE slows down at levels closeto zero – he/she should exit the trade and wait for another entry at ”maximumefficiency” level.
Stocks that have a PFE value greater than zero are deemed to be trending up,while a reading of less than zero indicates the trend is down. The strengh of thetrend is measured by the position of the PFE relative to the zero line.
As a general rule, the further the PFE value is away from zero, the stronger andmore efficient the given trend is. A PFE value that fluctuates around the zero

line could indicate that the supply and demand for the stock are in balance andprice may trade sideways.
A simple way to read this indicator is that if it is >50 (<-50) then the market islikely to reverse its trend from positive to negative (from negative to positive).
Here’s the Python code the I use to calculate PFE for a stock.



{% highlight ruby %}
#!/usr/bin/env python3
# -*- coding: utf-8 -*-
# Created on Sun May 3 14:02:35 2020
# @author: vikaslambadef calc_pfe():
# The below code is a snippet from one of my existing strategies and you might want to 
# edit and add to suit your needs.
# The purpose here is to explain how to derive pfe value.
# # ============================================ Snippet ============================================
# ................... 
pfe_length = 10 
pfe_period = pfe_length - 1 
pfe_values = [] 
for k in range(0, 9): 
    pfe_values.append(0) 
for i in range(9, len(df)): 
    diff = df['Close'][i] - df['Close'][i-pfe_period] # This line can be removed if diff is pfe1 = 100 * math.sqrt(pow(diff,2) + pow(pfe_period,2)) 
    # replaced with its value here pfe2 = 0 
    for j in range(0, pfe_period-1): 
        pfe2 += math.sqrt(1 + pow(df['Close'][i-j] - df['Close'][i-j-1],2)) 
    pfe = pfe1 / pfe2 
    if diff < 0: 
        pfe = -pfe 
    pfe_values.append(pfe) 
    df['PFE'] = pfe_values 
    df['PFE'] = df['PFE'].ewm(span=5, adjust=False).mean()
    # ...................
{% endhighlight %}

Mandelbrot was a French and American mathematician who referred to himselfas the “fractalist”. He coined the word “Fractal” and is recognized for hiscontribution to fractal geometry.

Below is a TED talk by Benoit Mandelbrot on ”Fractals and the Art ofRoughness”.

References:
1. [TED talk by Benoit Mandelbrot][TED-talk-by-Benoit-Mandelbrot] 


[TED-talk-by-Benoit-Mandelbrot]: https://www.ted.com/talks/benoit_mandelbrot_fractals_and_the_art_of_roughness?language=en
