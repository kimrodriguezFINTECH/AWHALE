# Unit 4 Homework Assignment: A Whale Off the Port(folio)


# Background
Harold's company has been investing in algorithmic trading strategies. Some of the investment managers love them, some hate them, but they all think their way is best.
You just learned these quantitative analysis techniques with Python and Pandas, so Harold has come to you with a challenge—to help him determine which portfolio is performing the best across multiple areas: volatility, returns, risk, and Sharpe ratios.
You need to create a tool (an analysis notebook) that analyzes and visualizes the major metrics of the portfolios across all of these areas, and determine which portfolio outperformed the others. You will be given the historical daily returns of several portfolios: some from the firm's algorithmic portfolios, some that represent the portfolios of famous "whale" investors like Warren Buffett, and some from the big hedge and mutual funds. You will then use this analysis to create a custom portfolio of stocks and compare its performance to that of the other portfolios, as well as the larger market (S&P 500 Index).

### For this homework assignment, I have three main tasks:

1. [Read in and Wrangle Returns Data](#Prepare-the-Data)

2. [Determine Success of Each Portfolio](#Conduct-Quantitative-Analysis)

3. [Choose and Evaluate a Custom Portfolio](#Create-a-Custom-Portfolio)

---

# Instructions

## Prepare the Data

First, read and clean several CSV files for analysis. The CSV files include whale portfolio returns, algorithmic trading portfolio returns, and S&P 500 historical prices and complete the following steps:

1. Use Pandas to read the following CSV files as a DataFrame. Be sure to convert the dates to a `DateTimeIndex`.

    * `whale_returns.csv`: Contains returns of some famous "whale" investors' portfolios.

    * `algo_returns.csv`: Contains returns from the in-house trading algorithms from Harold's company.

    * `sp500_history.csv`: Contains historical closing prices of the S&P 500 Index.

2. Detect and remove null values.

### WHALES:
<img width="264" alt="Screenshot 2024-01-17 at 8 51 46 PM" src="https://github.com/kimrodriguezFINTECH/AWHALE/assets/152752672/941cb061-b51f-4e38-acae-ce543936a574">

### ALGO 1 & 2
<img width="211" alt="Screenshot 2024-01-17 at 9 59 09 PM" src="https://github.com/kimrodriguezFINTECH/AWHALE/assets/152752672/6970b009-3a8b-4298-bf42-0817126bdc80">

### SP500:
<img width="351" alt="Screenshot 2024-01-17 at 9 59 27 PM" src="https://github.com/kimrodriguezFINTECH/AWHALE/assets/152752672/d019fe8c-9eea-4806-847b-c65e07ac56f0">


3. If any columns have dollar signs or characters other than numeric values, remove those characters and convert the data types as needed.

<img width="705" alt="Screenshot 2024-01-17 at 10 01 57 PM" src="https://github.com/kimrodriguezFINTECH/AWHALE/assets/152752672/8b5b2b45-2ad4-47e4-bfee-551f515d9241">

4. The whale portfolios and algorithmic portfolio CSV files contain daily returns, but the S&P 500 CSV file contains closing prices. Convert the S&P 500 closing prices to daily returns.
   
<img width="453" alt="Screenshot 2024-01-17 at 10 02 34 PM" src="https://github.com/kimrodriguezFINTECH/AWHALE/assets/152752672/df8971a0-178c-4dee-81c2-c8601d4925c4">


5. Join `Whale Returns`, `Algorithmic Returns`, and the `S&P 500 Returns` into a single DataFrame with columns for each portfolio's returns.

joined_data_columns = pd.concat([clean_whales, clean_algo, clean_daily_returns], axis="columns", join= "inner")
joined_data_columns

## Conduct Quantitative Analysis

Analyze the data to see if any of the portfolios outperform the stock market (i.e., the S&P 500).

## Performance Analysis

1. Calculate and plot daily returns of all portfolios.
   
<img width="1001" alt="Screenshot 2024-01-17 at 10 08 24 PM" src="https://github.com/kimrodriguezFINTECH/AWHALE/assets/152752672/e3037571-8761-43a8-b500-2b820b525a2e">


3. Calculate and plot cumulative returns for all portfolios. Does any portfolio outperform the S&P 500?
   
<img width="999" alt="Screenshot 2024-01-17 at 10 09 07 PM" src="https://github.com/kimrodriguezFINTECH/AWHALE/assets/152752672/32b96c25-291a-4afa-8757-e94701f5d68c">

## Risk Analysis


1. Create a box plot for each of the returns.
   
<img width="817" alt="Screenshot 2024-01-17 at 10 20 37 PM" src="https://github.com/kimrodriguezFINTECH/AWHALE/assets/152752672/4c5587dc-bbee-4dbc-a7b5-28b039ebaa45">


2. Calculate the standard deviation for each portfolio.

<img width="472" alt="Screenshot 2024-01-17 at 10 21 08 PM" src="https://github.com/kimrodriguezFINTECH/AWHALE/assets/152752672/e53ef2f9-aad0-4d87-9d98-caa23e80a911">


3. Determine which portfolios are riskier than the S&P 500.

<img width="701" alt="Screenshot 2024-01-17 at 10 15 12 PM" src="https://github.com/kimrodriguezFINTECH/AWHALE/assets/152752672/4b21721e-cd3b-4bd7-a7d7-df8dd50fc662">


4. Calculate the Annualized Standard Deviation.

<img width="511" alt="Screenshot 2024-01-17 at 10 21 17 PM" src="https://github.com/kimrodriguezFINTECH/AWHALE/assets/152752672/c64b8c93-7454-4d0e-b16c-d4fe87b18e71">

## Rolling Statistics


1. Calculate and plot the rolling standard deviation for all portfolios using a 21-day window.

<img width="1074" alt="Screenshot 2024-01-17 at 10 26 53 PM" src="https://github.com/kimrodriguezFINTECH/AWHALE/assets/152752672/2d5fea12-2cc2-4535-abf1-5169b1dc3566">


2. Calculate and plot the correlation between each stock to determine which portfolios may mimick the S&P 500.

<img width="587" alt="Screenshot 2024-01-17 at 10 28 51 PM" src="https://github.com/kimrodriguezFINTECH/AWHALE/assets/152752672/91b67458-b60d-4930-982f-2e66fa1748ca">


3. Choose one portfolio, then calculate and plot the 60-day rolling beta between it and the S&P 500.
Rolling Statistics Challenge: Exponentially Weighted Average
An alternative method to calculate a rolling window is to take the exponentially weighted moving average. This is like a moving window average, but it assigns greater importance to more recent observations. Try calculating the ewm with a 21-day half-life.

<img width="758" alt="Screenshot 2024-01-17 at 10 30 04 PM" src="https://github.com/kimrodriguezFINTECH/AWHALE/assets/152752672/a926870a-53d8-4cfb-8a28-831186c8c23b">


## Sharpe Ratios

Using the daily returns, calculate and visualize the Sharpe ratios using a bar plot.

<img width="758" alt="Screenshot 2024-01-17 at 10 32 07 PM" src="https://github.com/kimrodriguezFINTECH/AWHALE/assets/152752672/ece75659-9136-48bc-a1c0-4fe786d68381">


Determine whether the algorithmic strategies outperform both the market (S&P 500) and the whales portfolios.
- Algo 1 outperformed SP 500 and Whale Returns however, Algo 2 did not completely


## Create a Custom Portfolio
Harold is ecstatic that you were able to help him prove that the algorithmic trading portfolios are doing so well compared to the market and whales portfolios. However, now you are wondering whether you can choose your own portfolio that performs just as well as the algorithmic portfolios. Investigate by doing the following:

For this section I used the Resources folder CSV files for: 
-APPLE 
-COSTCO 
-GOOGLE. 

NOTE: These were provided as a backup in the event that the Google Finance function is not functioning properly on my laptop.


## Run the following analyses:

### Calculate the Annualized Standard Deviation.

daily_std = full_portfolio.std()
annualized_std = daily_std * np.sqrt(252)
annualized_std
SOROS FUND MANAGEMENT LLC      0.146675
PAULSON & CO.INC.              0.116732
TIGER GLOBAL MANAGEMENT LLC    0.232531
BERKSHIRE HATHAWAY INC         0.247155
Algo 1                         0.133704
Algo 2                         0.139556
SP500                          0.152054
kims_port                      0.211496
dtype: float64

Calculate and plot rolling std with a 21-day window.

Calculate and plot the correlation.

Calculate and plot beta for your portfolio compared to the S&P 60 TSX.

Calculate the Sharpe ratios and generate a bar plot.



# How does your portfolio do?
My portfolio did great. My portfolio came in second right behind Algo 1. Also my porfolio did better than the SP500 as well.



# Resources
## Prepare the Data
### Tutor Meetings through FINTECH Bootcamp: 
#### Charles W.
#### -Monday 1/8/2024
#### -Tuesday 1/9/2024
#### -Monday 1/15/2024

### Tutor Meetings External Resources:
#### Website: https://www.edwardrees.info
#### Edward R.
#### -Monday 1/8/2024
#### -Sunday 1/14/2024

### Python:
https://www.python.org/about/gettingstarted/

## Conduct Quantitative Analysis
### Tutor Meetings through FINTECH Bootcamp: 
#### Charles W.
#### -Monday 1/8/2024
#### -Tuesday 1/9/2024
#### -Monday 1/15/2024

### Tutor Meetings External Resources:
#### Website: https://www.edwardrees.info
#### Edward R.
#### -Monday 1/8/2024
#### -Sunday 1/14/2024

## Sharpe Ratios
### Tutor Meetings through FINTECH Bootcamp: 
#### Charles W.
#### -Monday 1/8/2024
#### -Tuesday 1/9/2024
#### -Monday 1/15/2024

### Tutor Meetings External Resources:
#### Website: https://www.edwardrees.info
#### Edward R.
#### -Monday 1/8/2024
#### -Sunday 1/14/2024

### Study Partner taking FINTECH Bootcamp (Same Class):
#### German Romero 
#### -Helped eachother fix code errors 
#### -Cross Referenced work to help eachother understand why we are using a specific code and understand what the question is asking us for 

## Create Custom Portfolio
### Tutor Meetings through FINTECH Bootcamp: 
#### Charles W.
#### -Monday 1/8/2024
#### -Tuesday 1/9/2024
#### -Monday 1/15/2024

### Tutor Meetings External Resources:
#### Website: https://www.edwardrees.info
#### Edward R.
#### -Monday 1/8/2024
#### -Sunday 1/14/2024

### Study Partner taking FINTECH Bootcamp (Same Class):
#### German Romero 
#### -Helped eachother fix code errors 
#### -Cross Referenced work to help eachother understand why we are using a specific code and understand what the question is asking us for  

## Additional Resources:
### Python for Beginners
https://www.python.org/about/gettingstarted/

### Pandas API Docs
https://pandas.pydata.org/pandas-docs/stable/reference/index.html

### Exponential weighted function in Pandas
https://pandas.pydata.org/pandas-docs/stable/reference/api/pandas.DataFrame.ewm.html

