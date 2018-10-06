---

layout: yandex2

style: |
    /* собственные стили можно писать здесь!! */
    .img1 { margin: -60px auto 0; display: block; }


---

# ![](themes/yandex2/images/logo-{{ site.presentation.lang }}.svg){:.logo}

## {{ site.presentation.title }}
{:.title}

### ![](themes/yandex2/images/title-logo-{{ site.presentation.lang }}.svg){{ site.presentation.service }}

{% if site.presentation.nda %}
![](themes/yandex2/images/title-nda.svg)
{:.nda}
{% endif %}

<div class="authors">
{% if site.author %}
<p>{{ site.author.name }}{% if site.author.position %}, {{ site.author.position }}{% endif %}</p>
{% endif %}

{% if site.author2 %}
<p>{{ site.author2.name }}{% if site.author2.position %}, {{ site.author2.position }}{% endif %}</p>
{% endif %}

</div>

## Задание 1:<br />найди ошибки
{:.section}

## Задание

![](pictures/delivery.jpeg)
{:.image-right}

**Исправить ошибки в приложении, которое отображает данные на карте.**

Приложение использует:

- [API Яндекс Карт](https://tech.yandex.ru/maps/)
- [Chart.js](www.chartjs.org)
- [Webpack](https://webpack.js.org)

## Ошибки
{:.section}

## Приложение не запускается

&nbsp;

```
WARNING in ./src/index.js 4:2-9
"export 'default' (imported as 'initMap') was not found in './map'
```

## Приложение не запускается

&nbsp;

```
WARNING in ./src/index.js 4:2-9
"export 'default' (imported as 'initMap') was not found in './map'
```
<br/>/src/index.js

```js
// было
import initMap from "./map";

// стало
import {initMap} from "./map";
```
## Не отображается карта

![](https://jing.yandex-team.ru/files/dima117a/localhost9000_2018-10-06_14-10-10.png){:.img1}

## Не отображается карта

/public/index.css

```css
#map {
  height: 100%;
}
```

## Структура проекта

```
├─ public
│   ├─ index.css
│   └─ index.html
├─ src
│   ├─ api.js
│   ├─ chart.js
│   ├─ details.js
│   ├─ filter.js
│   ├─ index.js
│   ├─ map.js
│   ├─ mappers.js
│   └─ popup.js
│  ...
```

## Не отображаются метки

![](https://jing.yandex-team.ru/files/dima117a/localhost9000_2018-10-06_14-56-50.png){:.img1}

## Не отображаются метки

![](https://jing.yandex-team.ru/files/dima117a/localhost9000_2018-10-06_15-06-04.png){:.img1}

## Не отображаются метки

/src/map.js

```js
const objectManager = new ymaps.ObjectManager({
    // ...
});

loadList().then(data => {
    objectManager.add(data);
});
```

## Не отображаются метки

/src/map.js

```js
const objectManager = new ymaps.ObjectManager({
    // ...
});

loadList().then(data => {
    objectManager.add(data);
    
    // добавляем objectManager на карту
    myMap.geoObjects.add(objectManager);
});
```

### [https://tech.yandex.ru/maps/doc/jsapi/2.1/ref/reference/ObjectManager-docpage](https://tech.yandex.ru/maps/doc/jsapi/2.1/ref/reference/ObjectManager-docpage/)

## Метки не в Москве

![](https://jing.yandex-team.ru/files/dima117a/localhost9000_2018-10-06_15-24-52.png){:.img1}

## Метки не в Москве

![](https://jing.yandex-team.ru/files/dima117a/localhost9000_2018-10-06_15-32-46.png){:.img1}

### [https://tech.yandex.ru/maps/doc/jsapi/2.1/dg/concepts/geoobjects-docpage](https://tech.yandex.ru/maps/doc/jsapi/2.1/dg/concepts/geoobjects-docpage/)

## Неправильный маркер

![](https://jing.yandex-team.ru/files/dima117a/localhost9000_2018-10-06_15-37-27.png){:.img1}

## Неправильный маркер

/src/map.js

```js
const objectManager = new ymaps.ObjectManager({
    clusterIconLayout: 'default#pieChart',
    // ...
});

// эту строчку нужно удалить
objectManager.clusters.options.set('preset', 'islands#greenClusterIcons');
```

### [https://tech.yandex.ru/maps/jsbox/2.1/clusterer_pie_chart](https://tech.yandex.ru/maps/jsbox/2.1/clusterer_pie_chart)

## Не открывается попап

![](https://jing.yandex-team.ru/files/dima117a/localhost9000_2018-10-06_16-43-08.png){:.img1}

## Не открывается попап

![](https://jing.yandex-team.ru/files/dima117a/localhost9000_2018-10-06_16-45-47.png){:.img1}

### [https://tech.yandex.ru/maps/jsbox/2.1/placemark_balloon_layout](https://tech.yandex.ru/maps/jsbox/2.1/placemark_balloon_layout)

## Не отображается график

![](https://jing.yandex-team.ru/files/dima117a/localhost9000_2018-10-06_17-22-02.png){:.img1}

### [http://www.chartjs.org/docs/latest/axes/cartesian/linear.html#axis-range-settings](http://www.chartjs.org/docs/latest/axes/cartesian/linear.html#axis-range-settings)

## Неиспользуемый файл

![](https://jing.yandex-team.ru/files/dima117a/popup.js__entrance-task-1-2_2018-10-06_17-17-37.png){:.img1}

## Ошибки в Codestyle

<div class="next">
установить [eslint](https://eslint.org/docs/user-guide/getting-started)

```
$ npm install eslint --save-dev
```
</div>

<div class="next">
исправить codestyle
{:.next}

```js
{
    "scripts": {
        // ...
        "lint": "eslint --fix \"src/**/*.js\""
    }
    // ...
}
```
</div>

## Ошибки в Codestyle
{:.fullscreen}

```js
// .eslintrc

{
    "rules": {
        "indent": ["error", 4],
        "quotes": ["error", "single"],
        "no-undef": "error"
    },
    "env": { "browser": true },
    "globals": { "ymaps": true },
    "parserOptions": {
        "ecmaVersion": 6,
        "sourceType": "module",
        "ecmaFeatures": { "experimentalObjectRestSpread": true }
    }
}
```

## Вопросы?
{:.section}

## Задание 2:<br />найди ошибки
{:.section}

## Предметная область

## Технические требования

## Критерии

- соответствие макетам
- кроссбраузерность
- качество кода
- инфраструктура

## Ключевые места
{:.section}

## Компоновка страницы

## Листание

## Анимация попапа

## Слайдер

## Крутилка

## Дополнительные критерии
{:.section}

## Контакты 
{:.contacts}

{% if site.author %}

<figure markdown="1">

### {{ site.author.name }}

{% if site.author.position %}
{{ site.author.position }}
{% endif %}

</figure>

{% endif %}

{% if site.author2 %}

<figure markdown="1">

### {{ site.author2.name }}

{% if site.author2.position %}
{{ site.author2.position }}
{% endif %}

</figure>

{% endif %}

<!-- разделитель контактов -->
-------

<!-- left -->
- {:.skype}dima117a
- {:.mail}dima117a@yandex-team.ru
- {:.github}dima117













## Длинная цитата переносится на несколько строк
{:.blockquote}

### Источник

## Заголовок

Основной текст

**Ключевая мысль**

- Маркированный список
- Маркированный список

1. Нумерованный список
2. Нумерованный список

### Источник

## Заголовок

Элементы появляются по очереди

1. {:.next}Нумерованный список
2. {:.next}Нумерованный список
3. {:.next}Нумерованный список
4. {:.next}Нумерованный список


### Источник

## Заголовок
{:.images}

![](themes/yandex2/images/images-one.svg)

### Источник

## Заголовок
{:.images .two}

![](themes/yandex2/images/images-two.svg)
*Текст*

![](themes/yandex2/images/images-two.svg)
*Текст*

### Источник

## Заголовок
{:.images .three}

![](themes/yandex2/images/images-three.svg)
*Текст*

![](themes/yandex2/images/images-three.svg)
*Текст*

![](themes/yandex2/images/images-three.svg)
*Текст*

### Источник

## Заголовок

![](themes/yandex2/images/image-right.svg)
{:.image-right}

Основной текст

**Ключевая мысль**

- Маркированный список
- Маркированный список

1. Нумерованный список
2. Нумерованный список

### Источник

## Заголовок

<!-- библиотека пиктограмм https://patterns.yandex-team.ru/presentations?typeIn=icons -->

![](themes/yandex2/images/icons.svg)
{:.icon-left}

Основной текст

**Ключевая мысль**

- Маркированный список
- Маркированный список

1. Нумерованный список
2. Нумерованный список

### Источник

## Заголовок
{:.icons}

<!-- библиотека пиктограмм https://patterns.yandex-team.ru/presentations?typeIn=icons -->

![](themes/yandex2/images/icons.svg)
*Текст*

![](themes/yandex2/images/icons.svg)
*Текст*

![](themes/yandex2/images/icons.svg)
*Текст*

### Источник

## Заголовок
{:.icons .four}

<!-- библиотека пиктограмм https://patterns.yandex-team.ru/presentations?typeIn=icons -->

![](themes/yandex2/images/icons.svg)
*Текст*

![](themes/yandex2/images/icons.svg)
*Текст*

![](themes/yandex2/images/icons.svg)
*Текст*

![](themes/yandex2/images/icons.svg)
*Текст*

### Источник

## Заголовок
{:.icons .five}

<!-- библиотека пиктограмм https://patterns.yandex-team.ru/presentations?typeIn=icons -->

![](themes/yandex2/images/icons.svg)
*Текст*

![](themes/yandex2/images/icons.svg)
*Текст*

![](themes/yandex2/images/icons.svg)
*Текст*

![](themes/yandex2/images/icons.svg)
*Текст*

![](themes/yandex2/images/icons.svg)
*Текст*

### Источник

## Заголовок будет скрыт
{:.fullscreen}

![](themes/yandex2/images/images-fullscreen.svg)

## Заголовок будет скрыт
{:.fullscreen}

![](themes/yandex2/images/images-fullscreen.svg)

<figure markdown="1">
Текст
</figure>

## Таблица

|  Locavore     |  Umami       |  Helvetica |  Vegan     |
+---------------|--------------|------------|------------+
|  Fingerstache<br/>The second line |  Kale        |  Chips     |  Keytar    |
|  Sriracha     |  Gluten-free |  Ennui     |  Keffiyeh  |
|  Thundercats  |  Jean        |  Shorts    |  Biodiesel |
|* Terry        |* Richardson  |* Swag      |* Blog      |

Текст

### Источник

## Исходный код (html)

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <title>Shower</title> <!--Comment-->
    <link rel="stylesheet" href="screen.css">
</head>
<body>Hello!</body>
</html>
```

## Исходный код (js)

Пояснение для кода.

```js
var i, j, over, data = new Array(2, 34.12, 4.7, 0, 234, 5);
var test = false;

for (i = 1; i < data.length; i++) {
    over = data[i]; 
    for (j = i - 1; j >= 0 && data[j] > over; j--) {
        data[j + 1] = data[j];
    }
    data[j + 1] = over;
}
alert(data.join(','));
```

## Исходный код (css)

```css
.head {
    background-color: yellow;
}

.head__logo {
    background-image: url(images/logo.svg);
}

#test, body {
    font-weight: bold;
}

```

## Этот заголовок будет скрыт
{:.fullscreen}

```js
// исходный код (на весь экран)

var x = 10;
for (var i = 0; i < x; i++) {
    console.log('hello!');
}
```

## Контакты 
{:.contacts}

{% if site.author %}

<figure markdown="1">

### {{ site.author.name }}

{% if site.author.position %}
{{ site.author.position }}
{% endif %}

</figure>

{% endif %}

{% if site.author2 %}

<figure markdown="1">

### {{ site.author2.name }}

{% if site.author2.position %}
{{ site.author2.position }}
{% endif %}

</figure>

{% endif %}

<!-- разделитель контактов -->
-------

<!-- left -->
- {:.skype}author
- {:.mail}author@yandex-team.ru
- {:.github}author

<!-- right -->
- {:.twitter}@author
- {:.facebook}author

<!-- 

- {:.mail}author@yandex-team.ru
- {:.phone}+7-999-888-7766
- {:.github}author
- {:.bitbucket}author
- {:.twitter}@author
- {:.telegram}author
- {:.skype}author
- {:.instagram}author
- {:.facebook}author
- {:.vk}@author
- {:.ok}@author

-->
