# Links and Resources for Drupal 8

 - `hook_menu()` replacement: https://www.drupal.org/docs/8/converting-drupal-7-modules-to-drupal-8/d7-to-d8-upgrade-tutorial-convert-hook_menu-and-hook

- Routing `.yml` structure: https://www.drupal.org/node/2092643#section-requirements

- Managing config: Make changes, `config:export`, PULL from upstream, resolve conflicts (they are usually easy), `config:import`, PUSH and open PR.
 
 - Running PHPUnit tests: https://www.drupal.org/docs/8/phpunit/running-phpunit-tests
 
 - Writing/Running Custom module tests from the core testing module UI: https://www.drupal.org/docs/8/creating-custom-modules/testing-a-drupal-8-module
 
 - Using the services container and dependency injection: https://www.drupal.org/docs/8/api/services-and-dependency-injection/services-and-dependency-injection-in-drupal-8

 - Add a class to a field's markup based on a value: https://www.drupal.org/forum/support/module-development-and-code-questions/2017-03-31/add-class-to-field-in-drupal-8
 
 - Views Template names (Twig debug does not output this info): https://api.drupal.org/api/drupal/core%21modules%21views%21views.theme.inc/group/views_templates/8.2.x
   
   - Should be able to use [Twig Tweak](https://www.drupal.org/docs/8/modules/twig-tweak/cheat-sheet) (contrib module) to view variables/objects/arrays/etc. and understand values available within a given template (and what to add): 
   ```
   {{ drupal_dump(variable_name) }} 
   ```
   - ...to print out the results of any variable/object/array within a Twig template.
   
 
 - `cc` is very useful DX tool. Clearing the render cache is currently a very frequent event.
 https://www.drupal.org/docs/user_guide/en/prevent-cache-clear.html
 
 - Drupal 8 equivalent of `cc all` is `cr all`. `cr` stands for Cache Rebuild.
 
 - `srcset` and responsive images: https://chromatichq.com/blog/responsive-images-drupal-8-using-srcset
 
 - When you have a renderable array (`$variables` in a preprocess context is a render array now) you can set `$renderable['#cache']['max-age'] = 0` to avoid having to flush the render cache after *every* code change.
 
 - Rendering an exposed form (Views) programmatically: https://www.drupal.org/forum/support/module-development-and-code-questions/2017-02-20/how-to-programmatically-render-a-view
    - Twig Tweak also includes simpler (perhaps less robust) support for embedding views/blocks within Twig.
    ```
    {{ drupal_view('view_machine_name', 'display_machine_name', arg1, arg2, ...) }}
    
    {{ drupal_view('block_name') }}
    ```
    Arguments are passed as contextual filter values in the order they are supplied [see docs](https://www.drupal.org/docs/8/modules/twig-tweak/cheat-sheet).
    
    **Of note**: We have had some difficulty using entity references via contextual links (one content type referencing another content type in its display, etc.)  

 - Don't manage modules with drush anymore. Download them with `composer install drupal/MY_PROJECT_NAME`. If you need to _install_ the module from the CLI after -- use `vendor/bin/drupal moi MY_PROJECT_NAME`.

 - modules no longer can be disabled. only enabled and uninstalled. Uninstalling modules will remove all associated content/fields/etc.
    - Adding a `hook_uninstall` within `.install` is a good/valid way to clear out dead config settings after uninstalling a module (if custom):
    - Custom modules and contrib modules can be shipped with config that is installed when the module is first enabled (and not again unless fully uninstalled.) 
    
 
 - Some useful ReactJS resources to get up to speed on some core concepts:
 
    - [Hooks](https://reactjs.org/docs/hooks-intro.html)
    
    - [Functional Components](https://programmingwithmosh.com/react/react-functional-components/)

 - Serializing Nodes with the Serializer services and Type Data API:
 ```
 $serializer = \Drupal::service('serializer');
 // Useful for `drupalSettings` or PHP
 $arrayOfData = $serializer->normalize($entity, 'json', ['plugin_id' => 'entity']);
 // Useful for API responses or other output scenarios
 $jsonString = $serializer->serialize($entity, 'json', ['plugin_id' => 'entity'])
 ```

 - Implement new `Serializers` for entity types: https://www.drupal.org/docs/8/api/serialization-api/changing-the-way-serializer-handles-entities
 
  - JSON:API vs RESTful Web Services: https://www.drupal.org/docs/8/modules/jsonapi/jsonapi-vs-cores-rest-module

- Programmatically create blocks: https://hechoendrupal.gitbooks.io/drupal-console/en/commands/generate-plugin-block.html
