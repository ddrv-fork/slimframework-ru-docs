---
title: Документация
---

<div class="alert alert-info">
    <p>
        Эта документация предназначена для <strong>Slim 3</strong>. Документацию по Slim 2 можно найти на <a href="http://www.slimframework.com/docs/v2/">slimframework.com</a>.
    </p>
</div>

## Добро пожаловать

Slim - это микроструктура PHP, которая помогает быстро писать простые, но мощные веб-приложения и API. 
По сути, Slim - диспетчер, который получает HTTP-запрос, вызывает соответствующую процедуру обратного вызова и
 возвращает HTTP-ответ. Вот и все.

## В чем смысл?

Slim - идеальный инструмент для создания API-интерфейсов, которые потребляют, перенастраивают или публикуют данные. 
Slim - отличный инструмент для быстрого прототипирования. Черт, вы даже можете создавать полнофункциональные 
веб-приложения с пользовательскими интерфейсами. Что еще более важно, Slim очень быстрый и имеет очень мало кода. 
Фактически, вы можете читать и понимать его исходный код `только днем` (!in only an afternoon!)

> По сути, Slim - диспетчер, который получает HTTP-запрос, вызывает 
соответствующую процедуру обратного вызова и 
возвращает HTTP-ответ. Вот и все.

Вам не всегда нужно `kitchen-sink` решение , например, [Symfony][symfony] или [Laravel][laravel].
Это отличные инструменты, конечно. Но они часто переполняются. Вместо этого Slim предоставляет только 
минимальный набор инструментов, которые делают то, что вам нужно, и ничего больше.

## Как это работает?

Во-первых, вам нужен веб-сервер, такой как Nginx или Apache. Вы должны [настроить свой веб-сервер](/docs/start/web-servers.html)
 так, чтобы он отправлял все соответствующие запросы в один файл PHP «front-controller». Вы создаете экземпляр и 
 запускаете свое приложение Slim в этом файле PHP.

Приложение Slim содержит маршруты, отвечающие определенным HTTP-запросам. Каждый маршрут вызывает обратный 
вызов и возвращает HTTP-ответ. Чтобы начать работу, сначала создайте экземпляр и настройте приложение Slim. 
Затем вы определяете маршруты своего приложения. Наконец, вы запускаете приложение Slim. Это так просто. 
Вот пример приложения:


```php
<?php
// Create and configure Slim app
$config = ['settings' => [
    'addContentLengthHeader' => false,
]];
$app = new \Slim\App($config);

// Define app routes
$app->get('/hello/{name}', function ($request, $response, $args) {
    return $response->write("Hello " . $args['name']);
});

// Run app
$app->run();
```

## Запрос и ответ

Когда вы создаете Slim-приложение, вы часто работаете непосредственно с объектами Request and Response. 
Эти объекты представляют собой фактический HTTP-запрос, полученный веб-сервером, и возможный HTTP-ответ, 
возвращаемый клиенту.

Каждому маршруту Slim-приложения присваиваются текущие объекты Request and Response в качестве аргументов 
его подпрограммы обратного вызова. Эти объекты реализуют популярные интерфейсы [PSR 7](/docs/concepts/value-objects.html). 
Slim route приложения может проверять или манипулировать этими объектами по мере необходимости. 
 В конечном счете, каждый маршрут приложения Slim **MUST** возвращать ответ PSR 7  объекта.

## Принесите свои собственные компоненты

Slim также хорошо сочетается с другими компонентами PHP. Вы можете зарегистрировать дополнительные сторонние 
компоненты, такие как [Slim-Csrf][csrf], [Slim-HttpCache][httpcache],
или [Slim-Flash][flash] которые основываются на функциональных возможностях Slim по умолчанию. 
Также легко интегрировать сторонние компоненты, найденные в [Packagist](https://packagist.org/).

## Как читать эту документацию

Если вы новичок в Slim, я рекомендую вам прочитать эту документацию от начала до конца. 
Если вы уже знакомы с Slim, вы можете перейти прямо в соответствующий раздел.

Эта документация начинается с объяснения концепций и архитектуры Slim, прежде чем вникать в конкретные темы, 
такие как обработка запросов и ответов, маршрутизация и обработка ошибок.

[symfony]: http://symfony.com/
[laravel]: http://laravel.com/
[csrf]: https://github.com/slimphp/Slim-Csrf/
[httpcache]: https://github.com/slimphp/Slim-HttpCache
[flash]: https://github.com/slimphp/Slim-Flash
[eloquent]: http://laravel.com/docs/5.1/eloquent
[doctrine]: http://www.doctrine-project.org/projects/orm.html