create a Project Folder

mkdir apitest7

or

composer create-project --prefer-dist laravel/laravel apitest7

cd apitest7

php artisan serve

http://localhost:8000

Email Verification

php artisan make:auth

Updating the Users Table

Schema::create(‘users’, function (Blueprint $table) {
$table->increments(‘id’);
$table->string(‘name’);
$table->string(‘email’)->unique();
$table->string(‘password’);
$table->tinyInteger(‘verified’)->default(0);
$table->string(‘email_token’)->nullable();
$table->rememberToken();
$table->timestamps();
});

Adding Table for Queues
Let’s now add the table for queued jobs and failed job. For that, run the following Artisan commands:

php artisan queue:table
php artisan queue:failed-table

Migrating the Tables

php artisan migrate

Create the Email Template

create a new folder inside views folder with name email and then create a new file inside this folder with the name email.blade.php

<h1>Click the Link To Verify Your Email</h1>
Click the following link to verify your email {{url(‘/verifyemail/’.$email_token)}}


Create the SendVerficationEmail Queue Job

php artisan make:job SendVerificationEmail


## License

The Laravel framework is open-sourced software licensed under the [MIT license](https://opensource.org/licenses/MIT).
