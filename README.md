# Data-Driven Personalization in Retail: A Machine Learning Approach to Enhancing Customer Lifetime Value

Αυτό το αποθετήριο περιλαμβάνει τον κώδικα, τα δεδομένα και τα συνοδευτικά αρχεία της διπλωματικής εργασίας του ΠΜΣ «Οικονομική και Επιχειρησιακή Στρατηγική» του **Πανεπιστημίου Πειραιώς**.

## 📋 Περίληψη Εργασίας
Η εργασία διερευνά την εφαρμογή προηγμένων τεχνικών μηχανικής μάθησης και στατιστικών μοντέλων στην πρόβλεψη της αξίας πελάτη (**Customer Lifetime Value - CLV**) στο ηλεκτρονικό λιανεμπόριο. Ως βάση δεδομένων χρησιμοποιήθηκε το γνωστό `Online Retail II` dataset από το UCI Machine Learning Repository, το οποίο περιλαμβάνει πραγματικές συναλλαγές διετίας (2009–2011).

## 📌 Περιεχόμενα Αποθετηρίου
- `CLV_Final_Thesis.ipynb`: Το ολοκληρωμένο Jupyter Notebook που περιλαμβάνει:
  - **Προεπεξεργασία & Temporal Split:** Αυστηρός χρονικός διαχωρισμός (Feature Period: Δεκ. 2009 – Μάιος 2011 | Target Period: Ιούνιος – Δεκ. 2011) για την απολύτως ασφαλή αποφυγή διαρροής πληροφορίας (*data leakage*).
  - **RFM Analysis:** Υπολογισμός δεικτών Recency, Frequency και Monetary με εφαρμογή λογαριθμικού μετασχηματισμού (`log1p`) για τη διαχείριση της ασυμμετρίας.
  - **Customer Segmentation:** Μη επιβλεπόμενη ομαδοποίηση μέσω **K-Means Clustering (k=4)**, η οποία ανέδειξε τέσσερα διακριτά τμήματα (*Regular, Lost, High Value, VIP Customers*), επιβεβαιώνοντας εμπειρικά την αρχή Pareto.
  - **CLV Predictive Models:** Συγκριτική αξιολόγηση 6 μοντέλων:
    1. *Probabilistic Baseline:* BG/NBD + Gamma-Gamma
    2. *Machine Learning:* Random Forest, XGBoost, LightGBM, Gradient Boosting Regressor
    3. *Deep Learning:* Feedforward Neural Network (MLP)
  - **Model Interpretability:** Ανάλυση SHAP (*SHapley Additive exPlanations*) για την αποκάλυψη της παγκόσμιας και τοπικής σπουδαιότητας των χαρακτηριστικών.
- `requirements.txt`: Οι απαραίτητες βιβλιοθήκες Python για την πλήρη αναπαραγωγή των πινάκων και των διαγραμμάτων.

## 📊 Κύρια Αποτελέσματα & Συμπεράσματα
* **Κορυφαίο Μοντέλο ML:** Το **Gradient Boosting Regressor** αναδείχθηκε ως ο αποδοτικότερος αλγόριθμος μηχανικής μάθησης με συντελεστή προσδιορισμού R^2 = 0.5008 και χαμηλότερο σφάλμα MAE = £680.56 στο holdout test set, ξεπερνώντας το πιθανοθεωρητικό baseline (MAE = £687.77).
* **Feature Importance (SHAP):** Η ιστορική δαπάνη (`Monetary_log`) επιβεβαιώθηκε ως ο ισχυρότερος προβλεπτικός παράγοντας της μελλοντικής αξίας, ακολουθούμενη από τη χρονική εγγύτητα (`Recency`) και τη συχνότητα (`Frequency`).
* **Επιχειρησιακή Αξία:** Η τμηματοποίηση απέδειξε ότι μόλις το 0.79\% των πελατών (High Value & VIP) συνεισφέρει πάνω από το 25% των συνολικών εσόδων, καθορίζοντας στοχευμένες στρατηγικές διαχείρισης και διατήρησης.

## 🛠️ Απαιτήσεις & Εγκατάσταση
Βεβαιωθείτε ότι διαθέτετε Python 3.10+ και εγκαταστήστε τις βιβλιοθήκες εκτελώντας:
```bash
pip install -r requirements.txt
