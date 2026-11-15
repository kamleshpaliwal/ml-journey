# Insurance Hypothesis Testing

A notebook that applies hypothesis testing to a medical-insurance dataset: for each question it chooses a statistic, states the null and alternative hypotheses, sets a significance level, and interprets the p-value. It is adapted from the IBM Skills Network *Hypothesis Testing* lab (author: Svitlana Kramar), rewritten as a standalone analysis that runs locally.

## Dataset

[insurance.csv](https://cf-courses-data.s3.us.cloud-object-storage.appdomain.cloud/IBM-ML0232EN-SkillsNetwork/asset/insurance.csv) has 1,338 customers with `age`, `sex`, `bmi`, `children`, `smoker`, `region`, and `charges`. The notebook downloads it into `data/insurance.csv` when it is missing and never overwrites an existing copy. The CSV is excluded from Git.

## Environment

```bash
cd ~/Documents/ml-journey/projects/insurance-hypothesis-testing
python3 -m venv .venv
source .venv/bin/activate
python -m pip install --upgrade pip
python -m pip install -r requirements.txt
```

In VS Code, open `notebooks/hypothesis_testing.ipynb`, select the `.venv` interpreter as the kernel, and run the cells from top to bottom.

## Tests in the notebook

| # | Question | Test | Result |
|---|---|---|---|
| 1 | Does BMI differ between males and females? | Two-sample t-test, two-tailed | p = 0.090, fail to reject H₀ |
| 2 | Do smokers have higher charges than non-smokers? | Two-sample t-test, right-tailed | p ≈ 4e-283, reject H₀ |
| 3 | Does BMI differ for women with 0, 1, or 2 children? | One-way ANOVA | p = 0.716, fail to reject H₀ |
| 4 | Does the share of smokers differ by region? | Chi-square test of independence | p = 0.062, fail to reject H₀ |

"Fail to reject H₀" means there is not enough evidence of an effect. It does not prove that no effect exists.

## Changes from the original lab

- Removed the browser-only `piplite` and `skillsnetwork` code; the data is downloaded with `requests`.
- Replaced the deprecated `sns.distplot` with `sns.kdeplot`.
- The right-tailed test now uses `ttest_ind(..., alternative='greater')` instead of halving a two-tailed p-value.
- Rewrote the lab's exercises and solution toggles as ordinary analysis steps with written conclusions.
- Corrected the conclusions: the backwards "fail to reject … that there is a difference" message, "accept the null hypothesis" wording, the contradictory conclusion for the smoker-by-region test, the "greater than or equal to" alternative hypothesis, and a conclusion that used the two-tailed p-value for a right-tailed test.
