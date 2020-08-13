# INSTAGRAM API  [![License][packagist-license]][license-url]

[![Downloads][packagist-downloads]][packagist-url]

- [Installation](#Installation)
- [Example](#Example)
- Method Api
    - [Search User](#Search-User)
    - [Upload Photo](#Upload-Photo)
    - [Send Message](#Send-Message)
- [Use Proxy](#Use-Proxy)

## Installation
**Using Composer:**
```
composer require firusvictor/instagramapi
```
## Example
```php
require_once __DIR__ . '/vendor/autoload.php';
use InstaLite;

$instagram = new InstaLite("username", "password", "proxy");

/** search user (return array standart instagram) **/
$user = $instagram->searchUser('alex')->id();

/** check #tag on user wall **/
$is_tag = $instagram->isHashtagByName('alex', 'tag')->all();

/** check user subscription on this server profile **/
$is_tag = $instagram->isSubscriptionByName('alex')->all();

/** send photo **/
$instagram->uploadPhoto(__DIR__ . '/img.jpg', 'text #hashtag');

/** send message direct **/
$instagram->sendMessage('text message', [1233, 1233, 1223]);
```
# Method
## Search User
Search user instagram, nickname, username, last name, first name
```php
$key = "search first name or username ...";
$user = $instagram->searchUser($key);
 
$user->id();
/** return array user id **/
[1, 2, 3, 4, 5, 6]

$user->all();
/** return array user standart formate instagram **/
[
    [
        pk: ""
        username: ""
        full_name: ""
        is_private: false
        profile_pic_url: ""
        profile_pic_id: ""
        is_verified: false
        has_anonymous_profile_picture: false
        mutual_followers_count: 0
        social_context: ""
        search_social_context: ""
        friendship_status: {}
        latest_reel_media: 1580484486
        seen: 0
    ],[],[]
]

```
## Upload Photo
Send photo, upload instagram
```php
/** file photo mimetype JPEG **/
$photo = __DIR__ . '/image.jpg';
/** Message text and Hashtag **/
$message = 'Hello InstaGram';
$upload = $instagram->uploadPhoto($photo, $message);
/** Result **/
if($upload) {
    /** upload photo sussecc **/
    echo $upload;
    /** media id **/
}
```
## Send Message
Send message direct instagram
```php
/** Array user id **/
$user = [12356456, 45645465];
/** Message text **/
$message = 'Hello InstaGram';
$send = $instagram->sendMessage($message, $user);
/** Result **/
if($send) {
    /** message send sussecc **/
}
```
## Use Proxy
supports socks5 and http/https
```php
/** socks5 **/
$instagram = new InstaLite("username", "password", "socks5://login:password@ip:port");
/** http/https **/
$instagram = new InstaLite("username", "password", "http://login:password@ip:port");
```

----

[firus.victor@gmail.com][tioffs-url]

[tioffs-url]: mailto:firus.victor@gmail.com
[license-url]: https://github.com/tioffs/instalite/blob/master/LICENSE

[telegram-url]: https://t.me/joinchat/C9JmzQ-fc3SKXI0D-9h-uw

[packagist-url]: https://packagist.org/packages/firusvictor/instagramapi
[packagist-license]: https://img.shields.io/github/license/firusvictor/instagramapi
[packagist-downloads]: https://img.shields.io/packagist/dt/firusvictor/instagramapi