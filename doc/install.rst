.. install_:

*************************************************************
Installing and using the PyNAST command line application
*************************************************************

Required software
=================
PyNAST_ is built on the PyCogent_ package, and uses NCBI's BLAST_ software. You must have PyCogent_ 1.4.0 and BLAST_ 2.2.22 installed to run PyNAST_.

Optional software
=================
If you'd like to perform pairwise alignments using MUSCLE_, MAFFT_, or ClustalW_, you must have those programs installed on your machine and in your system path. Currently tested versions are MUSCLE_ v3.6, MAFFT v6.602b, and ClustalW 1.81.

Installation steps
==================
#. Download PyCogent_ 1.4.0 and its dependencies, Python_ 2.5.1 or greater (but less than Python 3.0) and NumPy 1.3.0 or greater.

#. Install BLAST_. Versions 2.2.16 through 2.2.21 have been tested extensively with PyNAST_, but other versions should work. (Note: we've had trouble with BLAST_ installed via package managers, so it may be best to download directly from NCBI and install per their instructions.)

#. From your command terminal on an OS X or Linux system, change to the directory where you wish to install PyNAST_. Checkout the latest version of PyNAST_ from the SVN repository with the command:
	::
      
		svn co https://pynast.svn.sourceforge.net/svnroot/pynast PyNAST
		
This will create a new folder in the current working directory called PyNAST_.

#. Add ``PyNAST/pynast`` to your ``$PYTHONPATH`` environment variable. Assuming you're using the bash shell, if you downloaded PyNAST_ to ``/home/hayduke/`` you can do this with the command:
	::
		
		export PYTHONPATH=/home/hayduke/PyNAST/:$PYTHONPATH

    For the best results, add the above line to the .bash_profile file in your home directory.

#. Change to the PyNAST/tests directory:
	::
		
		cd PyNAST/tests

#. Run the following commands:
	::
		
		python test_logger.py
		python test_util.py
	
      All tests should pass, unless you don't have MUSCLE_, MAFFT_, and/or ClustalW_ installed. These are optional external software packages, and you will get one test failure per missing software package. You can ignore test failures which indicate that these programs cannot be found.

#. If all tests pass, you can get the usage information for the command line version of PyNAST_ with the following command from the directory where you downloaded PyNAST_:
	::
		
		PyNAST/scripts/pynast -h

#. If you'd like to be able to call PyNAST_ from anywhere on your system, you have two (good) choices. To illustrate how to do this, let's assume that your PyNAST_ directory lives in ``/home/hayduke/``. You can either:

          * add /home/hayduke/PyNAST/scripts/ to your $PATH environment variable. Assuming you're using the bash shell, you can do this with the command:
			::
				
				export PATH=/home/hayduke/PyNAST/scripts/:$PATH
				
            For the best results, add the above line to the ``.bash_profile`` file in your home directory.

          * or, create a symbolic link from a directory in your system path (e.g. ``/usr/bin/``) to the pynast script:
			::
	
				ln -s /home/hayduke/PyNAST/scripts/pynast /usr/bin/pynast

Using the PyNAST command line application
=========================================

After installing the PyNAST_ software as described above, you should download the sample candidate sequences and template alignment. You can then apply the PyNAST_ command line tool as follows:
::
	
	pynast -i candidate_seqs_sample.fasta -t template_sample.fasta

This will result in three files being written to the current working directory: candidate_seqs_sample_pynast_aligned.fasta, candidate_seqs_sample_pynast_log.txt, and candidate_seqs_sample_pynast_fail.fasta, which correspond to the alignment, the run log, and the list of sequences which failed to align, respectively.

To get usage information for the PyNAST_ command line application run:
::
	
	pynast -h
	
	
.. _PyCogent: http://pycogent.sourceforge.net
.. _Python: http://www.python.org
.. _NumPy: http://numpy.scipy.org/
.. _MUSCLE: http://www.drive5.com/muscle/
.. _PyNAST: http://pynast.sourceforge.net
.. _ClustalW: http://www.ebi.ac.uk/Tools/clustalw2/index.html
.. _BLAST: ftp://ftp.ncbi.nlm.nih.gov/blast/executables/LATEST/
.. _MAFFT: http://align.bmr.kyushu-u.ac.jp/mafft/online/server/