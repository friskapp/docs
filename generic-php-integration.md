# Generic PHP Integration

Frisk support receiving errors from PHP applications (other than Laravel) partially using the MIT-Licensed package `facade/flare-client-php`.

So to start catching errors, add the dependency using composer:

    composer require facade/flare-client-php

Then add this code to report all unhandled errors and exception

    $frisk = (new Facade\FlareClient\Flare(new \Facade\FlareClient\Http\Client(
            'FRISK-API-KEY',
            null,
            'https://your-frisk-app-url.com/api'
        )))
        //this will set set_error_handler & set_exception_handler for you.
        ->registerFlareHandlers()
        // uncomment next line if you want to disable IP collecting of your application users.
        //->anonymizeIp()
        ;
    
> {note} You can get FRISK-API-KEY from Frisk's project settings/API page.

## [Send custom and detailed information](#send-extra-information)

To send more information about users, use group with key:user such as: 

    $frisk->group('user', [
        'email' => $user->email, //$user depends on your app structure
        'name' => $user->name,
        'extra_information' => '...',
    ]);

To send extra information about an error context use group with key:context, such as 

    $frisk->group('context', [
        'key1' => 'value1',
    ]);

To intercept all your errors, and modify you them before being sent to Frisk API, use:

    $frisk->registerMiddleware(function (\Facade\FlareClient\Report $report, $next) {
        // Add custom information to the report
        $report->context('key1', 'value1');

        //or even delete something
	    $context = $report->allContext();
	    $context['session'] = null;
        $report->userProvidedContext($context);

        return $next($report);
    });