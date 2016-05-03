# Routing with Raw React / Uniloc

Thanks for subscribing!

This repository holds a modified version of the final exercise for [Learn Raw React, part 3](http://jamesknelson.com/routing-with-raw-react/). Instead of storing the location state as an array of hash parts separated by `/`, it uses [uniloc](http://unicornstandard.com/packages/uniloc.html) to match the URL hashes against a number of predefined routes.

Here is a rundown of the major differences:

- I've added a `vendor` directory containing 3rd-party code, including `uniloc` and the `Object.assign` polyfill
- I've added a `ROUTER` constant which holds the `makeURI` and `lookupURI` functions, which are respectively configured to generate URIs from a `name` and `options` object, and parse URIs into a {name, options} object
- I've added an `APPLICATION_CONFIG` constant which maps the various named routes to view components, as well as the actions and state parameters which should be pased along as `props`
- Along with the above two constants, I've moved any other constant variables into a separate `constants.js` file
- `state.location` is now stored as an object with the properties `name` and `options`, as opposed to an array of URL hash parts.
- The `Application` component now decides what to render by using `APPLICATION_CONFIG`, as opposed to a `switch` statement.
- I've added a `Link` component which can generate an `<a>` tag for a given `location` (with `name` and `options` properties).
- The navigation actions have been updated to ensure that the user is always redirected to the *canonical* URL for a given page.
- The root redirect is now handled with a uniloc redirct route
