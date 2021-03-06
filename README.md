DashboardBundle
=========

Dashboard Bundle for symfony >= 3.3

This bundle will require symfony/assetic-bundle
symfony's document for assetic : https://symfony.com/doc/current/assetic/asset_management.html

####Requirements :
    
* twbs/bootstrap 4.0.0-beta
    * add `"twbs/bootstrap": "4.0.0-beta"` to your composer.json
    * then run `composer update`


####Installation :
1) `composer require kodoyosa/dashboard`

2) add `new Kodoyosa\DashboardBundle\KodoyosaDashboardBundle(),` to $bundles[] in registerBundles() from app/AppKernel.php

3) call the routes in app/config/routing.yml. Basically you can add :
    
        kodo_dashboard:
            resource: "@KodoyosaDashboardBundle/Resources/config/routing.yml"
            prefix:   /dashboard

4) Assetic configuration in app/config/config.yml to get access to `bootstrap_js` and `bootstrap_css`
    
        # Assetic Configuration
        assetic:
            filters:
                cssrewrite: ~
            assets:
                bootstrap_js:
                    inputs:
                        - '%kernel.root_dir%/../vendor/twbs/bootstrap/assets/js/vendor/popper.min.js'
                        - '%kernel.root_dir%/../vendor/twbs/bootstrap/dist/js/bootstrap.js'
                bootstrap_css:
                    inputs:
                        - '%kernel.root_dir%/../vendor/twbs/bootstrap/dist/css/bootstrap.min.css'
                        - '%kernel.root_dir%/../vendor/twbs/bootstrap/dist/css/bootstrap-grid.min.css'
                        - '%kernel.root_dir%/../vendor/twbs/bootstrap/dist/css/bootstrap-reboot.min.css'
                        
5) Update database schema : `php bin/console doctrine:schema:update --force`

6) run : `php bin/console assetic:dump

*That's it !*