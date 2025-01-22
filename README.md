# Bot-SDK
A professional SDK BOT Telegram for PHP

## Requirements

- PHP >= 5.4
- Composer

## Installation

You can install this SDK package via Composer:

```bash
composer require natilosir/Telegram-Bot-SDK
php vendor/natilosir/bot/install.php
```

### [ORM](https://github.com/natilosir/orm)
  - [select](https://github.com/natilosir/ORM#select)
  - [insert](https://github.com/natilosir/ORM#insert-array)
  - [table](https://github.com/natilosir/ORM#select)
  - [update](https://github.com/natilosir/ORM#update-array)
  - [delete](https://github.com/natilosir/ORM#delete)
  - [eloquent](https://github.com/natilosir/ORM#update-model)
  - [search](https://github.com/natilosir/ORM#search)
  - [Count](https://github.com/natilosir/ORM#Count)
  - [orderBy](https://github.com/natilosir/ORM#orderBy)
  - [DISTINCT](https://github.com/natilosir/ORM#DISTINCT)
  - [JSON](https://github.com/natilosir/ORM#JSON)
  - [query](https://github.com/natilosir/ORM#query)

### [Error log](https://github.com/natilosir/BOT/blob/main/log.txt) 
- Advanced error management and storing logs in a separate file `log.txt` for every request to the server.
# Route Class
Please provide the code you would like me to review.
```php
use natilosir\bot\Route; 
Route::add(['/start', 'بازگشت', 'انصراف'], 'start')
    // Add route for the purchase command
    ->add('خرید', 'buy')
    // Add route for the sale command
    ->add('فروش', 'sell');

// Define the default file to handle the start command
Route::def('start'); // Default file

// Handle the input text from the user
Route::handle($text); // Process the incoming text
```
Now we will review all sections of the code. To use this class, make sure to include `use natilosir\bot\Route;` before calling the Route class.

### add Method Overview

```php
Route::add(['/start', 'بازگشت', 'انصراف'], 'start')
```

This method accepts two parameters: `patterns` and `action`.

1. **Patterns (Input 1)**: 
   - You can specify the patterns as either an array or a string. This defines the command or phrase that, when triggered by the user, will determine which file to open.
   - For example, if the user types and sends the command `/start`, you would specify this command in the patterns parameter.

2. **Action (Input 2)**: 
   - The second input is the path to the file located within the `controller` directory.
   - For instance, if there is a file named `start.php` in the `controller` folder, you should provide the second input simply as `start`. The system will automatically understand that it needs to open the file located at `controller/start.php`.

3. **Accessing Files from Other Directories**: 
   - If you want to open a file from a different folder, you can use the `.` notation.
   - For example, if you want to open the file `controller/user/send.php`, you would specify the second input as `user/send`.

### Example Usage add methods

```php
Route::add('/start', 'start');        // This will open controller/start.php when /start is triggered.
Route::add('/send', 'user/send');     // This will open controller/user/send.php when /send is triggered.
```

## Default Method Overview

```php
// Define the default file to handle the start command
Route::def('start'); // Default file
```

Using the `def` method, you can specify a default file to be opened. This is particularly useful when a user sends a command that does not match any of the patterns defined in the `add` method.

### How It Works

- If the user sends a command that does not match any of the patterns specified in the `add` method, the `def` method allows you to display a default message or response.
- This can help guide users or provide them with additional options when they input an unrecognized command.

### Example Usage
```php
Route::def('default_message');        // Opens controller/default_message.php if no patterns match
```


## Handle Method Overview

The `handle` method is designed to process user input. It allows the system to receive a specific string or command sent by the user.

### How It Works

- You can use the `Route::handle($text);` method to capture the `$text` input from the user.
- This method is essential for handling commands or messages that users send to your bot.

### Example Usage

```php
// Assuming you have set up your routes
Route::add('/start', 'start');        // This will open controller/start.php when /start is triggered.
Route::add('/send', 'user/send');     // This will open controller/user/send.php when /send is triggered.

Route::def('default_message');        // Opens controller/default_message.php if no patterns match
Route::handle($text); // Processes the user input
```

### Object Method api telegram
   - HTTP request
   - answerCallbackQuery
   - sendChatAction
   - deleteMessage
   - forwardMessage
   - sendMessage
   - copyMessage
     - inline
     - keyboard
       - editMessageReplyMarkup
       - column
       - row
