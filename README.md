# Русификация Asana

Расширение для браузера,
здорово крашит языковой барьер между русским пользователем
и лучшим сервисом для ведения проектов и задач.  
На данный момент есть поддержка браузеров:
- Google Chrome

## Разработка

Для начала разработки необходимо установить зависимости:
```
yarn install
```
Далее собрать расширение и бандл:
```
yarn run build
``` 
В браузере необходимо установить расширение (оно будет находится в распакованном виде в каталоге **/dist**).   
При изменении исходников пересборка будет происходить автоматически.

## Наполнение словаря

Файлы словаря находятся в каталоге **/src/common/localization/dictionaries**.  
Наполнение осуществляется в двух файлах:

- codes.js
- phrases.js

В **phrases.js** ключом является исходная фраза из английского словаря Asana.
Ключ в 99% случаев является обычным текстом, а в остальных случаях
он просто немного "обременён" различными html-тэгами и прочими артефактами. 
Как выглядит исходная фраза можно узнать методом пробы или с помощью хэлпера (см. ниже).

В **codes.js** ключом явялется код фразы (сгенерирванный Asana),
который можно узнать, воспользовавшись хэлпером.
Делать перевод по коду полезно в тех случаях, когда перевод по фразе
неудобен из-за языковых особенностей, например слово *"Archive"*
в зависимости от "уголка" сервиса где-то будет переводиться как *"Архив"*,
а где-то как *"Архивировать"*

### Хэлпер

Данный помощник находится являеся глобальноый функцией, так что вызывается
через **window.translateHelper** или просто **translateHelper**.  
Функция принимает два аргумента:
- phrase (обяз.) - искомая фраза в формате строки или регулярного выражения
- length (необяз.) - длина искомой фразы

Функция пробежит по словарю Asana и при совпадении запишет в лог результат следующего формата:  
`${код} ${фраза}` 