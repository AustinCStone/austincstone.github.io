---
layout: post
title:  "Evolving the Perfect Lens"
date:   2021-09-21 14:10:01 -0700
categories: jekyll update
published: false
---

(WIP):

\\( a^2 = b^2 \\)

The eye is frequently given as an example of something which is hard to fathom was created by evolution.
The origins of this might be traced back to some words from Darwin (which are frequently pulled out of context).
In “On the Origin of Species” Darwin wrote that the idea that natural selection could produce such an intricate organ “seems, I freely confess, absurd in the highest possible degree.” What is often left out is that Darwin goes on to point out
how absurd the structure of the solar system once seemed, making the point that our intuitions are reality
can be misleading.

In this post, I will show how the lens of an eye can be evolved using genetic algorithms. A perfect
lens is actually pretty complicated. For a background on how lenses work, see From the Feynman Lectures:

Now suppose that we have a point at O, at a distance s from the front surface
of the glass, and another point O′ at a distance s′ inside the glass, and we desire to arrange the curved surface in such a manner that every ray from O which hits ′
the surface, at any point P, will be bent so as to proceed toward the point O . For that to be true, we have to shape the surface in such a way that the time it takes for the light to go from O to P, that is, the distance OP divided by the speed of light (the speed here is unity), plus n · O′P , which is the time it takes to go from P to O′, is equal to a constant independent of the point P. This condition supplies us with an equation for determining the surface. The answer is that the surface is a very complicated fourth-degree curve, and the student may entertain himself by trying to calculate it by analytic geometry. It is simpler to try a special case that corresponds to s → ∞, because then the curve is a second-degree curve and is more recognizable. It is interesting to compare this curve with the parabolic curve we found for a focusing mirror when the light is coming from infinity.

Test test test! You’ll find this post in your `_posts` directory. Go ahead and edit it and re-build the site to see your changes. You can rebuild the site in many different ways, but the most common way is to run `jekyll serve`, which launches a web server and auto-regenerates your site when a file is updated.

Jekyll requires blog post files to be named according to the following format:

`YEAR-MONTH-DAY-title.MARKUP`

Where `YEAR` is a four-digit number, `MONTH` and `DAY` are both two-digit numbers, and `MARKUP` is the file extension representing the format used in the file. After that, include the necessary front matter. Take a look at the source for this post to get an idea about how it works.

Jekyll also offers powerful support for code snippets:

{% highlight ruby %}
def print_hi(name)
  puts "Hi, #{name}"
end
print_hi('Tom')
#=> prints 'Hi, Tom' to STDOUT.
{% endhighlight %}

Check out the [Jekyll docs][jekyll-docs] for more info on how to get the most out of Jekyll. File all bugs/feature requests at [Jekyll’s GitHub repo][jekyll-gh]. If you have questions, you can ask them on [Jekyll Talk][jekyll-talk].

[jekyll-docs]: https://jekyllrb.com/docs/home
[jekyll-gh]:   https://github.com/jekyll/jekyll
[jekyll-talk]: https://talk.jekyllrb.com/
