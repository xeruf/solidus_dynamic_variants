SolidusDynamicVariants
======================

This Gems creates variants for a Solidus Shop when needed.
Useful for products with many, many options.
Dynamic Variant Creation is a better alternative than creating multimillion variant entries for each possible option combination.

#### 1. Backend Products: Adds a "Dynamic Variants" checkbox to products which makes the variant creation for the product dynamic.

![Backend Products](https://hefan.github.io/images/be_products.png)


#### 2. Backend Options: Adds a "Surcharge" field to option values which contains optional surcharges for specific options.

![Backend Options](https://hefan.github.io/images/be_options.png)


#### 3. Frontend Product Detail Screen: Renders Select Boxes for each Option instead of Radio Buttons for each Variant

![Frontend Products](https://hefan.github.io/images/fe_products.png)


The process of dynamic variant creation in the frontend works like this:
- Shows all available options as dropdowns in product screen (see above).
- When product is put in cart, the correct variant is created if it doesn't exist yet.
- The variant will have the price of the product plus the surcharges of its selected option values
- Existence of a products variant is checked by options and price (if the price is altered a new variant will be created).


Installation
------------

Add solidus_dynamic_variants to your Gemfile:

```ruby
gem 'solidus_dynamic_variants'
```

Bundle your dependencies and run the installation generator:

```shell
bundle
bundle exec rails g solidus_dynamic_variants:install
```


Caveats
-------
Assumes the Variant will be combined and sent after ordering (or is digital).
Therefore: If track inventory is on, the newly created variant will have track_inventory = false.
The newly created variant will have the same sku like the master variant plus a timestamp.

When you create Orders in Backend you still need to create the variant by hand.



Testing
-------

First bundle your dependencies, then run `rake`. `rake` will default to building the dummy app if it does not exist, then it will run specs, and [Rubocop](https://github.com/bbatsov/rubocop) static code analysis. The dummy app can be regenerated by using `rake test_app`.

```shell
bundle
bundle exec rake
```

When testing your application's integration with this extension you may use its factories.
Simply add this require statement to your spec_helper:

```ruby
require 'solidus_dynamic_variants/factories'
```

Copyright (c) 2020 stefan hartmann, released under the New BSD License
