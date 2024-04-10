.. image:: https://img.shields.io/badge/dmtn--290-lsst.io-brightgreen.svg
   :target: https://dmtn-290.lsst.io
.. image:: https://github.com/lsst-dm/dmtn-290/workflows/CI/badge.svg
   :target: https://github.com/lsst-dm/dmtn-290/actions/

##########################################################
Sasquatch: Rubin Observatory metrics and telemetry service
##########################################################

DMTN-290
========

At Rubin Observatory, we recently consolidated our high-frequency telemetry harness, which captures engineering facility data, with our metrics analysis system into a single unified service named Sasquatch. Within the LSST Science Pipelines, metrics are measured across various dimensions, such as instrument, detector, filter, exposure, dataset, and run, among others. With thousands of metrics measured during the 10-year survey, we will generate a high volume of time series data. Metrics and telemetry are both timestamped data, and to store and query this data efficiently we adopted InfluxDB, a specialized time series database. A crucial aspect of the architecture for capturing telemetry data is to ensure minimal data loss. This is achieved by deploying Kafka and InfluxDB on the Kubernetes platform. Sasquatch facilitates seamless real-time data access at the US Data Facility (USDF) through Kafka-based replication. Users access the data through Chronograf, an interface for time series visualization. They create alerts on the data using Kapacitor, and utilize the Rubin Science Platform's notebook environment for ad hoc analysis in Python. These tools have been extensively employed at Rubin during the ongoing System Integration Testing and Commissioning phase as  Rubin Observatory transitions into operations.

Links
=====

- Live drafts: https://dmtn-290.lsst.io
- GitHub: https://github.com/lsst-dm/dmtn-290

Build
=====

This repository includes lsst-texmf_ as a Git submodule.
Clone this repository::

    git clone --recurse-submodules https://github.com/lsst-dm/dmtn-290

Compile the PDF::

    make

Clean built files::

    make clean

Updating acronyms
-----------------

A table of the technote's acronyms and their definitions are maintained in the `acronyms.tex` file, which is committed as part of this repository.
To update the acronyms table in ``acronyms.tex``::

    make acronyms.tex

*Note: this command requires that this repository was cloned as a submodule.*

The acronyms discovery code scans the LaTeX source for probable acronyms.
You can ensure that certain strings aren't treated as acronyms by adding them to the `skipacronyms.txt <./skipacronyms.txt>`_ file.

The lsst-texmf_ repository centrally maintains definitions for LSST acronyms.
You can also add new acronym definitions, or override the definitions of acronyms, by editing the `myacronyms.txt <./myacronyms.txt>`_ file.

Updating lsst-texmf
-------------------

`lsst-texmf`_ includes BibTeX files, the ``lsstdoc`` class file, and acronym definitions, among other essential tooling for LSST's LaTeX documentation projects.
To update to a newer version of `lsst-texmf`_, you can update the submodule in this repository::

   git submodule update --init --recursive

Commit, then push, the updated submodule.

.. _lsst-texmf: https://github.com/lsst/lsst-texmf
