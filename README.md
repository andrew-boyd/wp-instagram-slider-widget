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


#Installation Instructions
Download this repo as a zip and install as a normal plugin. **Before you activate this plugin you must deactivate the original or you will likely encounter errors about attempting to re-define existing classes, etc.**

Keep the original plugin installed (but deactivated) in order to be alerted when there is an official fix from the plugin author.

#Disclaimer
These few lines of code were written and tested on a "well, that works for me!" basis. I take no responsibility if you run into issues while using this freely provided code. While its usage should be straightforward and safe, I can't possibly know all the variables that make your site yours, so install and use at your own risk.