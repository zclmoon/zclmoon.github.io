---
layout: post
title:  "Homebrew version value error"
date:   2023-03-04 22:54:55 +0800
categories: tools
permalink: /homebrew-version-value-error/
---

# Error

{% highlight bash %}
/usr/local/Homebrew/Library/Homebrew/version.rb:368:in `initialize': 
Version value must be a string; got a NilClass () (TypeError)
{% endhighlight %}

# Solution
{% highlight bash %}
brew update-reset
{% endhighlight %}

![image](../images/homebrew-issue-images/homebrew-version-error.png)
