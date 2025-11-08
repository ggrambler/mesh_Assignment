# mesh_Assignment
mixarAi - Assignment: https://drive.google.com/file/d/1oRb6XkodrXEShnYkNkxxDNdicH2sPz09/view?usp=sharing

# 🧩 Mesh Normalization, Quantization & Error Analysis

### SeamGPT Data Preprocessing Assignment

This project implements a complete 3D mesh preprocessing pipeline designed to **normalize, quantize, reconstruct, and analyze** 3D meshes before they are used in AI training workflows.
It follows the SeamGPT “data cleaning” methodology for consistent geometric data representation.

---

## 📦 Features

✅ Loads every `.obj` file in the `meshes/` directory <br>
✅ Prints vertex statistics — **count / min / max / mean / std** per axis<br>
✅ Performs **two normalization methods**:<br>
 • Min–Max Normalization
 • Unit Sphere Normalization<br>
✅ **Quantizes** coordinates into 1024 discrete bins<br>
✅ **Reconstructs** meshes by dequantization + denormalization<br>
✅ Computes **MAE / MSE** per axis and overall<br>
✅ Saves processed `.obj` files for: normalized, quantized, and reconstructed meshes<br>
✅ Generates **error plots** (per-axis MAE/MSE) and a combined **CSV summary**<br>
✅ Uses **Python static typing** for readability and strong fundamentals<br>

---

## ⚙️ Environment Setup

### 1️⃣ Create and activate a virtual environment

```bash
python3.10 -m venv .venv
# Windows
.venv\Scripts\activate
# Linux / macOS
source .venv/bin/activate
```

### 2️⃣ Install dependencies

```bash
pip install -r req.txt
```

---

## 🧠 Library Usage Explained

| Library        | Purpose                                                                                       |
| -------------- | --------------------------------------------------------------------------------------------- |
| **numpy**      | Core numerical operations on vertex coordinates (normalization, quantization, error metrics). |
| **matplotlib** | Generates bar plots of MAE / MSE per axis for visual error analysis.                          |
| **trimesh**    | Loads and exports `.obj` files, handles 3D mesh vertex and face data structures.              |
| **open3d**     | (Optional) Used for interactive 3D visualization of original vs processed meshes.             |

---

## 🗂️ Folder Structure

```
Mesh_Assignment/
│
├── meshes/                     # Input .obj meshes (e.g. branch.obj, cylinder.obj, etc.)
├── outputs/                    # Generated normalized, quantized, reconstructed meshes
├── plots/                      # MAE/MSE bar plots per mesh
│
├── mesh_pipeline.py            # Main processing script
├── requirements.txt            # Dependency list
└── README.md                   # Project documentation
```

---

## 🚀 How to Run

1. Place your `.obj` files inside the `meshes/` folder.
2. Run the pipeline:

```bash
RUNALL in mesh_processing.ipynb
```


3. Watch the console output — it will show the current mesh being processed and its statistics.
4. Results will appear in the **`outputs/`** and **`plots/`** directories.
5. A **summary CSV** (`outputs/summary.csv`) will contain MAE / MSE values for all meshes.

---

## 📊 Outputs

| Output Type                      | Description                             |
| -------------------------------- | --------------------------------------- |
| `*_normalized_minmax.obj`        | Min–Max normalized vertices             |
| `*_quantized_minmax.obj`         | Quantized mesh (Min–Max)                |
| `*_reconstructed_minmax.obj`     | Reconstructed original (Min–Max)        |
| `*_normalized_unitsphere.obj`    | Unit Sphere normalized vertices         |
| `*_quantized_unitsphere.obj`     | Quantized mesh (Unit Sphere)            |
| `*_reconstructed_unitsphere.obj` | Reconstructed original (Unit Sphere)    |
| `plots/*.png`                    | Per-axis MAE / MSE bar plots            |
| `outputs/summary.csv`            | Combined numeric results for all meshes |

---

## 📘 Technical Notes

* **Python Version:** 3.10.6 (recommended)
* The code automatically handles degenerate meshes (`s = 0`) to avoid division-by-zero errors.
* Quantization uses 1024 bins (values 0–1023).
* The script prints absolute folder paths for debugging.
* Static typing (via `typing`) improves maintainability and clarity.

---

## 🧾 Example Console Output

```
📂 Input Meshes Folder : C:\Users\user\Desktop\Mesh_Assignment\meshes
📁 Output Folder       : C:\Users\user\Desktop\Mesh_Assignment\outputs
📊 Plot Folder         : C:\Users\user\Desktop\Mesh_Assignment\plots

🧩 Processing mesh: branch.obj
Vertices: 2498
Min: [-1.45 -0.87 -0.99]
Max: [ 1.52  0.84  1.07]
Mean: [0.003 0.005 0.001]
Std:  [0.55  0.48  0.52]
Min–Max  | MAE per axis [0.00031 0.00029 0.00028] | MAE 0.00029 | MSE 0.00000012
UnitSphere| MAE per axis [0.00033 0.00032 0.00030] | MAE 0.00032 | MSE 0.00000013
```


