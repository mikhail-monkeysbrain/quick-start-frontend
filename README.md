# quickstart frontend
_Quickstart шаблон на webpack, pug, stylus, es6, postcss для многостраничных сайтов_

## Подготовка
### Установка пакетов
1. Установите или обновите [Node.js](https://nodejs.org/en/);
1. Установите [Yarn](https://yarnpkg.com/lang/en/) -  [Использование](https://yarnpkg.com/en/docs/usage).

### Опционально
1. Установите плагин editorconfig для вашего редактора ([PhpStorm](https://plugins.jetbrains.com/plugin/7294-editorconfig), [Sublime Text](https://packagecontrol.io/packages/EditorConfig), [Atom](https://atom.io/packages/linter-eslint), [VS Code](https://marketplace.visualstudio.com/items?itemName=EditorConfig.EditorConfig)) - единый стиль кодирования между различными редакторами и IDE;
1. Установите плагин eslint для вашего редактора ([PhpStorm](https://www.jetbrains.com/help/phpstorm/eslint.html), [Sublime Text](https://packagecontrol.io/packages/ESLint), [Atom](https://atom.io/packages/editorconfig), [VS Code](https://marketplace.visualstudio.com/items?itemName=dbaeumer.vscode-eslint)).

## Старт
1. Клонируйте или [загрузите](https://github.com/mikhail-monkeysbrain/quick-start-frontend/archive/master.zip) проект:
    ```
    git clone git@github.com:mikhail-monkeysbrain/quick-start-frontend.git project-name
    ```
1. Зайдите в проект и удалите папку .git:
    ```
    cd project-name && rm -rf .git
    ```
1. Установите зависимости с помощью yarn:
    ```
    yarn
    ```
1. Команды для сборки:
    * `yarn build` - Сборка проекта в продакшен (включая UglifyJSPlugin, cssnano);
    * `yarn watch` - Сборка проекта и вотч проекта для разработки (включая sourcemap);
    * `yarn start` - Сборка проекта, вотч и dev-сервер (включая livereload);
    * `yarn lint` - линтирование js.

## Использование

### Подключение изображений

```pug
+img('sample.jpg')(alt='image').some-class
```

Внимание! Для этого миксина требуется картинка в удвоенном размере (для srcset). Изображения помещаются в папку /src/static/upload

### Подключение плагинов/библиотек

#### CSS

Установите пакет (например, slick-carousel):
```
yarn add slick-carousel
```

Импортируйте пакет в main.styl:
```
@require '~slick-carousel/dist/css/slick-carousel.min.css'
```

Символ ~ в стилях смотрит в папку node_modules.

#### JS

##### jQuery плагины

Установите пакет (например, sticky-kit):
```
yarn add sticky-kit
```

Импортируйте пакет в main.js:
```js
import 'sticky-kit/dist/sticky-kit';
```

##### Другие библиотеки

Установите пакет (например, swiper):
```
yarn add swiper
```

Импорт в из файла, в котором есть зависимость::
```js
import Swiper from 'swiper/dist/js/swiper';
```

### Алиас @ в стилях и js

@ в пути к папке src, с его помощью можно создать абсолютный путь.:
CSS:
```
src: url('~@/font/PTSans/ptsans.woff2')
```
JS:
```
import module from '@/js/module';
```

### Использование svg-спрайтов
Разместите иконку в  ```/ico```

И добавьте код в шаблон:
```html
<svg class="your-class" width="193" height="40">
  <use xlink:href="#your-icon-file-name"></use>
</svg>
```

Или вы можете использовать миксин:
```pug
+icon('your-icon-file-name')(width=193 height=40).your-class
```
