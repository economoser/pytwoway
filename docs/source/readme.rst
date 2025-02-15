PyTwoWay
--------

.. image:: https://badge.fury.io/py/pytwoway.svg
    :target: https://badge.fury.io/py/pytwoway

.. image:: https://anaconda.org/tlamadon/pytwoway/badges/version.svg
    :target: https://anaconda.org/tlamadon/pytwoway

.. image:: https://anaconda.org/tlamadon/pytwoway/badges/platforms.svg
    :target: https://anaconda.org/tlamadon/pytwoway

.. image:: https://circleci.com/gh/tlamadon/pytwoway/tree/master.svg?style=shield
    :target: https://circleci.com/gh/tlamadon/pytwoway/tree/master

.. image:: https://img.shields.io/badge/doc-latest-blue
    :target: https://tlamadon.github.io/pytwoway/

.. image:: https://badgen.net/badge//gh/pytwoway?icon=github
    :target: https://github.com/tlamadon/pytwoway

`PyTwoWay` is the Python package associated with the following paper:

"`How Much Should we Trust Estimates of Firm Effects and Worker Sorting? <https://www.nber.org/system/files/working_papers/w27368/w27368.pdf>`_" 
by Stéphane Bonhomme, Kerstin Holzheu, Thibaut Lamadon, Elena Manresa, Magne Mogstad, and Bradley Setzler.  
No. w27368. National Bureau of Economic Research, 2020.

The package provides implementations for a series of estimators for models with two sided heterogeneity:

1. two way fixed effect estimator as proposed by Abowd Kramarz and Margolis
2. homoskedastic bias correction as in Andrews et al
3. heteroskedastic correction as in KSS
4. a group fixed estimator as in BLM
5. a group correlated random effect as presented in the main paper

.. |binder| image:: https://mybinder.org/badge_logo.svg 
    :target: https://mybinder.org/v2/gh/tlamadon/pytwoway/HEAD?filepath=docs%2Fnotebooks%2Fpytwoway_example.ipynb

If you want to give it a try, you can start the example notebook here: |binder|. This starts a fully interactive notebook with a simple example that generates data and runs the estimators.

The code is relatively efficient. Solving large sparse linear models relies on `PyAMG <https://github.com/pyamg/pyamg>`_. This is the code we use to estimate the different decompositions on US data. Data cleaning is handled by `BipartitePandas <https://github.com/tlamadon/bipartitepandas/>`_.

The package provides a Python interface as well as an intuitive command line interface. Installation is handled by `pip` or `Conda` (TBD). The source of the package is available on GitHub at `PyTwoWay <https://github.com/tlamadon/pytwoway>`_. The online documentation is hosted  `here <https://tlamadon.github.io/pytwoway/>`_.

Quick Start
-----------

To install via pip, from the command line run::

    pip install pytwoway


To run PyTwoWay via the command line interface, from the command line run::

    pytw --my-config config.txt --fe --cre


Example config.txt::

    data = file.csv
    filetype = csv
    col_dict = "{'i': 'your_workerid_col', 'j': 'your_firmid_col', 'y': 'your_compensation_col', 't': 'your_year_col'}"

Authors
-------

Thibaut Lamadon,
Assistant Professor in Economics, University of Chicago,
lamadon@uchicago.edu


Adam A. Oppenheimer,
Research Professional, University of Chicago,
oppenheimer@uchicago.edu

Citation
--------

Please use following citation to cite PyTwoWay in academic publications:

Bibtex entry::

  @techreport{bhlmms2020,
    title={How Much Should We Trust Estimates of Firm Effects and Worker Sorting?},
    author={Bonhomme, St{\'e}phane and Holzheu, Kerstin and Lamadon, Thibaut and Manresa, Elena and Mogstad, Magne and Setzler, Bradley},
    year={2020},
    institution={National Bureau of Economic Research}
  }


Development
-----------

If you want to contribute to the package, the easiest
way is to use poetry to set up a local environment::

    poetry install
    poetry run python -m pytest

To push the package to PiP, increase the version number in the `pyproject.toml` file and then::

    poetry build
    poetry publish

Finally to build the package for conda and upload it::

    conda skeleton pypi pytwoway
    conda config --set anaconda_upload yes
    conda-build pytwoway -c tlamadon --output-folder pytwoway
