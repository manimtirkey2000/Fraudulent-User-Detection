# Fraudulent User Detection in Bitcoin OTC Network

This project implements a fairness-goodness-based algorithm to detect **fraudulent users** in a peer-to-peer trust network using social graph theory. It leverages **network analysis** on the Bitcoin OTC trust dataset to assign trustworthiness scores to users.

---

## 📊 Dataset

- **Source:** `soc-sign-bitcoinotc.csv`
- **Description:** This dataset represents a weighted directed graph of trust ratings between users on the Bitcoin OTC platform.
- **Columns:** `SOURCE`, `TARGET`, `RATING`, `TIME`
- **Ratings Range:** Originally from -10 to 10, scaled to -1 to 1 for analysis.

---

## ⚙️ Methodology

The detection technique is based on iterative computation of:

- **Goodness:** Reflects how trustworthy a user is (based on incoming ratings).
- **Fairness:** Measures how fair a user is when rating others (based on outgoing ratings).

### 🧮 Algorithm

1. **Initialization**
   - Goodness: average of all scaled ratings
   - Fairness: initialized to 1.0

2. **Iterative Update**
   - Goodness of a node = weighted average of incoming edges
   - Fairness of a node = similarity between rating given and target’s goodness

3. **Convergence**
   - Iterates until fairness and goodness values stabilize (delta < 1e-6)

---

## 🧪 Usage

### 1. Clone the Repository

```bash
git clone https://github.com/yourusername/Fraudulent-User-Detection.git
cd Fraudulent-User-Detection
````

### 2. Install Dependencies

```bash
pip install pandas networkx numpy
```

### 3. Run the Notebook

Open `SMA-GroupProject.ipynb` and execute all cells to:

* Preprocess the dataset
* Build the trust network
* Compute fairness and goodness scores
* Identify suspicious (low-scoring) users

---

## 📈 Output

* A dictionary of users with their computed **fairness** and **goodness** scores
* Can be used to:

  * Rank users by trustworthiness
  * Visualize network structure (optional extensions)
  * Flag potentially fraudulent actors

---

## 📁 Project Files

```
├── soc-sign-bitcoinotc.csv          # Trust ratings dataset
├── SMA-GroupProject.ipynb           # Main notebook for analysis
├── SMA Group Project.pdf            # Presentation/Report
```

---

## 📄 License

This project is licensed under the MIT License.

---

## 👨‍💻 Authors

* Manim Tirkey

---

## 💡 Future Work

* Add visualizations using NetworkX or Gephi
* Extend the model to include temporal trends
* Benchmark with other trust prediction models

