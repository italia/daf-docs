DAF-DOC
=========

Welcome to the official documentation of the [DAF](https://developers.italia.it/it/daf/) project. The documentation is made using [readthedocs.io](https://readthedocs.org/).

Local Setup
-----------

To run the server on you local machine you need have a working python interpreter or you can use [Anaconda](https://www.anaconda.com).

### Anaconda Environment Setup

```bash

$ conda env create --name=daf-doc

$ source activate DAF-DOC

$ conda install sphinx sphinx-autobuild
```

### Run the website locally

To run the website locally

```bash
$ sphinx-autobuild . _build/html
```
