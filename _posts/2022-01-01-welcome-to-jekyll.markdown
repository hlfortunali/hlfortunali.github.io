---
# multilingual page pair id, this must pair with translations of this page. (This name must be unique)
lng_pair: id_What_is_this
title: "downgrade ubuntu!"

# post specific
# if not specified, .name will be used from _data/owner/[language].yml
author: lisir
# multiple category is not supported
category: lisir
# multiple tag entries are possible
tags: [heng, example post, sample, test]
# thumbnail image for post
img: ":post_pic3.jpg"
# disable comments on this page
#comments_disable: true

# publish date
date: 2022-09-16 22:04:30 +0900

# seo
# if not specified, date will be used.
#meta_modify_date: 2022-01-01 10:04:30 +0900
# check the meta_common_description in _data/owner/[language].yml
#meta_description: ""

# optional
# if you enabled image_viewer_posts you don't need to enable this. This is only if image_viewer_posts = false
#image_viewer_on: true
# if you enabled image_lazy_loader_posts you don't need to enable this. This is only if image_lazy_loader_posts = false
#image_lazy_loader_on: true
# exclude from on site search
#on_site_search_exclude: true
# exclude from search engines
#search_engine_exclude: true
# to disable this page, simply set published: false or delete this file
# published: false
---
<!-- outline-start -->

This is a guide to downgrade Ubuntu system version. I downgrade it from 22.04.5 to 22.04.1. 

First step is to downgrade sources list file to the previous version. You can find the code for each version on ubuntu website(https://releases.ubuntu.com/). The 22.04.5 is focal and the 22.04.1 is jammy. Using the following command to see your version code:
`cat /etc/os-release | grep -i version`
It will print the version in you console:
```
VERSION_ID="22.04"
VERSION="22.04.1 LTS (Jammy Jellyfish)"
VERSION_CODENAME=jammy
```

Then, use following command to change the source list:
`$ sudo sed -i 's/cosmic/bionic/g' /etc/apt/sources.list `   

You can check the result by using following commnad after change:
`cat /etc/apt/sources.list | grep -v ^# | grep . `


To add new posts, simply add a file in the `_posts` directory that follows the convention `YYYY-MM-DD-name-of-post.ext` and includes the necessary front matter. Take a look at the source for this post to get an idea about how it works.

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
