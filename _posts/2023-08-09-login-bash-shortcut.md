---
title:  "Shortcut to login as anyone in bash."
date:   2023-08-09 09:21:52 +0200
author: Abe
categories: snippets
---

If you ever find yourself switching users on Linux servers frequently, consider
using the following snippet in your `.bashrc` file.

{% highlight bash %}
for SU_USER in $(grep "/bin/bash" /etc/passwd | cut -f 1 -d:)
do
  alias $SU_USER="sudo -u $SU_USER -E /bin/bash"
done
{% endhighlight %}

Alternatively, you can put this snippet in your `.bashrc` file by doing `curl
https://avdw.dev/snippets/login-alias >> $HOME/.bashrc; source $HOME/.bashrc`

This will create a new alias for every user with a bash shell on your system,
allowing you to switch users by simply typing the username.
