# docums-autorefs

Automatically link across pages in Docums.

## Installation

With `pip`:
```bash
python3 -m pip install docums-autorefs
```

## Usage

```yaml
# docums.yml
plugins:
  - search
  - autorefs
```

In one of your Markdown files (e.g. `doc1.md`) create some headings:

```markdown
## Hello, world!

## Another heading

Link to [Hello, World!](#hello-world) on the same page.
```

This is a [*normal* link to an anchor](https://documsapp.github.io/docums/user-guide/writing-your-docs/#linking-to-pages). Docums generates anchors for each heading, and they can always be used to link to something, either within the same page (as shown here) or by specifying the path of the other page.

But with this plugin, you can **link to a heading from any other page** on the site *without* needing to know the path of either of the pages, just the heading title itself.  
Let's create another Markdown page to try this, `subdir/doc2.md`:

```markdown
We can [link to that heading][hello-world] from another page too.

This works the same as [a normal link to that heading](../doc1.md#hello-world).
```

Linking to a heading without needing to know the destination page can be useful if specifying that path is cumbersome, e.g. when the pages have deeply nested paths, are far apart, or are moved around frequently. And the issue is somewhat exacerbated by the fact that Docums supports only *relative* links between pages.

Note that this plugin's behavior is undefined when trying to link to a heading title that appears several times throughout the site. Currently it arbitrarily chooses one of the pages.

## Requirements

`docums-autorefs` requires Python 3.6 or above.

<details>
<summary>To install Python 3.6, I recommend using <a href="https://github.com/pyenv/pyenv"><code>pyenv</code></a>.</summary>

```bash
# install pyenv
git clone https://github.com/pyenv/pyenv ~/.pyenv

# setup pyenv (you should also put these three lines in .bashrc or similar)
export PATH="${HOME}/.pyenv/bin:${PATH}"
export PYENV_ROOT="${HOME}/.pyenv"
eval "$(pyenv init -)"

# install Python 3.6
pyenv install 3.6.12

# make it available globally
pyenv global system 3.6.12
```
</details>
