# Data Visualization

- [Data Visualization](#data-visualization)
  - [Chapter 1 Intro to Data Visualization](#chapter-1-intro-to-data-visualization)
    - [Intro to Data Visualization](#intro-to-data-visualization)
    - [Types of Bad Figures](#types-of-bad-figures)
    - [Principles of Data Visualization](#principles-of-data-visualization)
    - [Aesthetic Mapping](#aesthetic-mapping)
    - [Mappings](#mappings)
    - [Effective Mapping](#effective-mapping)
    - [Use case and plots](#use-case-and-plots)
  - [Chapter 2 Effective Storytelling](#chapter-2-effective-storytelling)
    - [Narrative Structures](#narrative-structures)
    - [Designing for Decision Makers](#designing-for-decision-makers)
    - [Image format](#image-format)
  - [Chapter 3: Visualising Amount and Distribution](#chapter-3-visualising-amount-and-distribution)
    - [3.1 Showing Amounts (Comparing Categories)](#31-showing-amounts-comparing-categories)
      - [3.1a Bar Chart](#31a-bar-chart)
      - [3.1b Grouped Bar Plot](#31b-grouped-bar-plot)
      - [3.1c Stacked Bar Plot](#31c-stacked-bar-plot)
      - [3.1d Faceted Bar Plot](#31d-faceted-bar-plot)
      - [3.1e Dot Plot](#31e-dot-plot)
      - [3.1f Heatmap](#31f-heatmap)
    - [3.2 Visualising Distributions (Single Numerical Variable)](#32-visualising-distributions-single-numerical-variable)
      - [3.2a Histogram](#32a-histogram)
      - [3.2b Density Plot](#32b-density-plot)
      - [3.2c Comparing Multiple Distributions](#32c-comparing-multiple-distributions)
    - [3.3 Advanced Distribution Comparisons](#33-advanced-distribution-comparisons)
      - [3.3a ECDF (Empirical Cumulative Distribution Function)](#33a-ecdf-empirical-cumulative-distribution-function)
      - [3.3b Highly Skewed Distributions (e.g., power‑law)](#33b-highly-skewed-distributions-eg-powerlaw)
      - [3.3c Q‑Q Plot (Quantile‑Quantile Plot)](#33c-qq-plot-quantilequantile-plot)
    - [3.4 Visualising Many Distributions](#34-visualising-many-distributions)
      - [3.4a Boxplot](#34a-boxplot)
      - [3.4b Violin Plot](#34b-violin-plot)
      - [3.4c Strip Plot](#34c-strip-plot)
      - [3.4d Sina Plot](#34d-sina-plot)
    - [Quick Reference: Which Plot to Choose?](#quick-reference-which-plot-to-choose)
  - [Chapter 4: Visualising Proportions and Associations](#chapter-4-visualising-proportions-and-associations)
    - [4.1 Visualising Proportions](#41-visualising-proportions)
      - [4.1a Pie Chart](#41a-pie-chart)
      - [4.1b Grouped Bar Chart](#41b-grouped-bar-chart)
      - [4.1c Stacked Bar Chart](#41c-stacked-bar-chart)
      - [4.1d Stacked Density Plot](#41d-stacked-density-plot)
      - [4.1e Separate Density Plots](#41e-separate-density-plots)
    - [4.2 Visualising Nested Proportions](#42-visualising-nested-proportions)
      - [4.2a Mosaic Plot](#42a-mosaic-plot)
      - [4.2b Treemap](#42b-treemap)
    - [4.3 Visualising Associations](#43-visualising-associations)
      - [4.3a Scatter Plot](#43a-scatter-plot)
      - [4.3b Paired Data Visualisation](#43b-paired-data-visualisation)
  - [Chapter 5: Visualising Time Series and Trends](#chapter-5-visualising-time-series-and-trends)
    - [5.1 Visualising Time Series](#51-visualising-time-series)
      - [5.1a Individual Time Series](#51a-individual-time-series)
      - [5.1b Multiple Time Series](#51b-multiple-time-series)
    - [5.2 Visualising Trends](#52-visualising-trends)
      - [5.2a Smoothing](#52a-smoothing)
      - [5.2b Functional Fits](#52b-functional-fits)
  - [Chapter 6: Visualising Geospatial Data and Uncertainty](#chapter-6-visualising-geospatial-data-and-uncertainty)
    - [6.1 Visualising Geospatial Data](#61-visualising-geospatial-data)
    - [6.2 Visualising Uncertainty](#62-visualising-uncertainty)
      - [6.2a Framing Probabilities as Frequencies](#62a-framing-probabilities-as-frequencies)
      - [6.2b Uncertainty of Point Estimates](#62b-uncertainty-of-point-estimates)
  - [Chapter 7: Principles of Figure Design - Part 1](#chapter-7-principles-of-figure-design---part-1)
    - [7.1 Proportional Ink](#71-proportional-ink)
    - [7.2 Overlapping Points](#72-overlapping-points)
    - [7.3 Colour Use](#73-colour-use)
    - [7.4 Redundant Encoding](#74-redundant-encoding)
    - [7.5 Multi-Panel Figures](#75-multi-panel-figures)
      - [7.5a Small Multiples](#75a-small-multiples)
      - [7.5b Compound Figures](#75b-compound-figures)
  - [Chapter 8: Principles of Figure Design - Part 2](#chapter-8-principles-of-figure-design---part-2)
    - [8.1 Titles, Captions, Tables](#81-titles-captions-tables)
    - [8.2 Balance Data \& Content](#82-balance-data--content)
    - [8.3 Use Larger Axis Labels](#83-use-larger-axis-labels)
    - [8.4 Avoid Line Drawing](#84-avoid-line-drawing)
    - [8.5 Avoid 3D Effects](#85-avoid-3d-effects)

## Chapter 1 Intro to Data Visualization

### Intro to Data Visualization

- **Data visualization**: Graphical representation of information and data
- **Purpose**: To ease communication and interpretation involving data
- Must be **accurate** and **aesthetically effective**

### Types of Bad Figures

- **Ugly**: technically correct and readable but visually unappealing (e.g. bad color choices)
- **Bad**: technically correct but misleading (e.g. truncated y-axis, cluttered data points, unclear labels)
- **Wrong**: technically incorrect in terms of math or logic (e.g. pie chart with percentages that don't add up to 100%, missing data points, incorrect scales)

### Principles of Data Visualization

- **Accurate** - Convey the data accurately, not distort it
- **Clear** - Make it not overloaded with decorations
- **Effective** - Do not let aesthetic distract from the interpretation
- **Simple** - Respect the audience perceptual limits and avoid confusion
- **Balance** - Both design and correctness are important

### Aesthetic Mapping

- Process of mapping data variables to visual properties (e.g. color, size, shape)
- Allow audience to perceive patterns and relationships in the data
- Attributes:
  - **Position**
  - **Shape**
  - **Size**
  - **Color**
  - **Line width**
  - **Line type**
- Data Types and Aesthetic Mapping:
  - **Numerical Continuous**: size, position, color gradient
  - **Numerical Discrete**: shape, color hue
  - **Nominal**: shape, color hue
  - **Ordinal**: color hue, size

### Mappings

- Line Plot: position (x, y), line type, color
- Heatmap: position (x, y), color gradient

### Effective Mapping

- Match data type with appropriate aesthetic
- Avoid overloading with too many aesthetics
- Use legends and labels effectively
- Consistent across multiple visualizations

### Use case and plots

- **Amount**
  - Bar Chart
  - Dot Plot
  - Grouped/Stacked Bar Chart
  - Heatmap (2D categorical combinations)
- **Distribution**
  - Histogram
  - Density Plot
  - Cumulative Distribution (For purpose such as comparing distributions and percentiles)
  - Boxplot/Violin Plot/Strip plot
  - Ridgeline Plot
- **Proportion**
  - Pie Chart
  - Stacked Bar Chart
  - Grouped Bar Chart
  - Multivariate
    - Mosaic Plot
    - Treemap
    - Parallel Sets
- **X-Y Relationship**
  - Scatter Plot
  - Bubble Plot
  - Line Plot
  - Slope Chart
  - Connected Scatter Plot
  - High density
    - Contour Plot
    - 2D bin/hex plot
    - Correlogram (multiple variables)
- **Geospatial**
  - Maps
  - Choropleth Map: encode data with regions colored
  - Cartogram: distort region sizes based on data values
- **Uncertainty**
  - Error Bars
  - Graded Bars (multiple levels of uncertainty)
  - Confidence Bands
  - Distribution + Intervals (e.g. violin plot, quantile dot plot, half-eye plot)

## Chapter 2 Effective Storytelling

- Guide audience through logical progression of ideas, from context and research question to visual evidence and finally interpretation and implications
- **Story**: Tension -> Resolution

### Narrative Structures

- **Opening - Challenge - Action - Resolution**
  - **Opening**: Introduce settings, status quo, stakeholders, explain why the topic matters
  - **Challenge**: Create tension by presenting core problem, barriers and its business impact
  - **Action**: Describe steps taken to address the challenge, including data collection, analysis, validation and visualization
  - **Resolution**: Conclude the results and real world implications, next steps
- **Lead - Development - Resolution**
  - **Lead**: Include surprising insights to grab audience attention, provide summarised story such as core problem statement, purpose and brief outcome
  - **Development**: Present context, data work, modeling and key findings by building depth and explore the analytical process
  - **Resolution**: Wrap up with key takeaways, recommendations and next steps

### Designing for Decision Makers

- **Make a figure for the Generals**
  - Should be able to grasp the key message quick
  - Avoid complexity, jargon, unnecessary dimensions
  - Avoid overloading with too much information
- **Build up complexity gradually**
  - Introducing figures from simple to complex
- **Make figures memorable**
  - Add visual cues relevant to the context (isotypes, pictograms)
  - Use unique visual twist (without confusing the message)
- **Consistent but not repetitive**
  - Use consistent color schemes, fonts, layouts
  - Avoid using same style and type of figures repeatedly
  - Less uniformity helps signal transitions between different sections
  - Order the figures from raw/less processed to derived/more processed
  - 3 to 6 figures is a good number for scientific paper

### Image format

- Bitmap / Raster
  - Made of colored pixels
  - Resolution dependent
  - Lossless and lossy compression
- Vector
  - Store geometric descriptions of graphic elements
  - Redrawn at rendering time
  - Resolution independent
  - BUT platform dependent (fonts may not be available on all systems)
    - But can be mitigated by embedding fonts in the file
  - Complex figures may be large and slow to render
- Tradeoff between performance and fidelity
- Use vector for publication, print, archival; Use bitmap for interactive/online use
  - JPEG for photographs
  - PNG for line art/charts
  - SVG for icons, interactive graphics
- Store master file as SVG, so it can be easily converted to other formats as needed, and maintain a high quality master file for future use

## Chapter 3: Visualising Amount and Distribution

### 3.1 Showing Amounts (Comparing Categories)

#### 3.1a Bar Chart

- **Core idea:** Bar height (or length) represents the value.
- **Orientation:**
  - Vertical bars – standard.
  - Horizontal bars – better for long category names.

- **Ordering bars:**
  - Sort by value (descending) unless a natural order exists (time, age groups, etc.).

- **Common uses:**
  - Compare categories (sum, average, frequency).
  - Identify dominant categories.
  - Spot anomalies or uneven distributions.

- **Bad practices & solutions:**

| Bad Practice                | Why it’s a problem                          | How to fix                                                             |
| --------------------------- | ------------------------------------------- | ---------------------------------------------------------------------- |
| Rotated labels              | Hard to read, looks ugly                    | Use a horizontal bar chart                                             |
| Arbitrary bar order         | Hides patterns (trends, outliers, skewness) | Sort by value (or natural order)                                       |
| Y-axis not starting at zero | Misleads because our eyes compare bar areas | Always start y-axis at zero; use a dot plot if tiny differences matter |

#### 3.1b Grouped Bar Plot

- **When to use:** Two categorical variables.

- **Limitation:** Gets cluttered with many categories/groups → best for small numbers.

- **Requirement:** Colour legend.

- **Alternative:** Separate bar plots for each group (easier within-group comparison, harder across groups).

- **Use cases:**
  - Compare categories inside each group.
  - Compare the same category across groups.
  - Find interactions (trends, outliers, skewness).

#### 3.1c Stacked Bar Plot

- **When to use:** The total value per group is meaningful.

- **Drawback:** Hard to compare individual categories because baselines differ.

- **Good for:** Cumulative values (e.g., population pyramids).

- **Use cases:**
      - Compare total values across groups.
      - Compare category proportions within groups.
      - Spot patterns/interactions.

#### 3.1d Faceted Bar Plot

- **What it is:** One separate bar plot per group (small multiples).

- **Advantages:** Less cluttered, easier comparison.

- **Disadvantage:** Requires more space.

- **Use cases:** Same as grouped bar plots – comparing categories within/across groups.

#### 3.1e Dot Plot

- **Core idea:** Dots only (no bars). Y-axis need not start at zero.

- **Important:** Order categories properly to avoid a “cloud of points”.

- **Use cases:**
  - Comparing categories (sum, average, frequency).
  - Finding dominant categories.
  - Spotting anomalies / uneven distributions.
  - **Best when:** Differences are small, or many categories would make a bar chart cluttered.

#### 3.1f Heatmap

- **Core idea:** Colour intensity encodes amount in a 2D matrix.

- **Strengths:** Handles large datasets, shows patterns over time.

- **Weakness:** Hard to read exact values (emphasises patterns, not specifics).

- **Tip:** Arrange rows to tell a story.

### 3.2 Visualising Distributions (Single Numerical Variable)

#### 3.2a Histogram

- **How it works:** Data divided into equal‑width bins; bar height = frequency.

- **Use cases:**
  - Understand distribution shape.
  - Identify skewness, modality (peaks), outliers, spread.
  - Compare groups (using colour or facets).

- **Bad practices & solutions:**

| Bad Practice                | Problem                                             | Solution                                  |
| --------------------------- | --------------------------------------------------- | ----------------------------------------- |
| Too few bins                | Oversimplifies, hides features (skewness, modality) | Increase bins or use a density plot       |
| Too many bins               | Overcomplicates, creates noise                      | Decrease bins or use a density plot       |
| Inconsistent bin widths     | Misleading – exaggerates or hides features          | Use equal‑width bins                      |
| X‑axis not starting at zero | Distorts perception (especially near zero)          | Start x‑axis at zero; or use density plot |

#### 3.2b Density Plot

- **What it is:** Smoothed version of a histogram – a continuous curve (Kernel Density Estimation).

- **Use cases:**
  - Understand distribution shape (skewness, modality, outliers, spread).
  - Compare groups (colour or facets).
  - **Best when:** Many data points (histogram too cluttered) or focus is on shape rather than exact values.

- **Bad practices & solutions:**

| Bad Practice                                                                  | Problem                      | Solution                                               |
| ----------------------------------------------------------------------------- | ---------------------------- | ------------------------------------------------------ |
| Inappropriate bandwidth (too large)                                           | Oversmooths – hides features | Use smaller bandwidth                                  |
| Too small bandwidth                                                           | Undersmooths – creates noise | Use larger bandwidth                                   |
| Curve extends beyond data range (e.g., negative values for non‑negative data) | Misleading                   | Choose appropriate bandwidth and/or truncate the curve |

#### 3.2c Comparing Multiple Distributions

| Method                         | Pros                                             | Cons                                         |
| ------------------------------ | ------------------------------------------------ | -------------------------------------------- |
| **Stacked - histogram**        | (none notable)                                   | Baselines not aligned → very hard to compare |
| **Overlapping density - plot** | Good for 2+ categories, clear                    | –                                            |
| **Faceted density - plots**    | One plot per group (same axes) – easy comparison | Requires space                               |

> [!NOTE]
>
> For faceting, a full density plot can be added using greyscale in the background to show the overall distribution, while the coloured density plot in the foreground shows the group‑specific distribution.
>
> This allows for proportional comparison of the group distribution to the overall distribution, while still allowing for easy comparison across groups.

### 3.3 Advanced Distribution Comparisons

#### 3.3a ECDF (Empirical Cumulative Distribution Function)

- **What it shows:** Percentage of data ≤ x.

- **Y‑axis:** Can be normalised to show proportions.

- **Interpretation:**
  - Slope = density (steeper = higher density, flatter = lower density).
  - Easy to read: median, percentiles, cutoffs.
  - **Hard to read:** Modality (peaks).

#### 3.3b Highly Skewed Distributions (e.g., power‑law)

- **Problem:** Right‑skewed data (income, city population, word frequency) is hard to visualise.

- **Solution:** Log transformation.
  - **Log‑Log ECDF** – transform both axes. A power‑law appears as a straight line, making groups easy to compare.

- **Caution:** Log scales can be hard to interpret for some audiences.

#### 3.3c Q‑Q Plot (Quantile‑Quantile Plot)

- **What it does:** Compares quantiles of your data against a reference distribution (e.g., normal distribution).

- **How to read:**
  - Points follow a 45° line → data matches the reference.
  - S‑shaped curve → skewed (above line = right‑skewed, below = left‑skewed).
  - Inverted S‑shaped → bimodal (two peaks).

- **Common use:** Checking normality assumption.

### 3.4 Visualising Many Distributions

#### 3.4a Boxplot

- **Shows:** Five‑number summary (min, Q1, median, Q3, max).
  - Box = IQR (interquartile range), line = median.
  - Whiskers extend to most extreme points within 1.5×IQR.
  - Points beyond = outliers.

- **Use cases:**
  - Compare distributions across groups.
  - Identify skewness, outliers, spread.
  - **Best when:** Many data points (histogram/density would be cluttered) or focus on summary statistics.

- **Bad practice:** Using boxplot with <10 data points → misleading. Use a strip plot instead.

#### 3.4b Violin Plot

- **What it adds:** Density shape on both sides of the boxplot (width = density).

- **Advantages over boxplot:** Shows modality (multiple peaks) and overall shape.

- **Use cases:**
- Compare distributions across groups.
  - Show both summary stats and shape.
  - **Best when:** You suspect multiple modes, or many data points.

- **Bad practice:** Using violin plot with <10 data points → misleading. Use a strip plot instead.

#### 3.4c Strip Plot

- **What it is:** Individual data points as dots.

- **Problem:** Overplotting (dots overlap).

- **Solution:** Jittering – add tiny random noise horizontally to spread points. The density can be visually estimated from the jittered spread.

#### 3.4d Sina Plot

- **What it is:** Strip plot + violin plot. Points are jittered according to the violin’s width – dense regions spread points more.

- **Benefit:** Shows both individual points and the overall distribution shape.

### Quick Reference: Which Plot to Choose?

| Goal                                    | Recommended plot(s)                                        |
| --------------------------------------- | ---------------------------------------------------------- |
| Compare amounts across categories       | Bar chart (sorted), dot plot                               |
| Two categorical variables (few groups)  | Grouped bar plot (or faceted bars)                         |
| Two categorical variables (many groups) | Faceted bar plot, heatmap                                  |
| Distribution shape (one variable)       | Histogram, density plot                                    |
| Compare many distributions              | Overlapping density, faceted density, boxplot, violin plot |
| Show raw data + distribution            | Strip plot (jittered), sina plot                           |
| Check normality                         | Q‑Q plot, ECDF                                             |
| Highly skewed / power‑law data          | Log‑log ECDF                                               |

## Chapter 4: Visualising Proportions and Associations

### 4.1 Visualising Proportions

- Used in demographics, markets, surveys, etc.

#### 4.1a Pie Chart

- **Core idea:** Circle divided into slices representing category proportions.

- **Ordering Slices:**
  - Sort by size (largest to smallest) starting at 12 o’clock clockwise.

- **Use cases:**
  - Identify proportion at a glance.
  - Compre categories directly for simple fractions
  - Detecting imbalance or biases

- **Bad practices & solutions:**

| Bad Practice    | Problem                 | Solution                                               |
| --------------- | ----------------------- | ------------------------------------------------------ |
| Too many slices | Cluttered, hard to read | Limit to 5‑7 categories; group small ones into “Other” |
| 3D effects      | Distorts perception     | Avoid 3D effects; use a bar chart or dot plot instead  |
| No labels       | Unclear proportions     | Always include labels with percentages or values       |

- **Limitations:**
  - Not great for comparison across time or conditions.
  - Difficult to compare similar‑sized slices accurately.

#### 4.1b Grouped Bar Chart

- **Strengths:** Comparing category across groups, compare relative proportions within groups

- **Limitations:** No part-of-a-whole view

#### 4.1c Stacked Bar Chart

- **Strengths:** Shows part-of-a-whole and proportion comparisons across groups

- **Limitations:**
  - Hard to compare individual categories across groups due to different baselines
  - Hard to compare relative proportions within groups
  - Total values of groups are obscured, can be misleading if total values differ significantly across groups

#### 4.1d Stacked Density Plot

- **Strengths:** Shows part-of-a-whole and proportion comparisons across continuous variable (e.g. time, age)

- **Limitations:**
  - Total values of groups are obscured, data is distorted if total values differ significantly across groups

#### 4.1e Separate Density Plots

- **Strengths:** Shows part-of-a-whole of each group, as well as showing absolute values of each group, visual is not distorted by differences in total values across groups

- **Method:** Plot separate density plot for each group in color, and use greyscale in the background to show the overall distribution.

### 4.2 Visualising Nested Proportions

- When there are overlapping categories, pie charts is invalid, as the total is over 100%.

- Bar charts technically can be used, but it is still not showing the overlapped proportions clearly.

#### 4.2a Mosaic Plot

- **What it is:** A 2D extension of a bar chart, where the area of each rectangle represents the proportion of data in that category combination.

- **Strengths:** Shows proportions of each category combination, and allows for comparison across groups.

- **Limitations:** Assumes that all proportions shown can be identified via combination of two or more orthogonal categories, which may not always be the case.

#### 4.2b Treemap

- **What it is:** Similar to mosaic plot, but uses nested rectangles to show hierarchical relationships between categories.

- **Strengths:** Works well with proportions cannot meaningfully be described by combining multiple categorical variables, and can show hierarchical relationships between categories.

- **Limitations:** Can be difficult to compare proportions across groups.

### 4.3 Visualising Associations

- Show how two or more variables are related
- Reveal trends, clusters, outliers, correlations, etc.

| Trends                                 | Patterns                                                                                                  |
| -------------------------------------- | --------------------------------------------------------------------------------------------------------- |
| General **direction** of data points   | Recognisable **repeating** behaviour/structure                                                            |
| Long-term scope                        | Short- to medium-term scope (within trend)                                                                |
| Typically observed in time series data | Often observed in time series, but can also be in other types of data (e.g. spatial, cross-sectional)     |
| Eg. Upward trend in sales over years   | Seasonal peaks in sales every December, or daily patterns in website traffic (e.g. higher during daytime) |

#### 4.3a Scatter Plot

- **What it is:** Plots individual data points on a 2D plane, with one variable on the x-axis and another on the y-axis. Can add color, size, shape to encode groups. (Eg. bubble plot)

- **Insights:**
  - **Correlation**: Positive, negative, or no correlation.
  - **Variability**: How the spread of points changes across the range of x.
  - **Outliers**: Points that deviate significantly from the overall pattern.
  - **Clusters**: Groups of points that are close together, indicating subgroups or patterns in the data.

- **Limitations:**
  - Can be hard to read with large datasets (overplotting).
    - Solution: use transparency and/or jittering.
  - Correlation does not imply causation.
  - May require additional analysis (e.g. regression) to quantify relationships.

- **Scatter plot matrix**: A grid of scatter plots showing pairwise relationships between multiple variables (3~5 variables is manageable, more can be overwhelming). Useful for exploring subgroups and interactions, but can be hard to interpret with many variables.

- **Bubble plot**: A scatter plot where the size of the points represents a third variable. Can show three dimensions of data, but can be hard to read if there are many points or if the size differences are not clear.
  - Don't use radius to encode size, as it can exaggerate differences. Use area instead for better perception.

#### 4.3b Paired Data Visualisation

- Using scatter plot to show paired data (e.g. CO2 emissions of countries in 1990 vs 2020) can reveal changes over time, identify outliers, and show overall trends. Adding a reference line (e.g. y=x) can help identify if the trend is increasing or decreasing.

- Using slope plot can reveal change over time grouped by categories (e.g. CO2 emissions of countries in 1990 vs 2020, grouped by country). Each line represents a country, and the slope of the line indicates the change in emissions. This can help identify which countries have increased or decreased their emissions, and by how much.

## Chapter 5: Visualising Time Series and Trends

### 5.1 Visualising Time Series

- Time: special independent variable with unique properties (e.g. autocorrelation, seasonality, trends)

#### 5.1a Individual Time Series

- **Scatter plot**: Shows individual data points over time, useful for identifying trends, variability, and outliers. Can be enhanced with a line of best fit to show overall trend.

- **Line plot**: Guide the eye to see trends and patterns over time
  - Dots can be removed to deemphasise individual points and focus on the overall trend. (Avoid cluttering with dense time points)
  - Not useful for sparse time points, as it may imply a continuous trend that does not exist.
  - Adding area shading can emphasise the overarching temporal pattern, but only use it if baseline = 0

#### 5.1b Multiple Time Series

- **Scatter plot** is NOT ideal as it can get cluttered and hard to read with multiple series.

- **Line plot** is good for showing multiple time series. Label at the end of each line can help identify which series is which without needing a legend.

### 5.2 Visualising Trends

- Trend sometimes much more important than the actual values, showing individual data points can be distracting.

#### 5.2a Smoothing

- **Moving Average:** Simple, but the smoother the curve, the more it lags behind the actual data, the shorter the curve is.

- **LOESS (Locally Estimated Scatterplot Smoothing):** Fit local polynomial regression to the data

  | Strengths                                   | Limitations                         |
  | ------------------------------------------- | ----------------------------------- |
  | Non-linear trends                           | Slower for large datasets           |
  | No need to specify a global functional form | Sensitive to outliers               |
  | Flexible and interpretable                  | Smoothing choice can affect results |

- **Spline Smoothing:** Fit piecewise polynomials to the data, with continuity constraints at the knots (where pieces join).
  - More flexible than LOESS, can capture more complex trends, but can also be more sensitive to noise and outliers. The choice of knot placement can also affect the results.

> [!CAUTION]
> Different methods of smoothing can lead to different trends. Check the robustness of the trend by trying multiple smoothing methods and parameters. Show data points along with the smoothed curve to provide context and avoid misleading interpretations.

#### 5.2b Functional Fits

- Use parametric models (linear or exponential) to fit the data and show the fitted curve.

- Interpretable parameters (e.g. slope) can provide insights into the rate of change, but the model assumptions must be checked (e.g. linearity, homoscedasticity, normality of residuals).

- Usually better to fit a straight line to transformed data (e.g. log transformation for exponential growth) rather than fitting a non-linear curve to untransformed data, as it is easier to interpret and check assumptions.

- Log-Linear plot (Exponential growth)

- Log-Log plot (Power-law growth)

- Linear-Log plot (Logarithmic growth)

## Chapter 6: Visualising Geospatial Data and Uncertainty

### 6.1 Visualising Geospatial Data

- Maps are better at showing spatial context
- Challenge: distortion, scaling, layering choices
- Essential Map Elements:
  - **Scale bar**: Shows distance on the map.
  - **North arrow**: Indicates map orientation.
  - **Labels**: Ensure not to clutter the map; use clear fonts and appropriate sizes.

- **Choropleth Map**: Color regions based on data values (e.g. population density).
  - **Common Mistakes**: Variables are not normalized (e.g. total population instead of population density) → misleading. Values should relate to the area being colored.
  - Continuous scale is smooth but hard to read; Discrete bins has clearer category boundary.

### 6.2 Visualising Uncertainty

- All data has uncertainty
- Need to show range of plausible values
- Avoid false sense of certainty.
- Typical audience: Researchers and knowledgeable stakeholders who understand the concept of uncertainty and its implications for decision-making.

#### 6.2a Framing Probabilities as Frequencies

- People understand frequencies better than probabilities.

- Example: Instead of saying “There is a 20% chance of rain tomorrow,” say “In 100 days with similar conditions, it rained on 20 of those days.”
  - This can be visualised with a grid of 10x10 squares, where 20 randomly selected squares are colored to represent the 20% chance of rain. This makes the concept of probability more concrete and easier to grasp for many people.

- Bell curve can be used to show the distribution of possible outcomes, with shaded areas representing the probability of different ranges of outcomes. This can help convey the idea of uncertainty and the likelihood of various scenarios.

#### 6.2b Uncertainty of Point Estimates

- **Error Bars**: Single interval around a point estimate (e.g. mean ± standard error). Shows the range of plausible values for the estimate.

- **Graded Error Bars**: Multiple intervals (e.g. 50%, 75%, 95% confidence intervals) to show different levels of uncertainty. Use of color intensity and width can help differentiate the intervals. Caps can be added to error bars to improve readability.

- **Statistical Significance**: Can be shown using error bars crossing a reference line (e.g. zero). No crossing = statistically significant

> [!NOTE]
> Match the data to audience, and always annotate what do the uncertainty infers for the real world implications. (Why does it matter to show uncertainty? What does it mean for decision making?)

## Chapter 7: Principles of Figure Design - Part 1

### 7.1 Proportional Ink

- Proportional ink means that the visual representation of data should be proportional to the actual values being represented.
  - For example, if one category has twice the value of another, its visual representation (e.g. bar height) should also be twice as large.

- Don't use shadings for plot that doesn't use baseline of zero, as well as plot that is log-transformed, as the area can be misleading.

- Prefer bars or dots as they are easier to read and compare

- Don't use radius encoding

### 7.2 Overlapping Points

- **Overplotting:** Many points overlap, making it hard to see density and patterns.

- Solution
  - **Transparency:** Make points semi-transparent to show density (darker areas = more points).
  - **Jittering:** Add small random noise to point positions to spread them out and reveal density. (Too much = distortion = misleading)
  - **Hexbinning:** Divide the plot into hexagonal bins and color them based on the number of points in each bin. This can show density without overplotting, but individual points are lost.

### 7.3 Colour Use

- Roles
  - **Distinguish categories** (qualitative)
    - Qualitative color schemes has distinct hues that are easily distinguishable, for categorical data without inherent order, eg. Okabe Ito
  - **Encode data values** (quantitative)
    - **Sequential**: Gradient of a single hue varying in intensity/saturation, for unidirectional data, eg. viridis
    - **Diverging**: Two contrasting hues diverging from a neutral midpoint, for data with meaningful center, eg. Blue-Red
  - **Highlight/Accentuate** important elements (e.g. outliers, trends, top categories), darken the element to make it stand out, and use a more muted color for the rest of the elements to avoid distraction.

- Pitfalls
  - **Too many colors**
    - Cluttering
    - Overwhelming
    - Distracting
    - Use limited color palette (5-7 colors) and use color strategically to highlight key information.
    - Eg. Group states into regions and use a different color for each region, rather than using a different color for each state.
  - **Rainbow scale for quantitative data**
    - Not monotonic
    - Mislead due to brightness fluctuations and nonlinear perception of hues
    - Map intensity to value
    - Perform grayscale test to check if the color scheme is interpretable
  - **Ignoring CVD (Color Vision Deficiency)**
    - Don't use red-green color schemes, as they are the most common type of color blindness (deuteranopia and protanopia).
    - Use colorblind-friendly palettes (e.g. Okabe Ito, ColorBrewer)
    - Use redundant encoding (e.g. shape, pattern) to differentiate categories in addition to color
    - For overlapping points of 2 groups in scatter plots, use distinct colors, and redundant encoding (e.g. shape, pattern) to differentiate the groups
    - For line plots, order the labels at the end of each line according to the end value of the line, so it can be easily identified without needing to rely on color alone. Can use line type (e.g. solid, dashed) to differentiate lines in addition to color.

### 7.4 Redundant Encoding

- Improves accessibility

- Use combinations of color, shape, and pattern to differentiate categories

- Use direct labelling to avoid reliance on legends, since lookup can be difficult and error-prone
  - Eg. Add text labels with color matching the data points directly inside the plot area, next to the corresponding data points, lines, or peaks

### 7.5 Multi-Panel Figures

#### 7.5a Small Multiples

- Faceting same chart type

- **Ensure consistency** across panels (same axes, ranges, scales, colors) to allow for easy comparison.

- **Arrange panels** in a logical order (e.g. by time, category, or value) to guide the audience through the story.

#### 7.5b Compound Figures

- Different chart types in the same figure

- Ensure consistent visual language (e.g. color scheme, fonts, layout) across different chart types to create a cohesive figure. Only one legend should be used for the entire figure, and it should be placed in a clear and consistent location (e.g. top right corner) to avoid confusion.

- Ensure plots are aligned properly (axes, grid, labels, range), with consistent spacing and margins.

- Use subtle panel labels (e.g. a, b, c) to help the audience navigate between different plots.

## Chapter 8: Principles of Figure Design - Part 2

### 8.1 Titles, Captions, Tables

- Use clear, concise and assertive titles that summarize the main message of the figure.

- Use captions to provide additional context, explain the data, and highlight key insights.

- Use clear axes labels with units, omit only when the meaning is obvious (e.g. time, country name, movie title, etc.)

- Use (a), (b) labels for multi-panel figures to help the audience navigate between different plots, as well as brief descriptions of each panel in the caption.

- **Tables**
  - Don't use vertical lines
  - Use horizontal lines as separators only (e.g. after header row, and at the end of the table)
  - Left align text columns
  - Right align numeric columns, and use consistent number of decimal places
  - Center align single character columns
  - Header align according to the data
  - Bold the header row
  
- **Captions**
  - Below figure
  - Above table

### 8.2 Balance Data & Content

- **Data Elements**: Points, bars, lines

- **Context Elements**: Axes, gridlines, labels

- Ensure context elements are enough to support interpretation, but avoid cluttering the figure and distracting from the data. Use subtle colors and thin lines for context elements, and avoid unnecessary gridlines or tick marks.

- Use light grids

- Use only horizontal or vertical gridlines, not both, UNLESS there is no primary axis (like scatter plot)

- Avoid dense/dark gridlines that can compete with the data for attention

- Use reference lines (y=100 for index, y=0 for change) to help interpret the data, but make them subtle and not overpowering.

### 8.3 Use Larger Axis Labels

- Labels carry important context

- Tiny text = hard to read, and may be ignored

- Consider scaled down when printing

- But if it is too large, it can be distracting and take up too much space, so find a balance that is readable but not overwhelming.

- Axis Title > Tick Labels > Legend Labels

### 8.4 Avoid Line Drawing

- Prefer filled shapes

- Use transparency for overlapping

- Thin borders only if really needed (Eg. reference lines, axes, highlight or boundaries)

### 8.5 Avoid 3D Effects

- 3D effects add distortion but not information

- Create depth and perspective, hard to align data with axes

- Only use 3D when the third dimension (depth) is meaningful, such as in a 3D scatter plot where the z-axis represents a third variable.

  > [!NOTE]
  > Consider using a 2D scatter plot with color or size encoding for the third variable instead, as it can be easier to read and interpret.
