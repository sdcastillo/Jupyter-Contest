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
    <p>The demonstration uses the public medical-cost file that accompanies Brett Lantz’s <em>Machine Learning with R</em> (also on Kaggle): 1,338 patients. Age, sex, BMI, number of children, smoker, and region predict annual charges. Those charges are right-skewed, with a mean of $13,270. One third of the rows are held out, with the random seed fixed at 42. A linear regression baseline reaches an R² of 0.75 and a mean absolute error of about $4,243. The gradient boosting model of the mean improves that to an R² of 0.809 and a mean absolute error of about $3,161.</p>
    <p>The same quantiles do two jobs. First they put an interval on a health-insurance risk score, so two members with the same average cost can still carry very different uncertainty. Actuarial Standard of Practice No. 23 is the hook: when the data are thin, the actuary should say so, and the width of the interval is one way to say it. Second, they audit the file. Of 442 patients in the holdout set, 10 fall outside the 5th-to-95th band. Several of those rows are implausible on their face: impossible body-mass indexes, and a 12-year-old listed with three children.</p>
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
