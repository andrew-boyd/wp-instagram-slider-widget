# Patched instagram-slider-widget
Temporary patched repo for Instagram slider widget that broke due to Instagram changes. Not my original work, just a quick fix I thought others may find helpful.

Instagram has silently added a cache parameter to the end if their image urls that breaks the scraping approach used by this plugin. This fix works by simply inserting a step to trim the cache parameter off of the end of the image url before attempting to detect if the provided url is a supported image type.

**original plugin:** https://wordpress.org/plugins/instagram-slider-widget/

The change applied by this patch is on lines `1041 - 1043` and is as follows if you wish to apply it manually:

```php
// temp fix, strip cache param off of url
$parsed_image_data = parse_url($image_data['url']);
$image_data['url'] = $parsed_image_data['scheme'] . '://' . $parsed_image_data['host'] . $parsed_image_data['path'];
// end temp fix;
```
