# Inviewr

Inviewr is a JavaScript library that allows you to detect when elements come into view. It has no dependencies, it's very lightweight (less than 1kB gzipped), and it's based on the new `IntersectionObserver`, so it's easy on browser resources as well.

Should you use the library on an older browser, Inviewr falls back to a compatibility mode that uses window events instead.

## Installation

Here's what you need to do to include the library in your project:

### NPM

If you're using NPM and a tool such as Webpack, simply download the package with the following command:

```
npm install inviewr --save
```

### Standard way

Download the [minified script](https://raw.githubusercontent.com/andreg/inviewr/master/dist/evolvethemes-inviewr.min.js) from the `dist` folder in this repository (the `master` branch holds the latest release, while the `dev` branch is for development purposes).

## Usage

In order for an element to be kept track of, it needs to be registered with the library.

Once included, the library activates itself on the `DOMContentLoaded` event, which means that before the event is actually fired we have time to declare which group of elements we are going to track.

To register elements, we can use their CSS selector:

```
window.inviewr.register( "img", { toggle: true } )
```

The above code will be interpreted by the library as a "_let's keep track of all `img` elements, and let's fire events whenever they come in or out of view".

When an element becomes viewable, two things happen:

* the element is given an `evolvethemes-inviewr` class,
* the element emits an `evolvethemes-inview` event.

When an element isn't viewable anymore, instead:

* the `evolvethemes-inviewr` class is removed from the element,
* the element emits an `evolvethemes-not-inview` event.

When registering an object for tracking, the second parameter is an options object. As of today, these are the option settings available:

* `toggle`: _false_ - When set to `true`, the classes are added/removed depending on the element's in-view status; if left to `false`, the class is not removed when the element goes out of view.
