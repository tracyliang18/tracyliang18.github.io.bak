---
layout: post
title: jeklly-note
---

date
{{ site.time | date_to_string }}

number of words

{{ page.content | number_of_words }}

listing tags

#{{ page.tags | array_to_sentence_string }}

####small tags####

note that sig.md should be in the main_dir/_include 

programming language highlight

{% highlight ruby  linenos %}
def foo
  puts 'foo'
end
{% endhighlight %}
note that linenos is optional, which will force the highlighted code to include line numbers


post url
[Name of Link]

