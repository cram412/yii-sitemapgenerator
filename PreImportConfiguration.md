Syntax:
```
'import'=>[coma-separated string or array],
'force_include'=>[boolean],
```
**import** - list of aliases to import (will be imported by _Yii::import()_ command).
**force\_include** - identical parameter of _Yii::import()_


---


Overall pre-import configuration:
```
'controllerMap'=>array(
	'sitemap'=>array(
		'class'=>'ext.sitemapgenerator.SGController',
		'import'=>array('application.modules.catalog.models.*'),
		'force_include'=>true,
		'config'=>array(
			'sitemap.xml'=>array(
				...
			),
		),
	),
),
```

---

Sitemap file pre-import configuration:
```
'controllerMap'=>array(
	'sitemap'=>array(
		'class'=>'ext.sitemapgenerator.SGController',
		'config'=>array(
			'sitemap.xml'=>array(
				'import'=>array('application.modules.catalog.models.*'),
				'force_include'=>true,
				...
			),
		),
	),
),
```

---

Sitemap file alias-based pre-import configuration:
```
'controllerMap'=>array(
	'sitemap'=>array(
		'class'=>'ext.sitemapgenerator.SGController',
		'config'=>array(
			'sitemap.xml'=>array(
				'aliases'=>array(
					'application.modules.catalog.controllers'=>array(
						'import'=>array('application.modules.catalog.models.*'),
						'force_include'=>true,
					),
				),
				...
			),
		),
	),
),
```