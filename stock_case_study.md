# Stock Portfolio Tracker

## Introduction
This web application allows you to keep track of your stocks, equities, ETFs, and any other type of financial securities. Real-time stock price is available for US stocks, forex and crypto thanks to the Finnhub Stock API (https://finnhub.io/).

This app was developed with Ruby on Rails, and it is backed by a PostgreSQL database. Save for the boilerplate tags and elements, the vast majority of the HTML and CSS are written from scratch.

## Designing the Schema and Routes

The schema for this project is relatively straightforward. Each portfolio can have one or many holdings, and each holding can have one or many transactions. For instance, a FAANG portfolio may contain each of the big five tech stocks. Each of the tech stock can then be traded

When it comes to the routes, it made sense to nest each child resource within its corresponding parent resource, e.g. nesting holdings within portfolios. Given that we have 

## Boosting Performance Through Caching
A major issue that impeded this app from scaling was its dependency on an external API, but this problem can be mitigated to a large extent by caching the results of the API calls.

This app was developed with the free tier of the Finnhub Stock API (https://finnhub.io/pricing). At the time of writing, a free user is limited to only 60 API calls per minute. There is also a 30 API calls per second limit on top of that.

## Future Plans
At present, the cache is refreshed only once per minute. This is undesirable for anyone who wants to see the latest market prices. One workaround would be to include a refresh button on the pages that are displaying live data, i.e. `Portfolio#index` and `Portfolio#show`.

Include more information about the stock symbol. This can be implemented by making an API call to `#stock_symbols` (https://finnhub.io/docs/api/stock-symbols).

Expand the breadth and depth of financial data, e.g. dividends, dividend payout dates, 52-week highs and lows, annualized profits or losses.

Visualize the holdings in each portfolio, e.g.  weighted distribution of stocks in a pie chart, performance of a holding in a line graph.

The ability to sell! At the moment, the app only keeps track of what you've bought. The only way to 'sell' a stock is to delete the transaction. This entails creating another column in the transactions database to indicate whether the transaction was a purchase or a sale.