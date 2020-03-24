# Installation

 <a name="download-frisk-app"></a>
## [Download the app](#download-frisk-app)
Frisk Uses [Composer](https://getcomposer.org) to manage its code & dependencies. So, make sure you have Composer installed on your machine.

    composer create-project friskapp/frisk-project your-project-name

After executing the command **it will asks you for a username and a password**, if you already have a [license](./license) then from you [account](/dashboard) page choose you license and it will show to you a username and a password to use.

<br>

> {note} Username:  Your email address that you used to create an account in this website. Password: The licence code you purchased. 

 <a name="configurations"></a>
## [Configurations](#configurations)
Change the values in `.env` file found in the root folder to right information.

    DB_CONNECTION=mysql
    DB_HOST=127.0.0.1
    DB_PORT=3306
    DB_DATABASE=name-of-your-database
    DB_USERNAME=user-of-your-database
    DB_PASSWORD=password-of-your-database


 <a name="database-installation"></a>
## [Database Installation](#database-installation)
Now that you edited the database information in your `.env`, you can run the command:

    php artisan frisk:install
    php artisan migrate


 You can head to [After installation](./after-installing-frisk) page to configure Frisk after installing it.