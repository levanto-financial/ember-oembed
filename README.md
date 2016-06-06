# ember-oembed [![Build Status](https://travis-ci.org/levanto-financial/ember-oembed.svg?branch=master)](https://travis-ci.org/levanto-financial/ember-oembed)

[oEmbed](http://oembed.com) is a standard for embedding arbitrary content into something else. 

**Note:** Many types of content don't support CORS when using oEmbed, which prevents us from using this client-side-only solution. Exceptions to this are sites like [facebook](http://facebook.com) and [soundcloud](http://soundcloud.com), both of which allow cross-origin requests to retrieve oEmbed information. If you need broad support, consider using a service like [iframely](https://iframely.com/), which can easily be used w/ this addon.


## Installation

Install this addon with ember-cli

```
ember install ember-oembed
```


## Use
 
Using ember-oembed is as easy as using an `<img>` tag.


**Using the standard embed content, delivered by the provider**
```hbs
{{ember-oembed src="https://soundcloud.com/vaughan-1-1/this-is-what-crazy-looks-like"}}
```


**Custom embed content**

```hbs

{{#ember-oembed
   src="https://soundcloud.com/vaughan-1-1/this-is-what-crazy-looks-like" as |c|}}
  
  <h1>{{c.title}}</h1>
  <p>{{c.description}}</p>

{{/ember-oembed}}

```


#### Adding a provider that's not already included with this addon**

**config/environment.js**
```js
var ENV = {
  ...
  oembed: {
    providers: {
      mysite: {
        regex: /www.mysite.com\/thing/g,
        providerUrl: 'http://mysite.com/oembed',
        defaultParams: {
          format: 'json'
        } 
      }
    }
  }
  ...
}
```

This would result in the addon attempting to fetch oEmbed info from
`http://mysite.com/oembed?url=http://mysite.com/thing/12345&format=json`


## Developing this Addon

* `git clone` this repository
* `npm install`
* `bower install`

## Running

* `ember server`
* Visit your app at http://localhost:4200.

## Running Tests

* `npm test` (Runs `ember try:testall` to test your addon against multiple Ember versions)
* `ember test`
* `ember test --server`

## Building

* `ember build`

For more information on using ember-cli, visit [http://ember-cli.com/](http://ember-cli.com/).
