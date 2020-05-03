
# jquery-datatables-rails
[![Gem Version](https://badge.fury.io/rb/jquery-datatables-rails.svg)](http://badge.fury.io/rb/jquery-datatables-rails)

This gem packages the jQuery [DataTables](http://datatables.net/) plugin for easy use with the Rails 3.1+ asset pipleine.
It provides all the basic DataTables files, and a few of the extras.

# Important

** Updated to dataTables 1.10.16 **
** Added Bootstrap 4 support **

**The current gem is released without updated plugins.**

**jQuery DataTables renamed the parameters names, if you are updating, please take a look http://www.datatables.net/upgrade/1.10-convert**

If you encounter any errors, please fork the repository, update the plugin files and send a pull-request.

## Upgrade Notes

1 - For people upgrading to 3.x.x who are using the responsive extension.
Due to an error displaying the plus icon in a recent version of this gem, the responsive code has now changed and uses the DataTables responsive extension instead. This requires some changes to your responsive configuration. See the Responsive Installation section below and follow the link.

## General Installation

1 - Add to your Gemfile:

```ruby
gem 'jquery-datatables-rails', '~> 3.4.1'
```

2 - Install the gem:

```bash
bundle install
```

3 - Run the install generator:

```bash
$ rails generate jquery:datatables:install
```

This will add to the corresponding asset files
```ruby
# app/assets/javascripts/application.js
//= require dataTables/jquery.dataTables
```

```ruby
# app/assets/stylesheets/application.css
*= require dataTables/jquery.dataTables
```



## Twitter Bootstrap 4 Installation

1 - Complete steps 1-2 of the General Installation

2 - Run the install generator:
```bash
$ rails generate jquery:datatables:install bootstrap3
```

This will add to the corresponding asset files

```ruby
# app/assets/javascripts/application.js
//= require dataTables/jquery.dataTables
//= require dataTables/extras/dataTables.bootstrap4.js

# Extra optional components
//= require dataTables/extras/dataTables.responsive.js
//= require dataTables/extras/dataTables.buttons.js
//= require dataTables/extras/buttons.bootstrap4.js
//= require dataTables/extras/buttons.html5.js
//= require dataTables/extras/responsive.bootstrap4.js

# app/assets/stylesheets/application.css

*= require dataTables/dataTables.jqueryui.css
*= require dataTables/extras/dataTables.bootstrap4.css

# Optional support for extra dataTables modules
*= require dataTables/extras/responsive.dataTables.css
*= require dataTables/extras/responsive.bootstrap4.css
*= require dataTables/extras/buttons.bootstrap4.css
```

3 - Initialize your datatables using these option:

```javascript
$('.datatable').DataTable({
  // ajax: ...,
  // autoWidth: false,
  // pagingType: 'full_numbers',
  // processing: true,
  // serverSide: true,

  // Optional, if you want full pagination controls.
  // Check dataTables documentation to learn more about available options.
  // http://datatables.net/reference/option/pagingType
});
```

## Zurb Foundation Installation

1 - Complete steps 1-2 of the General Installation

2 - Run the install generator:
```bash
$ rails generate jquery:datatables:install foundation
```

This will add to the corresponding asset files

```bash
# app/assets/javascripts/application.js
//= require dataTables/jquery.dataTables
//= require dataTables/jquery.dataTables.foundation

# app/assets/stylesheets/application.css
*= require dataTables/jquery.dataTables.foundation
```

## Responsive Installation

1 - Complete steps 1-3 of the General Installation.

2 -  Run the install generator:
```bash
$ rails generate jquery:datatables:install responsive
```

This will add to the corresponding asset files
```ruby
# app/assets/javascripts/application.js
//= require dataTables/jquery.dataTables
//= require dataTables/extras/dataTables.responsive

# app/assets/stylesheets/application.css
*= require dataTables/extras/dataTables.responsive
```

3 - Initialize your datatables using:

```javascript
$('#example').DataTable({
  responsive: true
});
```

5 - Add `responsive no-wrap` class to html `table`,

````html
<table class="display responsive no-wrap">
    <thead>
        <tr></tr>
    </thead>
    ...
</table>
````

6. More information at: http://www.datatables.net/extensions/responsive/init


## Plugins

Only a few plugins are currently available

* api
    * fnReloadAjax
    * fnGetColumnData
    * fnFilterOnReturn
    * fnSetFilteringDelay
* sorting
    * numbersHtml
* typeDetection
    * numberHtml

These files can be found in the [assets directory][assets].

## Extras

````ruby
# Official extras are available:
[Plugin]     : [ExtraName]
AutoFill     : dataTables.autoFill
ColReorder   : dataTables.colReorder
ColVis       : dataTables.colVis
FixedColumns : dataTables.fixedColumns
FixedHeader  : dataTables.fixedHeader
KeyTable     : dataTables.keyTable
Scroller     : dataTables.scroller
TableTools   : dataTables.tableTools
Responsive   : dataTables.responsive
````

### How to use Extras
1 - To add an extra into your application, add its JS file to `application.js` using the following pattern:

```javascript
//= require dataTables/extras/[ExtraName]
```

2 - Additionally, you may need to add any associated CSS files. For instance the TableTools extra requires
you to add the following line to your `application.css` file:

```css
*= require dataTables/extras/dataTables.tableTools
```

Make sure to also add it's initialization as described on [datatables extras' site][datatables_extras].

## Articles and Extras

[RailsCast #340 DataTables] Apr 11, 2012.

[ajax-datatables-rails] a wrapper around datatable's ajax methods that allow synchronization with server-side.

[assets]: app/assets/javascripts/dataTables
[datatables_extras]: http://datatables.net/extras/
[datatables-responsive]: https://github.com/Comanche/datatables-responsive
[RailsCast #340 DataTables]: http://railscasts.com/episodes/340-datatables
[ajax-datatables-rails]: https://github.com/antillas21/ajax-datatables-rails
