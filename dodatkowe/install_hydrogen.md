# Installing hydrogen (on Windows 10)
My last (successful) attempt at installing hydrogen package for Atom editor was on `2016-09-18`. At that time installing hydrogen on windows wasn't straightforward (maybe it is now). Here are the steps that led me to victory:

## make sure you have Visual Studio 2013
Make sure you have Visual Studio **2013** installed. I first installed Visual Studio 2015 and couldn't make hydrogen installation work. You can download relevant Visual Studio version [here](https://www.microsoft.com/en-US/download/details.aspx?id=44914).
Just choose the `.exe` file and run the installer - it will download all necessary files.
Then make sure that `apm --version` command in console displays it is using visual studio 2013. If it doesn't try running these commands in console:
```
apm config set msvs_version 2013 -g
set GYP_MSVS_VERSION=2013
```
You can also use `setx` instead of `set` to permanently set the value of the `GYP_MSVS_VERSION`.

## make sure `apm` is using python 2
You can check what version of python apm is using via:

```
apm --version
```

on my computer the result is:

```
apm  1.12.5
npm  3.10.5
node 4.4.5
python 3.5.1
git 2.8.1.windows.1
visual studio 2013
```

You can see that Atom Package Manager detects python 3.5.1. However to install
Hydrogen you need to use python 2. We need to provide apm with a path to
python 2. You can create a python 2 virtual environment with `conda`:

```
conda create -n py2 python=2.7
```

then you need to accept the download plan for the environment and once setup is
finished, you can activate the environment using `activate <env_name>`:

```
activate py2
```

Now we want to check where python executable for this environment is located.
We first run python REPL:

```
python
```

and then in python we execute these commands:

```python
import sys
sys.executable
```

In my case it prints: `'C:\\Anaconda3\\envs\\py2\\python.exe'`.
I then use this path when setting apm python path (remember to quit
python before - `quit()`):

```
apm config set python C:\\Anaconda3\\envs\\py2\\python.exe
```

## finally
Run `apm install hydrogen` and enjoy!
