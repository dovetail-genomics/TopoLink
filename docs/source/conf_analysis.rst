.. _CA:

Conformation Analysis
=====================

There are many open-source tools available that enable researchers to perform conformation analyses on contact matrices. We aim to hightlight the tools and commands we use here at Cantata Bio call features. This is not a comprenisve list, nor do we own or manage any of the tools listed below. Please refer to their source document pages for more information or for help in trouble shooting the use of these tools. 
For each analysis performed below we provide, a link to the tool repo, the input file, the example command, and an example output for you to check your results against.

Example input files (.mcool and .hic files)
+++++++++++++++++++++++++++++++++++++++++++

  - Example :download:`mcool <https://s3.amazonaws.com/dovetail.pub/TopoLink/mcool/TopoLink.mcool>` file
  - Example :download:`hic <https://s3.amazonaws.com/dovetail.pub/TopoLink/hic/TopoLink.hic>` file


A/B Compartments
++++++++++++++++

**Recommended Software**
  
  - Fanc-C https://fan-c.readthedocs.io/en/latest/

**Example Command**

.. code-block:: console

   	fanc compartments -f -v TopoLink_eigen_64kb.bed -d TopoLink_AB_64kb.bed -g hg38.fa TopoLink.mcool@64000 TopoLink_64kb.ab


**Example Output(s)**

  - Example :download:`AB compartments <https://s3.amazonaws.com/dovetail.pub/TopoLink/AB/TopoLink_64kb.ab>` file
  - Example :download:`AB compartments bed <https://s3.amazonaws.com/dovetail.pub/TopoLink/AB/TopoLink_AB_64kb.bed>` file
  - Example :download:`AB Eigenvector <https://s3.amazonaws.com/dovetail.pub/TopoLink/AB/TopoLink_eigen_64kb.bed>` file


Topologically Associated Domains
++++++++++++++++++++++++++++++++

**Recommended Software**

  - Juicer Arrowhead https://github.com/aidenlab/juicer 

**Example Command**

.. code-block:: console

   java -jar -Xmx48000m  -Djava.awt.headless=true -jar juicer_tools.jar arrowhead --threads 16 -k KR -m 2000 -r 10000 TopoLink.hic TAD_calls
   java -jar -Xmx48000m  -Djava.awt.headless=true -jar juicer_tools.jar arrowhead --threads 16 -k KR -m 2000 -r 5000 TopoLink.hic TAD_calls


**Example Output(s)**

  - Example :download:`10kb TADs <https://s3.amazonaws.com/dovetail.pub/TopoLink/TADs/TopoLink_10000_blocks.bedpe>` file
  - Example :download:`5kb TADs <https://s3.amazonaws.com/dovetail.pub/TopoLink/TADs/TopoLink_5000_blocks.bedpe>` file


Chromatin Loops
+++++++++++++++

**Recommended Software**

  - Mustache https://github.com/ay-lab/mustache 

**Example Command**

.. code-block:: console

   mustache -p 48 -f TopoLink.mcool -r 16000 -o TopoLink_16000kb_loops.tsv
   mustache -p 48 -f TopoLink.mcool -r 4000 -o TopoLink_4000kb_loops.tsv

**Example Output(s)**

  - Example :download:`16kb Loops <https://s3.amazonaws.com/dovetail.pub/TopoLink/loops/TopoLink_16000kb_loops.tsv>` file
  - Example :download:`4kb Loops <https://s3.amazonaws.com/dovetail.pub/TopoLink/loops/TopoLink_4000kb_loops.tsv>` file
