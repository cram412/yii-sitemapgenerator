_Note: model class must be imported._

Basic example:
```
/**
 * @sitemap route=/model/view dataSource=model:Catalog
 */
```
This one equals to
```
// Foreach
Catalog::model()->findAll()
// Add URL
Yii::app()->createAbsoluteUrl('/model/view',array('id'=>$data->id))
```
This is also equals to record:
```
/**
 * @sitemap route=/model/view dataSource=model:Catalog::model()->findAll() params=model:id
 */
```
This type of configuration also can be extended to more complex record which is also will be normally parsed:
```
/**
 * @sitemap route=/model/view dataSource=model:Post::model()->published()->findAll() params=model:array('user'=>$data->user->username,'title'=>$data->title) lastmod=model:update_time
 */
```

---

Available syntax:

---

**dataSource**
```
dataSource=model:[expression]
```
_expression_ can be a single **`ModelName`**, when it will resolved as
**`ModelName`::model()->findAll()**

Or it can be a full php expression like **`ModelName`::model()->someScopes()->findAll()**

---

**params**
```
params=model:[expression]
```
_expression_ can be a single **`attributeName`**, when it will resolved as
**array('attributeName'=>$data->attributeName)**

By default: **model:id**

Or it can be a full php array expression like **array('id'=>$data->id)** where **$data** is current model instance.

Or it can be a comma-separated set of model attributes. Like:
**params=model:id,userId**
which is equal to

**array('id'=>$data->id,'userId'=>$data->userId)**

---

**lastmod**, **priority** and **loc**
```
lastmod=model:[expression]
priority=model:[expression]
loc=model:[expression]
```
Usage of this parameters are identical to **params** except that it accepts only single attribute (no arrays).
Examples:
```
lastmod=model:update_time
priority=model:priority
loc=model:absolute_url
```