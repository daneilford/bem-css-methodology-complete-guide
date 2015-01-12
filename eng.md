#b_ BEM CSS methodology: The complete guide

__BEM prohibits put an elements in the elements!__  
You make the most typical error in BEM markup - writing a `block__element__element`.
You must create new blocks, rather than copying DOM-tree.

For example:  
Right HTML:

    <div class='block'>
        <div class='block__elem1'>
            <div class='block__elem2'></div>
        </div>
        <div class='block__elem3'></div>
    </div>

Right CSS:

    .block {}
    .block__elem1 {}
    .block__elem2 {}
    .block__elem3 {}

__If you need to make an element of an element, then you need to make a new block!__

WRONG:

    <div class='block'>
        <div class='block__elem1'>
            <div class='block__elem1__elem2'></div>
        </div>
    </div>
  
RIGHT:

    <div class='block1'>
        <div class='block2'>
            <div class='block2__elem'></div>
        </div>
    </div>


__Do not write strange names, putting the element name in the name of the block!__

WRONG:

    .block {}
    .blockelem1 {}
    .blockelem1__elem2 {}

Because you get a problem when you try to move the block:

    <div class='someblock'>
        <div class='blockelem1__elem2'></div>
    </div>

Nested html-elements is a DOM-tree.  
The names of the classes you write is a BEM-tree.  
Feel the difference!

DOM-tree:

    <ul>
      <li>
        <a>
          <span></span>
        </a>
      </li>
    </ul>

    .ul {}
    .ul > li {}
    .ul > li > a {}
    .ul > li > a > span {}


BEM-tree:

    <ul class="menu">
      <li class="menu__item">
        <a class="menu__link">
          <span class="menu__text"></span>
        </a>
      </li>
    </ul>

    .menu {}
    .menu__item {}
    .menu__link {}
    .menu__text {}


References: 
> "An element is a part of a block that performs a certain function. Elements are context-dependent: they only make sense in the context of the block they belong to."
> http://bem.info/method/definitions/

An element is a part of a block! Not element!
Read Vitaly Harisov, the author of BEM-methodology: https://twitter.com/harisov/status/403421669974618112
> Classname like "block__elem__elem___elem" means that coder didn't understand anything in BEM.
