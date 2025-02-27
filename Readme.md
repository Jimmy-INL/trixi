[![DOI](https://zenodo.org/badge/134823632.svg)](https://zenodo.org/badge/latestdoi/134823632)
[![PyPI version](https://badge.fury.io/py/trixi.svg)](https://badge.fury.io/py/trixi)
[![Build Status](https://img.shields.io/travis/MIC-DKFZ/trixi.svg)](https://travis-ci.org/MIC-DKFZ/trixi)
[![Documentation Status](https://readthedocs.org/projects/trixi/badge/?version=develop)](https://trixi.readthedocs.io/en/develop/?badge=develop)
[![Downloads](https://pepy.tech/badge/trixi)](https://pepy.tech/project/trixi)
[![GitHub](https://img.shields.io/pypi/l/trixi.svg)](https://github.com/MIC-DKFZ/trixi/blob/master/LICENSE)
<p align="center">
    <img src="https://raw.githubusercontent.com/MIC-DKFZ/trixi/master/doc/_static/logo/trixi-small.png">
</p>

Finally get some structure into your machine learning experiments.
**trixi** (Training & Retrospective Insights eXperiment Infrastructure) is a tool that helps you configure, log and visualize your experiments in a reproducible fashion.

* [Features](#features)
* [Installation](#installation)
* [Documentation](#documentation) ([trixi.rtfd.io](https://trixi.readthedocs.io/en/develop/))
* [Examples](#examples)
* [How to Cite](#how-to-cite)

# Contribute

We're always grateful for contributions, even small ones! We're PhD students and this is just a side project, so there will always be something to improve.

The best way is to create pull requests on Github. Fork the repository and work either directly on develop or create a feature branch, whichever you like best. Then go to "Pull requests" on our Github, select "New pull request" and "compare across forks". Select our develop as base and your work as head/compare.

We currently don't support the full Github workflow, because we have to mirror from our working repository to Github, but don't worry, we can export the pull requests and apply them so that your contribution will still appear on Github :)

# Features

**trixi** consists of three parts:
* Logging API<br>
    *Log whatever data you like in whatever way you like to whatever backend you like.*

* Experiment Infrastructure<br>
    *Standardize your experiment, let the framework do all the inconvenient stuff, and simply start, resume,
    change and finetune all your experiments*.

* Experiment Browser <br>
    *Compare, combine and visually inspect the results of your experiments*.

An implementation diagram is given [here](https://trixi.readthedocs.io/en/latest/class_diagram.html).

### Logging API

The Logging API provides a standardized way for logging results to different backends.
The Logging API supports
(among others):
* Values
* Text
* Plots (Bar, Line, Scatter, Piechart, ...)
* Images (Single, Grid)

And offers different Backends, e.g. :
* Visdom ([visdom-loggers](https://trixi.readthedocs.io/en/latest/_api/trixi.logger.html#module-trixi.logger.visdom))
* Tensorboard ([tensorboard-loggers](https://trixi.readthedocs.io/en/latest/_api/trixi.logger.html#module-trixi.logger.tensorboard))
* Matplotlib / Seaborn ([plt-loggers](https://trixi.readthedocs.io/en/latest/_api/trixi.logger.html#module-trixi.logger.plt))
* Local Disk ([file-loggers](https://trixi.readthedocs.io/en/latest/_api/trixi.logger.html#module-trixi.logger.file))
* Telegram & Slack ([message-loggers](https://trixi.readthedocs.io/en/latest/_api/trixi.logger.html#module-trixi.logger.message))

And an [experiment-logger](https://trixi.readthedocs.io/en/latest/_api/trixi.logger.html#module-trixi.logger.experiment) for logging your experiments, which uses a file logger to automatically create a structured directory and allows
storing of config, results, plots, dict, array, images, etc. That way your experiments will always have the same structure on disk.

Here are some examples:

* [Visdom](https://github.com/facebookresearch/visdom):<br>
<img src="https://camo.githubusercontent.com/d69475a01f9f327fc42931a21df8134d1fbdfc19/68747470733a2f2f6c68332e676f6f676c6575736572636f6e74656e742e636f6d2f2d62714839555843772d42452f574c3255736472726241492f41414141414141416e59632f656d727877436d6e7257345f434c54797955747442305359524a2d693443436951434c63422f73302f53637265656e2b53686f742b323031372d30332d30362b61742b31302e35312e30322b414d2e706e67253232766973646f6d5f626967253232" alt="visdom-logger" width="300"/>

* Files:<br>
<img src="https://raw.githubusercontent.com/MIC-DKFZ/trixi/master/doc/_static/trixi_file.png" alt="file-logger" height="200"/>

* Telegram:<br>
<img src="https://raw.githubusercontent.com/MIC-DKFZ/trixi/master/doc/_static/trixi_telegram.png" alt="telegram-logger" width="150"/>


### Experiment Infrastructure

The [Experiment Infrastructure](https://trixi.readthedocs.io/en/latest/_api/trixi.experiment.html) provides a unified way to configure, run, store and evaluate your results.
It gives you an experiment interface, for which you can implement the training, validation and testing.
Furthermore it automatically provides you with easy access to the Logging API and stores your config as well as the
results for easy evaluation and reproduction. There is an abstract [Experiment](https://trixi.readthedocs.io/en/latest/_api/trixi.experiment.html#trixi.experiment.experiment.Experiment) class and a [PytorchExperiment](https://trixi.readthedocs.io/en/latest/_api/trixi.experiment.html#trixi.experiment.pytorchexperiment.PytorchExperiment) with many convenience features.

<img src="https://raw.githubusercontent.com/MIC-DKFZ/trixi/master/doc/_static/trixi_exp2.png" alt="exp-train" height="300"/><img src="https://raw.githubusercontent.com/MIC-DKFZ/trixi/master/doc/_static/trixi_exp1.png" alt="exp-test" height="300"/>

For more info, visit the [Documentation](https://trixi.readthedocs.io/en/latest/_api/trixi.experiment.html).

### Experiment Browser

**(We're currently remaking this from scratch, expect major improvements :))**

The Experiment Browser offers a complete overview of experiments along with all config parameters and results.
It also allows to combine and/or compare different experiments, giving you an interactive comparison highlighting differences in the configs and a detailed view of all images,
plots, results and logs of each experiment, with live plots and more.
![trixi browser](https://raw.githubusercontent.com/MIC-DKFZ/trixi/master/doc/_static/trixi_browser.gif)

# Installation

Install **trixi**:
```
pip install trixi
```


Or to always get the newest version you can install **trixi** directly via git:
```
git clone https://github.com/MIC-DKFZ/trixi.git
cd trixi
pip install -e .
```

# Documentation

The docs can be found here: [trixi.rtfd.io](https://trixi.readthedocs.io/en/latest/)

Or you can build your own docs using Sphinx.

#### Sphinx Setup

Install Sphinx (fixed to 1.7.0 for now because of issues with Readthedocs):  
`pip install sphinx==1.7.0`

Generate HTML:  
`path/to/PROJECT/doc$ make html`

index.html will be at:  
`path/to/PROJECT/doc/_build/html/index.html`

#### Notes
* Rerun `make html` each time existing modules are updated (this will automatically call sphinx-apidoc)
* Do not forget indent or blank lines
* Code with no classes or functions is not automatically captured using apidoc


#### Example Documentation

We use Google style docstrings:

	def show_image(self, image, name, file_format=".png", **kwargs):
        """
        This function shows an image.

        Args:
            image(np.ndarray): image to be shown
            name(str): image title
        """


# Examples

Examples can be found here for:
* [Visdom-Logger](https://github.com/MIC-DKFZ/trixi/blob/master/examples/numpy_visdom_logger_example.ipynb)
* [Experiment-Logger](https://github.com/MIC-DKFZ/trixi/blob/master/examples/pytorch_example.ipynb)
* [Experiment Infrastructure](https://github.com/MIC-DKFZ/trixi/blob/master/examples/pytorch_experiment.ipynb) (with a
 simple MNIST Experiment example and resuming and comparison of different hyperparameters)
* [U-Net Example](https://github.com/MIC-DKFZ/basic_unet_example)

# How to Cite

If you use **trixi** in your project, we'd appreciate a citation, for example like this

    @misc{trixi2017,
      author = {Zimmerer, David and Petersen, Jens and Köhler, Gregor and Wasserthal, Jakob and Adler, Tim and Wirkert, Sebastian and Ross, Tobias},
      title = {trixi - Training and Retrospective Insight eXperiment Infrastructure},
      year = {2017},
      publisher = {GitHub},
      journal = {GitHub Repository},
      howpublished = {\url{https://github.com/MIC-DKFZ/trixi}},
      doi = {10.5281/zenodo.1345136}
    }
