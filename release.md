## Release process for `plotly-geo` package

The `plotly-geo` package contains the shape file resources used by plotly.py.
These files are relatively large and change infrequently so it is useful
to release them in a separate package.

### Update version

Update the version of the `plotly-geo` package in
`setup.py`.

This version is not intended to match the version of plotly.py.

### Update CHANGELOG

Add a new entry to the CHANGELOG at `CHANGELOG.md`
and commit the changes.

### Tag Release

Create a new tag for the release:

```bash
(plotly_dev) $ git checkout main
(plotly_dev) $ git stash
(plotly_dev) $ git pull origin main
(plotly_dev) $ git tag vX.Y.Z
(plotly_dev) $ git push origin vX.Y.Z
```

### Publishing to PYPI

Publish the final version to PyPI:

```bash
(plotly_dev) $ python setup.py sdist bdist_wheel
(plotly_dev) $ twine upload dist/plotly_geo-X.Y.Z.tar.gz
(plotly_dev) $ twine upload dist/plotly_geo-X.Y.Z-py3-none-any.whl
```

### Publish to plotly anaconda channel

From the repository's root directory, build the conda package:
```bash
(plotly_dev) $ conda build recipe/
```

Then upload to the plotly anaconda channel as described above