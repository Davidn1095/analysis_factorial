# analysis_factorial

### Data Loading and Setup:
- **Data Reading**: `datos <- read.table("factorial.txt", header = TRUE, row.names = 1)`: Reads data from "factorial.txt" into a DataFrame `datos`. The file has headers, and the first column is for row names.
- **Attaching Data**: `attach(datos)`: Makes `datos` DataFrame directly accessible in the R environment.

### Multivariate Shapiro-Wilk Test:
- **Package Loading**: `library(mvnormtest)`: Loads the `mvnormtest` package for multivariate normality tests.
- **Normality Test**: `mshapiro.test(t(datos))`: Conducts the multivariate Shapiro-Wilk test on the transposed data in `datos`.

### Correlation Analysis:
- **Correlation Matrix**: `Redatos <- cor(datos, method = "pearson")`: Calculates the Pearson correlation matrix for `datos`.
- **Symbolic Display**: `symnum(Redatos)`: Provides a symbolic display (like a heatmap) for the correlation matrix `Redatos`.
- **Determinant Calculation**: `det(Redatos)`: Computes the determinant of the correlation matrix.

### Kaiser-Meyer-Olkin (KMO) Measure and Bartlett's Test:
- **KMO Measure**: `KMO(datos)`: Computes the KMO statistic for adequacy of the factor analysis.
- **Bartlett's Test**: `cortest.bartlett(datos, n = NULL)`: Conducts Bartlett's test of sphericity.

### Principal Component Analysis (PCA):
- **PCA Performance**: `fac <- prcomp(datos, retx = FALSE, center = TRUE, scale. = TRUE)`: Performs PCA on `datos`.
- **PCA Summary**: `summary(fac)`: Provides a summary of the PCA results.
- **PCA Plotting**: `plot(fac)`: Plots the PCA results.

### Factor Loadings and Varimax Rotation:
- **Calculating Loadings**: Factor loadings are calculated and varimax rotation is applied.
- **Printing Loadings**: `print(cargas2, cutoff = 0.3)`: Prints the rotated factor loadings.

### Communality and Adjusted Loadings Calculation:
- **Communality Calculation**: Computes the proportion of variance explained by the factors for each variable.
- **Adjusted Loadings**: Adjusted loadings are computed.

### Residuals of the Fit:
- **Fit Residuals**: `ajuste <- cor(datos) - cargas2 %*% t(cargas2)`: Computes the residuals of the correlation matrix fit by the factor model.

### Biplot and Scatter Plots:
- **Biplot Creation**: `biplot(fac)`: Creates a biplot of the PCA.
- **Scatter Plots**: Scatter plots of factor loadings are generated and labeled.

### Multiple Factor Analysis:
- **Plotting Setup**: `par(mfrow = c(3, 2))`: Configures the plot area for multiple plots.
- **PCA Score Plots**: Scatter plots of PCA scores are created.
- **Factor Analysis**: `facmle <- vector("list", 4)`: Prepares for factor analysis. `for(i in 1:4) {facmle <- factanal(datos, i)}`: Conducts factor analysis for different numbers of factors and stores the results.
