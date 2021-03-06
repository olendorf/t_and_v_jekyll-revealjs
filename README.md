# Teaching and Vizualization Studio Jekyll/Reveal.js Slide Framework

This is a port of the Jekyll-based framework for creating presentations based on Reveal.js and Markdown called [Jekyll-revealjs](https://github.com/dploeger/jekyll-reveal.js). This port 
makes a few changes to Jekyll-Reveal to facilitate creating presentations for the Teaching and Vizualization Studio, but otherwise is the same. The documenation here likewise is mostly borrowed
from Jekyll-Reveal with changes as needed. It is recommended you visit [Reveal.js](https://github.com/hakimel/reveal.js/) for their excellent documentation on the Reveal slides framework. 

- [Introduction](#introduction)
- [Getting started](#getting-started)
- [Slide filenames](#slide-filenames)
- [Configuring the presentation](#configuring-the-presentation)
  - [Specifying reveal options and dependencies](#specifying-reveal-options-and-dependencies)
- [Custom reveal.js themes](#custom-revealjs-themes)
- [Markdown extensions and simplification](#markdown-extensions-and-simplification)
  - [Multiple slides](#multiple-slides)
  - [Vertical slides](#vertical-slides)
  - [Fragments](#fragments)
  - [Slide backgrounds](#slide-backgrounds)
  - [Speaker notes](#speaker-notes)

## Introduction

If you like [Reveal.js](https://github.com/hakimel/reveal.js/) for creating your online presentations, like the site management [Jekyll](https://jekyllrb.com/) gives you and like 
[Markdown](https://guides.github.com/features/mastering-markdown/) because of its easy and clean look, here's an easy way to create a presentation using Jekyll, Markdown and Reveal.js.

See the [example presentation](https://olendorf.github.io/t_and_v_jekyll-revealjs/) created using the contents in this repository.

## Getting Started

While you can **_Fork_** this repository or create a copy using **_Use this template_** and edit the files there, this can be very cumbersome in the long run. The steps below
will allow you to create a copy on your local machine and use your favorite editor or IDE to create your presentation.


Clone this repository and create a branch for your new presentation:

    git clone --recursive https://github.com/olendorf/t_and_v_jekyll-revealjs.git

or 

    git clone --recursive <your repo's URL>

Copy the Example presentation:

     mv _posts _templates
     mkdir _posts
     

After that, add your slides into the `_posts` subdirectory. You can use the examples in the new `_templates` folder to help too. Now install the needed dependencies
    
    gem install bundler
    bundle install
    
If all is working you can start the server local now 

    jekyll serve --host $IP --port $PORT



## Slide filenames

Because we're using Jekyll [posts][] to easily gather the slides for the presentation, we use their filename conventions with the following syntax:

    <year>-<month>-<day>-<title>.md

We recommend naming the files like

    0010-01-01-welcome.md
    0020-01-01-topics.md

and so forth. The dates need to be valid but the actual date doesn't matter for our purposes. The convention used here of `0010-01-01` then
`0020-01-01` allows you to easily move slide order by rename just some of the slides. If you number them without gaps you could find yourself
doing a lot of renaming.

## Configuring the presentation

You can configure almost any reveal.js setting using the `_config.yml` settings file in the root directory.

- `title`: The title of your presentation (displayed in the browser's title bar, optional and defaults to your repository’s name thanks to the `jekyll-github-metadata` plugin)
- `description`: A description for your presentation (displayed in the HTML head, optional and defaults to your repository’s description thanks to the `jekyll-github-metadata` plugin)
- `author`: Your name (displayed in the HTML head)
- `reveal_theme`: The reveal.js-theme to use [black.css]
- `reveal_transition`: The reveal.js-transition to use [default]
- `reveal_theme_path`: The path to the reveal.js-theme (can be changed for custom themes) [css/theme/]
- `reveal_notes_server`: Whether to support the speaker notes server [false (only local speaker notes)]
- `reveal_options`: Additional reveal.js [options][]

- `reveal_dependencies`: Additional reveal.js [dependencies][]
- `reveal_path`: Path to the reveal.js-installation [reveal.js]

You can also further customize the presentation:

- `extra_css`: Additional CSS files added after the reveal [theme][]
- `highlight_style_sheet`: CSS theme for highlight.js [reveal.js/lib/css/zenburn.css](reveal.js/lib/css/zenburn.css)

### Specifying reveal options and dependencies

`reveal_options` can be either a list of strings specifying the JavaScript options, e.g.:

```yaml
reveal_options:
  - 'width: "960px"'
  - 'height: "720px"'
```

or, as a convenience, it can be a mapping of options to their values:

```yaml
reveal_options:
  width: 960px
  height: 720px
```

Note that if a mapping is passed, the values will be inserted into the final JavaScript as quoted strings. If this is unacceptable (for example, if you want to pass a Boolean parameter that takes `true` or `false`), specify a list of strings.

`reveal_dependencies` takes a list of strings representing the JavaScript to specify a dependency [as you would in reveal.js](https://github.com/hakimel/reveal.js/#dependencies), for example:

```yaml
reveal_dependencies:
  # Speaker notes
  - "{ src: 'path/to/plugin.js', async: true },"
```

## Custom themes 

The Teaching and Viz port uses its own folder for style sheets `css/` and ignores any CSS in the reveal directory. If you want to add your own CSS
we recommend adding a new file in the `css/theme` directory. You can use either .css or .scss. If you use SCSS you must add the following to the first three 
lines of your file.

    ---
    
    ---
    
    
Then edit `_config.yml` to use that theme

    # The Reveal theme
    reveal_theme: your_theme.scss
    
    


## Markdown extensions and simplification

Reveal.js already includes a Markdown interpreter, which we use for **jekyll-reveal.js**. We have already configured it and included some simplification just for you!

### Multiple slides

To use multiple slides in one slide file, use a newline, three dashes and another newline like this:

```markdown
# Slide 1

This is the content of Slide 1

---

# Slide 2

This is the content of Slide 2
```

### Vertical slides

To use vertical slides, do the same, but use two dashes:

```markdown
# Slide 1

This is the content of Slide 1

--

And this is a vertical slide below Slide 1
```


### Fragments

Fragments allow slide elements to come one by one. This is often used in lists to subsequently show fragments of a list during a presentation.

**jekyll-reveal.js** simplifies the reveal.js syntax. To specify the current element as a fragment, use `<fragment/>` like this:

```markdown
# Slide

- This <fragment/>
- will <fragment/>
- come one by one <fragment/>
```

Or, if you find it cleaner, like this:

```markdown
# Slide

+ This
+ will
+ come one by one
```

### Slide backgrounds

To modify the background of the current slide, **jekyll-reveal.js** simplifies the syntax to `<background>color</background>`:

```markdown
# Slide

<background>white</background>

This slide has a white background
```

#### Image backgrounds

You can also set image backgrounds:

```markdown

# Slide

<backgroundimage>{{ site.github.url }}/images/image.jpg</backgroundimage>
<backgroundimageopacity>0.25</backgroundimageopacity>

This slide has an image background

```

Note: `{{ site.github.url }}` expands to the URL of your hosted site, but you could also use remote URLs.

### Speaker notes

To include speaker notes, add `Note:` on a separate line and write your notes below:

```markdown
# Slide

Some slide content

Note:

This is only displayed in the speaker notes.
```

[reveal.js]: http://lab.hakim.se/reveal-js/#/
[jekyll]: http://jekyllrb.com/
[markdown]: http://daringfireball.net/projects/markdown/
[example presentation]: http://dploeger.github.io/jekyll-revealjs/example
[install jekyll]: http://jekyllrb.com/docs/installation/
[options]: https://github.com/hakimel/reveal.js#configuration
[dependencies]: https://github.com/hakimel/reveal.js#dependencies
[posts]: https://jekyllrb.com/docs/posts/#creating-posts
[theme]: https://github.com/hakimel/reveal.js#theming
