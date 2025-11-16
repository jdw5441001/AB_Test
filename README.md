# 📊 A/B Test Calculator with Segmentation

A comprehensive, user-friendly A/B testing calculator built for Jupyter notebooks (Databricks compatible) that provides statistical analysis, visualization, and actionable insights for experimentation programs.

## 🎯 Overview

This interactive calculator helps you analyze A/B test results with detailed statistical rigor while remaining accessible to non-statisticians. It includes:

- **Statistical Significance Testing** - Two-proportion z-test with customizable confidence levels
- **Randomization Quality Checks** - Sample Ratio Mismatch (SRM) detection and independence validation
- **Segment Analysis** - Break down results by user groups to find hidden patterns
- **Revenue Impact Projection** - Estimate annual financial impact of your changes
- **Visual Analytics** - Beautiful charts that explain the statistical reasoning
- **Plain-Language Explanations** - Every metric comes with clear, jargon-free descriptions

## 🚀 Quick Start

### Prerequisites

```python
pip install ipywidgets numpy pandas scipy matplotlib
```

### Installation

1. Clone this repository:
```bash
git clone https://github.com/yourusername/ab-test-calculator.git
```

2. Copy the `ab_test_calculator.py` file into your Databricks notebook or Jupyter environment

3. Run all cells to launch the interactive UI

### Basic Usage

1. **Configure Your Test Settings**
   - Select confidence level (90%, 95%, or 99%)
   - Enter test duration and user return frequency
   - Specify expected traffic split

2. **Enter Your Test Data**
   - Control group: visitors and conversions
   - Treatment group: visitors and conversions
   - Optional: Monthly revenue for impact calculations

3. **Click "Calculate Results"**
   - View statistical significance
   - Check randomization quality
   - Analyze segment performance (if enabled)
   - Get actionable recommendations

## 📋 Features

### Core Statistical Analysis

- **Two-Proportion Z-Test**: Industry-standard method for comparing conversion rates
- **Confidence Intervals**: Understand the range of possible true effects
- **P-Value Calculation**: Determine probability results are due to chance
- **Effect Size (Lift)**: Both absolute (percentage points) and relative (%) improvements

### Quality Assurance

#### Sample Ratio Mismatch (SRM) Detection
Automatically detects if your traffic split deviates significantly from expectations, which could indicate:
- Buggy randomization implementation
- Bot traffic
- User switching between groups

#### Test Duration Assessment
Checks if your test ran long enough to:
- Capture weekly patterns (weekday vs. weekend)
- Allow for user independence
- Provide reliable results

#### User Overlap Analysis
Identifies if users saw both Control and Treatment variants, which can bias results

### Advanced Features

#### Segment Analysis
Break down results by user groups:
- Mobile vs. Desktop
- New vs. Returning customers
- Geographic regions
- Age groups, subscription tiers, etc.

**Benefits:**
- Find which user segments benefit most from changes
- Identify negative impacts on specific groups
- Enable personalized rollout strategies

#### Revenue Impact Projection
Automatically calculates estimated annual revenue impact based on:
- Current monthly revenue
- Observed lift in conversion rate
- Seasonal multipliers (optional)

### Visualizations

1. **Randomization Quality Charts**
   - Expected vs. actual traffic split
   - SRM statistical test
   - Split stability analysis
   - Overall quality scorecard

2. **Statistical Distribution Charts**
   - Null hypothesis distribution
   - P-value visualization
   - Confidence interval overlay
   - Statistical power analysis

3. **Segment Comparison Charts**
   - Conversion rates by segment
   - Relative lift by segment
   - Summary table with significance markers

## 📊 Example Use Cases

### E-Commerce: Testing a New Checkout Flow

```
Scenario: You redesigned your checkout page and want to know if it improves purchases.

Inputs:
- Control: 10,000 visitors, 1,200 purchases (12% conversion)
- Treatment: 10,000 visitors, 1,350 purchases (13.5% conversion)
- Test Duration: 14 days
- Monthly Revenue: $500,000

Results:
- Relative Lift: +12.5%
- P-Value: 0.0089 (Significant at 95% confidence)
- Projected Annual Revenue Impact: +$75,000
- Recommendation: ✅ LAUNCH - Treatment significantly outperforms Control
```

### SaaS: Testing Email Subject Lines

```
Scenario: Testing two subject lines for your onboarding email campaign.

Inputs:
- Control: 5,000 emails, 750 opens (15% open rate)
- Treatment: 5,000 emails, 800 opens (16% open rate)
- Test Duration: 7 days

Results:
- Relative Lift: +6.7%
- P-Value: 0.1523 (Not Significant at 95% confidence)
- Recommendation: ⚠️ MORE DATA NEEDED - Continue testing or accept neutral result
```

### Mobile App: Feature Test with Segmentation

```
Scenario: Testing a new navigation menu, segmented by user type.

Overall Results:
- Lift: +3.2% (Marginally significant)

Segment Results:
- New Users: +15.2% lift (✅ Significant)
- Returning Users: -2.1% lift (❌ Significant negative)

Recommendation: 🎯 TARGETED ROLLOUT - Deploy only to new users
```

## 🎓 Understanding the Statistics

### Key Metrics Explained

#### Conversion Rate
**What it is:** Percentage of users who completed your desired action  
**Example:** 1,200 purchases ÷ 10,000 visitors = 12% conversion rate

#### Statistical Significance
**What it is:** Confidence that results aren't due to random chance  
**Rule of thumb:** P-value < 0.05 (5%) is typically considered significant  
**What it means:** Less than 5% probability the results happened by luck

#### P-Value
**What it is:** Probability your results are due to random chance  
**How to read it:**
- P < 0.01: Very strong evidence
- P < 0.05: Strong evidence (standard threshold)
- P < 0.10: Moderate evidence
- P > 0.10: Weak/no evidence

#### Confidence Interval
**What it is:** Range where the true effect likely falls  
**Example:** [+0.8%, +2.2%] at 95% confidence  
**What it means:** We're 95% confident the true lift is between 0.8% and 2.2%  
**Key insight:** If the interval doesn't include zero, you have a clear winner!

#### Lift (Effect Size)
**Absolute Lift:** Raw percentage point difference (13.5% - 12% = +1.5pp)  
**Relative Lift:** Percentage improvement (+1.5pp / 12% = +12.5%)

### Sample Size Matters

**Small samples** (< 1,000 per group):
- Results can be noisy
- May miss small but meaningful effects
- Higher risk of false conclusions

**Medium samples** (1,000 - 10,000 per group):
- Good for detecting medium effects (2-5% lift)
- Standard for most tests
- Reliable for major decisions

**Large samples** (10,000+ per group):
- Can detect small effects (< 2% lift)
- Very reliable results
- May find "statistically significant" but practically insignificant differences

### Common Pitfalls to Avoid

#### 1. Peeking Problem
**Don't:** Stop your test early because results look good  
**Why:** Increases false positive rate  
**Do:** Pre-determine test duration and stick to it

#### 2. Multiple Testing
**Don't:** Run 20 tests at 95% confidence and expect all significant results to be real  
**Why:** Pure chance will give you ~1 false positive  
**Do:** Use segment analysis carefully and adjust confidence levels if testing many hypotheses

#### 3. Ignoring Practical Significance
**Don't:** Launch a change just because p < 0.05  
**Why:** Tiny improvements may not be worth implementation costs  
**Do:** Consider both statistical AND practical significance

#### 4. Sample Ratio Mismatch
**Don't:** Ignore warnings about traffic split issues  
**Why:** Indicates fundamental problems with test implementation  
**Do:** Fix technical issues before trusting results

## 📐 Statistical Methods

### Two-Proportion Z-Test
This calculator uses the standard frequentist approach for comparing two proportions:

```
Z = (p₁ - p₂) / SE
where SE = √[p̂(1-p̂)(1/n₁ + 1/n₂)]
p̂ = pooled conversion rate
```

### Confidence Intervals
Calculated using the Wald method:
```
CI = (p₁ - p₂) ± Z* × SE
```

### Sample Ratio Mismatch Test
Chi-square goodness-of-fit test:
```
χ² = Σ[(Observed - Expected)² / Expected]
```
Flags when p-value < 0.001 (highly unlikely by chance)

## 🛠️ Customization

### Adjusting Confidence Levels

```python
# Available options in the dropdown:
# 90% - Less strict, faster decisions, higher false positive risk
# 95% - Industry standard, balanced approach
# 99% - Very conservative, slower decisions, minimal false positive risk
```

### Modifying Revenue Calculations

```python
# Seasonal adjustment examples:
seasonal_multiplier = 1.0   # Normal season
seasonal_multiplier = 1.5   # 50% above normal (e.g., holidays)
seasonal_multiplier = 0.7   # 30% below normal (e.g., slow season)
```

### Adding Custom Segments

Enable segment analysis and create groups based on:
- Device type (mobile, tablet, desktop)
- User status (new, returning, churned)
- Geography (country, region, timezone)
- Demographics (age, gender, subscription tier)
- Behavior (high-value, low-engagement, etc.)

## 📊 Interpreting Results

### Decision Framework

| P-Value | Lift | Confidence Interval | Decision |
|---------|------|---------------------|----------|
| < 0.05 | Positive | Above zero | ✅ **LAUNCH** - Clear winner |
| < 0.05 | Negative | Below zero | ❌ **DON'T LAUNCH** - Treatment worse |
| > 0.05 | Any | Includes zero | ⚠️ **INCONCLUSIVE** - Need more data or neutral |
| < 0.05 | Small | Narrow, above zero | 🤔 **EVALUATE** - Significant but is it meaningful? |

### Segment Analysis Patterns

**Pattern 1: Universal Winner**
- All segments show positive lift
- **Action:** Full rollout to all users

**Pattern 2: Mixed Results**
- Some segments positive, others negative
- **Action:** Personalized rollout or redesign

**Pattern 3: No Clear Pattern**
- Results vary but nothing significant
- **Action:** Treatment likely has no real impact

**Pattern 4: Opposite of Overall**
- Overall positive, but key segment negative
- **Action:** Investigate before launching

## 🔧 Troubleshooting

### "Sample Ratio Mismatch Detected"
**Cause:** Traffic split deviates significantly from expected  
**Fix:** 
- Check randomization code for bugs
- Look for bot traffic or data quality issues
- Verify users aren't switching between groups

### "Test Duration Too Short"
**Cause:** Test ran for less than recommended time  
**Fix:**
- Continue running test to 14+ days
- Or accept results with caveat about limited data

### "High User Overlap"
**Cause:** Users seeing both Control and Treatment  
**Fix:**
- Implement persistent user IDs or cookies
- Use account-based bucketing instead of session-based
- Clean data to exclude users who saw both

### Results Change Dramatically Day-to-Day
**Cause:** Small sample size or confounding factors  
**Fix:**
- Run longer to accumulate more data
- Check for external events (holidays, outages, etc.)
- Ensure consistent traffic allocation

## 📚 Best Practices

### Pre-Test Planning

1. **Define Success Metrics** - What are you measuring?
2. **Calculate Required Sample Size** - How long to run?
3. **Set Up Proper Randomization** - User-level bucketing
4. **Document Hypotheses** - What do you expect and why?

### During Testing

1. **Don't Peek!** - Resist checking results early
2. **Monitor Technical Health** - Check for SRM daily
3. **Watch for Anomalies** - Sudden traffic changes, outages
4. **Maintain Consistency** - Don't change test mid-flight

### Post-Test Analysis

1. **Check Randomization Quality** - Review all SRM warnings
2. **Validate Against Guardrail Metrics** - Did anything break?
3. **Perform Segment Analysis** - Find hidden patterns
4. **Document Learnings** - Even "failed" tests are valuable

### Launch Strategy

1. **Gradual Rollout** - Don't go 0% → 100% instantly
2. **Monitor Key Metrics** - Watch for regression
3. **Have Rollback Plan** - Be ready to revert if needed
4. **Measure Long-Term Impact** - Do gains persist?

## 🤝 Contributing

Contributions are welcome! Here are areas for enhancement:

- **Bayesian Methods**: Add optional Bayesian analysis
- **Sequential Testing**: Support for early stopping rules
- **CUPED/Variance Reduction**: More advanced statistical techniques
- **Export Functionality**: Download results as PDF/CSV
- **API Integration**: Connect to data warehouses
- **A/A Test Validation**: Built-in test of randomization

## 📄 License

MIT License - feel free to use this in your own projects!

## 🙏 Acknowledgments

Built with:
- **ipywidgets** - Interactive UI components
- **scipy** - Statistical functions
- **matplotlib** - Data visualization
- **pandas** - Data manipulation
- **numpy** - Numerical computing

## 📞 Support

Found a bug? Have a question? Want to request a feature?

- Open an issue on GitHub
- Check existing documentation in the UI helper text
- Review the troubleshooting section above

## 🎯 Roadmap

Future enhancements planned:

- [ ] Multi-variant testing (A/B/C/D)
- [ ] Bayesian A/B testing option
- [ ] Integration with common analytics platforms
- [ ] Automated test duration calculator
- [ ] Power analysis before test launch
- [ ] Historical test comparison
- [ ] Export to presentation format

---

**Made with ❤️ for data-driven decision making**

*Last Updated: 2024*
```

This README provides:

1. **Clear Overview** - What the tool does and why it's useful
2. **Quick Start Guide** - Get up and running in minutes
3. **Detailed Feature Documentation** - Everything the calculator can do
4. **Real-World Examples** - Concrete use cases with sample data
5. **Statistical Education** - Explains key concepts in plain language
6. **Best Practices** - How to run good experiments
7. **Troubleshooting Guide** - Common issues and solutions
8. **Decision Frameworks** - How to interpret and act on results
9. **Contribution Guidelines** - How others can help improve it

The README is structured to be useful for both beginners (who can read the "Understanding the Statistics" section) and experienced practitioners (who can dive into the technical details and customization options).
