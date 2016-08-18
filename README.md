# woocommerce-custom-related-products
Woocommerce custom related products plugin with WPML support

This is an updated version of a publicly available plugin "Custom Related Plugin for Woocommerce" which can be downloaded from Wordpress plugin respository here: https://wordpress.org/plugins/custom-related-products-for-woocommerce/
This plugin allows you to define list of your own related products to be shown on product page, instead of using Woocommerce's internal related products algorithm which makes use of categories and tags to put up related products suggestions.

The plugin at it's current state isn't able to handle products in multi-language. After checking the support area of the plugin (https://wordpress.org/support/plugin/custom-related-products-for-woocommerce), I realized that lots of other users are also asking for the same thing but there has been no response on this particular topic. So I went ahead and tried to patch the plugin so that it supports related products in languages other than English (for websites specifically using WPML plugin for their translations).

# Problem
Problem with the plugin is that when we store related products in other languages, it pulls and stores the IDs of products in English language, not the language of the product which is being edited. So what we needed was that either we pull the products in other language at the time of selection. OR we change the IDS while storing them. The later option happened to be an easy one.

# Solution
I used a WPML function to get the translated product ID     icl_object_id($id, 'product', false,ICL_LANGUAGE_CODE);
And stored this in related[] array instead of $id.
