# Crypto Price Console v2.0

## **Place holder:**

## Table of Contents

- [About](#about)
- [Status](#status)
- [Getting Started](#getting_started)
- [Prerequisites](#prerequisites)
- [Installing](#installing)
- [Usage](#usage)

## About

Simple console application utility that calls a third party web api to retrieve crypto prices.

This application uses the following open source libraries.

-- [PublicHoliday nuget package](https://github.com/martinjw/Holiday/")

-- [Spectre Console and Spectre Console Cli](https://spectreconsole.net/)

## Status

.NET 9
[![build](https://github.com/dotnetdeveloperaz/CryptoPriceConsole/actions/workflows/build.yml/badge.svg?branch=main)](https://github.com/dotnetdeveloperaz/CryptoPriceConsole/actions/workflows/build.yml)

<a href="https://www.buymeacoffee.com/dotnetdev" target="_blank"><img src="https://cdn.buymeacoffee.com/buttons/default-orange.png" alt="Buy Me A Coffee" height="41" width="174"></a>

## Getting Started <a name = "getting_started"></a>

These instructions will get you a copy of the project up and running on your local machine.

## Prerequisites

1. .NET 9 runtime or SDK.
2. Account with [CoinCap.io](https://www.coincap.io/).
3. MariaDB (or MySQL) if using the --save switch without --cache and --cachefile. This is optional.
4. Configure appsettings or user-secrets **(Token) (DefaultDB) keys**


```json
"ApiServer": {
    "Token": "",
    "CacheFile": "MetalPrice.cache",
    "BaseURL": "https://api.coincap.io/v2/",
    "Currency": "USD",
  },
  "Logging": {
    "LogLevel": {
      "Default": "Information",
      "Microsoft": "Warning",
      "Microsoft.Hosting.Lifetime": "Information"
    }
  },
  "ConnectionStrings": {
    "DefaultDB": ""
  },
  "AllowedHosts": "*"
}
```

## Installing

Add your private settings for Token (ApiKey) and Database connection string or add them to appsettings.json above.

```bash
dotnet user-secrets init
dotnet user-secrets set "ApiServer:Token" "<YourApiKey>"
dotnet user-secrets set "ConnectionStrings:DefaultDB" "<YourDatabaseConnectionString>"
dotnet user-secrets list
```

Create the tables and stored procedures used by this utility.

If you would like the full history (Back to Dec 6th, 2018) of Metal Prices database, which will save you time and API calls if you want historical data, then restore the database in the db directory called MetalPrices.sql.gz.

```bash
```

Build the project by running the following in the project folder.

```bash
dotnet build
```

To run a simple test, run the following.

```bash
dotnet run account
```

You should see something similar to:

```bash
```

## Usage

Commands


### Switches

- --save writes the price data to the database on commands price and backtrack.

- --cache writes the data to a json file which later can be restored to the configured database, except when using the view command, which then will display data from the cache file.

- --fake will load sample data, instead of calling the WebApi. This is available for price, history and acct commands.

Example:

```bash
```

#### Base Currencies Supported - See the third party API documentation for any new additions.
``` text
USD - United States Dollar
```

#### Only U.S. Non-Holiday Week Days Are Processed

Passing --debug will output configuration data. If you pass --debug --hidden, it will also output private configuration data (eg: DB connection string, token) even when not put into appsettings.json but in user-secrets instead.

Run the application with no commands (dotnet run) and you will get the following usage screen.
*NOTE: view command does not use --fake or --token and they are ignored.

```bash
```
