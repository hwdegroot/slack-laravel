# Slack for Laravel

[![Total Downloads](https://poser.pugx.org/jeremykenedy/slack-laravel/d/total.svg)](https://packagist.org/packages/jeremykenedy/slack-laravel)
[![Latest Stable Version](https://poser.pugx.org/jeremykenedy/slack-laravel/v/stable.svg)](https://packagist.org/packages/jeremykenedy/slack-laravel)
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)

Laravel 5 integration for the Slack, including facades and service providers.
This package allows you to use [Slack for PHP](https://github.com/maknz/slack) easily and elegantly in your Laravel 5 app.

- [Requirements](#requirements)
- [Installation](#installation)
- [Configuration](#configuration)
- [Usage](#usage)
    - [1. Include Class](#1.-include-class)
    - [2. Trigging Slack Messages](#2.-trigging-slack-messages)
        - [Send to Default Channel](#send-to-default-channel)
        - [Send to Different Channel](#send-to-different-channel)
        - [Send to Private Message](#send-to-private-message)
- [Credits](#credits)
- [License](#license)

### Requirements

* [Laravel 5.3 or newer](https://laravel.com/docs/installation)

### Installation

##### 1. From your projects root folder in terminal run:

```bash
    composer require jeremykenedy/slack-laravel
```

##### 2a. Register App (Laravel 5.5 +)
Uses package auto discovery feature, no need to edit the `config/app.php` file.
* Skip to [4. Publish Assets](#4.-publish-assets)


##### 2b. Register App (Laravel 5.4 and below)
Register the package with laravel in `config/app.php` under `providers` with the following:

```php
    'providers' => [
        jeremykenedy\Slack\Laravel\ServiceProvider::class,
    ];
```

##### 3. Register App Alias (Laravel 5.4 and below)
Register the package with laravel in `config/app.php` under `aliases` with the following:

```php
    'aliases' => [
        'Slack' => jeremykenedy\Slack\Laravel\Facade::class,
    ];
```

##### 4. Publish Assets (All)
Publish the config file from your projects root folder in terminal by running:

```bash
    php artisan vendor:publish --tag=slacklaravel
```

##### 5. Create Webhook (All)
[Create an incoming webhook](https://my.slack.com/services/new/incoming-webhook) for each Slack team you'd like to send messages to. You'll need the webhook URL(s) in order to configure this package.

##### 6. Configure `.env` (All)
Configure Slack for Laravel in your `.env` file by adding and editing the following:

```php
DEFAULT_SLACK_WEBHOOK_ENDPOINT=https://hooks.slack.com/services/XXXXXXXX/XXXXXXXX/XXXXXXXXXXXXXX
DEFAULT_SLACK_CHANNEL='#general'
DEFAULT_SLACK_USERNAME=Robot
DEFAULT_SLACK_ICON=':ghost:'
DEFAULT_SLACK_LINKNAMES_CONVERTED=FALSE
DEFAULT_SLACK_UNFURL_LINKS_STATUS=FALSE
DEFAULT_SLACK_UNFURL_MEDIA_STATUS=TRUE
DEFAULT_SLACK_ALLOW_MARKDOWN=TRUE
DEFAULT_SLACK_MARKDOWN_FIELDS="'text','title'"
```

### Configuration

The config file comes with defaults and placeholders. Configure at least one team and any defaults you'd like to change.
Default configurations are published into `config/slack.php` and the values can be set in the `.env` file like so:

```
DEFAULT_SLACK_WEBHOOK_ENDPOINT=https://hooks.slack.com/services/XXXXXXXX/XXXXXXXX/XXXXXXXXXXXXXX
DEFAULT_SLACK_CHANNEL='#general'
DEFAULT_SLACK_USERNAME=Robot
DEFAULT_SLACK_ICON=':ghost:'
DEFAULT_SLACK_LINKNAMES_CONVERTED=FALSE
DEFAULT_SLACK_UNFURL_LINKS_STATUS=FALSE
DEFAULT_SLACK_UNFURL_MEDIA_STATUS=TRUE
DEFAULT_SLACK_ALLOW_MARKDOWN=TRUE
DEFAULT_SLACK_MARKDOWN_FIELDS="'text','title'"
```

### Usage

### 1. Include Class
* In the controller file that you will use this be sure to include the `Slack class in the head of the file:

```php
use Slack;
```

### 2. Trigging Slack Messages

###### Send to Default Channel
* Send a message to the default channel

```php
    Slack::send('Hi Slack, from the API :)');
```

###### Send to Different Channel
* Send a message to a different channel

```php
    Slack::to('#testing')->send('Hi Testing!');
```

###### Send to Private Message
* Send a message to a private channel

```php
    Slack::to('@jeremykenedy')->send('Hi Jeremy!');
```

### Credits
* Full development credit must go to [maknz](https://github.com/maknz/slack-laravel).
* This package was forked and improved. The original package states that it was no longer maintained.
* This package was forked and modified to be compliant with [MIT](https://opensource.org/licenses/MIT) licencing standards for production use.

### License
Slack for Laravel is licensed under the MIT license for both personal and commercial products. Enjoy!
