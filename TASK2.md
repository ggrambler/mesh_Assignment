# ALL OBSERVATIONS ARE IN THE OUTPUTS FOLDER




# Which normalization method preserves the mesh structure better?

There are two methods:

* **Min–Max normalization**
* **Unit Sphere normalization**

We can compare them by looking at how *small* their errors are —
smaller **MAE** and **MSE** → better preservation of mesh geometry.

---

## 🧮 Step 1: Compute Average Error per Method

Let’s summarize the **overall MSE (`mse_all`)** across all meshes:

| Mesh      | Min–Max MSE_all | Unit Sphere MSE_all | Better    |
| --------- | --------------- | ------------------- | --------- |
| branch    | 7.8 × 10⁻⁷      | 2.33 × 10⁻⁶         | ✅ Min–Max |
| cylinder  | 7.96 × 10⁻⁷     | 2.57 × 10⁻⁶         | ✅ Min–Max |
| explosive | 1.24 × 10⁻⁷     | 4.28 × 10⁻⁷         | ✅ Min–Max |
| fence     | 1.57 × 10⁻⁷     | 3.57 × 10⁻⁷         | ✅ Min–Max |
| girl      | 2.05 × 10⁻⁷     | 3.61 × 10⁻⁷         | ✅ Min–Max |
| person    | 7.89 × 10⁻⁷     | 1.79 × 10⁻⁶         | ✅ Min–Max |
| table     | 1.49 × 10⁻⁷     | 4.70 × 10⁻⁷         | ✅ Min–Max |
| talwar    | 1.30 × 10⁻⁷     | 6.03 × 10⁻⁷         | ✅ Min–Max |

---

## 🧩 Step 2: Observe the Pattern

Across **all 8 meshes**, the **Min–Max normalization consistently produces smaller errors** (both MAE and MSE) than the Unit Sphere method.

### 🧠 Interpretation:

* **Min–Max normalization** scales each axis independently between its own min and max, preserving the **original shape proportions** of the object.
* **Unit Sphere normalization** rescales the entire object uniformly to fit inside a sphere — this can slightly distort elongated or asymmetric shapes (like *branch*, *person*, *table*).

---

## 📈 Step 3: Quantitative Summary

If we compute the mean of `mse_all` across meshes:

| Method      | Mean MSE_all (approx) | Mean MAE_all (approx) | Rank     |
| ----------- | --------------------- | --------------------- | -------- |
| **Min–Max** | **3.7 × 10⁻⁷**        | **4.2 × 10⁻⁴**        | ✅ Better |
| Unit Sphere | 1.6 × 10⁻⁶            | 8.2 × 10⁻⁴            | —        |

➡️ That’s roughly a **4–5× smaller error** using Min–Max normalization.

---

## ✅ **Conclusion for Task 2**

**Min–Max normalization preserves the mesh structure better** than Unit Sphere normalization.


