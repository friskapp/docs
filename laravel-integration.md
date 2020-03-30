# Laravel Integration

In order to receive errors from a Laravel project, you must have Ignition as a composer's dependency

    composer require facade/ignition

Frisk uses Ignition ability to send errors to online third parties services (like Frisk), to make Ignition knows 
that you are sending errors to Frisk, publish the config file: 

    php artisan vendor:publish --provider="Facade\Ignition\IgnitionServiceProvider" --tag="flare-config"

This will publish a file in `config/flare.php`, open it and add this in the end of file just before `];`

    'base_url' => env('FRISK_URL'),

Then open `.env` file and add:

    FLARE_KEY=your-project-api-key
    FRISK_URL=https://your-frisk-website.com/api

> {note} You can get FLARE_KEY from Frisk's project settings/API page.


 <a name="frisk-intergration-laravel-5.8-and-below"></a>
## [Extra steps for Laravel 5.8 and below](#frisk-intergration-laravel-5.8-and-below)

You may need to change file `app/Exceptions/Handler.php` for Laravel versions 5.5 to 5.8, and add this method:

    protected function whoopsHandler()
    {
        try {
            return app(\Whoops\Handler\HandlerInterface::class);
        } catch (\Illuminate\Contracts\Container\BindingResolutionException $e) {
            return parent::whoopsHandler();
        }
    }

> {warning} you may also need to remove package `filp/whoops` from you composer to avoid any conflicts.

 <a name="frisk-logging-channels"></a>
## [Change logging channel to send errors to Frisk API](#frisk-logging-channels)
You need to modify `config/logging.php` to let Laravel send to third parties API (like Frisk). Open the file then add a new channel in `channels` array:

    'channels' => [
            'flare' => [
                'driver' => 'flare',
                //'level' => 'critical',
            ],

Then you can add `flare` channel to any channel you are using, let's say you are using `stack`, you add the newly created channel to its channel like this:

    'channels' => [
        //this is our new channel
        'flare' => [
            'driver' => 'flare',
        ],

        'stack' => [
            'driver' => 'stack',
            'channels' => ['daily', 'flare'], // <-- you can see here we added flare to its channels
            'ignore_exceptions' => false,
        ],

If you are using `vapor`, just do the same and add `flare` to `vapor` channels.

 <a name="test-integration"></a>
## [Test the integration](#test-integration)
After you complete all these simple steps and you want to test the integration with your Frisk app, run this from your command line inside your Laravel project:

    php artisan flare:test

 <a name="customize-sent-error"></a>
## [Customize sent errors](#customize-sent-error)
In `config/flare.php` you can add and modify as needed:

    'reporting' => [
        'anonymize_ips' => true,
        'collect_git_information' => true,
        'report_queries' => true,
        'maximum_number_of_collected_queries' => 200,
        'report_query_bindings' => true,
        'report_view_data' => true,
        'grouping_type' => \Facade\FlareClient\Enums\GroupingTypes::EXCEPTION,
        //or by
        //'grouping_type' => \Facade\FlareClient\Enums\GroupingTypes::TOP_FRAME,
    ],

also you can change what information about users can be sent from User model:

    class User extends Model {
        //...
        public function toFlare(): array {
            // Only `id` will be sent to Flare.
            return [
                'id' => $this->id
            ];
        }
    }

