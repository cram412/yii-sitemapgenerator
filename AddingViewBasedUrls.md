Basic syntax:
```
/**
 * @sitemap dataSource=view:application.views.site.pages
 */
public function actions() {
	return array(
		'page'=>array(
			'class'=>'CViewAction',
		),
	);
}
```

**dataSource** parameter must be set as:
```
dataSource=view:[aliases]
```
Where _aliases_ is comma-separated string of aliases, which directs to
folders with view files.

Script will try to resolve URL GET parameter (default 'view'), route (in this example is 'page') and will add to 'lastmod' attribute view-file last modification time (through _filemtime()_ function). Anyway, you can set some parameters manually.

Example:
```
/**
 * @sitemap dataSource=view:application.views.site.pages priority=0.6 params=view:ownGETViewParam route=/site/page
 */
```