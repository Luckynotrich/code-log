_Psst!_ Create a DigitalOcean account and get [$200 in free credit](https://try.digitalocean.com/css-tricks/?utm_medium=content_acq&utm_source=css-tricks&utm_campaign=global_brand_ad_en&utm_content=conversion_postarticle_psst) for cloud-based hosting and services.

## Comments

1.  Nice share! so target becomes the action=”url.html”.
    
2.  And I used to use java script to do this :O Thanks for sharing
    

4.  so if it is deprecated, what would be the alternative to open a form in a new window?
    
5.  Unfortunately, this is not totally ‘universally supported’ – it seems like if you try to have multiple forms doing this on one page (in a data grid, for example) – submitting one form kills the others so you get nothing on click (so far confirmed on latest webkit (safari 5.1, chrome 13), but the trick still works with Firefox 6)
    
    So if you’re using this on a site with multiple forms, you may wish to take a look at alternatives.
    
6.  Of course after being all doom & gloom I found the solution – each form must have a unique id attribute in order for this to work in Safari:
    
    This doesn’t work:
    
   ```
<form action="#" method="post" target="_blank">
<input type="submit">
</form>
<hr>
Then this: 
<form action="#" method="post" target="_blank">
<input type="submit">
</form>
```
    
but this does: 
    ```
    Click this:
    <form id="form1" action="#" method="post" target="_blank">
    <input type="submit">
    </form>
    <hr>
    ```
    
        
7.  So, can someone elaborate… I need a form with a drop down box with the names of some web pages. Choosing a web page and clicking submit should open to that page (in a new tab). How is this done?
    
    -   I’ve found the solution I need at [stackoverflow.com](http://stackoverflow.com/questions/10166596/open-page-in-new-tab-using-javascript-window-openelementname-elementvalue-in-a). The issue got convoluted because I didn’t want to use a regular submit button, as I would have had to create new styles, but already had existing styles for an anchor tag that emulated a button. You can see it in action here: [YourBeliefsMatter.com](http://www.yourbeliefsmatter.com/humanitarian-dreams/nicaragua-girls-orphanage/). Anyway, thanks for the post. It was helpful!!
        
8.  I have problem..  
    In my page there is table and number of rows increases the top-margin of table also increases..
    
9.  How to set the title for the new tab/window?
    
10.  if you set target=”\_blank” on form and you have , in IE11 it will break the file (image) .
    

### Leave a Reply