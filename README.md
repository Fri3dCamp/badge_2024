# badge_2024

The general repository for the Fri3dcamp 2024 badge. Access the documentation here: https://fri3dcamp.github.io/badge_2024/

Documentation will be written using the [mkdocs](https://www.mkdocs.org/) system as a reference. You can find them in the [docs](docs) folder.

Initially everything will be written in English, Dutch translation will be added later.

Something missing? Please open [an issue](https://github.com/Fri3dCamp/badge_2024/issues/new) or a [pull request](https://github.com/Fri3dCamp/badge_2024/compare).

# View docs locally

To see if your changes are correctly formatted, you can view the documentation locally with Python.

It is advised to run it inside a virtual environment such as [venv](https://docs.python.org/3/library/venv.html) or [virtualenv](https://virtualenv.pypa.io/en/latest/).

For `venv` you can create a virtual environment with:

```bash
python -m venv .venv
```

Then activate the virtual environment with:

```bash
source .venv/bin/activate
```

For Python 3.6 and higher, you can install mkdocs and the material theme with the following command:

```bash
pip -r requirements.txt
```

Then you can start the local server with:

```bash
mkdocs serve
```

The documentation then be available at http://127.0.0.1:8000/badge_2024/
