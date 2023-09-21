---
layout: post
title: Hex colors in bash
date: 2023-09-21 11:43 +0200
---

# Using HEX colors in bash terminal

If you've ever wanted to use custom colors in the bash terminal, you have
probably run into the ansi escape sequences for 256 colors or even the RGB
sequences.

In order to use hex colors in bash, you will need to convert the hex sequence
into three decimal numbers. To do exactly that, you can use the following code:

``` bash
function hex_to_dec() {
  color=$(echo $1 | tr '[:lower:]' '[:upper:]')
  red=$(echo $color | awk '{print substr($1,1,2)}')
  green=$(echo $color | awk '{print substr($1,3,2)}')
  blue=$(echo $color | awk '{print substr($1,5,2)}')
  red_dec=$(echo "ibase=16; $red"|bc)
  green_dec=$(echo "ibase=16; $green"|bc)
  blue_dec=$(echo "ibase=16; $blue"|bc)
  echo $red_dec $green_dec $blue_dec
}

function rgb_color() {
  echo -e "\033[38;2;$1;$2;$3m"
}

function rgb_bg_color() {
  echo -e "\033[48;2;$1;$2;$3m"
}
```

Using this, you can use hex colors like so:

``` bash
echo -e "$(rgb_color $(hex_to_dec ff0000))Foo"
```
