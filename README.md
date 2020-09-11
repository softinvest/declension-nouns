# Declension Nouns. Склонение существительных

## Установка

    composer require drandin/declension-nouns
    
##### После установки пакета необходимо последовательно выполнить следующие действия:

Добавить в файл конфигурации приложения _**config/app.php**_ сервис-провайдер. Строку указанную ниже следует внести в массив **'providers'**.

```php
 Drandin\DeclensionNouns\DeclensionNounsServiceProvider::class,
```

Для того, чтобы иметь доступ к функциям пакета через фасад следует добавить в _**config/app.php**_ в массив 'aliases' строку:

```php
 'DeclensionNoun' => \Drandin\DeclensionNouns\Facades\DeclensionNoun::class,
```

Выполнить в консоли команду, которая скопирует файл конфигурации _**declension-nouns.php**_ в каталог _**config**_ вашего приложения:

```
 php artisan vendor:publish --tag=config
```

Затем, выполните в консоли команду:

```
 php artisan config:cache
```

Если у вас установлен пакет ide-helper, то пересоздайте файл _ide_helper.php: 

```
 php artisan ide-helper:generate
```

## Использование

Предположим у нас есть число 4, и оно означат количество лет: 

```php
DeclensionNoun::make(4, "год");
```

В результате получим:

    4 года

Предположим у нас есть число 5, и оно означат количество страниц: 

```php
DeclensionNoun::make(5, "страница");
```

В результате получим:

    5 страниц

Предположим у нас есть число -304, и оно означат сумму в рублях, которую должен клиент: 

```php
DeclensionNoun::make(-304, "рубль");
```

В результате получим:

    -304 рублей
   
Предположим у нас есть число 5, и оно означат возраст ребёнка:

```php
DeclensionNoun::make(5, "год");
```

В результате получим:

    5 лет   
   
То же самое, что и в примере выше, но мы получаем только слово:

```php
DeclensionNoun::makeOnlyWord(5, "год");
```

В результате получим:

    лет     
   
### Как добавить слово в словарь?

Есть 2 способа.

**Способ № 1**

Внести в массив файла конфигурации _**config/declension-nouns.php**_ новое слово:

```php
    
    'телефон' => [
                'телефона',
                'телефонов'
            ],
    
``` 

Ключ элемента массива единственное число, первый элемент - существительное, которое описывает 2 телефона, второй элемент - существительное, которое описывает 5 телефонов.

**Способ № 2**

Добавить слово в момент выполнения:

```php
   DeclensionNoun::addToDictionary('телефон', 'телефона', 'телефонов');
``` 

Первым аргументом нудно передать единственное число, затем существительное, которое описывает 2 телефона, и третий аргумент - существительное, которое описывает 5 телефонов.

## Лицензия (License)

[MIT license](LICENSE)