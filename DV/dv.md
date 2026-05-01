# Data Visualization

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
