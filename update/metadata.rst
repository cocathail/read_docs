.. _updating-metadata:

=========================
Updating Metadata Objects
=========================

Metadata objects can be updated using either :doc:`Interactive Webin </submit/general-guide/interactive>` or our :doc:`Programmatic interface </submit/general-guide/programmatic>`.

.. warning::

   Not all attributes of objects can be updated, and any controlled vocabularies apply equally to updates
   as they do to the original submission.

The metadata object types that can be updated include studies, samples, experiments, and runs.
Note that the raw read file content (i.e. the submitted sequence data files) cannot be changed through this route;
only the associated metadata records are modifiable.

.. toctree::
   :maxdepth: 1

   metadata/interactive
   metadata/programmatic-study
   metadata/programmatic-sample
   metadata/programmatic-read
