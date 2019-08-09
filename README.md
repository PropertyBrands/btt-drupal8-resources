# Links and Resources for Drupal 8

 - Add a class to a field's markup based on a value: https://www.drupal.org/forum/support/module-development-and-code-questions/2017-03-31/add-class-to-field-in-drupal-8
 
 - Views Template names (Twig debug does not output this info): https://api.drupal.org/api/drupal/core%21modules%21views%21views.theme.inc/group/views_templates/8.2.x
 
 - `cc` is very useful DX tool. Clearing the render cache is currently a very frequent event.
 https://www.drupal.org/docs/user_guide/en/prevent-cache-clear.html
 
 - `srcset` and responsive images: https://chromatichq.com/blog/responsive-images-drupal-8-using-srcset
 
 - When you have a renderable array (`$variables` in a preprocess context is a render array now) you can set `$renderable['#cache']['max-age'] = 0` to avoid having to flush the render cache after *every* code change.
