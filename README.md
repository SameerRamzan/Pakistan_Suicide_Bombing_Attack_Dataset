# Pakistan Suicide Attacks Analysis

This project analyzes a dataset of suicide attacks in Pakistan to identify trends and patterns. The analysis is performed using a Jupyter Notebook (`Analysis.ipynb`).

## Tech Stack

A brief overview of the main technologies used in this project:

| Logo | Technology | Description |
|---|---|---|
| <img src="https://www.python.org/static/community_logos/python-logo-only.png" alt="Python Logo" width="50"> | Python | Core programming language. |
| <img src="https://pandas.pydata.org/static/img/pandas.svg" alt="Pandas Logo" width="100"> | Pandas | Data manipulation and analysis library. |
| <img src="https://numpy.org/images/logo.svg" alt="NumPy Logo" width="100"> | NumPy | Fundamental package for numerical computation. |
| <img src="https://upload.wikimedia.org/wikipedia/en/5/56/Matplotlib_logo.svg" alt="Matplotlib Logo" width="100"> | Matplotlib | Comprehensive library for creating static, animated, and interactive visualizations. |
| <img src="https://seaborn.pydata.org/_static/logo-wide-lightbg.svg" alt="Seaborn Logo" width="100"> | Seaborn | Statistical data visualization library based on Matplotlib. |
| <img src="https://plotly-marketing-website-2.cdn.prismic.io/plotly-marketing-website-2/Z7eNlJ7c43Q3gCJv_Plotly-Logo-Black.svg" alt="Plotly Logo" width="100"> | Plotly | Interactive graphing library. |
| <img src="https://jupyter.org/assets/main-logo.svg" alt="Jupyter Logo" width="50"> | Jupyter Notebook | Web-based interactive computing platform used for the analysis. |
| <img src="https://raw.githubusercontent.com/scikit-learn/scikit-learn/main/doc/logos/scikit-learn-logo.svg" alt="Scikit-learn Logo" width="100"> | scikit-learn | Machine learning library (used here for `LabelEncoder`). |

Other libraries used: `fuzzywuzzy`, `python-Levenshtein`, `chardet`, `warnings`.

## Data

The dataset used in this analysis is stored in CSV format. There appear to be two versions of the dataset in the repository:

* `PakistanSuicideAttacks Ver 11 (30-November-2017).csv`
* `PakistanSuicideAttacks Ver 6 (10-October-2017).csv`

The primary dataset used in the notebook is `PakistanSuicideAttacks Ver 11 (30-November-2017).csv`.

## Analysis Steps

The Jupyter Notebook `Analysis.ipynb` performs the following key steps:

1.  **Data Loading and Initial Exploration:**
    *   Loads the dataset using pandas.
    *   Determines the character encoding of the CSV file using `chardet`.
    *   Displays the first few rows and basic information about the dataset (shape, columns).
2.  **Data Cleaning and Preprocessing:**
    *   Drops irrelevant columns (e.g., `S#`).
    *   Handles inconsistencies in city names by converting to lowercase, stripping whitespace, and using fuzzy string matching (`fuzzywuzzy`) to standardize names (e.g., 'd.i khan' and 'd. i khan').
    *   Corrects inconsistencies and standardizes values in other categorical columns like `Province`, `Location Category`, `Target Type`, `Targeted Sect if any`, `Holiday Type`, and `Open/Closed Space`.
    *   Converts the `Date` column to datetime objects and extracts the `Year`.
    *   Cleans and fills missing values in `Injured Max` and `Injured Min` columns.
3.  **Exploratory Data Analysis (EDA):**
    *   Analyzes the number of people killed and injured per year, visualizing trends.
    *   Investigates the correlation between suicide bombing attacks and influencing events.
    *   Identifies and visualizes the top hospitals by the number of victims.
    *   Determines and lists the top 10 locations of blasts.

## Visualizations

*(Note: To see these visualizations, you need to run the `Analysis.ipynb` notebook after ensuring the image export code has been added to it. The images will be saved to an `images/` directory.)*

1.  **People Killed Per Year by Province:**
    ![People Killed Per Year by Province](images/killed_per_year_province.png)

2.  **People Injured Per Year by Province:**
    ![People Injured Per Year by Province](images/injured_per_year_province.png)

3.  **Max Killed by Hospital (Top 10):**
    ![Max Killed by Hospital](images/killed_max_by_hospital.png)

4.  **Injured/Killed by Hospital (Top 10):**
    *(Note: The y-axis in the notebook is 'Injured Max' while color is 'Killed Max'. This visualization shows that relationship.)*
    ![Injured/Killed by Hospital](images/injured_killed_by_hospital.png)

5.  **Number of Suicide Blasts by Location (Top 10):**
    ![Number of Suicide Blasts by Location](images/blasts_by_location.png)

## How to Run

1.  Ensure you have Python installed.
2.  Install the necessary libraries. You can typically do this using pip:
    ```bash
    pip install pandas seaborn matplotlib numpy fuzzywuzzy python-Levenshtein chardet plotly scikit-learn kaleido
    ```
    The notebook also includes commented-out pip install commands for `fuzzywuzzy`, `python-Levenshtein`, and `chardet`. The `kaleido` library is needed for exporting Plotly charts as static images.
3.  Ensure the `Analysis.ipynb` notebook includes the code to save plots as images (as previously discussed and added).
4.  Open and run the `Analysis.ipynb` notebook using Jupyter Notebook or JupyterLab. This will generate the plots and save them to the `images/` directory.
5.  Once the images are generated, they will appear in the "Visualizations" section of this README.

## Findings (Summary from EDA)

*   The years 2007, 2008, 2009, and 2010 saw a high number of casualties (killed and injured) from suicide blasts.
*   KPK province experienced a significant number of these incidents.
*   The analysis identifies hospitals most frequently dealing with victims of these attacks, with Lady Reading Hospital appearing prominently.
*   The notebook also lists the top 10 most frequent blast locations.
*   A weak positive correlation (around 0.075) was found between the number of suicide blasts and the encoded 'Influencing Event/Event' column after label encoding. An earlier calculation grouping by the event string showed a correlation of 0.58, suggesting that the nature of the influencing event might have some relationship with the number of blasts. However, the label encoding might obscure this.
