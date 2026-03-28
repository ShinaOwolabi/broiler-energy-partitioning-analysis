# Broiler Energy Partitioning Analysis

A Python data analysis of energy partitioning indices in pre-starter broiler chicks, derived from my MSc research at the University of Ibadan, Nigeria.

---

## What This Study Is About

Pre-starter broiler chicks (day 1 to day 10) partition dietary energy into three main fractions:

- **Heat Production (HP):** Energy lost as metabolic heat
- **Retained Energy (RE / NEp):** Energy stored in the body (fat + protein)
- **Metabolisable Energy Intake (MEI):** Total energy available after digestive losses

Understanding how different dietary ingredients affect these fractions is critical for precision nutrition in commercial broiler production. This study compares energy utilisation across three diet groups (Cereal, Protein, and Fibre sources) using two methods:

1. **Comparative Slaughter Technique (CST):** A direct biochemical method that measures actual carcass energy deposition
2. **Mathematical Modelling:** A nonlinear regression model fitted in R (PROC NLMIXED equivalent) using the van der Klein et al. (2020) framework

The model equation for Heat Production:

```
HP (kcal/day) = a × BW^b + c × ADWG^d
```

Where: a = 93.9781, b = 0.6438, c = 23.3313, d = 1.6229 (fitted via nlme ML, R v4.3.3)

---

## Dataset

| Sheet | Contents |
|-------|----------|
| Raw Data | 36 replicate observations; bomb calorimeter, carcass, and feed records |
| Corrected Calculations | ME, MEI, HP, RE, REF, REP, KREF, KREP per replicate |
| Treatment Means | Diet-level means across Cereal, Protein, and Fibre groups |
| CST vs Model | Direct comparison of CST and modelled HP, RE, and NEg values |
| Assumptions | Energy conversion factors and model parameter sources |

**Diet groups and treatments:**

| Group | Diets |
|-------|-------|
| Cereal | Reference, Maize, Sorghum, Pearl Millet, Wheat |
| Protein | Reference, Full-Fat Soya, Groundnut Cake, Soya Bean Meal |
| Fibre | Reference, Brewers Dried Grain, Wheat Bran, Rice Bran, Corn Bran |

---

## Key Variables

| Variable | Description | Unit |
|----------|-------------|------|
| MEI | Metabolisable Energy Intake | kcal/bird/10d |
| RE / NEp | Retained Energy (Net Energy for production) | kcal/bird/10d |
| HP | Heat Production | kcal/bird/10d |
| REF | Retained Energy as Fat | kcal/bird |
| REP | Retained Energy as Protein | kcal/bird |
| KREF | Efficiency of ME use for fat retention | ratio |
| KREP | Efficiency of ME use for protein retention | ratio |

---

## Analysis (Jupyter Notebook)

The notebook `energy_partitioning_analysis.ipynb` covers:

1. Data loading and cleaning from the raw Excel workbook
2. Descriptive statistics by diet group
3. Visualisation of MEI, HP, and RE across all diets
4. Fat vs protein energy retention comparison
5. CST vs Mathematical Model agreement analysis
6. Efficiency indices (KREF, KREP) by diet group

### Key Findings

- **Pearl Millet** produced the highest MEI (809.9 kcal/bird) and HP (610.3 kcal/bird) among cereal diets, suggesting lower net energy efficiency
- **Wheat** showed the lowest HP (398.4 kcal/bird) with the highest RE, indicating better energy retention efficiency
- **Full-Fat Soya** achieved the highest KREF (0.196) among protein sources, reflecting high efficiency of fat retention
- **Soya Bean Meal** had the lowest MEI (416.0 kcal/bird) but competitive RE, pointing to a different energy utilisation pattern
- The mathematical model consistently **underestimated HP** compared to CST values (mean delta: 53–59% for cereal diets), confirming CST captures maintenance costs more completely at this early growth phase
- **KREP consistently exceeded KREF** across all diet groups, confirming that protein accretion is energetically more efficient than fat deposition in pre-starter chicks

---

## How to Run

**Clone the repository:**

```bash
git clone https://github.com/ShinaOwolabi/broiler-energy-partitioning-analysis.git
cd broiler-energy-partitioning-analysis
```

**Install dependencies:**

```bash
pip install pandas numpy matplotlib seaborn openpyxl jupyter
```

**Launch the notebook:**

```bash
jupyter notebook energy_partitioning_analysis.ipynb
```

---

## Dependencies

- Python 3.8+
- pandas
- numpy
- matplotlib
- seaborn
- openpyxl
- jupyter

---

## Reference

This analysis is part of my MSc thesis:

> Owolabi, S. J. (2025). *Comparison of Energy Partitioning Indices in Pre-starter Broiler Chicks Derived by Mathematical Modelling and Comparative Slaughter Methodologies.* MSc Thesis, University of Ibadan, Nigeria. Supervisor: Dr. Oluwafunmilayo O. Adeleye.

Model framework adapted from:

> van der Klein, S. A. S., et al. (2020). Mathematical modeling of energy partitioning in broilers. *Poultry Science.*

Energy conversion factors from:

> Larbier, M., & Leclercq, B. (1992). *Nutrition and Feeding of Poultry.* Nottingham University Press.

---

## Author

**Shina James Owolabi, RAS**
PhD Candidate, Animal Science, University of Ibadan
Registered Animal Scientist | NIAS/RAS/02923

- ORCID: [0009-0005-2849-1045](https://orcid.org/0009-0005-2849-1045)
- LinkedIn: [shinajamesowolabi](https://www.linkedin.com/in/shinajamesowolabi)
- SciProfiles: [shinajamesowolabi](https://sciprofiles.com/profile/shinajamesowolabi)

---

## License

This repository is shared for academic and educational purposes. Please cite the MSc thesis if you use or adapt this work.
