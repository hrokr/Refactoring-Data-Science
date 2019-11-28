# uber-DRY

If you haven't heard of it before, let me introduce you to the concept of DRY - Don't Repeat Yourself. What does that mean?

Part of that that means putting everything repeatable into a function but really that seems obvious, doesn't it? Take it a step further and you have classes? Still, so what?

My argument is that you want to plan ahead if at all possible. More than likely though what happens is that you write something, perhaps more than once. Then think, "I'm probably going to use this again so let me make it into a function." Good call.

But if you want to get to uber-DRY you have to do two things:

1) Keep a collection of truly useful snippets for use across projects

2) Abstract those snippets as much as possible

Let's drill down on these two points a bit. Let's say I received a location that came as a Latitude/Longitude pair in degrees, minutes seconds. I need to convert the pair to decimal degrees so it can be plotted. If it's one set of coordinates once, there are several options. I could do it by hand, use an online calculator, hard code the results, and so on. But, let's say there are several set of coordinates with the possibility that I will have more. Lots more. And for all of which I have to from this:

```1°02'42"N \n103°39'00"E```

to this:

```1.045 	103.650000```

In my case I occasionally need to do this in pandas so it doesn't really make sense to use one function that makes columns, splits the coordinate pair, and applies the function to each as needed. But I does make sense to have a function converting from degrees, minutes and seconds to decimal degrees and later use pandas to apply the function as needed. That way I can keep this function in the event I need it for something else. 

```python
def dms2dd(s):
    """
    PURPOSE: Converts Lat/Long to Decimal Degrees
    REQUIREMENTS: Python re module
    PARAMATERS: 
    RETURNS: Decimal Degree for Lat or Long
    """
    degrees, minutes, seconds, direction = re.split('[°\'"]+', s)
    dd = float(degrees) + float(minutes)/60 + float(seconds)/(60*60);
    if direction in ('S','W'):
        dd*= -1
    return dd
```

But let's say later I figure out that I was wrong and that I only make such conversions in pandas. 