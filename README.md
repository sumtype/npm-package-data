# NPM Package Data

Easily get information about your [NPM](https://npmjs.com) packages.

## Installation

Navigate to your project's root directory and enter the following command in your terminal:

`npm install --save npm-package-data`

If your project doesn't rely on this module to run, enter this command instead:

`npm install --save-dev npm-package-data`

## Usage

NPM Package Data is a module which asynchronously gets package information based on a specified username, then passes that data to a specified callback function as an array of JSON objects.

To use this module, require it in and assign it to a variable.  This variable will be used to call the module as a function.

`var usernamePackageData = require('npm-package-data');`

Next, call the function.  The first parameter must be the username, in string form, to look for packages associated with.  The second parameter must be a callback function which takes one parameter, which will equal the array of package information JSON objects.  The callback function will be executed once the package information has been collected.

    usernamePackageData('username', function(data) {
      //Do something with the data here.
    });

#### Example

This example console logs the package information associated with the user, 'someone'.

    var someonePackageData = require('npm-package-data');
    someonePackageData('someone', function(data) {
      console.log(JSON.stringify(data));
    });

## Package Information JSON Structure

The package information JSON object passed to the callback function is an array of all of the package information associated with the specified username.  Each package's information is consolidated into an element of the array.  Each of these elements is a JSON object with the following form:

    [{
      "name": "The package's name.",
      "description": "The package's description.",
      "url": "The package's NPM URL.",
      "github": "The package's Github URL.",
      "version": "The package's version number.",
      "total_downloads": "The total number of times the package has been downloaded."
      "last_month_downloads": "The number of times the package has been downloaded in the last month."
    }, ...]
