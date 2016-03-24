1. Extract release files to **protected/extensions/sitemapgenerator**.
Expected directory structure: _protected/extensions/sitemapgenerator/SitemapGenerator.php_.


2. Configuration of **/protected/config/main.cfg**
```
<?php
return array(
	...
	'controllerMap'=>array(
		'sitemap'=>array(
			'class'=>'ext.sitemapgenerator.SGController',
			'config'=>array(
				'sitemap.xml'=>array(
					'aliases'=>array(
						'application.controllers',
					),
				),
			),
		),
	),
	...
	'components'=>array(
		'urlManager'=>array(
			'rules'=>array(
				array(
					'class'=>'ext.sitemapgenerator.SGUrlRule',
					'route'=>'/sitemap', // Optional. Default: '/sitemap'
					),
				
			),
		),
	),
);


```

That's all.
Now you can add to your sitemap.xml file any URLs from _'application.controllers'_ folder. File will be accessible by URL: `http://yourhost/sitemap.xml`

If you need more complex configuration or even index file for sitemaps, please see [Configuration wiki page](Configuration.md).