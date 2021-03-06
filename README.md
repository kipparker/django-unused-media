# Delete unused media files from Django project

This package provides management command `cleanup_unused_media` for Django application. With help of this command you can remove all media files which are no longer used (files without references from any Django model with `FileField` or `ImageField` fields or their inheritances).

# Installation
1.  Install ``django-unused-media``:
    ```
    pip install django-unused-media
    ```
    Python 2.7, 3.5, PyPy are tested with tox.
    
    Django 1.6, 1.7, 1.8, 1.9 are tested with tox.

2.  Add ``django-unused-media`` to ``INSTALLED_APPS``:
    ```python
    INSTALLED_APPS = (
        ...
        'django_unused_media',
        ...
    )
    ```

# Usage

For cleanup all unused media run management command:
```
./manage.py cleanup_unused_media
```
By default command runs in interactive mode. And before removing list of files will be displayed. User should confirm the action.

### Options

`--noinput` 

Non interactive mode. Command will remove files without confirmation from user. Useful for scripts.
```
./manage.py cleanup_unused_media --noinput
```

`-e`, `--exclude` 

To avoid operating on files whose names match a particular pattern. Pattern supports only `*` as any symbols. Can use multiple options in one command.

For example, to keep `.gitignore` and `*.png` files you can use:
```
./manage.py cleanup_unused_media --exclude .gitignore --exclude *.png
```

`-f`, `--folder` 

If you only need to check a particular folder for unused images, you can pass in the folder name. As above, can use multiple options in one command.

```
./manage.py cleanup_unused_media --folder images
```


# Tests
At first make sure that you are in virtualenv.

Install all dependencies:
```
make setup
```
To run tests:
```
make test
```

# License
[MIT licence](./LICENSE)
