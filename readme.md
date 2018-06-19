# Sketch Stickies
I’d recommend adding this to an existing Sketch Library you use often or starting a new one. 

It’s super easy to use just add the base Post It symbol and customize it from there. You can also add new typefaces or other typography options. If you make any cool changes please share it back. 

## Components

### Marker Felt Font

If you’d like to download the free Marker Felt font visit https://www.1001freefonts.com/marker-felt.font.
```
#### Card - Full Width

## Sass
The main style.css file is built by Sass. To make changes to styles, you want to edit the files
within `/sass`. The root entry file is `/sass/style.css`, which should only be used for importing
other partials.

A couple of CLI commands you'll want when working with Sass are below:

- One-off build of the stylesheet
  - `sass ./sass/style.scss:./style.css --style=compressed`
- Watch entire sass directory for changes and build automatically
  - `sass ./sass/style.scss:./style.css --style=compressed`

For even more magic, create a local `/bin` directory and put those commands into bash scripts for
easier use. For example:

``` bash
#!/bin/bash
sass --watch ./sass:./ --style=compressed
```

---

## JS
We use [Webpack](https://www.webpack.js.org) for bundling our js files. The main configuration file is
found at `./webpack.config.js`.

The main site js file is located at `/js/site.js` and compiles down to `./js/site.bundle.js`. Eventually I'd
like to move this to a more modern JS setup and modularize the code instead of it being in all one big file.

We also have a second bundle specifically for sermons. This entry file is found at `./js/sermons/index.js` and compiles
down to `./js/sermons.bundle.js`.

Dependencies are managed with `yarn` and there are a handful of commands available in the `package.json`, such as
`yarn sass:build` and `yarn sass:watch` for building/watching sass changes. For js the pattern is the same,
`yarn js:build` and `yarn js:watch` are available.

### Deployment
The Siteground server has a Git `post-receive` hook setup on a repo found at
`~/repos/westside-church-wp.git` that when added as a remote in your local repository, can be
pushed to and will automatically deploy those changes to `~/public_html/wp-content/themes/westside-church-wp`

Once you have an SSH key on the server, the URL for the remote is `ssh://westsi24@109.73.239.142:18765/~/repos/westside-church-wp.git`. The  Git command to add
this remote would be:
```
git remote add siteground ssh://westsi24@109.73.239.142:18765/~/repos/westside-church-wp.git
```

And the command to then push to the `master` branch and automatically deploy would be:
```
git push siteground master
```

You don't **have** to use this method to deploy, just ensure that any changes that are made directly
on the server to this plugin are also committed to the `master` branch of the repo, or they will be
lost on the next deployment.