# Like Post
Read detailed version of this source on the like button on [WordpressZone](http://wordpresszone.co/?p=43 "AJAX Like Button")
##Include the php files
note: these should be included in the functions.php
```php
   <?php
   include_once('inc/like-metabox.php');
   include_once('inc/like-post.php');
   ?>
```

##Enqueue the js file
note: this also has to be added to the functions.php file, if there's already a "wp_enqueue_scripts" present just add the script to that function
```php
<?php
function enqueue_js_files() {

   wp_register_script( 'like-post', get_template_directory_uri() . '/js/like-post.js', array('jquery') ,false,'1.0',true);
   wp_enqueue_script( 'like-post' );

}
add_action( 'wp_enqueue_scripts', 'enqueue_js_files' );
?>
```

##Show the like link
Make the like button show up in the front-end in it's most basic form, when the button has been clicked the js adds or removes the class "liked"
```html
<a class="like" rel="<?php echo $post->ID; ?>"><?php echo likeCount($post->ID); ?> likes</a>
```

###Show the metabox on multiple post types
Simply add new ones to the array and the metabox will show up on those pages. Just don't forget to add the like button/link in the front-end
```php
// You can find this on line 9 in the like-metabox.php file
$show_on = array('post', 'pets');
```