PathoScope 2.0
==========

### Pathoscope: Species identification and strain attribution with unassembled sequencing data


#### Introduction:
Pathoscope 2.0 consists of four core and two optional analysis modules for sequencing-based metagenomic profiling. The PathoLib module extracts genome reference libraries (target or host/filter) from all available sequences in the NCBI Nucleotide database that belong to a user-defined taxonomic clade. The PathoMap module aligns the reads to the target reference library and removes any reads that have sequence similarity with the host or filter genomes. PathoID resolves read ambiguity, identifies which of the target genomes are present in the sample and estimates the proportions of reads originating from each genome. PathoReport provides two report files: 1) a summary report (.tsv) that contains the numbers and proportions of reads aligned to each genome identified in the sample, and 2) detailed report (.xml) including read coverage, read assignments, and contiguous sequences generated by combining the reads. The PathoDB is an optional module that provides additional annotation (organism taxonomic lineage, gene loci, protein products) for all sequences identified in the sample. The PathoQC module can be used to preprocess the reads prior to alignment with PathoMap.


#### 1. Running

1.1 Prerequisite: Need to have python 2.7.3 or later version installed and add python to your PATH variable (Usually already done as part of python installation)
    
1.2 Change directory to where you downloaded the code 

1.3 Simply run `python pathoscope/pathoscope.py -h` for top level usage information.

- Run `python pathoscope/pathoscope.py LIB -h` for detailed usage information to run patholib.
- Run `python pathoscope/pathoscope.py MAP -h` for detailed usage information to run pathomap.
- Run `python pathoscope/pathoscope.py ID -h` for detailed usage information to run pathoid.
- Run `python pathoscope/pathoscope.py REP -h` for detailed usage information to run pathoreport.

1.4 There are also some unit tests for testing the validity of the functions. 

- Change directory to `pathoscope/pathomap/bowtie2wrapper/unittest` and simply run `python testBowtie2Wrap.py`.
- Change directory to `pathoscope/pathoid/unittest` and simply run `python testPathoID.py`.


####  2 Output TSV file format:

At the top of the file in the first row, there are two fields called "Total Number of Aligned Reads" and "Total Number of Mapped Genomes". They represent the total number of reads that are aligned and the total number of genomes to which those reads align from the given alignment file.

Columns in the TSV file:

1. Genome:  
This is the name of the genome found in the alignment file.
2. Initial Guess:  
This represent the percentage of reads that are mapped to the genome in Column 1 (reads aligning to multiple genomes are assigned proportionally) before pathoscope reassignment is performed.
3. Initial Best Hit:  
This represent the percentage of reads that are mapped to the genome in Column 1 after assigning each read uniquely to the genome with the highest score and before pathoscope reassignment is performed.
4. Initial Best Hit Read Numbers:  
This represent the number of best hit reads that are mapped to the genome in Column 1 (may include a fraction when a read is aligned to multiple top hit genomes with the same highest score) and before pathoscope reassignment is performed.
5. Final Guess:  
This represent the percentage of reads that are mapped to the genome in Column 1 (reads aligning to multiple genomes are assigned proportionally) after pathoscope reassignment is performed.
6. Final Best Hit:  
This represent the percentage of reads that are mapped to the genome in Column 1 after assigning each read uniquely to the genome with the highest score and after pathoscope reassignment is performed.
7. Final Best Hit Read Numbers:  
This represent the number of best hit reads that are mapped to the genome in Column 1 (may include a fraction when a read is aligned to multiple top hit genomes with the same highest score) and after pathoscope reassignment is performed.
8. Initial 50%-100% Hit:  
This represent the percentage of reads that are mapped to the genome in Column 1 with an alignment hit score of 50%-100% to this genome and before pathoscope reassignment is performed.
9. Initial 1%-50% Hit:  
This represent the percentage of reads that are mapped to the genome in Column 1 with an alignment hit score of 1%-50% to this genome and before pathoscope reassignment is performed.
10. Final 50%-100% Hit:  
This represent the percentage of reads that are mapped to the genome in Column 1 with an alignment hit score of 50%-100% to this genome and after pathoscope reassignment is performed.
11. Final 1%-50% Hit:  
This represent the percentage of reads that are mapped to the genome in Column 1 with an alignment hit score of 1%-50% to this genome and after pathoscope reassignment is performed.

####  3. License: GNU-GPL

This program is free software: you can redistribute it and/or modify it under the terms of the GNU General Public License as published by the Free Software Foundation, either version 3 of the License, or any later version.

This program is distributed in the hope that it will be useful, but WITHOUT ANY WARRANTY; without even the implied warranty of MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the GNU General Public License for more details.
    
You should have received a copy of the GNU General Public License along with this program.  If not, see <http://www.gnu.org/licenses/>.

####  5. Support and Contact

5.1 Pathoscope is developed at the JohnsonLab in Boston University.

W. Evan Johnson, Ph.D.  
Division of Computational Biomedicine  
Boston University School of Medicine  
72 E. Concord St., E-645  
Boston, MA 02118  

Developers:

Solaiappan Manimaran  
Changjin Hong
