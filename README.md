# Bagatto Story: Modular and fast static site

This directory contains everything needed to generate **Story** theme site using Bagatto.

## About the theme

Look [here](https://github.com/caressofsteel/hugo-story) for a description. HTML5UP and caressofsteel made *superb* work!

## Fast start:

To build the site, install or build Janet and Bagatto (in-depth installation
instructions are available in the Bagatto manual), download this repo or clone it,
`cd` into this directory (the one containing `index.janet`), and then run

```janet
bag index.janet
```

You should see Bagatto output its progress as it creates the site, but get ready: It's *quick!*


The generated HTML will now be available in `site/` and you can open `site/index.html` in your web browser.

### Demo site

It's the index.html file in this repo. See it [here](https://bagatto-story.github.com).

### Content choices

I chose to create the dynamic content as `.md` files, the rest is hard-coded in the templates.
For example, the gallery header will probably not change much, but the individual
pictures will. Same with the spotlights and items. I added a bit of markdown styles
to the dynamic content `Lorem ipsum...`, just for a show..

All dynamic content resides in the `content/` directory. Just makes sense.

## Why port a theme to Bagatto? Why use bagatto?

Have a look at the way [hugo](https://gohugo.io/), [zola](https://www.getzola.org/) and other mainstream big names SSGs work.
They are *clearly* not made to handle single-page sites, they are geared towards multi-page
sites and this logic is built into them. You have to bend their rules a bit to handle
single page sites. Look at the [hugo-story](https://github.com/caressofsteel/hugo-story) theme
source code in order to see it:

1. The site content resides in `data/` folder instead of `content/` folder.
2. All the text is pure html, since hugo by design processes markdown files
   only in `content/`.
3. All the text is in few big `.yaml` files, instead of small markdown files
   for each piece of content.
4. The `index.html` template calls the partial templates with the relevant
   `.yaml` files hard-coded for context, and there is no way (that I know of)
   to use context created in the `content/` folder.

I checked other single-pgae themes for hugo. They are all trying hard to find
ways around the limitations.
All this makes generating your preferred single-page site a bit inconvenient..

## Enter Bagatto & Janet

After seeing the problems with the usual SSG suspects, I looked for something
that will work better for single-page sites. I limited myself to compiled SSGs
because I wanted simple setup. The *least* probable choice was Bagatto of-coarse,
since I have to learn Janet now and enter the lisp world. And who have heard of
it anyhow?!

Well, how lucky!

Janet is an amazing language (I still don't understand much of it..), and the
runtime is unbelievable. The compiled `bag` binary (as per my requirement), is
just bytecode running on top of VM, all in a single app. So you have the
full Janet VM at your disposal.

Further, there are no rigid rules here. You have your data, and you have functions
operating on it and transforming it the way you like. So simple.

## RTFM

Have a look at `index.janet` it's the file that describes how to make the site.
Go take a look at Bagatto own site and the demo sites shipped with it. Read
all the `index.janet` files you can find and the Bagatto source (it's short).
It will make you smarter, I promise.

## Thanks

Calvin Rose, for [Janet](https://janet-lang.org/)
Zach Smith, for [Bagatto](https://git.sr.ht/~subsetpark/bagatto)
HTML5UP, for the initial [Story](https://html5up.net/story) theme
caressofsteel, for [hugo-story](https://github.com/caressofsteel/hugo-story) port

## License

<a rel="license" href="http://creativecommons.org/licenses/by/3.0/" class="license-button"><img alt="Creative Commons License" style="border-width:0" src="https://i.creativecommons.org/l/by/3.0/88x31.png"></a>

This Bagatto theme is licensed under the [Creative Commons Attribution 3.0 License](LICENSE).
