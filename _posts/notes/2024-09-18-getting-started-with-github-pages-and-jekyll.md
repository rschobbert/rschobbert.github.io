---
title: "Getting Started with github pages and jekyll - part 1"
excerpt_separator: "<!--more-->"
categories:
  - Blog
tags:
  - jekyll
  - github pages
---

In this post, I will document my first steps on how to use github pages and jekyll, to create my blog. I will describe the setup of github pages and jekyll with my chosen theme and will collect the syntax for posts. I will update this post on my way of learning and continuously improving the site and my skills.

<!--more-->

I will keep this post in short form, without much text and rather have it as a kind of summary for myself.

Further resources:
* [jekyll docs about posts](https://jekyllrb.com/docs/posts/)
* [github docs about pages](https://docs.github.com/de/pages)

The basic structure of a post:
```
---
title: "the title of the post"
excerpt_separator: "<!--more-->"
categories:
  - Category1
  - Category2
tags:
  - tag1
  - tag2
---

after the above front matter, add the excerpt. This is either the first paragraph, or if you included the `excerpt_separator` in the front matter everything up to this separator.

<!--more-->

Write the rest of the blog post from here...
```

