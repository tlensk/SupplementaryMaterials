# SupplementaryMaterials

Tatiana Lenskaia (lensk010@umn.edu) and Daniel Boley (boley@umn.edu)

High-throughput Computational Method to Evaluate Potential Host Range for Bacterial Viruses

LICENSE

## Part I. Computing intersection matrices

### Code:
#### CompIntM.py
The script computes the intersection ratios between viruses and prokaryotes. It outpus the results as two intersection matrices (one for forward and another one for the reverse direction). Each row of an intersection matrix except for the first one represents a prokaryote sequence. The first row contains information about the screening window size and viral identifiers for columns. Each column (except for the first one) represent a viral sequence. The first column contains information about the screening window size and prokaryotic identifiers for rows. Thus, each cell of an intersection matrix (except for the cells in the first row and the first column) contains a value of the intersection ratio between the corresponding prokaryote (row index) and virus (column index) sequences.

One can run the script on the test toy example of 10 viruses and 7 prokayotes using the following command:

`python3    CompIntM.py    40    Test_10viruses.fasta    Test_7prokaryotes.fasta     Test`

To run the script on data keep the order of the input parameters printed after the script name as follows:
1. screening window size
2. name of a multi-fasta file with viral sequences
3. name of a multi-fasta file with prokaryotic sequences
4. prefix for the output files generated by the script 

The script terminates execution and throws the corresponding error message if files with the specified prefix already exist.

### Input data for a test example:
#### Test_10viruses.fasta

This is a multi-fasta file that contains viral sequences for the test example.

#### Test_7prokaryotes.fasta

This is a multi-fasta file that contains 7 prokaryote sequences for the test example.

### Datasets description:
#### Test_10viruses_info.txt
This is a tab-delimited file that contains a brief description of viral sequences stored in 10viruses.fasta in the following format: VirusID  VirusName
#### Test_7prokaryotes_info.txt
This is a tab-delimited file that contains a brief description of the prokaryote sequences stored in 7prokaryotes.fasta in the following format: RepliconID RepliconName

### Files with the description for viruses and bacteria in Dataset1 and Dataset2:
#### Dataset1_820phages_info.txt
#### Dataset1_2699bacteria_info.txt
#### Dataset2_1962phages_info.txt
#### Dataset2_3244replicons_info.txt


### Results for Dataset1 and Dataset2:
These comma-separated files contain intersection matrices for the two datasets. 
Each file name includes a label for the direction of coomputing (F = forward and R = Reverse complement).
#### Dataset1_Matrix40_F.csv
#### Dataset1_Matrix40_R.csv
#### Dataset2_Matrix40_F.csv
#### Dataset2_Matrix40_R.csv


## PartII. Predicting hosts

### Code:
#### PredictHost.py
The script makes and validates the host prediction based on the provided information about annotated host and taxonomy for phages and prokaryotes needed in addition to the intersection matrices computed by CompIntM.py in PartI.

One can run the script on the test toy example of 10 viruses and 7 prokayotes using the following command:

`python3    PredictHost.py    Test_10viruses_taxa.txt Test_7prokaryotes_taxa.txt test_Matrix_F.csv test_Matrix_R.csv test`

To run the script on data keep the order of the input parameters printed after the script name as follows:
1. name of a file that contains information about the annotated host and taxonomy for viruses
2. name of a file that contains information about taxonomy for prokaryotes
3. forward intersection matrix
4. reverse intersection matrix
5. prefix for the output files generated by the script

### Input data for a test example:
#### Test_10viruses_taxa.txt
This tab-delimited file contains additional information about each virus in the following format:
ID	Name	Taxa	Annotated_host

The annotated host column should include at least a species name (e.g., Escherichia coli) for the annotated host (a strain name is allowed but not required). For the host species name, the use of binomial nomenclature is recommended. If the information about several hosts is given the hosts should be separated by a semicolon.

#### Test_7prokaryotes_taxa.txt
This tab-delimited file contains additional information about each prokaryote in the following format:
ID	Name	Taxa	Species

The species column should include binomial nomenclature for a prokaryote species

### Results for Dataset1 and Dataset2:
These tab-separated files contain information about the corresponding category for each virus shown in Table3 for Dataset1 and Dataset2 separately. For more details about virus categories, see Table3.csv.
#### Dataset1_820phages_predict.txt
#### Dataset2_1962phages_predict.txt

