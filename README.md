# **PDB-BRE**

PDB-BRE: a ligand-protein interaction binding residue extractor based on Protein Data Bank



## **1 Command line tools**

This page describes the command line of the four executable files (PDB-BRE-InterPair, PDB-BRE-DonSeqLabel, PDB-BRE-ProSeqLabel and PDB-BRE-PPISeqLabel) in the PDB-BRE package and their corresponding options.

### **1.1 PDB-BRE-InterPair option description**

The executable file PDB-BRE-InterPair is used to extract specific interaction pairs and binding residues from PDB file of the complex.

#### 1.1.1 Required Options of PDB-BRE-InterPair

- `-i, --Input_ComplexID`

  The structural ID(s) in the PDB database used for analysis, separated by commas. 

- `-f,  --Input_FilePath`

  The input .txt file for analysis that contains the structure ID(s) in the PDB database, separated by commas.

- `-t, --Type {protein, peptide, DNA, RNA, DNA&RNA hybrid, ligand}`

  The type of interaction in the analyzed PDB structure. For example: peptide-protein interaction (peptide).

- `-s, --Distance_Threshold`

  The distance threshold (in angstroms) used to determine whether there is an interaction. Default is 5.0.

#### 1.1.2 Optional Options of PDB-BRE-InterPair

- `-p, --PDB_Download_DirPath`

  The storage path of the downloaded PDB files. Default is ./PDBFile.

- `-w, --Output_Form {file, print}`

  The output form of the result ('file' or 'print'). Default is 'file'.

- `-o, --Output_DirPath`

  The storage path of the output results. Default is './Result'.

- `-c, --Cutoff_Value`

  The cut-off value of protein based on sequence length.

- `-m, --Distance_Mode {Any, CA}`

  The calculation method of residue interaction.  For the peptide-protein interaction (-t 'peptide'), the default is 'Any' (minimum atomic distance between two residues), optional is 'CA' (distance between two residue CA atoms). For other interaction types, only the default 'Any' is supported for analysis.

- `-n, --CPU_Num`

  The number of processes used by multiple processes. The default is half of the actual number of device CPU (rounded up).

- `-r, --DeRedundant`

  Remove redundant interaction pairs (where the sequence of residues and binding sites are identical in both pairs). The default is True. Besides, this parameter is invalid when Type is 'ligand' or Output_Form is 'print'.

- `-b, --Verbose`

  Output redundant progress information. Default is False. If set to True, the progress bar of parallel analysis is automatically turned off.

- `-d, --PDB_Delete`

  Delete automatically downloaded PDB files. Default is False.

- `-v, --Version`

  Display the version information of the software and exit. Default is False.

- `-h, --help`

  Show this help message and exit.


### **1.2 PDB-BRE-DonSeqLabel option description**

The executable file PDB-BRE-DonSeqLabel is used to extract the donor sequence labels from the output file of PDB-BRE-InterPair. The types of donors supported by the executable file include: _**peptides**_, _**DNA**_, _**RNA**_ and _**DNA&RNA hybrid**_.

#### 1.2.1 Required Options of PDB-BRE-DonSeqLabel

- `-i, --InterPair_FilePath`

  The input .csv file containing interaction pairs (the output file of PDB-BRE-InterPair). 

- `-p,  --PDB_DirPath`

  The storage path of the downloaded PDB files. Default is ./PDBFile.

- `-t, --Type {protein, peptide, DNA, RNA, DNA&RNA hybrid, ligand}`

  Donor type. The default is 'peptide', optional 'RNA',' DNA' or 'DNA&RNA hybrid'.

#### 1.2.2 Optional Options of PDB-BRE-DonSeqLabel

- `-o, --DonorSeqLabel_FilePath`

  Output file path. Automatically set according to InterPair_FilePath by default.

- `-m, --ModRes_Change {fasta, pdb}`

  Treatment of modified binding residues. The default is 'fasta', indicating that the sequence residues are consistent with the fasta file. Optional 'pdb', means that the sequence residue is consistent with the pdb file.

- `-v, --Version`

  Display the version information of the software and exit. Default is False.

- `-h, --help`

  Show this help message and exit.


### **1.3 PDB-BRE-ProSeqLabel option description**

The executable file PDB-BRE-ProSeqLabel is used to extract the protein sequence labels from the output file of PDB-BRE-InterPair. When using the executable file to extract protein sequence labels, the donor type in the PDB-BRE-InterPair output file should be one of _**peptides**_, _**DNA**_, _**RNA**_ or _**DNA&RNA hybrid**_.

#### 1.3.1 Required Options of PDB-BRE-ProSeqLabel

- `-i, --InterPair_FilePath`

  The input .csv file containing interaction pairs (the output file of PDB-BRE-InterPair). 

- `-p,  --PDB_DirPath`

  The storage path of the downloaded PDB files. Default is ./PDBFile.

#### 1.3.2 Optional Options of PDB-BRE-ProSeqLabel

- `-u,  --Sequence_FilePath`

  The file path of the uniprot database used during the protein chain mapping process. The default is the uniprot_sprot.fasta file path in the package of this software.

- `-o, --ProSeqLabel_FilePath`

  Output file path. Automatically set according to InterPair_FilePath by default.

- `-e, --OutError_FilePath`

  Path to the output directory of the error record file during the analysis. There are up to two files under this path, and the binding id stored in WebCon_Exception.txt and SeqMap_Exception.txt represent errors or prompts caused by network connection timeout and inability to map protein chains, respectively. Default is ./Exception/ProSeqLabelException/.

- `-m, --ModRes_Change {fasta, pdb}`

  Treatment of modified binding residues. The default is 'fasta', indicating that the sequence residues are consistent with the fasta file. Optional 'pdb', means that the sequence residue is consistent with the pdb file.

- `-n, --CPU_Num`

  The number of processes used by multiple processes. The default is half of the actual number of device CPU (rounded up).

- `-v, --Version`

  Display the version information of the software and exit. Default is False.

- `-h, --help`

  Show this help message and exit.

### **1.4 PDB-BRE-PPISeqLabel option description**

The executable file PDB-BRE-ProSeqLabel is used to extract the protein sequence labels from the output file of PDB-BRE-InterPair. When using the executable file to extract protein sequence labels, the donor type in the PDB-BRE-InterPair output file should be _**protein**_.

#### 1.4.1 Required Options of PDB-BRE-PPISeqLabel

- `-i, --InterPair_FilePath`

  The input .csv file containing interaction pairs (the output file of PDB-BRE-InterPair). 

- `-p,  --PDB_DirPath`

  The storage path of the downloaded PDB files. Default is ./PDBFile.

#### 1.4.2 Optional Options of PDB-BRE-PPISeqLabel

- `-u,  --Sequence_FilePath`

  The file path of the uniprot database used during the protein chain mapping process. The default is the uniprot_sprot.fasta file path in the package of this software.

- `-o1, --ProSeqLabel_1_FilePath`

  Output file path 1. Store the sequence labels of a group of proteins in a protein-protein pair. Automatically set according to InterPair_FilePath by default.

- `-o2, --ProSeqLabel_2_FilePath`

  Output file path 2. Store the sequence labels of another group of proteins in a protein-protein pair. Automatically set according to InterPair_FilePath by default.

- `-e, --OutError_FilePath`

  Path to the output directory of the error record file during the analysis. There are up to two files under this path, and the binding id stored in WebCon_Exception.txt and SeqMap_Exception.txt represent errors or prompts caused by network connection timeout and inability to map protein chains, respectively. Default is ./Exception/ProSeqLabelException/.

- `-m, --ModRes_Change {fasta, pdb}`

  Treatment of modified binding residues. The default is 'fasta', indicating that the sequence residues are consistent with the fasta file. Optional 'pdb', means that the sequence residue is consistent with the pdb file.

- `-n, --CPU_Num`

  The number of processes used by multiple processes. The default is half of the actual number of device CPU (rounded up).

- `-v, --Version`

  Display the version information of the software and exit. Default is False.

- `-h, --help`

  Show this help message and exit.


## **2 Authors**

### **2.1 Author Contributions**
- Main developer: Shutao Chen [@ShutaoChen97](https://github.com/ShutaoChen97), email: stchen@bliulab.net


### **2.2 Contact**
- Prof. Dr. Bin Liu, email: bliu@bliulab.net


### **2.3 Citation**
PDB-BRE: a ligand-protein interaction binding residue extractor based on Protein Data Bank. Proteins: Structure, Function, and Bioinformatics. 2024, 92(1): 145-153.
