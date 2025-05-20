# Probability-and-Statistics
This is code Probability and Statistics for Assignment "Computer parts"

# Intel CPU Analysis (with GPU Reference)

## 📁 Dataset

- **Intel CPU Dataset:** `Intel_CPUs.csv`
- **GPU Dataset (optional):** `All_GPUs.csv` *(used only for initial table preview)*

Place the CSV files in a folder such as `D:/data/` or adjust the path in the code accordingly.

---

## 📦 Required Libraries

Before running the code, install and load the following R packages:

```r
install.packages(c("GGally", "ggplot2", "corrplot", "dplyr", "mice", "ROSE",
                   "caret", "kableExtra", "glmnet", "knitr", "DT", "flextable",
                   "webshot2", "questionr", "reshape2", "gridExtra", "car"))
