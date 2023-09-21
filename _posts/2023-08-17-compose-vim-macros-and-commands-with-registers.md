---
layout: post
title: Compose Vim macros and commands with registers
date: 2023-08-17 11:03 +0200
---

# Compose Vim macros and commands with registers

While using *Vim*, you have probably come across writing *macros* and *commands* and
making a mistake. Editing your command in the *Command mode* readline input, is
a pain for complicated commands and don't even get me started on editing complex
*macros*.

The beauty of the way *Vim* is constructed however, makes it very easy to edit
either of these things using *registers*.

Let's start by creating a simple find *command*, that we want to read the output
of. Usually you would just type something like:

{% highlight bash %}
:.!find foo -name "bar.baz" -type f
{% endhighlight %}

This seems fine for short *commands* but for longer or more error prone things,
consider writing the whole command in your buffer and doing the following:

Buffer:
{% highlight bash %}
find foo -name "bar.baz" -type f -mtime +10 -more -options -etc -etc -etc
{% endhighlight %}

In *Normal mode*:
{% highlight vim %}
dd!!<C-R>"
{% endhighlight %}

As you can see, the *command* you had the comfort of editing in *Vim*, is
inserted in your *Command mode* input through the magic of *registers*.

You can do the same with *macros*. Let's say we want a *macro* that flips the
CSV values before and after a comma.

Buffer:
{% highlight csv %}
"foo column 1", "foo column 2"
"bar column 1", "bar column 2"
{% endhighlight %}

A way to do this would be to put your cursor at the start of the first line and
type:

{% highlight vim %}
qqda"lplda"0Pq
{% endhighlight %}

Another way creating that same *macro* would be to put a new line in the file that
reads:

{% highlight vim %}
da"lplda"0P
{% endhighlight %}

Now, since we are using deleting and pasting in our *macro*, we can't simply use
the `"` *register* to put our *macro* in. If we did that, the *macro* would be gone
after every execution. Let's put the *macro* in the `q` *register* like with our
regular *macro* record example using: `"qdd`.

You can now use `@q` like you could before, to play the *macro* we just wrote.

Obviously, this is not particularly useful for simple stuff like these examples,
but for large *macros* and *commands*, this can make editing and creating them
much more convenient.

Don't forget that if we want to change something in a *macro* we have placed in
*register* `q`, we can simply paste that *register* with `"qp`, edit it and place it back in
the *register* using `"qdd`.
