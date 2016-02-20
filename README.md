# Checkie for AngularJS
An AngularJS directive that checks against a minimum Internet Explorer version before including content.

## What does Checkie do?

Checkie is a simple directive to do a check to see if the browser is:

1. Internet Explorer
2. The Internet Explorer version is less than 9 (default) or the user specified version via the `checkie-min-ie` attribute

This directive can wrap any content you may wish to not include for old browsers, from navigation elements, to your ng-view (See Usage below).

    <div data-checkie data-checkie-min-ie="9" data-checkie-message="You are using a dodgy browser, please update.">
        <div data-ng-view="myApp"></div>
    </div>

## Installation

There are two easy ways to install the checkie directive:

#### Node

To install via npm, run:

    npm install @iamadamjowett/angular-check-ie

#### Bower

To install via Bower, run:

    bower install angular-check-ie 

#### Manual download

Download the `checkie.directive.js` folder, and include it in your index.html file with something like:
    
    <script type="text/javascript" src="/path/to/checkie.directive.js"></script>

Also be sure to include the module in your app.js file with:

    angular.module('yourAppName', ['angular-checkie'])

## Usage

To use the checkie directive, wrap some content in either a `<checkie>` tag, or via attribute for older browsers. This will check and not include the wrapped content if the browser is a version of Internet Explorer less than 9 (the default check value). e.g.

    <checkie>
        <div>This is content only for modern browsers.</div>
    </checkie>

or

    <div checkie>
        <div>This is content only for modern browsers.</div>
    </div>
    
or even

    <div data-checkie>
        <div>This is content only for modern browsers.</div>
    </div>
    
By default, the above will hide the content and leave a message of "You're using Internet Explorer [the ie version], please update your browser.". This is great for full page hides, but not great if hiding small elements, so you can override this with the `checkie-message` attribute (see Custom checkie message).

To hide your entire apps view from old browsers:

    <checkie>
        <div ng-view="myApp"></div>
    </checkie>
    
#### Custom Internet Explorer version checkdate

By default, checkie will look for Internet Explorer 8 and below, but if you want to change that, you can do that via the `checkie-ie-min` attribute:

    <checkie checkie-ie-min="9">
        <div ng-view="myApp"></div>
    </checkie>
    
or 

    <div data-checkie data-checkie-min-ie="9">
        <div ng-view="myApp"></div>
    </div>
    
#### Custom checkie message

You may want to display a message to the user of the old browser, this can be done via the `checkie-message` attribute:

    <checkie checkie-message="Please update your browser you poor sod">
        <div ng-view="myApp"></div>
    </checkie>
    
or

    <div data-checkie data-checkie-message="You are using a dodgy browser, please update.">
        <div ng-view="myApp"></div>
    </div>
    
#### Debugging

Checkie comes with a debug tag to test the functionality and visibility of elements. To simulate an Internet Explorer version add the `checkie-debug` tag and give a version to check:

    <checkie checkie-debug="6">
        <div ng-view="myApp"></div>
    </checkie>
    
or

    <div data-checkie data-checkie-debug="6">
        <div ng-view="myApp"></div>
    </div>
    
The above pretends the browser is Internet Explorer 6 and processes it accordingly.

## Display

The checkie directive will wrap your content in a div with the classes:

    - checkie
    - outdated - this is only shown if the Internet Explorer version check find it is an old version
    
This should allow you to style the checkie directive as you need on older browsers.

## Credits

This directive spawned from @padolsey's gist and it's associated discussion: [https://gist.github.com/padolsey/527683](https://gist.github.com/padolsey/527683)

## Licence

MIT, free to use in personal and commercial projects.
