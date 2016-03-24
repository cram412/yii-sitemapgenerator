### About sitemaps ###
[Sitemaps.org](http://www.sitemaps.org/)

### Robots.txt ###
Add to your robots.txt following directive:

**`Sitemap: http://www.example.com/sitemap.xml`**

[Details](http://www.sitemaps.org/protocol.php#informing)

### PHP Timezone ###
You may need to setup your timezone if it's not set correctly in
PHP config or datetime values for _'lastmod'_ attributes.
[More about datetime formats](http://php.net/manual/en/datetime.formats.php).
All datetime values will be converted to [W3C datetime format](http://www.w3.org/TR/NOTE-datetime).