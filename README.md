# streaminganalytics-sunsynk
Sunsynk integration for Cumulocity Streaming Analytics

## EPL Apps

The EPL Apps under the `epl/` folder can be added to a Cumulocity IoT tenant in order to gather data from a SunSynk PV/inverter/battery setup and Octopus Energy account. The live data from those sources are then visible in your Cumulocity IoT tenant. The EPL Apps also generate derived measurements and can also be used to automatically configure your inverter and batter depending on pricing and weather forecasts.

The Apps that are available are as follows:

* `epl/SunsynkDataCollector.mon` - Collects all the live data from your Sunsynk account
* `epl/OctopusPriceCollector.mon` - Collects pricing information from your Octopus account
* `epl/WeatherDataCollector.mon` - Collects weather forecasts for your location
* `epl/DerivedPricing.mon` - Calculates derived price metrics, like current cost per hour

There is also a file called `SyncApp.mon`, which is just used to keep this repository up to date with changes to the development tenant.

In order to deploy any of these files, just copy the contents into a new EPL App in your tenant. Configuration of the app is done via tenant options.

## Tenant Options

The following tenant options should be set in your tenant, depending which Apps you have loaded and features that you need:

* `apamax.sunsynk/username` - your Sunsynk username
* `apamax.sunsynk/password` - your Sunsynk password
* `apamax.sunsynk/inverterId` - The ID of your Sunsynk inverter
* `apamax.octopus/apiKey` - Your API key for your Octopus account
* `apamax.octopus/products` - A comma-separated list of product names for which you want prices
* `apamax.weather.location` - Your location in `lat,long` format
* `apamax.weather.timezone` - Your location in `Area/City` format

## Devices created

The following virtual devices will be created in your tenant against which measurements will be logged:

* `sunsynkINVERTERID` - The live data from your Sunsynk inverter
* `octopusPrices` - current and future pricing data for octopus products
* `weatherDataLAT.LONG` - weather forecast information for your location
* `derivedPricing` - derived pricing x usage data
