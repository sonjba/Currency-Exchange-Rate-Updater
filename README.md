# Currency-Exchange-Rate-Updater
Update conversion rates based on external API data
The updateCurrencyRates method updates currency records in Salesforce using data fetched from an external API. Here's a brief overview of how it works:

Retrieve Currency Records: It first retrieves currency records from a specified object (objName; either DatedConversionRate and/or CurrencyType) in Salesforce. These records contain information such as currency ISO codes and Salesforce record IDs.

Fetch Exchange Rates: It then makes a GET request to an external API (https://open.er-api.com/v6/latest/GBP) to fetch the latest exchange rates. This API returns exchange rates for various currencies in JSON format.

Update Currency Records: After fetching the exchange rates, the method loops through the rates and compares them with the ISO codes of the currency records retrieved from Salesforce. If a match is found, it constructs a new currency record with the updated conversion rate and adds it to a list (recordsToUpdate).

Batch Update: Finally, it calls the updateCurrencyType method to perform a batch update of the currency records using POST requests. Each POST request updates a single currency record in Salesforce with the new conversion rate.
