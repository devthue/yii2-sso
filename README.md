SSO server
============================

Hệ thống Signle Sign On (đăng nhập một lần) được viết trên nền tảng Yii2.

Toàn bộ hệ thống tài khoản được kế thừa thông qua yii2-user(https://github.com/dektrium/yii2-user)

Cài đặt
------------
### Cài đặt thông qua Composer

```php
composer install
```

### Cấu hình database

Import databas `yii2sso_server.sql` vào cơ sở dữ liệu sau đó thay đổi thông tin cấu hình trong file `config/db.php` theo mẫu sau:

```php
return [
    'class' => 'yii\db\Connection',
    'dsn' => 'mysql:host=localhost;dbname=yii2sso_server',
    'username' => 'root',
    'password' => 'root',
    'charset' => 'utf8',
];
```

Tài khoản quản trị
---------------------------

Hiện tại hệ thống SSO server chỉ phân quyền theo Admin và User, tài khoản quản trị được cấu hình cứng trong file config:

```php
    'modules' => [
        'user' => [
            'class' => '\dektrium\user\Module',
            'modelMap' => [
                'User' => 'app\models\User',
            ],
            'controllerMap' => [
                'security' => 'app\controllers\SecurityController'
            ],
            'admins' => ['dinhnhatbang'] // Tài khoản quản trị
        ],
    ],
```


