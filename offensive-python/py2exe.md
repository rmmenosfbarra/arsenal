# Overview
Library to compile Python scripts as standalone Windows executables. You can even choose to bundle all necessary DLL´s in a single .exe. 
Note that this files tend to be heavy even for the tiniest script.

To get started, simply download & install **py2exe** from: http://www.py2exe.org/. Unless you specifically need it, I would install the win32 version for compatibility reasons.

# Creating a "Hello world"
*Reference: http://www.py2exe.org/index.cgi/Tutorial*

* Create your hello world script `hello.py`

```python
print "Hello World!"
```


* Create a setup.py that will use the library to create your executable

```python
from distutils.core import setup
import py2exe

setup(
	console=['hello.py'] # Name of the Python script you want to "compile"
)
```

* Run from command line: `python setup.py py2exe`

# Bundling everything within a single .exe
*Reference: https://stackoverflow.com/questions/112698/py2exe-generate-single-executable-file#113014 *

Configure your `setup.py` as follows:

```python
from distutils.core import setup
import py2exe

setup(
	console=['hello.py'],
	options={'py2exe': {'bundle_files': 1, 'compressed': True} },
	zipfile= None
)
```

>Using "bundle_files" and "zipfile"
>
>An easier (and better) way to create single-file executables is to set bundle_files to 1 or 2, and to set zipfile to None. This approach does not require extracting files to a temporary location, which provides much faster program startup.
>
>Valid values for bundle_files are:
>
>    3 (default) don't bundle
>    2 bundle everything but the Python interpreter
>    1 bundle everything, including the Python interpreter
>
>If zipfile is set to None, the files will be bundle within the executable instead of library.zip.
