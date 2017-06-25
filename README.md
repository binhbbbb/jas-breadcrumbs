<!--
```
<custom-element-demo>
<template>
    <link rel="import" href="jas-breadcrumbs.html">
    <script>
        document.addEventListener('WebComponentsReady', function() {
          var breadCrumbMenu = [];
          breadCrumbMenu.push({text: "Main", id: "main"});
          breadCrumbMenu.push({text: "Second", id: "second"});
          breadCrumbMenu.push({text: "Third", id: "third"});
          this.$.test.setMenu(breadCrumbMenu);
        });
    </script>
</template>
</custom-element-demo>
```html
-->

# \<jas-breadcrumbs\>

Simple Breadcrumbs Menu with Help Icon at the right side of the Page.  A Polymer 2.0 Component Only.

## Using the Component

```

  <link rel="import" href="../bower_components/jas-breadcrumbs/jas-breadcrumbs.html">
  <jas-breadcrumbs id="breadcrumbs" selected="{{page}}"></jasbreadcrumbs>
  
```html
This will create a menu.  When the item is select the 'id' above is set to the attribute and also a message is fired.  You can use your most prefered method of processing the event.

You set the breadcrumbs by sending a json file in this format:

```
 var breadCrumbMenu = [];
          breadCrumbMenu.push({text: "Main", id: "main"});
          breadCrumbMenu.push({text: "Second", id: "second"});
          breadCrumbMenu.push({text: "Third", id: "third"});
          this.$.breadcrumbs.setMenu(breadCrumbMenu);

```js

## Events

There are two ways.  The first

```
  <jas-breadcrumbs id="breadcrumbs" selected="{{page}}"></jasbreadcrumbs>
  
```html

So you can trap the output in the Polymer way.  Or you can trap the fired dispatch event and you can use it to change the page.

```
    document.addEventListener("page_change", function(e) {
        console.log("Event: Page Change Requested - ", e.detail.page);
        // Do Your Page Change Stuff Here
    });
```js

When the help button is pressed it sets the attribute selected to "help_page" but also dispatches an event message of "page_help".

```
    document.addEventListener("page_help", function(e) {
        console.log("Help Page Requested");
        // Do Your Help Page Stuff Here
    });
```js

## Hooking into the Component

It also links itself to its base class.  So the last instance will overwrite the value, but normally you would only have one of these anyhow. This is useful "other" way of talking to the component. If there is a neater way let me know!

```

  JasBreadcrumbs.hook 
  
```js
