# Ibovespa daily data

The study uses 2,729 daily observations from January 2, 2015 to December 30, 2025. Store a copy you are authorized to use at `data/ibovespa.csv`. Investing.com requires permission to redistribute its quotes, so the price history is a local input. [Provider’s historical data](https://www.investing.com/indices/bovespa-historical-data) · [Provider’s terms](https://www.investing.com/about-us/terms-and-conditions)

## English input format

Use a UTF-8, comma-separated file with the columns `date,open,close`. Dates use `YYYY-MM-DD` and the two numeric columns use a decimal point. Both levels are in **thousands of index points**. For example, an illustrative index level of 100,500 points is entered as `100.500`. Dates must be unique daily trading sessions. Other columns are ignored.

## Original provider format

The notebook also recognizes the headers `Data` (date), `Abertura` (open) and `Último` (close) used in the Brazilian export. Keep its `DD.MM.YYYY` dates and its original numeric representation. The academic study interpreted the provider’s thousands separator as a decimal point to express levels in thousands of index points. Absolute errors and scenario estimates use that unit. MAPE is reported as a percentage.
