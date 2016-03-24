# Configuration #
Record syntax:
```
'cache'=>array('cache_component_id','duration','dependency'),
```

---

For all sitemap files:
```
'controllerMap'=>array(
	'sitemap'=>array(
		'class'=>'ext.sitemapgenerator.SGController',
		'cache'=>array('cache',60,null),
		'config'=>array(
			'sitemap.xml'=>array(
				...
			),
		),
	),
),
```
Will be applied if no cache option specified in sitemap file configuration.


---


For selected sitemap files:
```
'controllerMap'=>array(
	'sitemap'=>array(
		'class'=>'ext.sitemapgenerator.SGController',
		'config'=>array(
			'sitemap.xml'=>array(
				...
				'cache'=>array('cache',60,null),
			),
		),
	),
),
```