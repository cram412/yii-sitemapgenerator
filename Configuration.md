All configuration of sitemaps are processed from **protected/config/main.php** file.

## Single sitemap.xml file ##
Default configuration is:
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
);
```

**Parameters for sitemap.xml file**
```
...
'config'=>array(
	'sitemap.xml'=>array(
		'aliases'=>'application.controllers',		
// Other optional parameters (will be used as defaults for all sitemap URLs)
		'routeStructure'=>'application,modules,controllers',
		'lastmod'=>time(),
		'priority'=>0.6,
		'changefreq'=>'yearly',
		'enabled'=>true,	// allow to disable sitemap (debug option)
	),
),
...
```
Note:

**aliases** parameter describes where extension should search for URLs data for current sitemap file. Can direct to folder of controllers or single controller. Specified as basic yii-alias record. Can be set as an array of aliases, or comma-separated string.

**routeStructure** parameter describes structure of yii routes. By default it's: _'application,modules,controllers'_. Used for URL route resolving.

Also you may configure **class pre-import** and **caching** for sitemap files. Please see corresponding wiki articles PreImportConfiguration and CacheConfiguration.

## Multiple sitemaps and sitemap index file ##
Configuration of multiple sitemaps files is identical to single, except that _sitemap.xml_ record must have only single option _'index'_ set to **true**.

Example:
```
'config'=>array(
	'sitemap.xml'=>array(
		'index'=>true, // Indicates that index file used
	),
	// All keys must begin with 'sitemap'
	'sitemapForum.xml'=>array(
		'aliases'=>array(
			'application.modules.forum.controllers',
		),
	),
	'sitemapBlog.xml'=>array(
		'aliases'=>array(
			'application.modules.blog.controllers',
		),
	),
),
```
Note: for every sitemap file available the same configuration parameters as was shown in first section (single sitemap.xml file).