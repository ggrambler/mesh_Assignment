

### 🧾 Mesh Error Summary (MAE & MSE Comparison)

| Mesh      | Method     | MAE X      | MAE Y      | MAE Z      | MAE All    | MSE X      | MSE Y      | MSE Z      | MSE All    |
| --------- | ---------- | ---------- | ---------- | ---------- | ---------- | ---------- | ---------- | ---------- | ---------- |
| branch    | minmax     | 0.00081868 | 0.00093305 | 0.00045030 | 0.00073401 | 8.9832e-07 | 1.1737e-06 | 2.7254e-07 | 7.8153e-07 |
| branch    | unitsphere | 0.00129712 | 0.00136880 | 0.00130858 | 0.00132483 | 2.2970e-06 | 2.4499e-06 | 2.2716e-06 | 2.3395e-06 |
| cylinder  | minmax     | 0.00091642 | 0.00000000 | 0.00091642 | 0.00061095 | 1.1949e-06 | 0.0000e+00 | 1.1949e-06 | 7.9663e-07 |
| cylinder  | unitsphere | 0.00138241 | 0.00138238 | 0.00138241 | 0.00138240 | 2.5257e-06 | 2.6693e-06 | 2.5257e-06 | 2.5736e-06 |
| explosive | minmax     | 0.00019609 | 0.00043841 | 0.00019117 | 0.00027523 | 5.2543e-08 | 2.7206e-07 | 4.7972e-08 | 1.2419e-07 |
| explosive | unitsphere | 0.00055423 | 0.00062094 | 0.00054755 | 0.00057424 | 4.2093e-07 | 4.6481e-07 | 3.9739e-07 | 4.2771e-07 |
| fence     | minmax     | 0.00042581 | 0.00038879 | 0.00000387 | 0.00027282 | 2.6361e-07 | 2.0694e-07 | 8.5209e-11 | 1.5688e-07 |
| fence     | unitsphere | 0.00053168 | 0.00046401 | 0.00048588 | 0.00049385 | 4.0848e-07 | 3.4476e-07 | 3.1895e-07 | 3.5740e-07 |
| girl      | minmax     | 0.00049074 | 0.00044145 | 0.00017741 | 0.00036987 | 3.1480e-07 | 2.5946e-07 | 4.2004e-08 | 2.0542e-07 |
| girl      | unitsphere | 0.00051924 | 0.00053946 | 0.00050819 | 0.00052230 | 3.5489e-07 | 3.7837e-07 | 3.4883e-07 | 3.6069e-07 |
| person    | minmax     | 0.00082005 | 0.00104017 | 0.00021489 | 0.00069170 | 9.0837e-07 | 1.3971e-06 | 6.1547e-08 | 7.8901e-07 |
| person    | unitsphere | 0.00121134 | 0.00113378 | 0.00111642 | 0.00115384 | 1.9317e-06 | 1.7258e-06 | 1.7050e-06 | 1.7875e-06 |
| table     | minmax     | 0.00016382 | 0.00027136 | 0.00048505 | 0.00030674 | 4.3311e-08 | 1.0311e-07 | 3.0002e-07 | 1.4881e-07 |
| table     | unitsphere | 0.00060047 | 0.00059899 | 0.00059727 | 0.00059891 | 4.6852e-07 | 4.6750e-07 | 4.7387e-07 | 4.6996e-07 |
| talwar    | minmax     | 0.00003151 | 0.00053706 | 0.00011663 | 0.00022840 | 1.3872e-09 | 3.7259e-07 | 1.8060e-08 | 1.3068e-07 |
| talwar    | unitsphere | 0.00068928 | 0.00067058 | 0.00064706 | 0.00066897 | 6.3765e-07 | 6.0003e-07 | 5.7025e-07 | 6.0264e-07 |

---

# Conclusion

> Ans1:
Based on the reconstruction error metrics (MAE and MSE) computed across all eight meshes, the Min–Max normalization combined with 1024-bin quantization yields the least overall error. This method consistently produced lower MAE and MSE values compared to the Unit Sphere normalization for every mesh tested.

> Ans2:
The pattern observed indicates that Min–Max normalization preserves the relative geometric proportions of each axis better, as it scales each coordinate dimension independently within its own range. In contrast, Unit Sphere normalization applies uniform scaling, which can distort elongated or asymmetric meshes and increase reconstruction error.

Overall, Min–Max + 1024-bin quantization provides more stable, accurate, and structure-preserving results for mesh preprocessing before AI model training.

---

# All Plot Reconstructions are there in the 'plots' folder

# All Screeshots comparing meshes are there in SS Folder 
| Color    | Meaning                                                   |
| -------- | --------------------------------------------------------- |
| 🔴 Red   | Original mesh (`meshes/*.obj`)                            |
| 🟢 Green | Reconstructed mesh (`outputs/*_reconstructed_minmax.obj`) |
