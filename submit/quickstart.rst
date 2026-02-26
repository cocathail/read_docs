.. _quickstart:

============================
First Submission: Where To Start
============================

If you are new to ENA, this page will walk you through everything you need to
know before you begin, and point you to the right place for your data type.

.. note::

   If you get stuck at any point, the ENA helpdesk is available at
   `https://www.ebi.ac.uk/ena/browser/support <https://www.ebi.ac.uk/ena/browser/support>`_.


Step 1: Create a Webin Account
===============================

All submissions go through a single submission account called a **Webin account**.
If you do not have one yet, go to the
`Webin Portal <https://www.ebi.ac.uk/ena/submit/webin/login>`_ and click **Register**.

You will need to provide your institution name (called the "centre name") and at
least one contact person. The centre name is applied to all submissions you make
from this account, so make sure it is correct before you submit anything.

See :doc:`Register a Submission Account </submit/general-guide/registration>` for full details.


Step 2: Understand the Submission Order
========================================

Every submission to ENA follows the same order, regardless of what you are submitting:

1. **Register a study** — groups all your data together and controls the release date.
2. **Register one or more samples** — describe the biological material that was sequenced.
3. **Submit your data** — reads, assemblies, or sequences, linked to the study and samples above.

You must complete these steps in order. You cannot submit data without first having
a study and at least one sample to link it to.

.. tip::

   A study can hold many samples and many data files. If your project involves
   multiple experiments or samples, you only need to register the study once.


Step 3: Choose Your Path
=========================

Pick the option below that best describes what you want to submit.

----

I have raw sequencing reads
----------------------------

This is the most common submission type. Raw reads are the unprocessed output
from a sequencing instrument (e.g. Illumina FASTQ files, PacBio BAM files).

**What you will need:**

- A study (your project)
- One sample per sequenced specimen or environmental collection
- Your read files (FASTQ, BAM, or CRAM)

**Steps:**

1. :doc:`Register a study </submit/study>`
2. :doc:`Register your samples </submit/samples>`
3. :doc:`Submit your raw reads </submit/reads>`

.. tip::

   The easiest way to submit reads is through the
   :doc:`Webin Portal interactive interface </submit/general-guide/interactive>`.
   If you have many files or need pre-submission validation, use
   :doc:`Webin-CLI </submit/general-guide/webin-cli>` instead.

----

I have an assembled genome
---------------------------

A genome assembly is a reconstructed genome sequence produced by assembling raw reads.
This includes isolate genomes, metagenome-assembled genomes (MAGs), and transcriptome assemblies.

**What you will need:**

- A study
- One sample per assembled organism
- Your assembly files (FASTA or annotated EMBL flat file)

.. tip::

   It is strongly recommended to also submit the raw reads the assembly was produced
   from, and to link them to the same sample. This makes your data more reproducible
   and is required for some assembly types.

**Steps:**

1. :doc:`Register a study </submit/study>`
2. :doc:`Register your samples </submit/samples>`
3. *(Recommended)* :doc:`Submit your raw reads </submit/reads>`
4. :doc:`Submit your assembly </submit/assembly>`

Genome assemblies can only be submitted using :doc:`Webin-CLI </submit/general-guide/webin-cli>`.

----

I have targeted sequences (e.g. 16S, COI, ITS)
------------------------------------------------

Targeted sequences are short, assembled and annotated sequences representing a
specific gene or region of interest. Examples include 16S rRNA, COI barcodes,
and ITS sequences.

.. note::

   This route is for sets of individual annotated sequences only — typically a few
   to a few hundred. If you have a whole genome assembly, see the section above.

**What you will need:**

- A study
- Your sequences in EMBL flat file format, or a completed annotation checklist spreadsheet

**Steps:**

1. :doc:`Register a study </submit/study>`
2. *(Optional)* :doc:`Register samples </submit/samples>` — not mandatory but recommended
3. :doc:`Submit your targeted sequences </submit/sequence>`

----

I have metagenomic data
------------------------

Metagenomic submissions involve data sampled from an entire environment rather
than a single organism, and follow a specific assembly hierarchy.

**Steps:**

1. :doc:`Register a study </submit/study>`
2. Register an environmental (biome-level) sample — see :ref:`biome-level-taxonomy`
3. :doc:`Submit your raw reads </submit/reads>`
4. Submit your assemblies following the
   :doc:`metagenome assembly guidelines </submit/assembly/metagenome>`

See also the :doc:`metagenome submission FAQ </faq/metagenomes>` for common questions.

----


What Happens After Submission?
===============================

Once submitted, ENA will assign **accession numbers** to your study, samples, and
data. Make a note of these — they are the permanent identifiers for your submission
and are what you will cite in publications.

Your data will be held privately until the study release date (the default is two
months after submission). You can change this date at any time before the data goes
public. See :doc:`Data Release Policies </faq/release>` for more information.

See :doc:`Accession Numbers </submit/general-guide/accessions>` for a full explanation
of the different accession formats.
