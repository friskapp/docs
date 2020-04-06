# After Installing Frisk

 <a name="creating-admin-account"></a>
### [Creating an Admin](#creating-admin-account)

After installing Frisk, you can create an admin account using the command:

    php artisan frisk:admin --email=your@email.com

This will create an account and save it to the database and add it to FriskServiceProvider as an admin.
if account is already existed it will be added only to FriskServiceProvider as an Admin

> {note} You can provide `--password=` option too ...

### [FriskServiceProvider Gate Customization](#gate-customize)

Assuming you already installed Frisk and published the necessary files (see [Installation](./installation#database-installation) for detailed information).
You can add admins (their emails) manually or change the gate code by modifying ``FriskServiceProvider@gate`` .

```php
Gate::define('isFriskAdmin', function ($user) {
    return in_array($user->email, [
         //any email
    ]);
});
```

 <a name="receiving-errors"></a>
### [Start receiving errors](#receiving-errors)
> {warning} Assuming that you did the following steps, if not go back to [Installation](/installation) page:
<br> ✔️ Installed Frisk (and the database).
<br> ✔️ Created an admin account.
<br> ✔️ you logged in and created a project (see [Projects](/projects) for detailed information).
<br> ✔️ You copied the API key from the project settings.


Now you need to integrate Frisk with your website to receive errors, head to [Integration with Laravel](/laravel-integration) if your website is built using Laravel or  [Integration with any generic PHP website](/generic-php-integration) or [Javascript Integration](/javascript-integration) for Javascript websites.

 <a name="mail-configurations"></a>
### [Configure mail notifications](#mail-configurations)
In order to send emails from Frisk app you need to set the email settings in `.env` file

    MAIL_MAILER=smtp #or `sendmail`, `ses` or `mailgun`
    MAIL_HOST=smtp.your-provider.com
    MAIL_PORT=2525
    MAIL_USERNAME=null
    MAIL_PASSWORD=null
    MAIL_ENCRYPTION=null
    MAIL_FROM_ADDRESS=website@your-website-domain.com
    MAIL_FROM_NAME="${APP_NAME}"

Check out [Laravel mail configuration docs](https://laravel.com/docs/7.x/mail#configuration) for more information.
