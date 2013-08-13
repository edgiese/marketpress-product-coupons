marketpress-product-coupons
===========================

This is a drop-in replacement to improve coupon handling in Marketpress.  It is tied to 2.8.7.  If you have a different version, then do a diff between the original file and the edited one, and apply similar changes.

What this Enhancement Does
--------------------------

1. Improves Handling of Coupons generally, particularly with better messages.
2. Adds two fields to the coupon table, "Products" and "Message".
3. Does additional processing depending on the coupon code.


The "products" string is based on SKUs.  It can be as simple as an sku to match, and also way more complex.  The general form of the 'products' line is:

    Products = required skus[;any-of-skus[;discountamounts]]

The "required skus" (you can have multiple specified, all separated by commas) must _all_ be there, or the coupon won't work.  The "any-of-skus" must have one or more present of the products in the list.  __Note:__ You can use wildcards.  A '?' matches a single character, and a '*' matches multiple characters.

There is also a "Message String."  This is a failure message that will be displayed if your product rules are not being met.  This is your chance to explain to the customer why the coupon isn't working.    

Here are some examples of strings you could use:

    Product = premium-content
    Message = This coupon only works for a premium content subscription

_In the above example, the product with sku "premium-content" must be present, or the message indicated will be displayed.  If it is, the standard fields in the coupon will apply._


    Product = recipe-book;video-*
    Message = You must purchase the recipe book and at least one video to use this coupon

_In the above example, the recipe-book product must be present, with at least one of video-1, video-2, or video-3.  If it is, the standard fields in the coupon will apply._


    Product = recipe-book;video-*;2,5,9
    Message = You must purchase the recipe book and at least one video to use this coupon

_In the above example, the recipe-book product must be present, with at least one of video-1, video-2, or video-3.  If only the book is present, then it is $2 off, if the book and one video is chosen, it is $5 off, if the book and two or more videos are chosen, it is $9 off._


    


    
