# Leiden University System & Software Security Assignment 2: Hands-on Project - Group 8

Welcome to the official repository for Assignment 2, Group 8 of the Leiden University Master's course Systems and Software Security.

# CENTRIS: Reproduction and Java language dataset experiments

### Requirements

#### Install Ctags
Install the universal-ctags tool to parse function definitions:
```bash
sudo apt install universal-ctags
```
#### Install python3-tlsh
Install the python-tlsh library using pip:
```bash
sudo apt-get install python3-pip
sudo pip3 install py-tlsh
```
#### Specify Ctags Path
Update the ctags path
```bash
ctags_path = "/path/to/ctags"  # Replace with the correct ctags path
```
# Using the Provided Dataset to reproduce the paper experiment

## Dataset
### Download the Dataset

Download the dataset from [Zenodo](https://zenodo.org/records/4514689#.YB7sN-gzaUk) (5 GB).

### Steps:

1. **Extract the downloaded file**  
   Extract `Centris_dataset.tar`:
   ```bash
   tar -xvf Centris_dataset.tar

2. There are four sample target software (ArangoDB, Crown, Cocos2dx, and Splayer), which are utilized in the in-depth comparison in the paper

3. To check the detection result for these four target software programs, set "**testmode**" in **line 193** of "**Detector_for_OSSList.py**" file to **1**, and adjust the file paths in **lines 196 and 197** in the "**Detector_for_OSSList.py**" file.

4. Execute the "Detector_for_OSSList.py".
   ```bash
   python3 Detector_for_OSSList.py
   ```
5. See the results (default output path: ./res/.)

# Verify CENTRIS using Java language dataset

### Running CENTRIS

## OSSCollector (`./Adaptation_java_datasets/osscollector/`)

1. **Specify Directory Paths**  
   Edit `OSS_Collector.py` (lines 17 to 21) to specify:
   - Directory for cloned repositories.
   - Directory for storing extracted functions.
   - Path to the installed `ctags`.

2. **Run the OSS_Collector Script**
   ```bash
   python3 OSS_Collector.py

## Preprocessor (`./Adaptation_java_datasets/preprocessor/`)
1. **Run the preprocessor based on your preprocessing choice:**
   For full preprocessing:
      ```bash
      python3 Preprocessor_full.py
      ```
   For lite preprocessing:
      ```bash
      python3 Preprocessor_lite.py
      ```
## Detector (`./Adaptation_java_datasets/detector/`)
1. **Run the Detector**
Execute the `Detector.py` script with the root path of the target software as an argument:

   ```bash
   python3 Detector.py /path/of/the/target/software
   ```

## Results (`./Adaptation_java_datasets/detector/res`)
**Check the component identification results (default output path: ./detector/res/)**

# Identifying the most reused library using CENTRIS
## Execute under the MostReuseFinder folder.
### Step 1: Clone Repositories
**Use the osscollector/clone_repositories.py script to clone the target repositories. This step downloads the required repositories for further analysis.
Run the following command:**
```bash
python osscollector/clone_repositories.py
```
### Step 2: Analyze Cloned Repositories
**Analyze the cloned repositories to extract relevant functions by using the osscollector/parse_functions.py script.
Run the following command:**
```bash
python osscollector/parse_functions.py
```
### Step 3: Preprocess Data
**Preprocess the data to prepare it for detection. Use the preprocessor/Preprocessor_full.py script.
Run the following command:**
```bash
python preprocessor/Preprocessor_full.py
```

### Step 4: Detection Pipeline
#### 4.1 Clone Target Detection Project
**Detect the target OSS projects using the detector/clone.py script.
Run the following command:**
```bash
python detector/clone.py
```
#### 4.2 Generate Hashes for Target Files
**Generate hashes for the target detection files with the detector/parse.py script.
Run the following command:**
```bash
python detector/parse.py
```
#### 4.3 Compare Detected Clones
**Compare and identify detected clones using the detector/Detector.py script.
Run the following command:**
```bash
python detector/Detector.py
```
### Step 5: Visualize Results
**Visualize the results of the detection and analysis by using the detector/statistics.py script.
Run the following command:**
```bash
python detector/statistics.py
```
