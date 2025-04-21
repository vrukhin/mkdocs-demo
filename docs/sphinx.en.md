# Sphinx

## Project Creation

1. Create a new project following the wizard prompts
   ```bash
   sphinx-quickstart
   ```
1. Edit `conf.py` according to the
[instructions](https://www.sphinx-doc.org/en/master/usage/configuration.html)
1. Start the server
   ```bash
   sphinx-reload .
   ```

## Adding Pages

In the `sources` folder, create your documentation pages in `.rst` format. Each
folder must contain an `index.rst` file with links to other files.

## Building a Static Site

To build a static site, run the command

```bash
sphinx-build -M html sourcedir outputdir
```

If a makefile is present, you can start the build with the command

```bash
make html
```

## Adding Translations

1. Add the following lines to `conf.py`
   ```python
   locale_dirs = ['locale/']
   gettext_compact = False
   ```
1. Run the build in `gettext` format
   ```bash
   make gettext
   ```
1. Generate localization files
   ```bash
   sphinx-intl update -p _build/gettext -l en
   ```
1. Add string translations to localization files
1. Run the build
   ```bash
   make -e SPHINXOPTS="-D language='en'" html
   ```
