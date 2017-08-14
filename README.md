# Qiwi API Client
API клиент для работы с API личного кабинета Qiwi
[Документация Qiwi](https://developer.qiwi.com/qiwiwallet/qiwicom_ru.html)

# Установка
* Скопируйте QiwiApi.php из папки src/ и включите его в скрипт
```php
require_once 'QiwiApi.php';
$qiwi = new FindYanot\QiwiApi('79997965958', 'd86e556798678df67606fs876f9');
```

#### Установка с помощью Composer
```
composer require findyanot/qiwi_api_php
```
# Пример

```php
require_once 'QiwiApi.php';
$qiwi = new FindYanot\QiwiApi('79997965958', 'd86e556798678df67606fs876f9');
$sendMoney = $qiwi->sendMoneyToQiwi([
    'id' => time() + 10 * 5,
    'sum' => [
        'amount'   => 1000,
        'currency' => 643
    ], 
    'source' => 'account_643',
    'paymentMethod' => [
        'type' => 'Account',
        'accountId' => 643
    ],
    'comment' => 'Тестовый платеж',
    'fields' => [
        'account' => '+79997965958'
    ]
]);

```

# Методы

Метод | Описание
------------ | -------------
getAccount(Array $params) | Профиль пользователя
getPaymentsHistory(Array $params) | История платежей
getPaymentsStats(Array $params) | Статистика платежей
getBalance() | Баланс QIWI Кошелька
getTax($providerId) | Комиссионные тарифы
sendMoneyToQiwi(Array $params) | Перевод на QIWI Кошелек
sendMoneyToProvider($providerId, Array $params) | Оплата услуг по ID получателя