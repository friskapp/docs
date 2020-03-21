- ## Project setup

to connect a project your frisk website you need to configure your project with flare

[Flare install](https://flareapp.io/docs/ignition-for-laravel/installation)

make sure you publish flare config :

`'base_url' => env('FRISK_URL'),`

in your env

`FLARE_KEY=your-project-api-key
FRISK_URL=https://your-frisk-website.com/api`

to test :

`php artisan flare:test`