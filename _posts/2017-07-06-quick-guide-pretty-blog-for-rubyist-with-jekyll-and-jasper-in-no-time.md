---
layout: post
cover: 'assets/images/cover2.jpg'
title: 'Quick Guide: A Pretty Blog for a Rubyist with Jekyll and Jasper in No Time'
date:   2017-07-06 13:00:00
tags: [Ruby, Jekyll, Jasper, Git, GitHub Pages]
subclass: 'post tag-test tag-content'
categories: 'piotr'
navigation: True
logo: 'assets/images/iamp.png'
description: "Love Ruby? With Jekyll, you can have your personal blog as a Ruby application."
image: '/assets/images/cover2.jpg'
disqus: true
---

I know, I know. Ruby is not a hyped language anymore, as it used to be only a few years ago.
On the other hand, it's ecosystem has matured and there are a lot of gems around that help make
things easier, whereas with your modern-hyped-language-of-choice it might be a totally different story.
And most importantly, Ruby is still undeniably beautiful and loved by many (including myself).

So let's say you are a little like me: a Ruby lover who wants to start a blog. What's the first
thing that comes to your mind?

> Huh, can I maybe have this blog set up as a Ruby app, too?
And possibly, could it look quite pretty, like maybe this one I'm reading right now?

[comment]: <> (if you're reading this on Medium, [click here](http://iampiotr.com) to check it out).

Luckily for you, it is possible and not at all hard. Let's get to it right away.

### Jekyll

First of all, of course you could write your
[blog as a Rails app from scratch in 15 minutes](https://www.youtube.com/watch?v=Gzj723LkRJY&feature=youtu.be)
(a classic!) but unless you're a beginner Rubyist, in which case this migth be
a good exercise, you likely don't want to spend time writing another CRUD with Rails
for this purpose. And of course, if you had decided to go that route, you'd still need
to spend quite some time styling your blog, etc. etc.. That's not what we are going to
do today. This is where [Jekyll](https://jekyllrb.com/) comes in.

So what is Jekyll? As it's described on it's official website:

> Jekyll is a simple, blog-aware, static site generator. It takes a template directory
containing raw text files in various formats, runs it through a converter (like
[Markdown](https://daringfireball.net/projects/markdown/)) [...] and spits out a complete,
ready-to-publish static website suitable for serving with your favorite web server.

Doesn't it sound nice? And there is even more to that, like easy deploying to
[GitHub Pages](https://pages.github.com/), but we will get to that later. Setting
up Jekyll is dead simple, head over to [their homepage](https://jekyllrb.com/)
to see how to get it up and running. I advise you to play around with it for a bit,
if you haven't had a chance to do that before, as well as read through their docs,
to further understand how it works in detail.

Again, we won't be going through the barebones Jekyll setup, we are going to take
advantage of it's community and the fact that there are a lot of great themes we
can use without much hassle. After all, we want our new little blog to look pretty
from the start, don't we?

### Jasper

[Jasper](https://github.com/biomadeira/jasper) is a simple and pretty looking theme,
which in fact is a clone of a Casper theme from the [Ghost](https://ghost.org/)
publishing platform. It's a matter of taste, in the end, so if you don't like it,
you can skip the Jasper setup part and skip to the next one (plus, of course, set up
you themed or unthemed Jekyll blog in the meantime).

Alright, let's start with cloning the Jasper repo and then getting it running.
From your terminal shell:

<pre>
  git clone https://github.com/biomadeira/jasper.git
  cd jasper && bundle exec jekyll serve
</pre>

Alternatively, you can also fork the repository, then clone your fork and go from there.
Then go to `localhost:4000/jasper/` in your favourite browser and voila - we have
it running and looking as pretty as it gets. So far, so good:

<p>
  <img src="{{ site.url }}/assets/images/jasper_home.jpg" alt="Jasper Blog Home Page" />
  <small><em>this is what you should be seeing right know</em></small>
</p>

Fire up the code in your favourite editor and head over to `_config.yml`. There are
some configuration options you might want to change. Most should be self explanatory,
I'll leave the setup alone, let's just change two things:

<pre>
  <strong><em>_config.yml</em></strong>
  ...
  nickname: myname
  ...
  base_url: /
  ...
</pre>

The latter change will make our site render on the root url, instead of the `/jasper` one.
Regarding nickname, it's a Jasper convention - we'll be using this nickname to tag
ourselves as a post author in just a second.

### Writing Blog Posts with Jekyll

Alright, our setup should be ready. Let's write our first post! You might have noticed,
that our little blog already has a few example posts written. Let's take a look at one
of them:

<pre>
  <strong><em>_posts/1963-08-28-i-have-a-dream.md</em></strong>

  ---
  layout: post
  cover: false
  title: I Have a Dream
  date:   1963-08-28 10:18:00
  tags: speeches
  subclass: 'post tag-speeches'
  categories: 'casper'
  navigation: True
  logo: 'assets/images/ghost.png'
  cover: 'assets/images/cover4.jpg'
  ---

  ...
</pre>

This piece betwee three-dashed lines above is called a YAML front matter.
All of the values here are optional and most of them are custom setup for Jasper
theme. You can [read more about the front matter here](https://jekyllrb.com/docs/frontmatter/).
For now, we'll steal this setup with some minor changes for the purpose of our new post.

Let's make ourselves a new file in the `_posts` directory. From the command line:

<pre>
  touch _posts/2017-07-05-an-awesome-post.md
</pre>

As you probably noticed, we are using the `.md` extension for our file.
That's right, with Jekyll it's possible to write our posts using a great, terse
[Markdown](https://daringfireball.net/projects/markdown/) syntax, but you can also
use the regular HTML if that's your preference. We'll stick to Markdown for our
example post. Let's set up the contents of our newly created file to:

<pre>
  <strong><em>_posts/2017-07-05-an-awesome-post.md</em></strong>

  ---
  layout: post
  cover: false
  title: An Awesome Post
  date: 2017-07-05 12:00:00
  tags: posts
  subclass: 'post tag-content'
  categories: 'myname'
  navigation: True
  logo: 'assets/images/ghost.png'
  cover: 'assets/images/cover3.jpg'
  ---

  # Hello World!

  This is our awesome post!
</pre>

The most important piece of the above, is the `categories` line, which link your
post to the author we created before (remember the nickname setting from the `_config.yml`?).
Let's refresh our homepage at `localhost:4000`, and you shall see your new post
on top of the posts list. Tada!

<p>
  <img src="{{ site.url }}/assets/images/jasper_post.jpg" alt="Jasper Blog Home Page" />
  <small><em>ah, your awesome new Jekyll post is here</em></small>
</p>

Alright, this should get you going and blogging in no time now! Go read the contents of
`_posts/2014-09-27-a-full-and-comprehensive-style-test.html` for a style guide of
the Jasper theme, we won't be going further with that. There is one important thing left
to do, though: so we have our blog, we can add posts, all that we now need
is to push to the Internetzz, so that other people can read our precious writings.

### GitHub Pages

If you are not familiar with GitHub Pages yet, they provide an extremely convenient
way of hosting websites, directly from a GitHub repository, with practically zero hassle.
As it says on [GitHub pages website](https://pages.github.com/):

> Just edit, push, and your changes are live.

There isn't really much that can go wrong here, just follow the steps from the link above.
The only change to the described flow would be, that you don't clone the newly
created repository. Instead, connect the previously cloned Jasper repo to your new
one at github. Let's quickly commit the changes we have made before and do that:

<pre>
  git commit -m "Update configuration & create a new blog post"
  git remote remove origin
  git remote add origin https://github.com/user/repo.git
</pre>

Of course, substitute the `user` and `repo` parts with the data from your
new GitHub repository. You can confirm that everything worked, by using
`git remote origin -v`.

There is one more gotcha regarding deploying to GitHub Pages with Jasper, which
gave me quite a headache during setting up my own blog. It was all my fault, though,
I had simply missed a piece of the [gem's readme regarding deployment](https://github.com/biomadeira/jasper#deployment),
so do yourself a favour and don't repeat my mistakes.

Okay, we did it! You should have your blog live and accessible for all your friends
and the whole wide world. From here, you can configure it, so that it [runs from your
custom domain of choice](https://help.github.com/articles/about-supported-custom-domains/)
and do whatever customizations you like. But most importantly, nothing should stop
you from blogging like crazy right now.

It was a pleasure writing this piece ("A blog about a blog!"), I hope it was also helpful for you.
If so, don't hesitate and let me know by writing a comment. Do the same in case of any questions.
