# Quantifying "Coder Bias" in Democracy Indices

### 1. The Hypothesis
The narrative of "Global Democratic Backsliding" relies heavily on expert-coded (subjective) data from organisations like V-Dem. However, recent research ([Little & Meng, 2024](https://www.cambridge.org/core/journals/ps-political-science-and-politics/article/measuring-democratic-backsliding/9EE2044CDA598BD815349912E61189D8)) suggests that objective metrics (election turnover, constitutionality) show much more stability.

**My Question:** Are the experts measuring reality, or has the *standard* for democracy just become stricter over time?

### 2. The Methodology
*   **Data:** Merged V-Dem (Subjective) and NELDA/DPI (Objective) datasets (1990–2021).
*   **Model:** Random Forest Regressor.
*   **Features:** Strictly institutional metrics (Incumbent Loss, Electoral Competitiveness, Term Limits, Journalist Imprisonment).
*   **Training Strategy (Temporal Split):**
    *   **Train:** 1990–2010 (The "Optimistic Era"). The model learns the relationship between objective institutions and democracy scores.
    *   **Test:** 2011–2021 (The "Backsliding Era").

### 3. Key Findings

#### A. The 2020 Structural Break
My residual analysis challenges the "gradual backsliding" narrative.
*   **2011–2019:** The Subjectivity Gap was near zero. Experts and the Model (Objective Data) agreed.
*   **2020–2021:** A sharp divergence appears. Experts rated countries ~6-10% lower than their objective institutions warranted. This suggests that **pandemic-era emergency powers** were coded as "autocracy" by experts, despite institutions remaining stable.

<img width="1025" height="553" alt="image" src="https://github.com/user-attachments/assets/89fb59bc-3503-4423-bf73-b6030b1ab8a9" />

#### B. The "Potemkin Village" Effect (Geospatial Analysis)
Mapping the residuals reveals a geographic split in why the model disagrees with experts:
1.  **The "Red Belt" (Russia, China):** The model predicts higher scores because these regimes successfully mimic democratic institutions (holding elections, having term limits) while suppressing their function. The "Gap" here reflects the failure of objective metrics to capture repression.
2.  **The "Democratic Panic" (India, Eastern Europe):** In functional democracies, the model predicts high scores based on robust institutions, while experts penalise them heavily for qualitative shifts in rhetoric or media environment.

<img width="1570" height="825" alt="image" src="https://github.com/user-attachments/assets/9cdb1d28-806a-4505-95b7-629acdfb8687" />

### 4. Tech Stack
*   **Python:** Pandas, NumPy
*   **ML:** Scikit-Learn (Random Forest, Imputation)
*   **Viz:** Seaborn, Matplotlib, Geopandas
