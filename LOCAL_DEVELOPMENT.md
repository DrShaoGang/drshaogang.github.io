# Local development on macOS

## First-time setup

From the repository directory:

```sh
bundle install
```

Dependencies are installed under `vendor/bundle` and are ignored by Git.

## Preview the site

```sh
LANG=en_US.UTF-8 LC_ALL=en_US.UTF-8 \
  bundle exec jekyll serve \
  --config _config.yml,_config.dev.yml \
  --host 127.0.0.1 --port 4000 --livereload
```

Open <http://127.0.0.1:4000/>. Most content and style changes rebuild
automatically. Restart the server after changing `_config.yml`.

To check the site without starting a server:

```sh
LANG=en_US.UTF-8 LC_ALL=en_US.UTF-8 \
  bundle exec jekyll build --config _config.yml,_config.dev.yml
```

The unauthenticated GitHub metadata warning is expected during local builds.

## Safe editing workflow

Start each change from an up-to-date `master` branch:

```sh
git switch master
git pull --ff-only origin master
git switch -c edit/short-description
```

Edit content, inspect the preview, and review exactly what changed:

```sh
git status --short
git diff
LANG=en_US.UTF-8 LC_ALL=en_US.UTF-8 \
  bundle exec jekyll build --config _config.yml,_config.dev.yml
```

Commit only after the build succeeds:

```sh
git add path/to/edited-file
git diff --cached
git commit -m "Describe the website update"
```

Nothing leaves the Mac until an explicit push. After reviewing the commit,
publish the branch (not `master`) and open a pull request:

```sh
git push -u origin edit/short-description
```

Do not force-push `master`. If the remote changed while editing, fetch it and
review the difference before integrating it:

```sh
git fetch origin
git log --oneline --decorate --graph HEAD..origin/master
```

## Where common edits live

- Site identity, author details, navigation behavior: `_config.yml`
- Homepage/about text: `_pages/about.md`
- Publications: `_publications/`
- Teaching: `_teaching/`
- Talks: `_talks/`
- CV page: `_pages/cv.md`
- Downloadable files: `files/`
- Images, including the author avatar: `images/`
- Navigation links: `_data/navigation.yml`
- Theme styles: `_sass/` and `assets/css/`

GitHub Pages publishes this user site at <https://drshaogang.github.io/>. The
repository currently has no custom GitHub Actions workflow, so publishing is
controlled by the repository's Pages source setting on GitHub.
