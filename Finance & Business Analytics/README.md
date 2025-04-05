# Finance & Business Analytics 
This repository presents a comprehensive analysis of financial and business performance through the application of regression models. Using aggregate, disaggregate, and lead/lag variables, the analysis explores factors affecting market share and Tobin’s Q across various retail firms. The project integrates key financial indicators such as advertising intensity, marketing investment, firm size, liquidity, and leverage to evaluate their impact on firm performance. By applying advanced data analytics techniques, this work offers insights into effective strategies for enhancing both market share and market value.

## Abstract
The retail industry is a mature and highly competitive market that continues to show steady growth year after year. Business drivers are essential for growth and continued success. This report explores the key drivers of firm performance within the retail industry and provides actionable recommendations for retailers.

## Data

### The Industries in the Data

The dataset includes several types of retailers, all part of the fashion industry:
- Women’s clothing stores (SIC code: 5621)
- Family clothing stores (SIC code: 5651)
- Shoe stores (SIC code: 5661)

In total, the dataset contains 43 distinct retailers:
- 19 Women’s clothing stores
- 14 Family clothing stores
- 10 Shoe stores

The dataset includes both very large retailers that operate globally, such as "Urban Outfitters Inc." and "Foot Locker Inc.," as well as smaller retailers like "Francesca's Holdings Corp" and "dELiAs Inc."

### Investment: Mobile App
The data was cleaned and merged to create the final dataset. Of the companies in the dataset, 28% launched a mobile app during the specified period.
Sources of Data Collection

Primary data was sourced from various platforms:

- Google Play and App Store: Official stores for apps
  - Google: Google Play
  - Apple: App Store

- Press releases from retailer websites that launched apps
  - Example: Nordstrom iPad App Launch

- APKPure and AppAdvice: Websites offering app-related news and information, particularly launch dates
  - AppAdvice: AppAdvice
  - APKPure: APKPure

Motivations for Choosing This Investment

- General Reasons:
  - The mobile app variable can be stored as a numeric (double) datatype.
  - It is actionable: Retailers can choose to launch an app.
  - The fashion industry widely uses apps, although not all retailers have one; 28% of firms in the dataset have an app.
  - Information on app launches is relatively easy to obtain.

- Influence on Firm Performance:
  - A mobile app can provide a competitive advantage.
  - Apps simplify customer data collection.
  - They offer various touchpoints in the customer journey.
  - Operating costs are lower for apps compared to opening new stores.

- Engaging Customers:
  - Mobile apps provide more personalized customer engagement compared to websites or in-store experiences.
  - Social-oriented features in apps help retail industries deliver personalized recommendations directly to users.
  - Apps create communities and promote brand engagement with modern, tech-savvy customers.

- Convenience of an App:
  - Payment: Apps simplify payments with built-in smartphone features, such as credit card scanning and secure keychains for storing customer details.
  - Ease of Use: Smartphones are always accessible, enabling customers to shop anytime and anywhere. Unlike websites, apps are designed for mobile browsing.
  - Logistics: Apps remove geographic barriers, allowing companies to sell products to customers wherever they are. Push notifications and in-app messaging enhance customer interaction.

- Disadvantages:
  - High competition with numerous retailer apps makes differentiation difficult.
  - Convincing customers to download apps can be challenging.
  - Consumers are reluctant to install numerous retailer apps.
  - App stores (e.g., Apple) charge taxes to store owners.
  - Retailers must regularly update their apps to meet software requirements.
  - App stores control access and can remove apps.

- Sources:
  - NN4M: 10 Reasons Retailers Need a Mobile App
  - Inman, J.J., Nikolova, H. (2017), "Shopper-Facing Retail Technology: A Retailer Adoption Decision Framework Incorporating Shopper Attitudes and Privacy Concerns," Journal of Retailing, 93(1), 7–28.
  - Lamey, L., Breugelmans, E., Vuegen, M., ter Braak, A. (forthcoming), "Retail Service Innovations and their Impact on Retailer Value: Evidence from an Event Study," Journal of the Academy of Marketing Science.
 
- Facts about Retailers' Mobile Apps:
  - 17 out of 43 companies in the dataset have mobile apps.
  - The first app was launched by Nordstrom Inc. in 2012.
  - Two apps were launched in 2021.
  - The peak year for app launches was 2016, with 5 companies launching apps.

The dataset spans from 2010 to 2020, though data for some firms is only available for selected financial years. Some app launches occurred outside the dataset's time range. After merging the two datasets, only 12 companies' apps were considered, making the percentage of companies with a mobile app 28%.

### Data Cleaning
The dataset was cleaned by excluding unnecessary variables, handling missing values, checking for outliers, and correcting data types. All data points that were redundant or inconsistent with logical expectations were removed.

The following variables were excluded:
- "rdip" (unary variable with all zero values)
- "bkvlps," "ni," "oibdp," "gsubind" (no descriptions available)
- "busdec" (not required for analysis)

There are 104 missing values in total, distributed across various variables. The most missing values occur in:
- "xad" (Advertising expenditures) with 36 missing values
  - Missing values in "xad" were replaced with 0, assuming that the firm did not allocate advertising expenditures during that period.
- "prcc_f" (Closing share price at the end of the year) with 25 missing values
- Observations with more than one missing value were removed to avoid inaccurate imputation, preserving the quality of the analysis.
- Remaining missing values (18) were imputed using a decision tree algorithm (mice).

The following new variables were created:
- Firm Performance Metrics: market share, Tobin's q
- Managerial Decisions: advertising intensity, marketing investments
- Firm Characteristics: age, size, financial liquidity, leverage
- Industry Characteristics: industry-specific dummy variables (3 dummies)

The firm’s foundation year was merged with the dataset to calculate the age of each firm.

Several variables, including investment status and SIC codes, were initially stored as numeric values. These were corrected to categorical data types.

Several outliers were identified, primarily due to large retailers like TJX Companies, Gap, and Nordstrom. These outliers did not necessitate the removal of data points but were acknowledged for further analysis.
- Outliers, especially in the variable "market share," were addressed by removing a specific observation for the year 2020. Further, a Z-score approach was applied to detect and remove extreme outliers.

For further analysis, the data will be normalized using Min-Max normalization to ensure all variables are on the same scale.

#### Summary Statistics for Numerical Variables

A table of summary statistics for numerical variables was generated, including measures of center, spread, and range. Most variables exhibited right-skewness, with the exception of advertising intensity.

The following bar plot shows the number of retailers per industry.

The market share analysis provides insight into how the key players within each industry have evolved over the years, with particular attention paid to the major shifts from 2010 to 2019. This allows us to observe the competition dynamics and dominance of major players.
- Shoe Industry:
  - In 2010, the shoe industry was primarily dominated by Foot Locker and Collective Brands. This reflects a competitive landscape with a few key players controlling the market share.
  - By 2019, Foot Locker strengthened its position, increasing its market share by 20%, claiming over 50% of the market. This shift highlights Foot Locker's dominance and its ability to outpace competitors during this period.

- Women's Clothing Industry:
  - The 2010 market share for women's clothing was more fragmented, with no single player holding a dominant position.
  - By 2019, there was a marked shift in the market landscape. The Ascena Retail Group emerged as the market leader, controlling 42% of the market share. This indicates consolidation in the market, where larger firms are increasingly controlling a more significant portion of sales.

- Family Clothing Industry:
  - The 2010 market was highly competitive, with TJX Companies holding a significant portion of the market share, followed by other key players such as Gap, Nordstrom, and Ross Stores.
  - By 2019, TJX Companies' dominance increased by 10%, further consolidating its position as the leader in the market. Despite this, the market remained relatively fragmented with many smaller players, indicating more competition than in other industries.


  The correlation analysis provides valuable insight into the relationships between different numerical variables. By looking at the correlation matrix and corresponding p-values, we can observe the degree of linear relationships between key firm characteristics.

- Key Observations:
  - Sales, Assets, Advertising Expenditures: A strong positive correlation exists between sales and assets, as firms with higher sales tend to accumulate more assets. Similarly, firms with larger sales volumes also tend to spend more on advertising, which in turn can influence their sales and market share.
  - Firm Size and Characteristics: The number of employees and firm size correlate strongly with other financial metrics. Larger firms, in general, have higher sales, assets, and expenditures
  - Financial Liquidity: The correlation between financial liquidity and firm performance measures (such as sales and assets) indicates that firms with more available short-term capital tend to have more stable financial conditions, which can positively influence performance.

The correlations also highlight the significant relationships between firm size, asset base, and overall financial health. Larger companies tend to have greater financial resources, which can fuel further expansion, innovation, and advertising spend

This analysis demonstrates the intricate relationship between a firm's size, sales performance, financial liquidity, and other important financial metrics. By understanding these correlations, firms can make more informed decisions to optimize their advertising budgets, sales strategies, and overall business operations.

--- 

### Aggregate Data Models
#### Cross-Sectional Data
- Data Aggregation: The dataset was aggregated to create a cross-sectional representation, with one observation per firm, by calculating the mean of the numerical variables across each firm.
- Categorical Data Handling: Since categorical variables (e.g., industry dummies, mobile app availability) cannot be averaged, these were extracted and merged with the aggregated dataset.
- Dataset Structure: The code snippet below demonstrates the aggregation and merging process, followed by handling of missing categorical values.

- Correlation Analysis:
  - Observation: The correlation between the variables is generally low, with firm size and market share showing a slight correlation.
  - Visualization: A correlation matrix was generated to visualize the relationships between numerical variables.

- Summary Statistics:
  - Minimal Impact of Outliers: Summary statistics were calculated, showing that removing outliers had minimal effect on the variables.

 - Normalization:
   - Procedure: All independent numerical variables were normalized, with the exception of the dependent variables (market share and Tobin's Q), which do not require normalization.

### Models Built On Aggregate Data
#### Linear Regression:
- Model Details:
  - The dependent variable is market share, while Tobin’s Q was excluded from the model.
  - A regression model was fit using normalized data, showing that firm size and industry type are significant predictors of market share.
  - The variable family_clothes was excluded because we used it as our reference level

- Quality of the model:
  - The adjusted R-squared shows that the model explains 75.64% of the variance in the dependent variable. This is a relatively good fit.
  - The p-value associated with the F-statistic is lower than the 5% significance level, meaning that at least one independent variable is significantly related to the market share.
  - While this model does not explain the relationships between all of the predictors and market share, it can be used to indicate which managerial investment decisions and firm characteristics are related to the market share and in what way.

- Interpretation of the results:
  - Since the variables are normalized, we cannot say by how much the market share would change with a change in any of the independent variables. However, we can compare the influence of different predictors and whether they are positively or negatively related to the market share.
  - Based on the t-statistic and corresponding p-values, we can conclude that the coefficients of only 3 out of 9 predictors are significantly different from zero: firm size and industry dummy variables. There is not enough evidence to conclude a linear relationship between the other predictors and the response variable.
  - The coefficient of the `firm_size` is positive, meaning the larger the firm, the higher the market shares.
  - The coefficients of the industry dummy variables indicate that, out of the three industries analyzed in this report, retailers selling shoes have, on average, the highest market share and retailers selling family clothes (reference level) have on average the lowest market shares.
  - Even though the rest of the variables are not significant in predicting the market share, we may analyze them as if they were statistically significant:
    - Firms with higher advertising intensity (ratio of advertising expenditures and total revenues) are expected to have larger market shares than otherwise identical companies with low advertising intensity.
    - Firms whose marketing investments (ratio of marketing expenditures and total assets) are higher, holding all else equal, are expected to have a lower market share.
    - The model indicates that younger firms, on average, have a larger market share.
    - Firms with high financial liquidity (more working capita) have a lower market share on average.
    - Retailers with high firm leverage (firms relying more heavily on debt as a source of financing) are expected to have a lower market share (holding all else equal).
    - Introducing a mobile app is associated with a higher market share, assuming that we compare otherwise identical companies.

 - Firm’s with the objective to increase their market share should satisfy the following characteristics:
   - High advertising intensity
   - Low marketing investment ratio
   - Be young and large
   - Low financial liquidity
   - Low firm leverage
   - Have a mobile app
 - However, the only statistically significant firm characteristic is the firm size (apart from the industry). Hence, a retailer should try to grow in size.

Overall:
- Larger firms tend to have higher market shares.
- Retailers in the shoe industry tend to have higher market shares compared to family clothing retailers.
- Industry dummies and firm size were the only statistically significant variables.
        
#### Tobin’s Q Regression:
- Model Details:
  - The dependent variable is Tobin’s Q, and similar to the market share regression, industry and firm-specific variables were included.
  - Only advertising intensity was found to have a significant impact, with a negative relationship to Tobin’s Q.
- The variable family_clothes was excluded because we used it as our reference level

- Quality of the model:
  - The adjusted R-squared shows that the model explains 25.25% of the variance in the dependent variable. Since this value is much lower than for the market share model, it is a relatively poor fit.
  - The p-value associated with the F-statistic is also lower than the 5% significance level, which means that at least one independent variable is significantly related to Tobin's Q. 

- Interpretation of the results:
  - Similar to the market share regression model, the variables are also normalised. This means we cannot precisely determine how much Tobin's Q would change due to a change in the independent variables. However, it is possible to compare the significance of the different predictors and whether these predictors are positively or negatively related to Tobin's Q. 
  - Based on the t-score and corresponding p-values, we can conclude that only one predictor has coefficients significantly different from zero, which is advertising intensity (adv_int) .
  - Advertising intensity: The coefficient of `adv_int` is negative. This inverse relationship implies that firms that invest more intensely in advertising are expected to have a lower Tobin's Q ratio.

- Despite the other variables are not significant in predicting the market share, we may analyse them as if they were statistically significant:
  - `marketing_inv`: Firm that invests more in marketing, ceteris paribus, are expected to have a lower Q ratio.
  - `firm_age`: younger firms are expected to have a lower Q ratio. 
  - `firm_size`: firms that are larger are expected to have a higher Q ratio.
  - `liquidity`: firms with higher financial liquidity are expected to have a lower Q ratio.
  - `leverage`: firms with higher firm leverage are expected to have a lower Q ratio.
  - `Mobile_app`: firms with a mobile app are expected to have a higher Q ratio
  - `women_clothes` and `shoes`: the coefficients indicate that firms that sell women's clothes have, on average, the highest Q ratio.

- All in all, it can be concluded that for a firm to have a high Q ratio, it should have the following characteristics:
  - Low advertising intensity
  - Low marketing investments
  - A young and large firm
  - Low financial liquidity
  - Low firm leverage
  - Have a mobile app
- Since the only statistically significant firm characteristic was advertising intensity, a retailer wishing to increase their Tobin's Qshould lower their advertising intensity.
  
        
#### Model Differences:
- The key differences between the market share and Tobin's Q models were noted, with the market share model performing better due to a higher adjusted R-squared value. Tobin's Q, being more focused on long-term value, reflects less immediate impact from current strategies.

#### Expected Performance of an Average Firm:
- Predictions were made for an "average" firm, using the means of numerical variables and categorical combinations for different industries.
- Results:
  - The shoe industry is predicted to have the highest market share (14.4%), with a slight increase when a mobile app is introduced
  - Women's clothing firms are predicted to have a 9% market share, with an increase to 10.2% with a mobile app.
  - Family clothing retailers show the lowest market share but have the highest average Tobin’s Q ratio.
This analysis provides insight into how various factors such as advertising intensity, firm size, and industry type impact key performance indicators like market share and Tobin’s Q, with recommendations for firms based on regression results.

---

### Disaggregate Data Models
- All numerical variables in the dataset are first normalised to standardize the range of values. 
- Lead and lag variables for certain predictors (e.g. market share and Tobin’s Q) are then created, to capture time-based effects.

#### Panel Data Model
- Now that we have the disaggregated data and lead/lag variables, we can proceed with building a panel data model. Panel data allows us to control for both time-variant and time-invariant effects.
- For this model, we will use firm-fixed effects or random effects, depending on the assumptions about the correlation between individual firm characteristics and the predictors.
- The model will estimate the effects of various predictors (including advertising intensity, marketing investment, firm size, etc.) on market share, accounting for firm-specific factors that remain constant over time.

The within model accounts for the unobserved heterogeneity across firms by using firm fixed effects. This means the model will control for time-invariant factors that differ between firms but do not vary over time (like location or organizational structure).

#### Random Effects Model
- In addition to fixed effects, we can also estimate a random effects model. The choice between fixed and random effects can be made using the Hausman test, which tests whether the firm-specific effects are correlated with the explanatory variables.
- The random effects model assumes that the unobserved heterogeneity across firms is uncorrelated with the independent variables. This model is more efficient than the fixed effects model if the assumption holds true.

- 



