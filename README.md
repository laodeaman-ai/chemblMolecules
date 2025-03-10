# ChEMBL Molecule Search & IC50 Data Extraction

This Python script automates the process of searching for target molecules in the ChEMBL database, extracting relevant IC50 data, validating SMILES notations, and combining the results into comprehensive CSV files. It utilizes parallel processing for efficiency and handles multiple target searches at once.

## Features

- **Target Search:** Search for targets in ChEMBL and retrieve their `chembl_id`.
- **IC50 Data Extraction:** Pull IC50 activity data for molecules associated with the targets.
- **SMILES Validation:** Clean and standardize SMILES notations using RDKit.
- **Parallel Processing:** Speed up data extraction with `ProcessPoolExecutor`.
- **Automatic CSV Merging:** Combine individual target results into a single CSV file.
- **Dynamic Directory Management:** Create directories for each target and organize results.

## Requirements

- Python 3.8+
- `pandas`
- `numpy`
- `rdkit`
- `chembl_webresource_client`
- `tqdm`

Install the required packages with:

```sh
pip install pandas numpy rdkit chembl_webresource-client tqdm
```

## Usage

1. Place your target search results (`targets_<target_name>.csv`) in the working directory.
2. Run the script:

```sh
python script.py
```

3. The results will be saved in the current working directory, organized into folders per target, with a final merged CSV file.

## File Structure

```
|-- targets_alpha_glucosidase.csv
|-- script.py
|-- alpha_glucosidase/
|   |-- CHEMBL12345.csv
|   |-- CHEMBL67890.csv
|-- merging_alpha_glucosidase.csv
```

## Output

Each target directory contains CSVs for individual molecules with the following columns:

- `molecule_chembl_id`
- `canonical_smiles`
- `standard_value` (IC50)
- `search_term` (target name)

The final merged CSV consolidates all results across targets.

## Example Workflow

1. Search for targets (e.g., alpha-glucosidase) and save the result as `targets_alpha_glucosidase.csv`.
2. Run the script to extract IC50 data for each target's molecules.
3. Validate and standardize SMILES, remove duplicates, and save the cleaned data.
4. Merge all the molecule data into a single CSV for easy analysis.

## Error Handling

The script handles exceptions during data retrieval and prints informative error messages. It also skips empty or invalid CSVs to prevent workflow interruptions.

## Future Improvements

- Add more activity types (e.g., Ki, EC50).
- Include optional filtering by IC50 thresholds.
- Add logging for better tracking.

## Contributions

Feel free to fork this repo, submit issues, or create pull requests! 🚀

---

Let me know if you’d like any adjustments! ✨

