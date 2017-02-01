# Caching problem with Liquid

The SASS stylesheet in this project is set up to pull in a Jekyll-provided
variable. This works great on the first generation of the site, but subsequent
builds do not pick up changes made to the Jekyll data because of the way the
caching is working. Only by changing the actual content of the
`_assets/css/styles.scss` file will it get properly regenerated.

# Reproducing

First do a build:

```
bundle
bundle exec jekyll build
cat _site/assets/manifest.css
```

You'll note we have:

```
body { background-color: white; }
```

Now change the `background_color` variable in `_config.yml` to `red`. Rebuild
the site:

```
bundle exec jekyll build
cat _site/assets/manifest.css
```

The `manifest.css` file did not get updated to use the `red` value.

