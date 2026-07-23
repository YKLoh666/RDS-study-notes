# Machine Learning Notes

- [Machine Learning Notes](#machine-learning-notes)
  - [Chapter 4: Convolutional Neural Networks (CNNs)](#chapter-4-convolutional-neural-networks-cnns)
    - [Convolution Layer](#convolution-layer)
    - [Pooling Layer](#pooling-layer)
    - [Dense Layer](#dense-layer)
  - [Chapter 5: Regression Model Evaluation Metrics](#chapter-5-regression-model-evaluation-metrics)
  - [Chapter 6: Model Generalization, Validation, and Parameter Regularization](#chapter-6-model-generalization-validation-and-parameter-regularization)
    - [Model Generalization](#model-generalization)
    - [Validation Techniques](#validation-techniques)
    - [Regularization Techniques](#regularization-techniques)
  - [Chapter 7: Interpolation and Extrapolation, Linear Regression](#chapter-7-interpolation-and-extrapolation-linear-regression)
    - [Interpolation vs Extrapolation](#interpolation-vs-extrapolation)
    - [Linear Regression](#linear-regression)
    - [Optimise Linear Regression Training](#optimise-linear-regression-training)
  - [Chapter 8: Dimensionality Reduction](#chapter-8-dimensionality-reduction)
    - [Feature Selection](#feature-selection)
    - [Dimensionality Reduction Algorithms](#dimensionality-reduction-algorithms)
  - [Chapter 9: Decision Tree](#chapter-9-decision-tree)
    - [Impurity Measures: Entropy](#impurity-measures-entropy)
    - [Impurity Measures: Gini Index](#impurity-measures-gini-index)
    - [Information Gain (IG)](#information-gain-ig)
    - [Classification Error](#classification-error)
  - [Chapter 10: Distance Metrics](#chapter-10-distance-metrics)
    - [Euclidean Distance](#euclidean-distance)
    - [Manhattan Distance](#manhattan-distance)
    - [Cosine Distance](#cosine-distance)
    - [Jaccard Distance](#jaccard-distance)
    - [Comparison of Distance Metrics](#comparison-of-distance-metrics)
  - [Chapter 11: Unsupervised Learning Algorithms](#chapter-11-unsupervised-learning-algorithms)
    - [Hierarchical Agglomerative Clustering](#hierarchical-agglomerative-clustering)
    - [Cluster Linkage Methods](#cluster-linkage-methods)
    - [K-Means Clustering](#k-means-clustering)
    - [Inertia](#inertia)
    - [K-Means vs Hierarchical Clustering](#k-means-vs-hierarchical-clustering)
    - [DBSCAN](#dbscan)
    - [Gaussian Mixture Model (GMM)](#gaussian-mixture-model-gmm)
    - [Mean Shift](#mean-shift)
    - [Spectral Clustering](#spectral-clustering)
    - [Fuzzy C-Means Clustering](#fuzzy-c-means-clustering)
    - [LDA](#lda)
    - [LSA](#lsa)

## Chapter 4: Convolutional Neural Networks (CNNs)

- Convolutional Neural Networks (CNNs), deep learning models, well-suited for image recognition and processing tasks.
- Convolution Advantages:
  - **Parameter Sharing**: Reduces the number of parameters by using the same filter (kernel) across different parts of the input.
  - **Sparsity of Connections**: Each neuron is connected to only a small region of the input, which helps in capturing local patterns.
- Key Components of CNNs:
  - **Convolutional Layers**: Apply filters to the input to create feature maps.
  - **Pooling Layers**: Reduce the spatial dimensions of the feature maps, typically using max pooling or average pooling.

### Convolution Layer

- Involves a sliding window (filter/kernel) that moves across the input data and performs element-wise multiplication and summation.
- **Filter/Kernel**: A small matrix that is convolved with the input, associated with weights that are learned during training.
  - Can have multiple filters, each filter outputting a different feature map, which stacks as channels of the output map.
- Hyperparameters:
  - **Filter Size ($F$)**: Size of the filter (e.g., 3x3, 5x5).
  - **Stride ($S$)**: Step of shift of the filter across the input.
  - **Padding ($P$)**: Adding zeros around the input to control the spatial size of the output.
- Output Dimension Calculation:
  $$ \text{W}_{\text{out}} = \lfloor\frac{(W - F + 2P)}{S} + 1 \rfloor $$
  $$ \text{H}_{\text{out}} = \lfloor\frac{(H - F + 2P)}{S} + 1 \rfloor $$
  - $W$: Input width
  - $H$: Input height
  - $\lfloor \cdot \rfloor$: Floor function
- Operation
  1. Input data is in the dimension of (`height`, `width`, `channel`).
     - Channels represent color channels (e.g., RGB) or feature maps from previous layers.
  2. Pad the input data with zeros if padding is specified.
  3. The filter slides over the input data.
  4. At each position, perform element-wise multiplication between the filter and the corresponding input region and sum the results to produce a single output value.
     $$ \text{Output}(i, j) = \sum_{m=0}^{F-1} \sum_{n=0}^{F-1} \text{Input}_{pad}(i \cdot S+m, j \cdot S+n) \times \text{Filter}(m, n) $$
  5. Repeat this process for all positions skipped by the stride to fill the output feature map.
  6. If multiple filters are used, repeat the above steps for each filter to generate multiple feature maps.
  7. Stack the feature maps along the `channel` dimension to form the final output tensor.
- Example Question:

  - Calculate the output dimensions and perform the convolution operation for the following parameters:

    - Input Matrix (5x5):

      ```math
      \begin{bmatrix}
      1 &0 &2 &3 &0 \\
      4 &6 &6 &8 &1 \\
      3 &1 &1 &0 &2 \\
      1 &2 &2 &4 &1 \\
      0 &1 &3 &2 &0 
      \end{bmatrix}
      ```

    - Filter (3x3):

      ```math
      \begin{bmatrix}
      1 &0 &1 \\
      0 &1 &0 \\
      1 &0 &1
      \end{bmatrix}
      ```

    - Stride: 2
    - Padding: 1

  - Solution:

    1. Calculate output dimensions:
       - Input size: 5x5
       - Filter size: 3x3
       - Stride: 2
       - Padding: 1
       - Output Width:
         $$ \text{W}\_{\text{out}} = \lfloor\frac{(5 - 3 + 2 \times 1)}{2} + 1 \rfloor = \lfloor\frac{(5 - 3 + 2)}{2} + 1 \rfloor = \lfloor\frac{4}{2} + 1 \rfloor = \lfloor2 + 1\rfloor = 3 $$
       - Output Height:
         $$ \text{H}\_{\text{out}} = \lfloor\frac{(5 - 3 + 2 \times 1)}{2} + 1 \rfloor = \lfloor\frac{(5 - 3 + 2)}{2} + 1 \rfloor = \lfloor\frac{4}{2} + 1 \rfloor = \lfloor2 + 1\rfloor = 3 $$
       - **Output dimensions: 3x3**
    2. Feature map after performing convolution operation:

        ```math
         \begin{bmatrix}
         7 &16 & 8 \\
        11 &21 &14 \\
         2 & 9 & 4
         \end{bmatrix}
        ```

### Pooling Layer

- Reduces the spatial dimensions (width and height) of the input feature maps while retaining important information.
- Common Pooling Methods:
  - **Max Pooling**: Takes the maximum value from each region of the feature map.
  - **Average Pooling**: Takes the average value from each region of the feature map.
- Hyperparameters:
  - **Pool Size ($F$)**: Size of the pooling window (e.g., 2x2).
  - **Stride ($S$)**: Step size for moving the pooling window.
  - **Type**: `max()` or `avg()`.
- Padding is generally not used in pooling layers.
- No learnable parameters in pooling layers.
- Output Dimension Calculation:
  $$ \text{W}_{\text{out}} = \lfloor\frac{(W - F)}{S} + 1 \rfloor $$
  $$ \text{H}_{\text{out}} = \lfloor\frac{(H - F)}{S} + 1 \rfloor $$
  - $W$: Input width
  - $H$: Input height
- Example Question:

  - Calculate the output dimensions and perform **max pooling** for the following parameters:

    - Input Matrix (4x4):

      ```math
      \begin{bmatrix}
       1  &3  &2  &4 \\
       5  &6  &7  &8 \\
       9 &10 &11 &12 \\
      13 &14 &15 &16
      \end{bmatrix}
      ```

    - Pool Size: 2x2
    - Stride: 2 (center at bottom-right)

  - Solution:

    1. Calculate output dimensions:
       - Input size: 4x4
       - Pool size: 2x2
       - Stride: 2
       - Output Width:
         $$ \text{W}_{\text{out}} = \lfloor\frac{(4 - 2)}{2} + 1 \rfloor = \lfloor\frac{2}{2} + 1 \rfloor = \lfloor1 + 1\rfloor = 2 $$
       - Output Height:
         $$ \text{H}_{\text{out}} = \lfloor\frac{(4 - 2)}{2} + 1 \rfloor = \lfloor\frac{2}{2} + 1 \rfloor = \lfloor1 + 1\rfloor = 2 $$
       - **Output dimensions: 2x2**
    2. Perform max pooling:

       ```math
       \begin{bmatrix}
       6 &8 \\
       14 &16
       \end{bmatrix}
       ```

### Dense Layer

- Fully connected layer where each neuron is connected to every neuron in the previous layer.
- Same as traditional neural networks.
- Used for high-level reasoning after feature extraction by convolutional and pooling layers.
- Typically placed at the end of the CNN architecture for classification or regression tasks.

## Chapter 5: Regression Model Evaluation Metrics

- Evaluation metrics for regression models assess how well the model predicts continuous outcomes.

| Metric                                       | Formula                                                                           | Advantages                                                                   | Disadvantages                                                                                  |
| -------------------------------------------- | --------------------------------------------------------------------------------- | ---------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------- |
| Mean Absolute Error/Deviation (MAE/MAD)      | $\frac{1}{n} \sum_{i=1}^{n} \|y_i - \hat{y}_i\|$                                  | Easy to interpret, less sensitive to outliers                                | Does not penalize large errors as much as MSE                                                  |
| Mean Squared Error (MSE)                     | $\frac{1}{n} \sum_{i=1}^{n} (y_i - \hat{y}_i)^2$                                  | Penalizes larger errors more, useful for optimization, differentiable        | Sensitive to outliers, assume normal distribution, harder to interpret                         |
| Root Mean Squared Error (RMSE)               | $\sqrt{\frac{1}{n} \sum_{i=1}^{n} (y_i - \hat{y}_i)^2}$                           | More interpretable (using same unit), penalizes large errors, differentiable | Sensitive to outliers, assume normal distribution                                              |
| Coefficient of Determination (R²), Chapter 6 | $1 - \frac{\sum_{i=1}^{n} (y_i - \hat{y}_i)^2}{\sum_{i=1}^{n} (y_i - \bar{y})^2}$ | Indicates proportion of variance explained, unitless, easy to interpret      | Can only be used for linear models, sensitive to outliers, only increases with more predictors |

## Chapter 6: Model Generalization, Validation, and Parameter Regularization

### Model Generalization

- The ability of a machine learning model to perform well on unseen data.
- Generalisation Issues:
  - **Overfitting**: Model learns noise and details from training data, performs poorly on new data.
  - **Underfitting**: Model is too simple to capture underlying patterns in the data.
- **Bias-Variance Tradeoff**:
  - **Bias**: Error due to overly simplistic assumptions in the learning algorithm. High bias can cause underfitting.
  - **Variance**: Error due to excessive sensitivity to small fluctuations in the training set. High variance can cause overfitting.

| Model Complexity | Bias   | Variance | Fit      | Train | Test |
| ---------------- | ------ | -------- | -------- | ----- | ---- |
| Low              | High   | Low      | Underfit | Poor  | Poor |
| Medium           | Medium | Medium   | Good Fit | Good  | Good |
| High             | Low    | High     | Overfit  | Good  | Poor |

### Validation Techniques

- **Holdout Validation (Train-Test Split)**: Split dataset into training and testing sets (e.g., 80/20 split).
- **K-Fold Cross-Validation**
  1. Divide dataset into K equal parts (folds).
  2. For each fold:
     - Use the fold as the validation set.
     - Use the remaining K-1 folds as the training set.
  3. Average the performance across all K iterations to get an overall performance estimate.

```text
Illustrate K=3

----------------------------------------------------
| Training Split | Training Split | Validation Set |
----------------------------------------------------

---------------------------------------------------
| Training Split | Validation Set | Training Split |
---------------------------------------------------

----------------------------------------------------
| Validation Set | Training Split | Training Split |
----------------------------------------------------

Average Performance across 3 folds (e.g., accuracy, RMSE)
```

### Regularization Techniques

$$ Loss_{total} = Loss_{original} + \lambda \cdot Penalty $$

- Loss function augmented with a penalty term to discourage complex models.
- Common Regularization Methods:
  - **L1 Regularization (Lasso)**: Adds the absolute value of coefficients as a penalty term to the loss function.
    - Encourages sparsity, can lead to feature selection (by driving some coefficients to zero).
    - Slower to converge than L2.
    $$\text{Penalty} = \lambda \sum_{j=1}^{k} |\beta_j|$$
  - **L2 Regularization (Ridge)**: Adds the squared value of coefficients as a penalty term to the loss function.
    - Encourages smaller weights, helps prevent overfitting.
    $$\text{Penalty} = \lambda \sum_{j=1}^{k} \beta_j^2$$
  - **Elastic Net**: Combines L1 and L2 regularization.
    $$\text{Penalty} = \lambda_1 \sum_{j=1}^{k} |\beta_j| + \lambda_2 \sum_{j=1}^{k} \beta_j^2$$
- Use validation data to tune the regularization parameter(s) ($\lambda$) instead of testing data to avoid data leakage (testing data leaking into model training).

## Chapter 7: Interpolation and Extrapolation, Linear Regression

### Interpolation vs Extrapolation

| Interpolation                                            | Extrapolation                                                      |
| -------------------------------------------------------- | ------------------------------------------------------------------ |
| Estimating values within the range of known data points. | Estimating values outside the range of known data points.          |
| Generally more reliable and accurate.                    | More uncertain and prone to error.                                 |
| Commonly used to identify missing data within a dataset. | Used to forecast future trends or values beyond the observed data. |

### Linear Regression

$$ y_\beta(x) = \beta_0 + \beta_1 x_1 $$
$$ error = (\beta_0 + \beta_1 x_{obs}^{(i)}) - y_{obs}^{(i)} $$
$$ MSE = \frac{1}{m} \sum_{i=1}^{m} \left( (\beta_0 + \beta_1 x_{obs}^{(i)}) - y_{obs}^{(i)} \right)^2 $$
$$ J(\beta_0, \beta_1) = \frac{1}{2m} \sum_{i=1}^{m} \left( (\beta_0 + \beta_1 x_{obs}^{(i)}) - y_{obs}^{(i)} \right)^2 $$

- $J(\beta_0, \beta_1)$: Cost function to minimize.

| Linear Regression                                   | K Nearest Neighbors (KNN)                           |
| --------------------------------------------------- | --------------------------------------------------- |
| Fitting by minimizing cost function (Slow training) | Fitting by memorizing training data (Fast training) |
| Model has few parameters (memory efficient)         | Model stores all training data (memory intensive)   |
| Predict by calculation (fast prediction)            | Predict by searching neighbors (slow prediction)    |

### Optimise Linear Regression Training

1. **Feature Scaling**

   - Ensures all features contribute equally to the distance calculations.

   | Method                        | Pros                                                   | Cons                                                                           | Use Cases                                                                                                 |
   | ----------------------------- | ------------------------------------------------------ | ------------------------------------------------------------------------------ | --------------------------------------------------------------------------------------------------------- |
   | **Standardization (Z-score)** | Reduce sparsity issues, handles outliers better        | May not bound values within a specific range                                   | Preferred for algorithms assuming normal distribution (e.g., Linear Regression, Logistic Regression, SVM) |
   | **Min-Max Scaling**           | Bounds values within a specific range (e.g., $[0, 1]$) | Sensitive to outliers                                                          | Preferred for distance-based algorithms (e.g., KNN, K-Means)                                              |
   | **Max Absolute Scaling**      | Preserves sparsity, scales data to $[-1, 1]$           | No mean centering (may affect some algorithms i.e. PCA), sensitive to outliers | Useful for sparse data (e.g., text data)                                                                  |

2. **Skewed Data Transformation**

   - Linear regression assumes residuals are normally distributed, but data often is skewed.
   - Apply transformations to reduce skewness and improve model performance.
   - Example Transformations (Extra):

      | Transformation Method | Formula                                                                                                     | Use Case                        |
      | --------------------- | ----------------------------------------------------------------------------------------------------------- | ------------------------------- |
      | Log1p                 | $\log(1 + x)$                                                                                               | Right skewed data               |
      | Square Root           | $\sqrt{x}$                                                                                                  | Moderate right skewed data      |
      | Box-Cox               | $y(\lambda) = \begin{cases} (y^\lambda - 1)/\lambda, & \lambda \neq 0 \\ \ln(y), & \lambda = 0 \end{cases}$ | Both left and right skewed data |
      | Square                | $x^2$                                                                                                       | Moderate left skewed data       |
      | Cube                  | $x^3$                                                                                                       | Severe left skewed data         |

3. **Feature Transformation**

   | Feature Type   | Transformation Method            |
   | -------------- | -------------------------------- |
   | Numerical      | Standardization, Min-Max Scaling |
   | Binary/Nominal | One-Hot Encoding                 |
   | Ordinal        | Ordinal Encoding                 |

4. **Polynomial Features**
   - Introduce non-linearity by adding polynomial terms of existing features.
     - Helps capture complex relationships between features and target variable.
     - Example: For a feature `x`, add `x^2`, `x^3`, etc. as new features.

## Chapter 8: Dimensionality Reduction

### Feature Selection

- **Importance**:
  - Reduces overfitting.
  - Decreases training time.
  - Enhances model performance.
  - Improves model interpretability.
- **Methods**:
  - L1 Regularization (Lasso).
  - Recursive Feature Elimination (RFE).
    - Iteratively builds models and removes the least important features based on model coefficients or feature importance.

### Dimensionality Reduction Algorithms

- **Curse of Dimensionality**:
  - As the number of features increases
  - Data becomes sparse in high-dimensional space
  - Distance metrics become less meaningful
  - Model performance may degrade
  - The more features, the exponentially more data is needed to maintain the same density
- **PCA**:
  - Reduce dimensionality by transforming original features into a new set of uncorrelated variables (principal components).
  - Each principal component captures the maximum variance in the data.
  - **PCA Steps**:
    1. Compute mean-vector ($\mu$) of the data.
    2. Calculate the covariance matrix of the mean-centered data.
        $$Cov = \frac{\sum(x_i-\mu)^T(x_i-\mu)}{n}$$
       - $\mu$: Mean vector
       - $n$: Number of data points
       - $x_i$: Data point i
    3. Find eigenvalues ($\lambda$) and eigenvectors ($v$) of the covariance matrix.
        $$|Cov - \lambda I| = 0$$
        $$Cov \cdot \vec{v} = \lambda \vec{v}$$
    4. Sort eigenvalues in descending order and select the top k eigenvectors to form a projection matrix (W).
    5. Project the original data onto the new subspace:
        $$X_\text{new} = v^T \cdot (X - \mu)$$
  - Example:
  
    - Apply PCA to reduce to 1D

    | Feature 1 | Feature 2 |
    | --------- | --------- |
    | 1         | 2         |
    | 5         | 8         |
    | -4        | -1        |
    | -3        | 1         |
    | 6         | 7         |
    | 1         | 4         |

    1. Compute mean vector:
       $$\mu = \frac{1}{6} \begin{bmatrix} 1 + 5 - 4 - 3 + 6 + 1 \\ 2 + 8 - 1 + 1 + 7 + 4 \end{bmatrix} = \begin{bmatrix} 1 \\ 3.5 \end{bmatrix}$$
       - Mean-centered data:
        $$X_{centered} = \begin{bmatrix} 0 & -1.5 \\ 4 & 4.5 \\ -5 & -4.5 \\ -4 & -2.5 \\ 5 & 3.5 \\ 0 & 0.5 \end{bmatrix}$$
    2. Calculate covariance matrix:
       $$Cov = \frac{1}{6}\begin{bmatrix} 0 & -1.5 \\ 4 & 4.5 \\ -5 & -4.5 \\ -4 & -2.5 \\ 5 & 3.5 \\ 0 & 0.5 \end{bmatrix}^T \cdot \begin{bmatrix} 0 & -1.5 \\ 4 & 4.5 \\ -5 & -4.5 \\ -4 & -2.5 \\ 5 & 3.5 \\ 0 & 0.5 \end{bmatrix} = \begin{bmatrix} 13.6667 & 11.3333 \\ 11.3333 & 10.25 \end{bmatrix}$$
    3. Find eigenvalues and eigenvectors:
       - Eigenvalues:
       $$|\begin{bmatrix} 13.6667 & 11.3333 \\ 11.3333 & 10.25 \end{bmatrix} - \begin{bmatrix} \lambda & 0 \\ 0 & \lambda \end{bmatrix}| = 0$$
       $$|\begin{bmatrix} 13.6667-\lambda & 11.3333 \\ 11.3333 & 10.25-\lambda \end{bmatrix}| = 0$$
       $$(13.6667-\lambda)(10.25-\lambda) - (11.3333)^2 = 0$$
       $$\lambda^2 - 23.9167\lambda + 11.64 = 0$$
       $$\lambda_1 = 23.4197, \lambda_2 = 0.4970$$
       - Discard $\lambda_2$ (smaller eigenvalue, which captures less variance).
       - Eigenvector for $\lambda_1$:
       $$\begin{bmatrix} 13.6667 & 11.3333 \\ 11.3333 & 10.25 \end{bmatrix} \cdot \begin{bmatrix} x_1 \\ x_2 \end{bmatrix} = 23.4197 \begin{bmatrix} x_1 \\ x_2 \end{bmatrix}$$
       - For $\lambda_1 = 23.4197$:
       $$13.6667x_1 + 11.3333x_2 = 23.4197x_1$$
       $$11.3333x_1 + 10.25x_2 = 23.4197x_2$$
       - Simplifying gives (Both are same direction, just different magnitudes, choose either):
       $$9.7530x_1 = 11.3333x_2 \Rightarrow x_1 = 1.1620x_2$$
       $$11.3333x_1 = 13.1697x_2 \Rightarrow x_1 = 1.1620x_2$$
       $$\text{Eigenvector}: \begin{bmatrix} 1.1620 \\ 1 \end{bmatrix}$$
    4. Project data onto the new subspace:
        $$X_\text{new} = \begin{bmatrix} 1.1620 & 1 \end{bmatrix} \cdot \begin{bmatrix} 0 & -1.5 \\ 4 & 4.5 \\ -5 & -4.5 \\ -4 & -2.5 \\ 5 & 3.5 \\ 0 & 0.5 \end{bmatrix}^T$$
        $$X_\text{new} = \begin{bmatrix} -1.5000 \\ 9.1480 \\ -10.3100 \\ -7.1480 \\ 9.3100 \\ 0.5 \end{bmatrix}$$
- **Kernel PCA**:
  - Use **kernel functions** to project data into higher-dimensional space before applying PCA.
  - Project non-linearly separable data into a space where linear separation is possible.
  - Kernel Functions:
    - **Linear Kernel**: $K(x, y) = x^T y$
    - **Polynomial Kernel**: $K(x, y) = (x^T y + c)^d$
    - **Radial Basis Function (RBF) Kernel**: $K(x, y) = exp(-\gamma \|x - y\|^2)$
- **Multi-Dimensional Scaling (MDS)**:
  - Dimensionality reduction technique that preserves pairwise distances between data points instead of overall variance.
- **Fisher’s Linear Discriminant Analysis (LDA)**:
  - Supervised dimensionality reduction technique that maximizes class separability.
  - Projects data onto a lower-dimensional space while preserving class-discriminative information.

## Chapter 9: Decision Tree

- Non-parametric supervised learning algorithm
- Does not assume any underlying data distribution
- Terminology:
  - **Root Node**: Topmost node representing the entire dataset.
  - **Split**: Decision point dividing data based on feature values.
  - **Node**: Represents a feature or outcome.
  - **Leaf Node**: Terminal node representing a class label (classification) or continuous value (regression).
  - **Pruning**: Technique to reduce tree size and prevent overfitting by removing branches that do not provide significant predictive power.
  - **Branch/Sub-tree**: A section of the tree that includes a node and all its descendants.
- Splitting Criteria:
  - **Classification Trees**: Use impurity measures like Entropy and Gini Index to determine the best feature to split on.
  - **Regression Trees**: Use variance reduction or Mean Squared Error (MSE) to determine the best feature to split on.
- When splitting continous features, consider all possible split points (midpoints between sorted unique values) to find the optimal split.

| Strength                                         | Weakness                                              |
| ------------------------------------------------ | ----------------------------------------------------- |
| Handle any data type (numerical, categorical)    | High variance, prone to overfitting (require pruning) |
| No preprocessing needed (scaling, normalization) | Favor majority class in imbalanced datasets           |

### Impurity Measures: Entropy

- Used by ID3, C4.5 and C5.0 algorithms to measure impurity in classification tasks.
- Measures the uncertainty or randomness in the dataset.

$$ I_\text{Entropy} = - \sum_{i=1}^{j} p_i \log_2(p_i) $$

- Where:
  - $D$: Dataset
  - $j$: Number of classes
  - $p_i$: Proportion of instances belonging to class i in dataset D.

- Example:
  
  | ID  | Feature 1 | Feature 2 | Class |
  | --- | --------- | --------- | ----- |
  | 1   | A         | X         | 0     |
  | 2   | A         | Y         | 0     |
  | 3   | B         | X         | 1     |
  | 4   | B         | Y         | 1     |

  - Calculate Entropy for the entire dataset:
    - Class 0: 2 instances, Class 1: 2 instances
    - $p_0 = \frac{2}{4} = 0.5$, $p_1 = \frac{2}{4} = 0.5$
    - $I_\text{Entropy} = - (0.5 \log_2(0.5) + 0.5 \log_2(0.5)) = 1$

### Impurity Measures: Gini Index

- Used by CART (Classification and Regression Trees) algorithm to measure impurity in classification tasks.
- Measures the impurity of a dataset.
- Ranges from 0 (pure) to 0.5 (impure with equal class distribution).

$$ I_\text{Gini} = 1 - \sum_{i=1}^{j} p_i^2 $$

- Where:
  - $D$: Dataset
  - $j$: Number of classes
  - $p_i$: Proportion of instances belonging to class i in dataset D.

- Example:
  - Using the previous dataset, calculate Gini Index for the entire dataset:
    - Class 0: 2 instances, Class 1: 2 instances
    - $p_0 = \frac{2}{4} = 0.5$, $p_1 = \frac{2}{4} = 0.5$
    - $I_\text{Gini} = 1 - (0.5^2 + 0.5^2) = 0.5$

### Information Gain (IG)

- Measures the **reduction in uncertainty** about the target variable after splitting the data based on a feature.

$$ IG(D_p, f) = I(D_p) - \sum_{j=1}^{m} \frac{N_j}{N_p} I(D_j) $$

- Where:
  - $D_p$: Parent dataset before the split.
  - $f$: Feature used for the split.
  - $\sum_{j=1}^{m} \frac{N_j}{N_p} I(D_j)$: Weighted impurity of child datasets after the split.
    - $m$: Number of unique values of feature f.
    - $N_p$: Number of instances in parent dataset.
    - $N_j$: Number of instances in child dataset $D_j$ after the split.
  - $I(D)$: Impurity measure (e.g., Entropy, Gini Index) of dataset D.

- Example:
  - Using the previous dataset, calculate IG for splitting on each feature using Gini Index:
    - Gini before split = 0.5
    - Split on Feature 1:
      - For Feature 1 = A: Class 0 (2), Class 1 (0) → Gini = 0
      - For Feature 1 = B: Class 0 (0), Class 1 (2) → Gini = 0
      - Weighted Gini after split = $\frac{2}{4} \times 0 + \frac{2}{4} \times 0 = 0$
      - IG = Gini before split - Weighted Gini after split = 0.5 - 0 = 0.5
      - Thus, splitting on Feature 1 provides an Information Gain of 0.5.
    - Split on Feature 2:
      - For Feature 2 = X: Class 0 (1), Class 1 (1) → Gini = 0.5
      - For Feature 2 = Y: Class 0 (1), Class 1 (1) → Gini = 0.5
      - Weighted Gini after split = $\frac{2}{4} \times 0.5 + \frac{2}{4} \times 0.5 = 0.5$
      - IG = Gini before split - Weighted Gini after split = 0.5 - 0.5 = 0
      - Thus, splitting on Feature 2 provides no Information Gain.
  - Feature 1 is the better split based on Information Gain.

### Classification Error

- Measures the proportion of misclassified instances in a dataset.
- Less sensitive and effective compared to Entropy and Gini Index for decision tree splits.
- Used primarily for pruning decision trees rather than for splitting nodes.
  - i.e. prune the tree when Classification Error is less than a certain threshold.

$$ E(t) = 1 - \max_i[p(i|t)] $$

- Where:
  - $p(i|t)$: Proportion of instances belonging to class i at node t.
  - $\max_i[p(i|t)]$: Proportion of the majority class at node t.
- Example:
  - Using the previous dataset, calculate Classification Error for the entire dataset:
    - Class 0: 2 instances, Class 1: 2 instances
    - $\max_i[p(i|t)] = \max(0.5, 0.5) = 0.5$
    - $E(t) = 1 - 0.5 = 0.5$

## Chapter 10: Distance Metrics

- Used to measure similarity or dissimilarity between data points in various machine learning algorithms (e.g., KNN, clustering).

### Euclidean Distance

- Measures the straight-line distance between two points in Euclidean space.
$$ d(p, q) = \sqrt{\sum_{i=1}^{n} (p_i - q_i)^2} $$
- Where:
  - $p$ and $q$: Two points in n-dimensional space.
  - $p_i$ and $q_i$: Coordinates of points p and q in the i-th dimension.
  - $n$: Number of dimensions.
- Example:
  - Calculate the Euclidean distance between points p(2, 3) and q(5, 7):
    - $d(p, q) = \sqrt{(2 - 5)^2 + (3 - 7)^2} = \sqrt{(-3)^2 + (-4)^2} = \sqrt{9 + 16} = \sqrt{25} = 5$

### Manhattan Distance

- Measures the distance between two points by summing the absolute differences of their coordinates.
$$ d(p, q) = \sum_{i=1}^{n} |p_i - q_i| $$
- Where:
  - $p$ and $q$: Two points in n-dimensional space.
  - $p_i$ and $q_i$: Coordinates of points p and q in the i-th dimension.
  - $n$: Number of dimensions.
- Example:
  - Calculate the Manhattan distance between points p(2, 3) and q(5, 7):
    - $d(p, q) = |2 - 5| + |3 - 7| = 3 + 4 = 7$

### Cosine Distance

- Measures the dissimilarity between two vectors by calculating the cosine of the angle between them.
- Cosine Similarity is first calculated, then converted to distance.
- Cosine Similarity Range: [-1, 1]
  - 1: Vectors are perfectly aligned (same direction).
  - 0: Vectors are orthogonal, 90 degrees apart (no similarity).
  - -1: Vectors are diametrically opposed (opposite direction).
- Cosine Distance Range: [0, 2]
  - 0: Vectors are perfectly aligned (same direction).
  - 2: Vectors are diametrically opposed (opposite direction).
$$ d(p, q) = 1 - \frac{p \cdot q}{\|p\| \|q\|} $$
- Where:
  - $p$ and $q$: Two vectors.
  - $p \cdot q$: Dot product of vectors p and q.
  - $\|p\|$ and $\|q\|$: Magnitudes (norms) of vectors p and q.
  - n$: Number of dimensions.
- Example:
  - Calculate the Cosine distance between vectors p(1, 2, 3) and q(4, 5, 6):
    - Dot product: $p \cdot q = 1*4 + 2*5 + 3*6 = 4 + 10 + 18 = 32$
    - Magnitudes: $\|p\| = \sqrt{1^2 + 2^2 + 3^2} = \sqrt{14}$, $\|q\| = \sqrt{4^2 + 5^2 + 6^2} = \sqrt{77}$
    - Cosine similarity: $\frac{p \cdot q}{\|p\| \|q\|} = \frac{32}{\sqrt{14} \cdot \sqrt{77}}$
    - Cosine distance: $d(p, q) = 1 - \frac{32}{\sqrt{14} \cdot \sqrt{77}} = 1 - \frac{32}{\sqrt{1078}} = 0.02537$

### Jaccard Distance

- Measures dissimilarity between two sets by calculating the ratio of the size of their intersection to the size of their union.
$$ d(A, B) = 1 - \frac{|A \cap B|}{|A \cup B|} $$
$$ d(A, B) = 1 - \frac{\text{len}(\text{shared})}{\text{len}(\text{unique})} $$

### Comparison of Distance Metrics

| Distance Metric    | Use Case                  | Advantages                   | Disadvantages                                                 |
| ------------------ | ------------------------- | ---------------------------- | ------------------------------------------------------------- |
| Euclidean Distance | Continuous numerical data | Intuitive, easy to compute   | Sensitive to scale and outliers, curse of dimensionality      |
| Manhattan Distance | High-dimensional data     | Less sensitive to outliers   | May not capture true distance                                 |
| Cosine Distance    | Text data, sparse data    | Scale-invariant, effective   | Ignores magnitude differences                                 |
| Jaccard Distance   | Categorical/binary data   | Effective for set comparison | Not suitable for measurement of similarity in continuous data |

## Chapter 11: Unsupervised Learning Algorithms

- User does not provide labels for the data.
- Discover hidden patterns or intrinsic structures in input data.

### Hierarchical Agglomerative Clustering

- Build tree-like structure (dendrogram) to represent nested clusters.
- Bottom-up approach:
  1. Initialise distance matrix.
  2. Merge closest pair of clusters.
  3. Update distance matrix.
  4. Repeat until all points are in a single cluster.
  5. Cluster selection by cutting dendrogram at desired level.
- Pros:
  - Produce dendrogram for visualising cluster relationships.
  - No need to specify number of clusters in advance.
  - Identify nested clusters.
- Cons:
  - Computationally expensive, $O(n^2 \log n)$ time complexity.
  - Sensitive to noise and outliers.
  - Not online (cannot update clusters with new data unless re-computed).
- Stopping Criteria:
  - Predefined number of clusters.
  - Minimum average cluster distance threshold.

### Cluster Linkage Methods

- **Single Linkage**: Minimum distance between points in two clusters.
- **Complete Linkage**: Maximum distance between points in two clusters.
- **Average Linkage**: Average distance between all points in two clusters.
- **Ward Linkage**: Minimise increase in total within-cluster variance after merging.

### K-Means Clustering

- Steps:
  1. Choose number of clusters K.
  2. Initialise random K data points as centroids of clusters.
  3. Assign each data point to the nearest centroid.
  4. Recalculate centroids of each cluster based on mean of assigned points.
  5. Repeat steps 3-4 until convergence criteria met (centroids do not change or max iterations reached).
- Pros
  - Simple and easy to implement.
  - Efficient for large datasets (linear time complexity $O(n)$).
- Cons
  - Requires predefined number of clusters K.
  - Outlier sensitive.
  - Assumes hyper-spherical cluster shapes.

### Inertia

- Measure of how tightly data points are clustered around their centroids in K-Means clustering.
- Lower inertia indicates more compact clusters.
$$ \text{Inertia}_k = \sum_{i=1}^{n} (x_i - C_k)^2 $$
$$ \text{Total Inertia} = \sum_{k=1}^{K} \text{Inertia}_k $$
- Where:
  - $n$: Number of data points.
  - $x_i$: Data point i.
  - $C_k$: Centroid of cluster k to which data point i is assigned.
- Elbow Method:
  - Plot inertia against number of clusters K.
  - Look for "elbow" point where inertia decrease slows down.
  - Choose K at this point as optimal number of clusters.

### K-Means vs Hierarchical Clustering

| K-Means Clustering                        | Hierarchical Agglomerative Clustering                          |
| ----------------------------------------- | -------------------------------------------------------------- |
| Handle big data well                      | Computationally expensive, not suitable for large datasets     |
| Linear time complexity $O(n)$             | Quadratic time complexity $O(n^2 \log n)$                      |
| Not reproducible unless fixed random seed | Reproducible results                                           |
| Works well with hyper-spherical clusters  | Can capture complex cluster shapes depending on linkage method |
| Requires predefined number of clusters    | No need to specify number of clusters in advance               |

### DBSCAN

- Density-Based Spatial Clustering of Applications with Noise
- Can find clusters of arbitrary shapes and sizes.
- Effectively identifies and handles noise/outliers.
- Hyperparameters:
  - **Epsilon (ε)**: Radius of neighborhood around a point.
  - **MinPts**: Minimum number of points required to form a dense region (core point).
- Key Features:
  - Not require predefined number of clusters.
  - Discovers clusters of arbitrary shapes and densities.
  - Points classified as core points, border points, or noise.
    - **Core Point**: Has at least MinPts within ε radius.
    - **Border Point**: Has fewer than MinPts within ε radius but is within ε of a core point.
    - **Noise Point**: Neither core nor border point, normally situated in sparse regions.
- Steps:
  1. For each point, identify its ε-neighborhood.
  2. Classify points as core, border, or noise.
  3. Expand clusters from core points by adding reachable points.
  4. Repeat until all points are processed.
  5. Output clusters and noise points.
- Pros:
  - No need to specify number of clusters in advance.
  - Able to identify noise, instead of forcing all points into clusters (i.e. mean shift, K-Means).
  - Able to find clusters of arbitrary shapes.
- Cons:
  - Not effective for clusters with varying densities.
  - Curse of dimensionality causes sparsity in high-dimensional data, making it difficult to define ε-neighborhoods.

### Gaussian Mixture Model (GMM)

- Probabilistic model that assumes data points are generated from a mixture of several Gaussian distributions with unknown parameters.
- Model-based clustering approach.
- Steps to fit GMM using Expectation-Maximization (EM) algorithm:
  1. Randomly initialise parameters for K Gaussian components (means, covariances, weights).
  2. Expectation Step (E-step): Calculate the probability of each data point belonging to each Gaussian component based on current parameters.
  3. Maximization Step (M-step): Update parameters of Gaussian components to maximise the likelihood of the data given the current assignments.
  4. Repeat E-step and M-step until convergence (parameters do not change significantly or max iterations reached).
- Performance Evaluation:
  - Use metrics like log-likelihood, Bayesian Information Criterion (BIC), or Akaike Information Criterion (AIC) to assess model fit and select optimal number of components K.
- Pros:
  - Model complex data distributions better than K-Means.
  - Soft clustering: provides probabilities of cluster membership.
  - Can model clusters with different shapes and sizes.
- Cons:
  - Computationally intensive, especially for large datasets or high-dimensional data.
  - Prone to overfitting if too many components are used, requiring regularization.
  - Sensitive to initial parameter settings; may converge to local optima.

### Mean Shift

- Non-parametric clustering technique that identifies clusters by finding modes (peaks) in the data distribution.
- Does not require specifying the number of clusters in advance.
- Specifies a bandwidth parameter that defines the size of the window used to compute the mean shift.
- Steps:
  1. Initialise a set of points (can be random or all data points).
  2. For each point, define a window (bandwidth) and compute the mean of data points within the window.
  3. Shift the point to the computed mean.
  4. Repeat steps 2-3 until convergence (points do not move significantly).
  5. Group points that converge to the same mode into clusters.
- Pros:
  - No need to specify number of clusters in advance.
  - Able to find clusters of arbitrary shapes.
  - Robust to outliers as they do not affect the mean significantly.
- Cons:
  - Computationally expensive, especially for large datasets.
  - Sensitive to bandwidth parameter; inappropriate bandwidth can lead to poor clustering results.
  - May converge slowly, requiring many iterations for convergence.

### Spectral Clustering

- Treats clustering as a graph partitioning problem.
- Utilising eigenvalues and eigenvectors of a similarity matrix derived from the data.
- Does not assume any specific cluster shape.
- Steps:
  1. Construct a similarity graph from the data points using a similarity measure (e.g., Gaussian kernel).
  2. Edges represent similarities between points.
  3. Compute the graph Laplacian matrix from adjacency matrix.
  4. Perform eigen decomposition on the Laplacian matrix to obtain eigenvalues and eigenvectors.
  5. Select the top K eigenvectors corresponding to the smallest eigenvalues to form a new feature space.
  6. Apply K-Means clustering on the new feature space to obtain final clusters.
- Performance Evaluation:
  - NMI (Normalized Mutual Information): Measures similarity between true labels and predicted clusters.
  - Running Time: Time taken to perform clustering.
- Pros:
  - Able to capture complex cluster structures.
  - Does not assume specific cluster shapes (unlike K-Means).
  - Handle non-linearly separable data effectively.
- Cons:
  - Sensitive to the choice of similarity measure and parameters used to construct the similarity graph.
  - Computationally intensive due to eigen decomposition.
  - Scaling issues with large datasets as similarity matrix grows quadratically with number of data points.

> [!WARNING]
> BIRCH and Affinity Propagation clustering algorithms are excluded from the notes.

### Fuzzy C-Means Clustering

- Soft clustering variant of K-Means.
- Allows data points to belong to multiple clusters with varying degrees of membership (Percentage based on distance to cluster centroids).
- Steps:
  1. Choose number of clusters C and fuzziness parameter m (m > 1).
  2. Initialise membership of each data point to each cluster randomly.
  3. Calculate cluster centroids using weighted average based on membership values.
  4. Update membership values for each data point based on distance to centroids and fuzziness parameter.
  5. Repeat steps 3-4 until convergence (membership values do not change significantly or max iterations reached).
- Pros:
  - More flexible in representing data with overlapping clusters and complex structures.
  - Better handling of noise and outliers compared to hard clustering methods.
- Cons:
  - Sensitive to initialisation of membership values.
  - Difficult to determine optimal number of clusters C and fuzziness parameter m.
  - Slower computation due to additional calculations for membership values.

### LDA

- Latent Dirichlet Allocation (LDA)
- Identify degree of topic membership for text documents.
- Applications: Topic modelling, document classification, etc. on news articles, research papers, social media posts.

### LSA

- Latent Semantic Analysis (LSA)
- Reduce dimensionality of text data while preserving semantic relationships.
- Applications: Information retrieval, document clustering, text similarity analysis.
