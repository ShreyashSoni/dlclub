## Anaconda
[Anaconda](https://anaconda.org/anaconda/python) is a distribution of packages built for data science. It comes with conda, a package and environment manager. You'll be using conda to create environments for isolating your projects that use different versions of Python and/or different packages. You'll also use it to install, uninstall, and update packages in your environments. Using Anaconda has made my life working with data much more pleasant.<br>
With Anaconda, it's simple to install the packages you'll often use in data science work. You'll also use it to create virtual environments that make working on multiple projects much less mind-twisting. Anaconda has simplified my workflow and solved a lot of issues I had dealing with packages and multiple Python versions.<br>
Anaconda is a fairly large download (~500 MB) because it comes with the most common data science packages in Python.You probably already have Python installed and wonder why you need this at all. Firstly, since Anaconda comes with a bunch of data science packages, you'll be all set to start working with data. Secondly, using conda to manage your packages and environments will reduce future issues dealing with the various libraries you'll be using.<br>
Often you’ll be working with code that depends on different versions of some library. For example, you could have code that uses new features in Numpy, or code that uses old features that have been removed. It’s practically impossible to have two versions of Numpy installed at once. Instead, you should make an environment for each version of Numpy then work in the appropriate environment for the project. This issue also happens a lot when dealing with Python 2 and Python 3. You might be working with old code that doesn’t run in Python 3 and new code that doesn’t run in Python 2. Having both installed can lead to a lot of confusion and bugs. It’s much better to have separate environments.

[//]: # (Image References)
[image1]: ./images/image1.png

### Installing Anaconda
Anaconda is available for Windows, Mac OS X, and Linux. You can find the installers and installation instructions at https://www.anaconda.com/download/ <br>
If you already have Python installed on your computer, this won't break anything. Instead, the default Python used by your scripts and programs will be the one that comes with Anaconda.<br>
Choose the Python 3.6 version. Also, choose the 64-bit installer if you have a 64-bit operating system, otherwise go with the 32-bit installer. Go ahead and choose the appropriate version, then install it. Continue on afterwards!<br>
After installation, you’re automatically in the default conda environment with all packages installed which you can see below. You can check out your own install by entering `conda list` into your terminal.
![image1]<br>

### On Windows
A bunch of applications are installed along with Anaconda:
* **Anaconda Navigator**, a GUI for managing your environments and packages.
* **Anaconda Prompt**, a terminal where you can use the command line interface to manage your environments and packages.
* **Spyder**, an IDE geared toward scientific development.

To avoid errors later, it's best to update all the packages in the default environment. Open the **Anaconda Prompt** application. In the prompt, run the following commands:
```
conda upgrade conda
conda upgrade --all
```
and answer yes when asked if you want to install the packages. The packages that come with the initial install tend to be out of date, so updating them now will prevent future errors from out of date software.<br>
**Note:** In the previous step, running conda upgrade conda should not be necessary because --all includes the conda package itself, but some users have encountered errors without it.

### Managing Packages
Once you have Anaconda installed, managing packages is fairly straightforward. To install a package, type `conda install package_name` in your terminal. For example, to install numpy, type `conda install numpy`.<br>
You can install multiple packages at the same time. Something like `conda install numpy scipy pandas` will install all those packages simultaneously. It's also possible to specify which version of a package you want by adding the version number such as `conda install numpy=1.10`.<br>
Conda also automatically installs dependencies for you. For example `scipy` depends on `numpy`, it uses and requires `numpy`. If you install just `scipy (conda install scipy)`, Conda will also install numpy if it isn't already installed.<br>
Most of the commands are pretty intuitive. To uninstall, use `conda remove package_name`. To update a package `conda update package_name`. If you want to update all packages in an environment, which is often useful, use `conda update --all`. And finally, to list installed packages, it's `conda list` which you've seen before.

### Managing Environments
As I mentioned before, conda can be used to create environments to isolate your projects. To create an environment, use `conda create -n env_name list of packages` in your terminal. Here `-n env_name` sets the name of your environment (`-n` for name) and list of packages is the list of packages you want installed in the environment. For example, to create an environment named `my_env` and install `numpy` in it, type `conda create -n my_env numpy`.<br>
When creating an environment, you can specify which version of Python to install in the environment. This is useful when you're working with code in both Python 2.x and Python 3.x. To create an environment with a specific Python version, do something like `conda create -n py3 python=3` or `conda create -n py2 python=2`. These commands will install the most recent version of Python 3 and 2, respectively. To install a specific version, use `conda create -n py python=3.3` for Python 3.3.

#### Entering an environment
Once you have an environment created, use `source activate my_env` to enter it on OSX/Linux. On Windows, use `activate my_env`.<br>
When you're in the environment, you'll see the environment name in the terminal prompt. Something like `(my_env)`. The environment has only a few packages installed by default, plus the ones you installed when creating it. You can check this out with `conda list`. Installing packages in the environment is the same as before: `conda install package_name`. Only this time, the specific packages you install will only be available when you're in the environment. To leave the environment, type `source deactivate` (on OSX/Linux). On Windows, use `deactivate`.

#### Listing Environments
If you forget what your environments are named (happens to me sometimes), use `conda env list` to list out all the environments you've created. You should see a list of environments, there will be an asterisk next to the environment you're currently in. The default environment, the environment used when you aren't in one, is called `root`.

#### Removing Environments
If there are environments you don't use anymore, `conda env remove -n env_name` will remove the specified environment (here, named `env_name`).

#### More to Learn
To learn more about conda and how it fits in the Python ecosystem, check out this article by Jake Vanderplas: [Conda myths and misconceptions](https://jakevdp.github.io/blog/2016/08/25/conda-myths-and-misconceptions/). And here's the [conda documentation](https://conda.io/docs/user-guide/tasks/index.html) you can reference later.


