# Heroku CRUD Demo

## How I got to here

I followed the tutorials [Deploying a Laravel Application to Heroku](http://www.easylaravelbook.com/blog/2015/01/31/deploying-a-laravel-application-to-heroku/) & [Installing a Laravel app on Heroku](https://mattstauffer.co/blog/installing-a-laravel-app-on-heroku).

I then installed a [crud-generator](https://packagist.org/packages/appzcoder/crud-generator) to make generating scaffolding easy.

## Things to run before we start

Add the buildpack to tell Heroku we are PHP app and not a node app

    heroku config:add BUILDPACK_URL=https://github.com/heroku/heroku-buildpack-php

Then add the laravel config keys

    heroku config:add APP_KEY=f9F8w6B0sQnXK94vCgM2fh76ewMKE7Hp &&
    heroku config:add APP_DEBUG=true

Then lets make a database!

    heroku addons:create heroku-postgresql:hobby-dev

## Making our CRUD

    php artisan crud:generate Person --fields="name:string, email:string, phone:integer, message:text"

Add the route

    Route::resource('person', 'PersonController');

Deploy up to heroku, then run

    php artisan migrate
