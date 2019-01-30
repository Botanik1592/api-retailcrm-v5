версия для retailCRM API v5

Ruby-клиент для retailCRM API
=============================


### Установка

Gemfile:
```
gem 'retailcrm', github: 'Botanik1592/api-retailcrm-v5'
```

### Примеры использования

#### Получение информации о заказе

```ruby
require 'retailcrm'

api = Retailcrm.new('https://yourcrmname.retailcrm.ru', 'yourApiKeyHere')

response = api.orders_get(345, 'id').response
order = response[:order]

```

#### Создание заказа

```ruby
require 'retailcrm'

api = Retailcrm.new('https://yourcrmname.retailcrm.ru', 'yourApiKeyHere')

order = {
  :externalId => 171,
  :number => '171',
  :email => 'test@example.com',
  :createdAt => '2014-10-28 19:31:10',
  :discountPercent => 10,
  :firstName => 'Jack',
  :lastName => 'Daniels',
  :customer => {
    :externalId => 8768,
    :firstName => 'Jack',
    :lastName => 'Daniels',
    :phones => [{ :number => '+79000000000' }],
  },
  :delivery => {
    :code => 'courier',
    :cost => 500,
    :address => {:text => '300000, Russia, Moscow, Tverskaya st., 56'}
  },
  :items => [
    {
      :productId => 170,
      :initialPrice => 500,
      :quantity => 2
    },
    {
      :productId => 175,
      :initialPrice => 1300,
      :quantity => 1
    }
  ]
}

response = api.orders_create(order).response
order_id = response[:id]

```

#### Документация REST API

http://www.retailcrm.ru/docs/Developers/ApiVersion3

#### Документация API библиотеки

http://www.rubydoc.info/gems/retailcrm
