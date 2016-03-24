# Adding URLs to sitemap #
### Single URL ###
```
/**
 * @sitemap
 */
public function actionIndex()
{
  ...
}
```
### Single URL with parameters ###

Parameters must be space-separated. URL will be resolved by action.
```
/**
 * @sitemap priority=0.5 lastmod=2012-12-25 changefreq=monthly
 */
public function actionIndex()
{
  ...
}
```
**route=/site/index2** - overrides resolved route to URL.

**loc=`http://www.example.com/`** - overrides link generation via _Yii::app()->createAbsoluteUrl()_, escapes and inserts to URL's 'loc' xml attribute.

**priority=0.5** - URLs priority attribute.

**changefreq=daily** - URLs changefreq attribute.

**lastmod=2012-12-25** - URLs datetime of last modification. Will be formatted to W3C datetime format.

**dataSource=methodName** - controllers public method, which will provide data for dynamic URLs generation (for examples see section of adding urls). More about these xml attributes: [sitemap.xml tag definitions](http://www.sitemaps.org/protocol.php#xmlTagDefinitions)

Note: _all parameters are optional._

### Predefined methods of adding URLs ###
Extension already has built-in methods for simple adding URLs based on **CActiveRecord** models and view files for **CViewAction**.
Please see corresponding wiki articles AddingModelBasedUrls and AddingViewBasedUrls. If your case is more complex, you can add URLs with your own controllers method. See example below.


### Multiple (dynamic) URLs ###
You can dynamically add URLs by setting _dataSource_ parameter to controllers public method name, which will generate URLs data array. URLs will be created by Yii::app()->createAbsoluteUrl($route,$params).
```
/**
 * @sitemap dataSource=getModelsUrls
 */
public function actionView($id) { ... }
public function getModelsUrls()
{
    $models=MyModel::model()->findAll();
    $data=array();
    foreach($models as $model)
        $data[]=array(
            'params'=>array('id'=>$model->id),
                // Optional parameters
            'changefreq'=>'monthly',
            'priority'=>0.5,
            'lastmod'=>$model->update_time,
        );
    return $data;
}
```
Note: _if @sitemap parameters is specified, they will be used as default for all parameters of URLs_.