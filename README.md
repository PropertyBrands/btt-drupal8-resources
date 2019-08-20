# Links and Resources for Drupal 8

 - Using the services container and dependency injection: https://www.drupal.org/docs/8/api/services-and-dependency-injection/services-and-dependency-injection-in-drupal-8

 - Add a class to a field's markup based on a value: https://www.drupal.org/forum/support/module-development-and-code-questions/2017-03-31/add-class-to-field-in-drupal-8
 
 - Views Template names (Twig debug does not output this info): https://api.drupal.org/api/drupal/core%21modules%21views%21views.theme.inc/group/views_templates/8.2.x
   
   - Should be able to use [Twig Tweak](https://www.drupal.org/docs/8/modules/twig-tweak/cheat-sheet) (contrib module) `{{ drupal_dump(variable_name) }}` to print out the results of any variable/object/array within a Twig template.
 
 - `cc` is very useful DX tool. Clearing the render cache is currently a very frequent event.
 https://www.drupal.org/docs/user_guide/en/prevent-cache-clear.html
 
 - `srcset` and responsive images: https://chromatichq.com/blog/responsive-images-drupal-8-using-srcset
 
 - When you have a renderable array (`$variables` in a preprocess context is a render array now) you can set `$renderable['#cache']['max-age'] = 0` to avoid having to flush the render cache after *every* code change.
 
 - Rendering an exposed form (Views) programmatically: https://www.drupal.org/forum/support/module-development-and-code-questions/2017-02-20/how-to-programmatically-render-a-view

 - Don't manage modules with drush anymore. Download them with `composer install drupal/MY_PROJECT_NAME`. If you need to _install_ the module from the CLI after -- use `vendor/bin/drupal moi MY_PROJECT_NAME`.
 
 - Some useful ReactJS resources to get up to speed on some core concepts:
 
    - [Hooks](https://reactjs.org/docs/hooks-intro.html)
    
    - [Functional Components](https://programmingwithmosh.com/react/react-functional-components/)
- Serializing Nodes with the Serializer services and Type Data API: https://drupal.stackexchange.com/questions/191419/drupal-8-node-serialization-to-json
