Overview
This project performs Principal Component Analysis (PCA) on the Iris dataset and visualizes the first three principal components in a 3D scatter plot. It also includes a Seaborn pairplot for quick exploratory analysis. The 3D plot colors points by species and can include a legend and cleaner styling.

Files
pca.ipynb: Main script that mounts Google Drive, loads iris.csv, runs PCA to 3D, and plots pairplot and a 3D scatter.

iris.csv: Input dataset with columns sepal_length, sepal_width, petal_length, petal_width, species.

Requirements
Python 3.9+

Packages: google-colab (runtime), pandas, seaborn, matplotlib, scikit-learn

Optional (notebook interactivity): ipympl for interactive 3D rotation in notebooks

Install
In Colab, most libraries are preinstalled. If needed:

pip install pandas seaborn matplotlib scikit-learn

Optional for interactive 3D in notebooks: pip install ipympl

Data
Place iris.csv at /content/drive/MyDrive/iris.csv in Google Drive, or adjust the path in pca.py. The file must have:

Features: sepal_length, sepal_width, petal_length, petal_width

Label: species (e.g., setosa, versicolor, virginica)

How to run (Colab)
Upload pca.py or open a notebook.

Ensure iris.csv is in Drive at /content/drive/MyDrive/iris.csv.

Run pca.py:

In a cell: %run pca.py

Or copy the code into the notebook cells and run sequentially.

Outputs:

A Seaborn pairplot colored by species.

A Matplotlib 3D scatter of PCA components (PC1, PC2, PC3).

Legend
The simplest legend uses the scatter’s auto handles mapped to species names after plotting:

handles, _ = scatter.legend_elements()

ax.legend(handles, df['species'].astype('category').cat.categories.tolist(), title="Species")

Make markers smaller
Set the s parameter in the scatter call, e.g., s=10, and remove facecolor overrides so the colormap reflects classes:

scatter = ax.scatter(..., c=colors, s=10, cmap="viridis", edgecolors="none")

Interactive 3D (notebook)
For left‑click rotation in notebooks, enable the interactive backend:

Install once: pip install ipympl

At the top of a notebook cell: %matplotlib widget

Keep the same plotting code; left‑drag rotates, middle pans, right zooms.

Optional: ax.mouse_init(rotate_btn=1, pan_btn=2, zoom_btn=3)

Troubleshooting
Syntax error in scatter: ensure the closing parenthesis is present after the argument list.

Colors all black: remove facecolor='black' if using c=... for class-based colors.

No legend: add the two lines under “Legend” after plotting.

File not found: confirm iris.csv path; adjust the path if Drive mount location differs.

Why PCA here
PCA reduces the original 4D measurements to 3D while preserving most variance, making species patterns easier to see in a 3D plot.

License
This script is for educational use. Add a license file if distributing.
