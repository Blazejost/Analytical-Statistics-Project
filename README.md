# Analytical-Statistics-Project

This project focuses on statistical analysis using Python to simulate, analyze, and visualize a dataset inspired by Kaggle's "Medical Cost Personal Dataset." The goal is to explore statistical metrics, uncover potential trends, and provide meaningful insights from the data.

## Features
- **Data Simulation**: Generates a dataset with fields such as age, sex, BMI, number of children, smoker status, region, and medical charges, incorporating realistic dependencies.
- **Statistical Analysis**: Computes key measures like mean, median, standard deviation, skewness, and kurtosis for the `charges` variable.
- **Data Visualization**: Provides visual insights using histograms, pair plots, and other graphical representations.
- **Reproducibility**: Generates all data programmatically, eliminating the need for external dependencies.

## Dataset Description
The dataset includes the following fields:
- `age`: Age of the individual.
- `sex`: Gender of the individual (`male` or `female`).
- `bmi`: Body Mass Index (BMI), a measure of body fat.
- `children`: Number of children covered by health insurance.
- `smoker`: Whether the individual is a smoker (`yes` or `no`).
- `region`: The area of residence in the U.S. (`southwest`, `southeast`, `northwest`, or `northeast`).
- `charges`: Annual medical costs for the individual.

## Statistical Methods
- Computation of descriptive statistics (mean, median, standard deviation, skewness, kurtosis).
- Analysis of relationships between variables.
- Use of visualization tools to identify patterns and outliers.

## Tools and Libraries
The project uses the following libraries:
- **Pandas**: For data manipulation and analysis.
- **Numpy**: For numerical computations.
- **Matplotlib** and **Seaborn**: For data visualization.
- **Statsmodels**: For statistical modeling and hypothesis testing.

## Installation
1. Clone the repository:
   ```bash
   git clone https://github.com/Blazejost/Analytical-Statistics-Project.git
   ```
2. Navigate to the project directory:
   ```bash
   cd Analytical-Statistics-Project
   ```
3. (Optional) Set up a virtual environment:
   ```bash
   python -m venv venv
   source venv/bin/activate  # On Windows: venv\Scripts\activate
   ```
4. Install dependencies:
   ```bash
   pip install -r requirements.txt
   ```

## Usage
1. Open and run the `StatystykaProjekt.ipynb` notebook:
   - Use Jupyter Notebook or Jupyter Lab to execute the code interactively.
2. Explore the outputs:
   - Generated dataset displayed in the first cell.
   - Statistical measures and visualizations will be displayed throughout the notebook.

## Example Output
### Sample Data
| Age | Sex    | BMI   | Children | Smoker | Region     | Charges   |
|-----|--------|-------|----------|--------|------------|-----------|
| 56  | Male   | 25.80 | 0        | Yes    | Southwest  | 51,224.70 |
| 46  | Male   | 31.28 | 0        | No     | Northeast  | 24,180.56 |
| 32  | Male   | 29.33 | 3        | No     | Northeast  | 20,719.65 |
| 60  | Male   | 28.67 | 1        | Yes    | Southwest  | 51,332.40 |
| 25  | Male   | 33.69 | 2        | No     | Northwest  | 21,592.57 |

### Statistical Analysis
Key descriptive statistics (e.g., mean, variance) and insights regarding the dataset are presented visually and analytically throughout the notebook.

## Contribution
Contributions are welcome! Please follow these steps:
1. Fork the repository.
2. Create a new branch:
   ```bash
   git checkout -b feature-name
   ```
3. Make and test your changes.
4. Commit changes:
   ```bash
   git commit -m "Add new feature"
   ```
5. Push to the branch:
   ```bash
   git push origin feature-name
   ```
6. Open a Pull Request.

## License
This project is open-source and available under the [MIT License](LICENSE).

## Acknowledgments
- Inspired by the Kaggle dataset "Medical Cost Personal Dataset."
- Special thanks to the open-source community for the tools and libraries used.
