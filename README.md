# Scraping PDB files from Uniprot Entries (SPBDUE)
This is a Jupyter-notebook for scraping protein structure files from the [Uniprot database](https://www.uniprot.org/uniprot) entries. 

With the advent of [AlphaFold2](https://alphafold.ebi.ac.uk/) and other precise structure predictions, [Uniprot database](https://www.uniprot.org/uniprot) has started to list structure predictions for within entries. As for now, AlphaFold2 provides a [download page](https://alphafold.ebi.ac.uk/download) proteome-wide predictions for dozens of species. When focusing on variants represented in isoforms and/or orthologs, it is teadious to click every entry of the Uniprot and download the predections. Therefore I prepared a python script to scrape all the structure predictions of the given search result.

Please feel free to contact me through this repository for bugs and issues.
<br>
:Dan

## News
- 2022-01-12 Version 1.0.0 made public!
<details>
<summary>Archive</summary>
<br>  
  
- 2022-01-12 Version 1.0.0 made public!
  
</details>


## Installation
Please make sure you have appropriate Python and pip before starting.
```sh
Python version >=3.5
pip    version >= 1.1.0
```

Dependencies :
```sh
requests version >=2.27.1
beautifulsoup4 version >=4.10.0
openpyxl version >=3.0.9
tqdm version >=2.2.4
selenium version >=3.11.0
```
To install these packages, first clone this repository by
```sh
git clone https://github.com/DanYamamotoEvans/SPDBUE.git
```
Next, go to the location of the SPDBUE folder in the terminal, and install the dependencies by
```sh
pip install .
```

Other core programs to install:
- [Jupyter-notebook](https://jupyter.org/install)
```sh
pip install jupyterlab
```

Now you're ready to scrape the PDB files!


## Usage
### Overview
**Inputs:** 
- Excel file from Uniprot search result
- Output directory name
- Fasta file from Uniprot search result (optional)

**Outputs:**
- A directory with all the PDB files
- A summary file with Uniprot ID to the PDB files. If fasta file is provided you will also have the protein sequence.


### Step 1. Enter your query in Uniprot
Go to [UniProt database](https://www.uniprot.org/uniprot/), and search the proteins of your interest by entering a query in the search bar.
Hit search to get the results. You can select the proteins of interest from the search result. 
<img width="855" alt="Screen Shot 2022-01-12 at 5 08 54" src="https://user-images.githubusercontent.com/15228616/149120516-ae165c00-712f-4043-b9d4-079702cafeaa.png">

### Step 2. Download the search result 
Above the table of search results, you will see a download button. Click this, and select 'Excel'. The download will begin shortly. Make sure you rename the file once donload is cmomplete.<br> 
<img width="485" alt="Screen Shot 2022-01-12 at 5 09 56" src="https://user-images.githubusercontent.com/15228616/149120432-a50abbd5-ad8f-40f8-ab55-c4e0dacbfc12.png">

<br>

_Option_ 
- You can also download the fasta file and put it as input so you can access the sequence information easily.
<br>

_Tips_
- Make sure you use the _Advanced option_ for searching Uniprot entries with 3D structures. 
- The scraping needs to wait for the java script to load, making it slow (~10 sec per protein). Make sure you have <1000 entries after searching.

<br>
<img width="712" alt="Screen Shot 2022-01-12 at 5 09 33" src="https://user-images.githubusercontent.com/15228616/149120477-7aacfcd1-0d9d-407d-b0a1-d913c46f8892.png">


### Step 3. Run the Jupyter-notebook
1. Open your terminal, and go to the SPDBUE directory.
2. Open jupyter-notebook by entering  
```sh
jupyter-notebook
```
this will open your browzer.

3. Click and open **SPDBUE_main.ipynb**.
4. Change _path_, _xlsx_f_, and _fasta_f_ to your directory/files. Make sure you place the xlsx and fasta in the indicated directory. 
5. Execute cells by going to the header -> Cell -> Run all.
6. The script will create a new directory under that with the name of the xlsx file (without the extension). Within it, there will be a summary file and a folder with all the pdb files.

The default has a test file for downloading 10 entries. I reccomend you run the script with this before you test your own list. You can undo the comment out by deleting the '#' before fasta_f to see result when inputing a fasta file. 



One last thing:
If you make use of an AlphaFold prediction, please cite the following papers:
Jumper, J et al. Highly accurate protein structure prediction with AlphaFold. Nature (2021).
Varadi, M et al. AlphaFold Protein Structure Database: massively expanding the structural coverage of protein-sequence space with high-accuracy models. Nucleic Acids Research (2021).
