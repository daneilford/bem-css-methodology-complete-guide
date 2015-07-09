#b_ BEM CSS методология: Полное руководство

Главное: классы b-someblock__someelement__element__element-modificator - это не BEM!
Как правильно верстать по BEM - читайте ниже.

1. Длинное необязательное вступление
2. Суть #b_
 - Зачем это всё?
 - Блок
 - Элемент
 - Модификатор
 - Префикс b- и его воображаемые друзья: l-,i-,g- и еретический js-
 - Как менять внешний вид блока: правила модификации
3. Три главных правила
4. Ошибки, про которые нигде не написано
5. Типичные вопросы, ответов на которые вы не нашли на bem.info
6. Альтернативы или же братья: SMASS, OOCSS, MCSS и BEM.
7. Семантика в BEM.
8. BEM и CSS-препроцессоры: Sass и LESS.
9. Путь Яндекса: кому и зачем нужны bem-tools и прочие "ужасы"
10. bem-bl и bem-bl в сниппетах от Яндекса (скоро!)
11. Альтернативные реализации BEM-методологии
12. Примеры сайтов на BEM
- Яндекс-сайтов по BEM
- НЕ-Яндекс-сайтов по BEM
- Редизайна по BEM
13. Отзывы: Мнения людей меняется за пару месяцев работы с BEM. Путь к пониманию.
14. BEM для атеистов - почему это не религия


## 1. Длинное необязательное вступление
История понимания BEM и зачем он нужен.
Можно смело пропустить и читать сразу пункт №2.

— Я не понимал BEM ("что за ерунда придуманная программерами, которые не знают CSS"). Нет не программерами. И не ерунда.
— Потом я думал что понимал BEM ("[у меня типа независимые стили: специфичность длиной в ширину экрана](http://delka.name/blog/2013/04/bem-otkroveniya-prinyavshih-veru/)").
— Потом не знал как же правильно его применять, особенно в рамках веб-студии.

Теперь понимаю и знаю. И хочу рассказать и доказать вам что BEM - единственный правильный вариант организации вёрстки.
- Да-да, и для небольших студий, у которых не один большой, а множество средних проектов.
- И для фрилансера с маленькими сайтами.
- И для лендингов.
- И даже когда вы делаете правки в чужом спагетти-коде - вы можете (и должны) примерять BEM!

В BEM прекрасно вписываются SMACSS, OOCSS, MCSS. Большинство не знает что такое BEM, или думает, но знает неправильно. Если вы знаете что такое BEM и считаете что он не для вас (или вообще только Яндексу нужен) - дочитайте до конца. Я расскажу вам о том что BEM - это не "xslt, bem-bl, xml, bem-tools, js", а это методология которая решает проблемы с которыми сталкиваемся мы все. Нужная всем. Незаменимая для компаний, значительно ускоряющая скорость и стоимость разработки, поддержки, развития, передачи проекта другим разработчикам, масштабирования. Это прорыв уровня ООП для CSS.

И более того: BEM - семантичен как ничто другое при правильном применении!
Поехали, я расскажу вам о тех идеях и логике, что стоят за BEM, и почему и как вы можете его использовать!

Существует огромное кол-во статей, докладов, презентаций про BEM. Почти все - от Яндекса. Я читал все статьи, все доклады по BEM, ездил на субботники, общался с Харисовым, Ткаченко и разработчиками библиотеки bem-bl. Но чтоб понять всё (а не думать что понял) мне потребовалось 5 лет.

Вообще если бы было меньше бредовых статей типа этой: http://habrahabr.ru/post/203440/ которые пишут те, кто сам ничего не понял, было бы лучше. И ошибок было бы меньше.

## 2. Суть #b_
### 2.1 Зачем это всё?
#### Главная проблема вёрстки: каскад.
Зачем был придуман BEM? Чтоб уйти от каскада.

##### Почему надо уходить от каскада?
Идея убрать каскад кажется дикой - как, это же каскад. У нас каскадные таблицы стилей! Каскад сверху до низу по всей странице! Мы в ~~детстве~~ 2000-х играли в игру "кто напишет меньше тегов"!

Но. У нас страница состоит из блоков. Независимых блоков. Ее части не есть один большой текст, со стилями что спускаются вниз. Это блоки, что могут и должны иметь возможность переноситься.


#### Разновидности BEM: НБ, АНБ, Лего, текущий BEM, BEM-CSS у "не Яндекса".
Всё это BEM. Разновидности называются "подмножествами BEM".

#### Что не является BEM.
НЕ BEM:
- длинные строки каскада ради высокой специфичности селекторов - это не та независимость и ни разу не BEM.
- базовые стили и их переопределения ниже _от_контекста_ - как общий стиль вёрстки
- BEM это не только bemjson, bem-tools и прочее. АНБ - тоже BEM

#### Главные правила BEM.
Чтобы их осознать, мы с вами должны вспомнить как писать правильно. Вспомнить правила.
Я говорю "вспомнить", потому что то о чем мы будем говорить - это ручная верстка по BEM.
В правильных терминах bem это называется "CSS подмножество BEM".
Потому что bem он не только про CSS.

Нам придётся совершить экскурс в историю и пройти путь развития BEM чтобы сформулировать четкие правила "BEM CSS" из общей методилогии.
Чтоб собрать все пришлось читать апокрифы. Нет единого стандарта. Есть множество толкований - диалектов BEM. Евангелие от Вегеда, проповедь на внутренней коференции и статьи других апостолов, простите евангелистов BEM. Сам BEM допускает множество вариантов самой методологии. А уж какой путь выбирать в каждом конкретном случае, при модификации кода например - можно спорить и спорить. Поэтому -тот- старый добрый ручной BEM и правду похож на религию.

Сводим всё из разных источников. Очень подробно. Много примеров.

##### .block
Главное в BEM - понятие независимого блока.</h2>
> Независимый блок (НБ или просто блок) это самодостаточный элемент страницы, который при перемещении в другое место на странице или на другую страницу не теряет своей самодостаточности.
> BEM.Клуб на Я.рушке, [Независимый блок](http://clubs.ya.ru/bem/replies.xml?item_no=4)

__Формальное определение__
> Правила независимости блока:
> 1. для описания элемента используется class, но не id
> 2. каждый блок имеет префикс
> 3. в таблице стилей нет классов вне блоков
> BEM.Клуб на Я.рушке, [История создания BEM (часть первая)](http://clubs.ya.ru/bem/replies.xml?item_no=1398)

Формальное определение нужно только затем чтоб описать при каких условиях он должен таким стать.
Что такое стили вне блоков я опишу ниже.

__"Как его таким написать?"__
Просто писать стили тупо на каждый блок. BEM хорош тем, что позволяет не забивать голову ерундой с каскадом, а сосредоточимся на семантике и логике кода. А с препроцессорами BEM позволяет писать еще и очень чистый и логичный код. Но про это чуть позже.

__Как проверить?__
Просто навести на блок в инспекторе кода. У него не должно быть каскада.
Слайд инспектор кода


##### .block__element
Не бывает элементов вложенных в элементы!

Я тоже раньше так писал:
```css
.form-buy-results__to-city__slider__tab__column_buy
```
Так делать нельзя.

__Как надо?__
```html
<div class='block'>
  <div class='block__elem1'>
    <div class='block__elem2'></div>
  </div>
  <div class='block__elem3'></div>
</div>
```

А в CSS:
```css
.block {}
.block__elem1 {}
.block__elem2 {}
.block__elem3 {}
```

__Если вам нужно сделать элемент у элемента, значит вам нужно сделать новый блок!__
Вместо:
```html
<div class='block'>
    <div class='block__elem1'>
        <div class='block__elem1__elem2'></div>
    </div>
</div>
```
Надо делать новый блок
```html
<div class='block1'>
    <div class='block2'>
        <div class='block2__elem'></div>
    </div>
</div>
```

__Не пишите странные имена__
```css
.block {}
.blockelem1 {}
.blockelem1__elem2 {}
```
У вас будут проблемы при переносе:
```html
<div class="someblock">
  <div class="blockelem1__elem2"></div>
```

Бейте на блоки!

##### Модификатор
Модификаторы в #yandex #b_:
```css
.block-name__elem_key_value
```

Но для всего мира ([csswizardry](http://csswizardry.com/2013/01/mindbemding-getting-your-head-round-bem-syntax/),[cssguidelin](http://cssguidelin.es/#bem-like-naming),[sitepoint](http://www.sitepoint.com/bem-smacss-advice-from-developers/)) это:
```css
.blockname__elem--mod {}
```
Синтаксис модификаторов `.blockname__elem--mod` был запущен в 2012 с легкой руки Nicolas Gallagher @necolas в http://nicolasgallagher.com/about-html-semantics-front-end-architecture/
Причина:
> This is merely a naming pattern that I’m finding helpful at the moment. It could take any form. But the benefit lies in removing the ambiguity of class names that rely only on (single) hyphens, or underscores, or camel case.
> http://nicolasgallagher.com/about-html-semantics-front-end-architecture/

> The reason for double rather than single hyphens and underscores is so that your block itself can be hyphen delimited, for example:
> http://csswizardry.com/2013/01/mindbemding-getting-your-head-round-bem-syntax/

###### Сокращённые модификаторы

Вариацией модификаторов являются "Сокращенные модификаторы" через multiple classes

```html
 <div class="blockName -mod_val"></div>
```
```scss
.blockName {
  &.-mod_val {}
}
```
Синтаксис с "-", а не с "_", т.к. иначе имя класса будет не валидно.

Стили модификаторов НЕ пишутся без привязки к имени блока
То что в Классическом BEM пишется как `.block_mod_val {}`
в сокращенных модификаторах пишут как `.block.-mod_val {}`

Компании и разработчики, которые используют сокращённые модификаторы:
* [Dan Tello "Sassier (BE)Modifers"](http://viget.com/extend/bem-sass-modifiers)
* [iDeus Team](https://github.com/ideus-team/guidelines/blob/master/frontend/bem.md)
* [2Gis](https://twitter.com/Chaptykov/status/570587770432962561)
* [Одноклассники](https://twitter.com/from_anywhere/status/570602747915059200)

Проблемы с сокращенными модификаторами:
 - Если у вас генерация html кода
 - Если у вас миксование блоков с модификаторами: http://codepen.io/hudochenkov/pen/OPEMwK?editors=110
 - Доводы от BEM-team: http://getbem.com/faq/#why-the-modifier-classes-are-prefixed
 - "когда ты начнёшь использовать i-bem.js и добавлять/удалять модификаторы динамически, ты поймёшь, что сокращённая запись этому мешает" (c) harisov https://twitter.com/harisov/status/571191436315631616

###### Сравнение Сокращённых модификаторов и BEViS состояний
...

##### Абстрактные блоки
Абстрактный блок = блок который является основой других блоков, но сам не существует в верстке без миксования с другми.
Тут ещё формальные определения из Ярушки и примеры.


###### Разница между модификатором и абстрактным блоком
Модификаторы - изменяют или дополняют уже существующий блок. Они нужны тогда когда у вас есть _уже готовый блок_, который _не сильно_ изменяется и это реализовывается модификаторами.
А абстрактные блоки - это кирпичи для _ещё не построенного блока_, с их помощью можно построить _значительно отличающиеся_ блоки.

Итого - если вам надо:
 * набор похожих блоков - модификаторы
 * набор сходных, но непохожих блоков - абстрактные классы


- Префикс b- и его воображаемые друзья: l-,i-,g- и еретический js-

А префикс js- (недолго существовавший как с- в #b_) вероятно тоже популяризировал Nicolas Gallagher @necolas в той же статье http://nicolasgallagher.com/about-html-semantics-front-end-architecture/

 - Как менять внешний вид блока: правила модификации

##4. Ошибки, про которые нигде не написано
### 1. Повторение DOM-дерева

### 2. Привязка к блоку-родителю
https://twitter.com/delaz/status/580353955244482560

##8. BEM и CSS-препроцессоры: Sass и LESS.
Extend-Only Selectors в Sass == абстрактный блок (i-блок) в #b_
```SCSS
%i-block {
  // стили абстрактного блока
}
.b-block {
  @extend %i-block;
}
```


#Взять примеры ошибок из https://dl.dropboxusercontent.com/u/66873654/%D0%91%D0%AD%D0%9C%D0%BE%D1%81%D0%B8%D0%BF%D0%B5%D0%B4.pdf

#Дополнение из доклада:

##Семантика БЭМ
БЭМ всегда ругали за то что он ужасный и «для роботов», а на самом деле он довольно семантичный.

_Имена БЭМ-классов создают дополнительный уровень логики._

Есть DOM-дерево, а есть БЭМ-дерево.

Вот обычное DOM-дерево:
```html
<input class="big_red_button order-button">
```
Раньше мы писали „big-red-button“ (для кнопки покупки) и стало хорошим тоном чтобы название класса отображало не его представление, а его суть, это назвали семантикой, а класс переименовали в например, а „order-button“. Такой код стало легче поддерживать.
А БЭМ дополняет это, создавая новый уровень логики, где БЭМ описывает связи между элементами.

Вот БЭМ-дерево:
```html
<input class="order-button b-checkout__submit">
```
Т.е. обычно имена классов описывают конкретные кусочки, что из себя представляет каждый блок, а БЭМ описывает связи между блоками, положение этого блока в логике документа, это и есть дополнительный уровень семантики.


##Зачем нужен БЭM?
БЭМ придумали в Яндексе для решения собственных проблем по поддержке огромного Яндекс-портала. Он был решением проблемы поддерживать html-код легко и быстро.
Нам БЭМ нужен т.к он удобен для верстки и позволяет не думать о именах классов, ликивидирует конфликты в коде, код легче расширять.
Также благодаря тому что БЭМ это методология — она позволяет легче вводить людей в проекты и заменять их. Нет проблемы ухода сотрудника в отпуск или непонятности его кода.


##БЭМ CSS
Ручная верстка по БЭМ называется «BEM CSS». Точнее официльного названия нет, я предлагаю такое.
Яндекс предлагает именовтаь его как «CSS подмножество БЭМ», потому что БЭМ он не только про CSS, это огромная методология, вершиной которой является Full Stack BEM с bemjson, bemtools и т.д:

##Full stack BEM?
![Full stack BEM](http://delka.github.io/talks/webcamp/2015/bem/pictures/full-bem-stack.png "Full stack BEM")
Когда вам надоесть вручную писать HTML и вам захочется его генерировать и манипулировать им – переходите на Full Stack BEM. Не обязательно полностью отказываться от HTML, можно использовать „BEM project-stub HTML edition“: https://github.com/tadatuta/bem-project-stub-he и https://ru.bem.info/forum/469/

##Пример певерстки по БЭМ
Давайте попробуем переверстать «по-БЭМ» такую верстку.
Макет:
![BEM remarkup example](http://delka.github.io/talks/webcamp/2015/bem/pictures/example-bem-1.png)
Вот так она была сверстана:
![BEM remarkup example](http://delka.github.io/talks/webcamp/2015/bem/pictures/example-bem-2.png)
Похоже на БЭМ, но давайте приглядимся, вот так там назначаются стии:
![BEM remarkup example](http://delka.github.io/talks/webcamp/2015/bem/pictures/example-bem-2-css.png)
Тут происходит повышение специфичности, на самом деле это не БЭМ, я [написал статью на эту тему](http://bit.ly/not-bem).

##Методология
Чтобы разобраться как верстать правильно, давайте обратимся к методологии.
Проблема непонятости БЭМ в том, что БЭМ рос настолько быстро, что первая крайне сырая документация появилась только спустя 4 года. Яндекс придумал свой шаблонизатор и язык, а мы, простые верстальщики только в прошлом году всерьез задумались о том, что стоит писать код по БЭМ.

Методология не менялась, менялась реализация и от правил по написанию CSS Яндекс дошел до стройной системы. Но нам, чтоб правильно писать код вручную, неободимо вспомнить те самые базовые правила:

##.block
![.block](http://delka.github.io/talks/webcamp/2015/bem/pictures/block.png)

__Независимый блок__
>НБ или просто блок, это самодостаточный элемент страницы, который при перемещении в другое место на странице или на другую страницу не теряет своей самодостаточности.

БЭМ.Форум, [Независимый блок](https://ru.bem.info/forum/-43/)

__Правила независимости блока__
>1. для описания элемента используется class, но не id
>2. каждый блок имеет префикс
>3. в таблице стилей нет классов вне блоков

БЭМ.Форум, [История создания БЭМ](https://ru.bem.info/forum/-147/)

##Как его таким написать?
Просто писать стили тупо на каждый блок.
БЭМ хорош тем, что позволяет не забивать голову ерундой с каскадом, а сосредоточимся на семантике и логике кода.
А с препроцессорами БЭМ позволяет писать еще и очень чистый и логичный код.

##Как проверить?
Просто навести на блок в инспекторе кода.
У него не должно быть каскада.

##.block__element
![.block__element](http://delka.github.io/talks/webcamp/2015/bem/pictures/element.png)

__Элемент__
>Элемент – это часть блока, отвечающая за отдельную функцию.
>_Он может находиться только в составе блока и не имеет смысла в отрыве от него._

bem.info, [Методология](https://ru.bem.info/method/definitions)

Элемент можно представить себе как папку в файловой системе, это способ организации кода, чтобы было понятно, что к чему относится.

##DOM-дерево
```html
<ul>
  <li>
    <a>
      <span></span>
    </a>
  </li>
</ul>
```

```css
.ul {}
.ul > li {}
.ul > li > a {}
.ul > li > a > span {}
```

Вложенные html-элементы - это DOM-дерево.
Имена классов, которые вы пишите - это БЭМ-дерево.
Почувствуйте разницу!

##БЭМ-дерево
```html
<ul class="menu">
  <li class="menu__item">
    <a class="menu__link">
      <span class="menu__text"></span>
    </a>
  </li>
</ul>
```

```css
.menu {}
.menu__item {}
.menu__link {}
.menu__text {}
```

##БЭМ дерево — чистая логика
Оно не зависит ни от чего, даже от размещения в документе.
БЭМ-дерево не привязано к визуальному представлению блоков, оно отображает только логику, это и есть новый уровень семантики!

##Самая страшная ошибка — .block__el__el__el
Так #b_ поняли и используют зарубежом
![block__el__el](http://delka.github.io/talks/webcamp/2015/bem/pictures/block__el__el.png)

##Я тоже раньше так писал
```css
.form-buy-results__to-city__slider__tab__column_buy
```

embed/twitter-lehazyo_chatik.html

##Как правильно реализовывать вложенность
```html
<div class="block">
    <div class="block__elem1">
        <div class="block__elem2"></div>
    </div>
    <div class="block__elem3"></div>
</div>
```

```css
.block {}
.block__elem1 {}
.block__elem2 {}
.block__elem3 {}
```

##Элемент у элемента?
```html
<div class="block">
    <div class="block__elem1">
        <div class="block__elem1__elem2"></div>
    </div>
</div>
```
Если вам нужно сделать элемент у элемента, значит вам нужно:
- или создать новый блок
- или сделать ваше БЭМ-дерево с одинарной вложенностью элементов

##Есть 2 варианта как это переписать
__1. Бить на блоки!__
Делать новый блок
```html
<div class="block1">
    <div class="block2">
        <div class="block2__elem"></div>
    </div>
</div>
```
__2. Рубить ветки!__
Делать БЭМ-дерево с 1-ой вложенностью элементов</h2>
```html
<div class="block1">
    <div class="block1__elem1">
        <div class="block1__elem2"></div>
    </div>
</div>
```

##Типичная ошибка
Попытка вложить имя элемента в имя блока
Чтоб «схитрить» и «как-будто не вложить», написать не `.block__el1__el2` а `.blockel1__el2` или `.block__el1el2`.
      Так нельзя.
C кодом ниже будут проблемы при переносе:
```css
.block {}
.blockel1 {}
.blockel1__el2 {}
```

Попытавшись перенести «странный элемент» в другое место - мы получим элемент, что завис «в воздухе» без блока-родителя:
```html
<div class='someblock'>
    <div class='blockel1__el2'></div>
</div>
```
Так можно делать только если .blockelem сохранит логический смысл при переносе в другой блок.</p>

##element > element нельзя в CSS, но можно в HTML!
Обратите внимание - вы не можете вкладывать элементы в элементы в CSS, но можете и должны вкладывать элементы в элементы в HTML! DOM-дерево и БЭМ-дерево могут быть разными.

##Запрет есть исключительно про нейминг!
>БЭМ-дерево на то и дерево, что поддерживает вложенность, поэтому в БЭМ-дереве, разумеется, разрешается вкладывать элементы в элементы, блоки в блоки, блоки в элементы.

Vladimir Grinenko, [@tadatuta](http://twitter.com/tadatuta)

##Давайте переверстаем наш макет:
![BEM remarkup example](http://delka.github.io/talks/webcamp/2015/bem/pictures/example-bem-3-mod.png)
![BEM remarkup example](http://delka.github.io/talks/webcamp/2015/bem/pictures/example-bem-3-01.png)
![BEM remarkup example](http://delka.github.io/talks/webcamp/2015/bem/pictures/example-bem-3-02.png)
![BEM remarkup example](http://delka.github.io/talks/webcamp/2015/bem/pictures/example-bem-3-03.png)
![BEM remarkup example](http://delka.github.io/talks/webcamp/2015/bem/pictures/example-bem-3-04.png)
![BEM remarkup example](http://delka.github.io/talks/webcamp/2015/bem/pictures/example-bem-3-05.png)
![BEM remarkup example](http://delka.github.io/talks/webcamp/2015/bem/pictures/example-bem-3-06.png)
![BEM remarkup example](http://delka.github.io/talks/webcamp/2015/bem/pictures/example-bem-3-07.png)
![BEM remarkup example](http://delka.github.io/talks/webcamp/2015/bem/pictures/example-bem-3-08.png)
![BEM remarkup example](http://delka.github.io/talks/webcamp/2015/bem/pictures/example-bem-3-09.png)
![BEM remarkup example](http://delka.github.io/talks/webcamp/2015/bem/pictures/example-bem-3-10-mf.png)

---
Сырой html, переписать:
  <h2>Мы написали BEM-дерево:</h2>
    <pre>
<code>&lt;div class="block"&gt;</code>
<code>    &lt;div class="block<mark>__elem1</mark>"&gt;</code>
<code>        &lt;div class="block<mark>__elem2</mark>"&gt;&lt;/div&gt;</code>
<code>    &lt;/div&gt;</code>
<code>    &lt;div class="block<mark>__elem3</mark>"&gt;&lt;/div&gt;</code>
<code>&lt;/div&gt;</code>
    </pre>
  </div></section>

  <section class="slide"><div>
    <h2>Нет каскада:</h2>
    <pre>
<code>.block {}</code>
<code>.block__elem1 {}</code>
<code>.block__elem2 {}</code>
<code>.block__elem3 {}</code>
    </pre>
  </div></section>

<section class="slide shout"><div>
  <h2>Модификация</h2>
</section>

<section class="slide"><div>
  <h2>6 видов</h2>
<ol>
<li>Модификатором
<ul>
  <li>модификатором блока</li>
  <li>модификатором элемента</li>
</ul>
</li>
<li>Контекстом (т.е. каскадом от блока выше)</li>
<li>Уровнем переопределения (добавлением-перезаписью файла стилей)</li>
<li>Миксованием (добавлением классов других блоков)
  <ul>
    <li>включая глобальный класс</li>
  </ul>
</li>
</ol>
</section>

<section class="slide"><div>
  <h2>Просто добавляйте модификатор!</h2>
    <pre>
<code>&lt;div class="block-name__elem<mark>_key_value</mark>"&gt;</code>
    </pre>
  <p>А для элементов — делай каскад от модификатора.</p>
</div></section>

<section class="slide"><div>
  <h2>Модификаторы для элементов, можно?</h2>
  <p>Если речь идет о простых правках, типа «активный пункт меню», то да, можно:</p>
    <pre>
<code>&lt;a class="menu__link menu__link<mark>_state_active</mark>"&gt;</code>
    </pre>
</div></section>

<section class="slide"><div>
  <h2>Булевые модификаторы</h2>
  <p>Кстати в таких простых случаях, можно писать модификаторы просто одним словом:</p>
    <pre>
<code>&lt;a class="menu__link menu__link<mark>_active</mark>"&gt;</code>
    </pre>
</div></section>

<section class="slide cover"><div>
  <img src="pictures/example-bem-3-mod.png" alt="">
</div></section>

<section class="slide"><div>
  <h2>Но подумайте, может это новый блок?</h2>
  <iframe src="embed/twitter-bxxx.html"
id="twitter-widget-0" scrolling="no" frameborder="0" allowtransparency="true" class="twitter-tweet twitter-tweet-rendered" allowfullscreen="" style="display: block; max-width: 99%; min-width: 220px; padding: 0px; border-top-left-radius: 5px; border-top-right-radius: 5px; border-bottom-right-radius: 5px; border-bottom-left-radius: 5px; margin: 50px auto; border-color: rgb(238, 238, 238) rgb(221, 221, 221) rgb(187, 187, 187); border-width: 1px; border-style: solid; box-shadow: rgba(0, 0, 0, 0.14902) 0px 1px 3px; position: static; visibility: visible; width: 500px;" title="Встроенный твит" height="257"></iframe>
<!--
На самом деле в случае ручной верстки это сигнал об ошибках в вашей логике разбиения на блоки.
Признак неудачного проектирования родительского блока.
Если вам нужен модификатор на элемент - вам скорее нужно сделать из этого элемента новый блок.
-->
</div></section>

<!--
<section class="slide"><div>
    <h2>Статья на Frontender Magazine</h2>
    <p><a href="https://github.com/FrontenderMagazine/bem-css-methodology-complete-guide/blob/master/rus.md">https://github.com/FrontenderMagazine/bem-css-methodology-complete-guide/blob/master/rus.md</a></p>
</div></section>
-->

<section class="slide shout"><div>
  <h2>БЭМ допускает ошибки</h2>
</div></section>

<section class="slide shout dark"><div>
  <h2>Самые популярные ошибки</h2>
</div></section>

<section class="slide"><div>
  <h2>1. block__el__el</h2>
<p>
Например, слайдеры очень часто верстают дикой вложенностью.
</p>
</div></section>

<section class="slide"><div>
  <h2>2. Повышение специфичности</h2>
   <p>В html как-будто всё ok:
    <pre>
<code>&lt;div class="block"&gt;</code>
<code>  &lt;div class="block__el"&gt;</code>
    </pre>
    <p>А на деле сели в машину и сгорели:</p>
    <pre>
<code>/* CSS */</code>
<code><mark class="important">.block</mark> .block__el {}</code>
    </pre>
</div></section>

<section class="slide"><div>
  <h2>3. Стили вне блоков</h2>
    <pre>
<code>&lt;ul class="menu checkoutForm big <mark class="important">myfuckingclass-bold</mark>"&gt;</code>
    </pre>
</div></section>

<section class="slide"><div>
  <h2>Почему это ошибки?</h2>
  <p>Да потому что из-за этого потом тяжелей вносить правки и сложно переместить блок в другое место.</p>
</div></section>

<section class="slide shout dark"><div>
  <h2>Как мне?...</h2>
</div></section>

<section class="slide"><div>
<!--
Что делать фрилансеру, который верстает небольшой сайт на Wordpress? Как ему черт возьми просто вывести текст из БД? Назначить класс каждому заголовку и абзацу? Но он же получает их из визивига!
-->
  <h2>Вывести текст из WYSIWYG?</h2>
    <figure>
      <blockquote>
        <p>Как назначаются стили для типографики? Не будешь же назначать каждому тегу какой-то класс?</p>
      </blockquote>
        <figcaption>Artur Kornakov, <a href="http://twitter.com/fliptheweb">@fliptheweb</a></figcaption>
    </figure>
</div></section>

<section class="slide"><div>
<h2>Добавить <code>.b-text</code> блоку родителю</h2>
   <p>И использовать каскад.</p>
    <pre>
<code><mark>.b-text</mark> h2 {}</code>
<code><mark>.b-text</mark> p {}</code>
<code><mark>.b-text</mark> img {}</code>
<code><mark>.b-text</mark> ul li {}</code>
    </pre>
    <p class="note">Конечно при <strong>большом</strong> желании можно настроить визивиг, тот же TinyMCE, чтоб он добавлял нужные имена классов в тегах из визивига.</p>
</div></section>

<section class="slide shout"><div>
<h2>Задавайте вопросы: <a href="https://ru.bem.info/forum/">ru.bem.info/forum</a></p>
<!-- https://docs.google.com/document/d/1KD9tNdArCv1U1NvFX7rYPvUdbpPGVkuPZ2723KW5p4Y/edit">https://docs.google.com/document/d/1KD9tNdArCv1U1NvFX7rYPvUdbpPGVkuPZ2723KW5p4Y/edit -->
</div></section>

<section class="slide"><div>
<h2>Пример переверстки по БЭМ (упрощенный)</h2>
<ul>
  <li><a href="http://net-craft.com/old">http://net-craft.com/old</a></li>
  <li><a href="http://net-craft.com/">http://net-craft.com/</a></li>
  <li><a href="http://net-craft.com/wp-content/themes/netcraft/dev/sass/main.scss">http://net-craft.com/wp-content/themes/netcraft/dev/sass/main.scss</a></li>
</ul>
</div></section>

<section class="slide shout dark"><div>
  <h2>Диалекты БЭМ</h2>
</div></section>

<section class="slide"><div>
<h2>Вот это вот всё на 5 минут:</h2>
<ul>
<li>Использование префиксов</li>
<li>Альтернативный синтаксис</li>
<li>Сокращённые модификаторы</li>
<li>JS-блоки</li>
</ul>
</div></section>

<section class="slide"><div>
<h2>Префиксы</h2>
<p>
  <code>b-</code>,
  <code>l-</code>,
  <code>g-</code>,
  <code>i-</code>,
  <code>h-</code>,
  <code>m-</code>,
  <code>js-</code>…
</p>
  <p>
    Придумывайте любые правила<br>
    Они нужны вам только для пространства имен.
  </p>
<!--
Яндекс отказался от них потому что им вначале нужно было создать своё пространство имен (т.к изначальный сайт был сверстан студией Лебедева и им нужно было отличать свой код от нового кода по БЭМ). Так они создали пространство имен и когда обнаружили, что весь код написан по БЭМ им префиксы оказались не нужны. Это просто совпало с тем, что пояилась сборка. Целенаправленно Яндекс сейчас не пишет префиксы (разве что они остались на старых проектах).
Ну вы то живете не в своём замкнутом мире, у вас есть и legacy-код и сторонний код, вам нужно своё пространство имен, чтоб избегать конфликтов.
-->
</div></section>

<section class="slide"><div>
  <h2>Альтернативный синтаксис и camelCase</h2>
  <p>Многим нравится зарубежный формат модификаторов, через „--“, он читабельней.</p>
<code>&lt;a class="block-name__element-name<mark>--state_active</mark>"&gt;</code>
</div></section>

<section class="slide"><div>
  <h2>Альтернативный синтаксис и camelCase</h2>
  <p>А через camelCase – ещё читабельней!</p>
<code>&lt;a class="<mark>blockName__elementName</mark>--state_active"&gt;</code>
</div></section>

<section class="slide shout"><div>
<h2>Сокращенные модификаторы</h2>
</div></section>

<section class="slide"><div>
<h2>Сокращенные модификаторы</h2>
  <p>
    Правильно писать так:<br>
    <code>.block-name__elem<mark>_key_value</mark></code>
  </p>
  <p>
    Или так:<br>
    <code>.blockName__elem<mark>--key_value</mark></code>
  </p>
</div></section>

<section class="slide"><div>
<h2>Сокращенные модификаторы</h2>
  <p>Но некоторых из тех, кто пишет код вручную, такие модификаторы бесят нечитабельностью кода:</p>
<code>&lt;div class="block-name <mark>block-name_key1_value1 block-name_key2_value2 block-name_key3_value3</mark>"&gt;</code>
</div></section>

<section class="slide"><div>
<h2>Сокращенные модификаторы</h2>
  <p>…и отсутствием дуракоустойчивости:</p>
<code>&lt;div class="<mark class="important">block-name_key1_value1</mark> some-another-block"&gt;</code>
</div></section>

<section class="slide"><div>
<h2>Сокращенные модификаторы</h2>
  <p>Им хочется так:</p>
<code>&lt;div class="block-name <mark>-key1_value1 -key2_value2 -key3_value3</mark>"&gt;</code>
</div></section>

<section class="slide"><div>
<h2>Сокращенные модификаторы</h2>
    <pre>
<code>&lt;div class="blockName__elem<mark>.-key_value</mark>"&gt;</code>
<code>.blockName {</code>
<code>  &__elem {</code>
<code>    &<mark>.-key_value {</mark></code>
<code><mark>    }</mark></code>
<code>  }</code>
<code>}</code>
    </pre>
</div></section>

<section class="slide cover" id="warning"><div>
  <img src="pictures/warning.png" alt="">
  <h2>
    Миксы!<br>
    Full BEM Stack!
  </h2>
  <style>
    #warning h2 {
      position: absolute;
      top: 300px;
      left: 150px;
      font-size: 70px;
      margin: 0;
      color: #000;
    }
  </style>
<!--
Модифкаторы без именеми блока родителя - создают проблемы про миксовании, когда сложные миксы и ты не сможешь определить к какому блоку у тебя относится микс. Довод против - что мы связываем их внутри CSS как .block { &.-type_val}
НО! Теряем миксы 2х блоков с модификаторами (непонятно - какой мод. к какому блоку относится).

Правильно писать полные модификаторы и Яндекс так рекомендует настоятельно. Вы тереяете возможность юзать full stack BEM - нельзя будет из js узнать "есть ли модификатор у такого блока"
-->
</div></section>

<section class="slide"><div>
<h2>Решением может быть запись модификаторов в столбик</h2>
<code>&lt;div class="block-name <mark>block-name_key1_value1 block-name_key2_value2 block-name_key3_value3</mark>"&gt;</code>
<pre><code>&lt;!-- VS --&gt;</code>
<code>&lt;div class="block-name</code>
<code>            <mark>block-name_key1_value1</mark></code>
<code>            <mark>block-name_key2_value2</mark></code>
<code>            <mark>block-name_key3_value3</mark>"&gt;</code>
</pre>
</div></section>

<section class="slide"><div>
<h2>JS-блоки</h2>
    <pre>
<code>$('<mark>.js-</mark>fancybox').fancybox();</code>
    </pre>
</div></section>

<section class="slide"><div>
  <h2>Вы можете создавать свои гайдлайны</h2>
  <p>БЭМ дает лишь базовый набор правил, конкретную реализацию и синтаксис вы выбираете сами.</p>
<ul>
  <li><a href="https://github.com/ideus-team/guidelines/blob/master/frontend/bem.md">https://github.com/ideus-team/guidelines/blob/master/frontend/bem.md</a></li>
  <li><a href="http://nano.sapegin.ru/all/opor-methodology">http://nano.sapegin.ru/all/opor-methodology</a></li>
</ul>
</div></section>

<section class="slide shout"><div>
  <h2>Это всё БЭМ</h2>
</div></section>

