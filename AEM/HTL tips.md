

# HTL Tips

doc Adobe : https://experienceleague.adobe.com/fr/docs/experience-manager-htl/content/getting-started#
 
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

## Use list
```html
<sly data-sly-list.items="${resource.getChildren}">
	<sly data-sly-test="${items.name == 'itemsNamePropertie'}">
		<div data-sly-list.item="${items.children}">
			<div>${item.name}</div>
		</div>
	</sly>
</sly>
```

The check on items name propertie is optionnal.

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

Usally put template components on a "partials" folder and use relative path.

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

## Use context
doc : https://github.com/adobe/htl-spec/blob/master/SPECIFICATION.md#121-display-context 

doc with examples : https://medium.com/@manumathew28.94/htl-display-context-context-38e2fc34d927 
