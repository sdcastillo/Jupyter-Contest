---
layout: default
title: Predicting Uncertainty
description: Prediction intervals from gradient boosting quantile regression.
samwiki: true
---

<section class="sw-lede" aria-labelledby="sw-about-title">
  <div class="sw-lede-copy">
    <h2 id="sw-about-title">A range, not a single guess</h2>
    <p>This is Sam Castillo’s notebook for the Society of Actuaries Predictive Analytics and Futurism Section Jupyter contest: <em>Predicting Uncertainty: Prediction Intervals from Gradient Boosting Quantile Regression</em>. It is student-era work in mathematics and actuarial science from the University of Massachusetts Amherst. The proofs and the fitted models stay in the notebook. This page is the front door.</p>
    <p>A point prediction hides how much the data can support it. The notebook’s line is that fortune tellers hand you one number, and actuaries hand you an interval. Quantile regression changes the loss so a gradient boosting model can aim at a percentile. Squared error targets the mean. The pinball loss, with quantile level τ, targets any percentile. Here the band runs from the 5th percentile to the 95th.</p>
    <p>The demonstration uses the public medical-cost file that accompanies Brett Lantz’s <em>Machine Learning with R</em> (also on <a href="https://www.kaggle.com/datasets/mirichoi0218/insurance">Kaggle</a>): 1,338 patients. Age, sex, BMI, number of children, smoker, and region predict annual charges. Those charges are right-skewed, with a mean of $13,270. One third of the rows are held out, with the random seed fixed at 42. A linear regression baseline reaches an R² of 0.75 and a mean absolute error of about $4,243. The gradient boosting model of the mean improves that to an R² of 0.809 and a mean absolute error of about $3,161.</p>
    <p>The same quantiles do two jobs. First they put an interval on a health-insurance risk score, so two members with the same average cost can still carry very different uncertainty. <a href="https://www.actuarialstandardsboard.org/asops/data-quality/">Actuarial Standard of Practice No. 23</a> is the hook: when the data are thin, the actuary should say so, and the width of the interval is one way to say it. Second, they audit the file. Of 442 patients in the holdout set, 10 fall outside the 5th-to-95th band. Several of those rows are implausible on their face: impossible body-mass indexes, and a 12-year-old listed with three children.</p>
    <p>Percentiles do not add the way averages do. A mean can be split by group and reassembled; a 95th percentile cannot. The notebook shows that algebra, and it keeps the two short proofs — mean squared error, then the quantile loss — next to the code that uses them.</p>
  </div>
  <aside class="sw-find" aria-labelledby="sw-find-title">
    <h2 id="sw-find-title">Takeaways</h2>
    <ul>
      <li><strong>Intervals, not points</strong> A prediction interval shows when the data behind a member are thin. A single risk score does not.</li>
      <li><strong>The loss picks the target</strong> Mean squared error estimates the mean. Quantile loss at τ = 0.05 and τ = 0.95 bounds the interval in this notebook.</li>
      <li><strong>What the holdout showed</strong> On 1,338 medical-cost records, gradient boosting beat linear regression: R² 0.809 versus 0.75, and mean absolute error about $3,161 versus $4,243.</li>
      <li><strong>Ten outliers in 442</strong> The same 5th and 95th percentile models flag rows that look like coding errors, including impossible BMIs.</li>
      <li><strong>Do not average the percentiles</strong> Group means recombine. Quantiles do not. The Discussion section spells out why.</li>
    </ul>
  </aside>
</section>

<section class="sw-section" id="submission">
  <div class="sw-section-head">
    <h2>Read the submission</h2>
    <p>The contest entry is the notebook. The rendered HTML and the <code>.ipynb</code> in this repository are unchanged.</p>
  </div>
  <div class="sw-grid">
    <article class="sw-card">
      <div class="sw-card-top">
        <h3 class="sw-name"><a href="Final%20Jupyter%20Submission.html">Rendered notebook</a></h3>
        <span class="sw-lang">HTML</span>
      </div>
      <p class="sw-badge">Submission</p>
      <p class="sw-desc">The full write-up as exported from Jupyter: theorems, figures, tables, and the two applications.</p>
      <div class="sw-actions">
        <a class="sw-btn sw-btn-live" href="Final%20Jupyter%20Submission.html">Open the notebook</a>
      </div>
    </article>
    <article class="sw-card">
      <div class="sw-card-top">
        <h3 class="sw-name"><a href="https://github.com/sdcastillo/Jupyter-Contest/blob/master/Final%20Jupyter%20Submission.ipynb">Source notebook</a></h3>
        <span class="sw-lang">Python</span>
      </div>
      <p class="sw-badge">Source</p>
      <p class="sw-desc">scikit-learn gradient boosting, a linear baseline, and the 5th and 95th percentile fits. Random seed 42.</p>
      <div class="sw-actions">
        <a class="sw-btn sw-btn-source" href="https://github.com/sdcastillo/Jupyter-Contest/blob/master/Final%20Jupyter%20Submission.ipynb">View on GitHub</a>
      </div>
    </article>
    <article class="sw-card">
      <div class="sw-card-top">
        <h3 class="sw-name"><a href="https://nbviewer.jupyter.org/github/sdcastillo/Jupyter-Contest/blob/master/Final%20Jupyter%20Submission.html">nbviewer</a></h3>
        <span class="sw-lang">Notebook</span>
      </div>
      <p class="sw-badge">Original link</p>
      <p class="sw-desc">The link from the original repository README, plus the short URL <a href="http://bit.ly/2LfHf9u">bit.ly/2LfHf9u</a>.</p>
      <div class="sw-actions">
        <a class="sw-btn sw-btn-source" href="https://nbviewer.jupyter.org/github/sdcastillo/Jupyter-Contest/blob/master/Final%20Jupyter%20Submission.html">Open in nbviewer</a>
      </div>
    </article>
  </div>
</section>

<section class="sw-section" id="map">
  <div class="sw-section-head">
    <h2>Where to start in the notebook</h2>
    <p>Jump straight to a section of the rendered submission.</p>
  </div>
  <nav class="sw-jumps" aria-label="Notebook sections">
    <a href="Final%20Jupyter%20Submission.html#Introduction">Introduction</a>
    <a href="Final%20Jupyter%20Submission.html#Quantile-Regression">Quantile regression</a>
    <a href="Final%20Jupyter%20Submission.html#Gradient-Boosting">Gradient boosting</a>
    <a href="Final%20Jupyter%20Submission.html#Application-1:-Adding-Prediction-Intervals-to-Risk-Scores">Risk scores</a>
    <a href="Final%20Jupyter%20Submission.html#Predicting-Quantiles">Predicting quantiles</a>
    <a href="Final%20Jupyter%20Submission.html#Application-2:-Data-Auditing-with-Outlier-Detection">Outlier audit</a>
    <a href="Final%20Jupyter%20Submission.html#Discussion">Discussion</a>
  </nav>
  <p>Also collected on <a href="https://sdcastillo.github.io/samwiki/">SamWiki</a>, the index of Sam Castillo’s public math, machine learning, and actuarial projects.</p>
</section>

<section class="sw-section" id="sources">
  <div class="sw-section-head">
    <h2>Sources the notebook names</h2>
    <p>Each card opens a source the submission already cites, and the same place in the rendered notebook. The <code>.ipynb</code> and the exported HTML in this repository are unchanged.</p>
  </div>
  <div class="sw-grid">
    <article class="sw-card">
      <div class="sw-card-top">
        <h3 class="sw-name"><a href="https://www.kaggle.com/datasets/mirichoi0218/insurance">Medical cost file</a></h3>
        <span class="sw-lang">Data</span>
      </div>
      <p class="sw-badge">Kaggle</p>
      <p class="sw-desc">1,338 patients. The notebook links this public file, the companion data for Brett Lantz’s <em>Machine Learning with R</em>.</p>
      <div class="sw-actions">
        <a class="sw-btn sw-btn-live" href="https://www.kaggle.com/datasets/mirichoi0218/insurance">Open the data</a>
        <a class="sw-btn sw-btn-source" href="Final%20Jupyter%20Submission.html#Data">In the notebook</a>
      </div>
    </article>
    <article class="sw-card">
      <div class="sw-card-top">
        <h3 class="sw-name"><a href="https://www.actuarialstandardsboard.org/asops/data-quality/">ASOP No. 23</a></h3>
        <span class="sw-lang">Standard</span>
      </div>
      <p class="sw-badge">ASB</p>
      <p class="sw-desc">Data Quality. The introduction quotes section 3.1: when the data are limited, say so.</p>
      <div class="sw-actions">
        <a class="sw-btn sw-btn-live" href="https://www.actuarialstandardsboard.org/asops/data-quality/">Read the standard</a>
        <a class="sw-btn sw-btn-source" href="Final%20Jupyter%20Submission.html#Introduction">In the notebook</a>
      </div>
    </article>
    <article class="sw-card">
      <div class="sw-card-top">
        <h3 class="sw-name"><a href="https://www.casact.org/library/studynotes/hardy4.pdf">Risk measures</a></h3>
        <span class="sw-lang">PDF</span>
      </div>
      <p class="sw-badge">CAS</p>
      <p class="sw-desc">The study note the notebook uses for Value at Risk as a quantile of the loss.</p>
      <div class="sw-actions">
        <a class="sw-btn sw-btn-live" href="https://www.casact.org/library/studynotes/hardy4.pdf">Open the note</a>
        <a class="sw-btn sw-btn-source" href="Final%20Jupyter%20Submission.html#Introduction">In the notebook</a>
      </div>
    </article>
    <article class="sw-card">
      <div class="sw-card-top">
        <h3 class="sw-name"><a href="https://www.statlearning.com/">Statistical learning</a></h3>
        <span class="sw-lang">Book</span>
      </div>
      <p class="sw-badge">ISL</p>
      <p class="sw-desc">Chapter 8.2 of <em>An Introduction to Statistical Learning</em> is the notebook’s boosting reference. The faculty page in the file no longer resolves.</p>
      <div class="sw-actions">
        <a class="sw-btn sw-btn-live" href="https://www.statlearning.com/">Open the book site</a>
        <a class="sw-btn sw-btn-source" href="Final%20Jupyter%20Submission.html#Gradient-Boosting">In the notebook</a>
      </div>
    </article>
    <article class="sw-card">
      <div class="sw-card-top">
        <h3 class="sw-name"><a href="https://doi.org/10.1177/1471082X18759142">Quantile regression, 2018</a></h3>
        <span class="sw-lang">Paper</span>
      </div>
      <p class="sw-badge">Journal</p>
      <p class="sw-desc">Elisabeth Waldmann, “Quantile regression: A short story on how and why,” <em>Statistical Modelling</em>. The notebook’s citation for work outside contest leaderboards.</p>
      <div class="sw-actions">
        <a class="sw-btn sw-btn-live" href="https://doi.org/10.1177/1471082X18759142">Open the paper</a>
        <a class="sw-btn sw-btn-source" href="Final%20Jupyter%20Submission.html#Quantile-Regression">In the notebook</a>
      </div>
    </article>
    <article class="sw-card">
      <div class="sw-card-top">
        <h3 class="sw-name"><a href="https://www.investopedia.com/terms/m/modernportfoliotheory.asp">Modern portfolio theory</a></h3>
        <span class="sw-lang">Primer</span>
      </div>
      <p class="sw-badge">Investopedia</p>
      <p class="sw-desc">The introduction’s comparison: a dollar forecast needs the spread around the average, not only the average.</p>
      <div class="sw-actions">
        <a class="sw-btn sw-btn-live" href="https://www.investopedia.com/terms/m/modernportfoliotheory.asp">Read the primer</a>
        <a class="sw-btn sw-btn-source" href="Final%20Jupyter%20Submission.html#Introduction">In the notebook</a>
      </div>
    </article>
  </div>
  <nav class="sw-jumps" aria-label="Further sources named in the notebook">
    <a href="https://en.wikipedia.org/wiki/Supervised_learning">Supervised learning</a>
    <a href="https://en.wikipedia.org/wiki/Interquartile_range">Interquartile range</a>
    <a href="https://scikit-learn.org/stable/">scikit-learn</a>
    <a href="https://www.kaggle.com/competitions">Kaggle competitions</a>
    <a href="https://towardsdatascience.com/regression-prediction-intervals-with-xgboost-428e0a018b">XGBoost intervals</a>
    <a href="https://towardsdatascience.com/quantile-regression-from-linear-models-to-trees-to-deep-learning-af3738b527c3">Quantile methods</a>
  </nav>
  <p>Supervised learning and the contest comparison are in <a href="Final%20Jupyter%20Submission.html#Quantile-Regression">Quantile regression</a>. The interquartile range is in the <a href="Final%20Jupyter%20Submission.html#Application-2:-Data-Auditing-with-Outlier-Detection">outlier audit</a>. scikit-learn and the two essays are in the <a href="Final%20Jupyter%20Submission.html#Discussion">discussion</a>.</p>
</section>

<section class="sw-section" id="related">
  <div class="sw-section-head">
    <h2>Other public pages</h2>
    <p>Separate notes on the same shelf. They are not part of the contest file. SamWiki lists them with this one.</p>
  </div>
  <div class="sw-grid">
    <article class="sw-card">
      <div class="sw-card-top">
        <h3 class="sw-name"><a href="https://sdcastillo.github.io/SOA-PA-Exam/">Exam PA notes</a></h3>
        <span class="sw-lang">Notes</span>
      </div>
      <p class="sw-badge">SOA</p>
      <p class="sw-desc">Open notes for the Society of Actuaries Predictive Analytics exam, June 2019 sitting: a business problem, a data set, and a report.</p>
      <div class="sw-actions">
        <a class="sw-btn sw-btn-live" href="https://sdcastillo.github.io/SOA-PA-Exam/">Open the notes</a>
        <a class="sw-btn sw-btn-source" href="https://github.com/sdcastillo/SOA-PA-Exam">Source</a>
      </div>
    </article>
    <article class="sw-card">
      <div class="sw-card-top">
        <h3 class="sw-name"><a href="https://sdcastillo.github.io/Predictive-Modeling-App/">Predictive Modeling App</a></h3>
        <span class="sw-lang">R</span>
      </div>
      <p class="sw-badge">Exam PA</p>
      <p class="sw-desc">An R Shiny explorer for Exam PA datasets, plus a modeling report scored on mean absolute error.</p>
      <div class="sw-actions">
        <a class="sw-btn sw-btn-live" href="https://sdcastillo.github.io/Predictive-Modeling-App/">Open the app page</a>
        <a class="sw-btn sw-btn-source" href="https://github.com/sdcastillo/Predictive-Modeling-App">Source</a>
      </div>
    </article>
    <article class="sw-card">
      <div class="sw-card-top">
        <h3 class="sw-name"><a href="https://sdcastillo.github.io/Consumer-Health-Cost-Ideas/">Health cost ideas</a></h3>
        <span class="sw-lang">Note</span>
      </div>
      <p class="sw-badge">Health</p>
      <p class="sw-desc">A separate note about people comparing what treatment cost and how it turned out. It is not this contest model.</p>
      <div class="sw-actions">
        <a class="sw-btn sw-btn-live" href="https://sdcastillo.github.io/Consumer-Health-Cost-Ideas/">Open the note</a>
        <a class="sw-btn sw-btn-source" href="https://github.com/sdcastillo/Consumer-Health-Cost-Ideas">Source</a>
      </div>
    </article>
    <article class="sw-card">
      <div class="sw-card-top">
        <h3 class="sw-name"><a href="https://sdcastillo.github.io/Kaggle-Advanced-Regression/">Housing prices</a></h3>
        <span class="sw-lang">R</span>
      </div>
      <p class="sw-badge">Contest</p>
      <p class="sw-desc">A 2018 Kaggle notebook on Ames sale prices, from a two-covariate line to a tuned XGBoost.</p>
      <div class="sw-actions">
        <a class="sw-btn sw-btn-live" href="https://sdcastillo.github.io/Kaggle-Advanced-Regression/">Open the page</a>
        <a class="sw-btn sw-btn-source" href="https://github.com/sdcastillo/Kaggle-Advanced-Regression">Source</a>
      </div>
    </article>
    <article class="sw-card">
      <div class="sw-card-top">
        <h3 class="sw-name"><a href="https://sdcastillo.github.io/Prior-Weights-with-XGboost/">Prior weights in XGBoost</a></h3>
        <span class="sw-lang">Method</span>
      </div>
      <p class="sw-badge">XGBoost</p>
      <p class="sw-desc">A per-row <code>base_margin</code> for sparse rows. The contest notebook’s further reading is a custom quantile loss, not this prior.</p>
      <div class="sw-actions">
        <a class="sw-btn sw-btn-live" href="https://sdcastillo.github.io/Prior-Weights-with-XGboost/">Open the note</a>
        <a class="sw-btn sw-btn-source" href="https://github.com/sdcastillo/Prior-Weights-with-XGboost">Source</a>
      </div>
    </article>
    <article class="sw-card">
      <div class="sw-card-top">
        <h3 class="sw-name"><a href="https://sdcastillo.github.io/samwiki/">SamWiki</a></h3>
        <span class="sw-lang">Index</span>
      </div>
      <p class="sw-badge">Catalog</p>
      <p class="sw-desc">The index entry for this contest notebook, next to the other public math and actuarial projects.</p>
      <div class="sw-actions">
        <a class="sw-btn sw-btn-live" href="https://sdcastillo.github.io/samwiki/">Open the index</a>
        <a class="sw-btn sw-btn-source" href="https://github.com/sdcastillo/Jupyter-Contest">This repository</a>
      </div>
    </article>
  </div>
</section>
