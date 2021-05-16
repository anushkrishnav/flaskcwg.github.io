# Flask Community Workgroup

## How does the site gets built

**Note:** You need to have the **[jamstack library](https://pypi.org/project/jamstack/)** installed.

1. Run [**docs/serve.py**](docs/serve.py)
2. You will be provided with the **IP** and **PORT** to view the site
3. Edit files in the [**/templates**](/templates) folder
4. Run [**static.py**](static.py) file in another terminal
5. Refresh the url provided in step **2** to see the changes
6. The final files are generated in the [**/docs**](/docs) folder

Alternatively, you can also run `tox`.

## How to add a new page?

In `static.py`, under generate, add another generate function:

```python
def main(args):
    def gen():
        generate('index.html', join(settings.OUTPUT_FOLDER, 'index.html'), **context)
```

Like this:

```python
def main(args):
    def gen():
        generate('index.html', join(settings.OUTPUT_FOLDER, 'index.html'), **context)
        generate('source_file.html', join(settings.OUTPUT_FOLDER, 'output_file.html'), **context)
```

Where `source_file.html` is the name of the file located in `templates/` and `output_file.html` is the output file which will be located in `docs/`.

## What is the techstack behind?

**[jamstack](https://jamstack.org)**: Generate pages using Jinja templates.

**flask + livewatch**: If you want to auto regenerate files without executing `static.py`.