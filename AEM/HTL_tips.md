

# HTL Tips


 
## Set and use variable
```html
<sly data-sly-set.myVariable="hello"></sly>

<div>${myVariable}</div>
```

## Test simple
```html
<sly data-sly-test="${numberItems === 5}">
  <p>I have 5 items</p>
</sly>
```
## Use dialog properties
```html
<h1 data-sly-test="${properties.title}">${properties.title}</h1>
```

## Call a resource component (without properties)
```html
<sly data-sly-resource="${'myComponentHtml' @ 
resourceType='project/components/myComponent'}">
</sly>
```

## Import and use a component template (with properties)
```html
// import
<sly data-sly-use.myTemplateComponent="../partials/myTemplateComponent.html"></sly>

...

// use
<sly data-sly-call="${myTemplateComponent.template @ prop1='value', prop2='test'}"></sly>
```

## Use i18n trad
```html
<div>${'my-traduction-key' @ i18n}</div>
```

```json
// fr.json file

{
  "my-traduction-key": "Bonjour",
  ...
}

// en.json file

{
  "my-traduction-key": "Hello",
  ...
}
```
