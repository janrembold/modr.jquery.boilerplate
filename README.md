# modr.jquery.boilerplate

Any module should follow some structural and coding conventions:
 
- Use boilerplate code shown below to kickstart your module
- Set modules default options in configs `defaults` object
- Set dependencies to other modr modules in configs `dependencies` object
- Add optional `prepare()` function if anything should be executed before module gets initialized, e.g. listeners that init the module
- Use `init()` and `destroy()` functions that create/destroy plugins functionality
- Remove all variables, listeners and additional classes set to plugins element. Reset anything to the default state
- Use `var self = this;` in any function to access modules public variables/methods

```js
(function($) {
    'use strict';

    // the modr config object
    var config = {
        plugin: 'pluginName',
        module: 'moduleName',
        defaults: {
            defaultOption: 'someValue'
        },
        dependencies: {
            pluginName: [ 'moduleName' ]
        }
    };

    // the modules methods
    modr.registerModule( config, {

        /** prepare function is optional and gets automatically
         *  executed after all modules were loaded by jQuery wrapper */
        prepare: function() {
            console.log('prepare module');
        },

        init: function() {
            console.log('init module');
        },

        destroy: function() {
            console.log('destroy module');
        }

    });

})(jQuery);
```