Using npm:
```shell
$ npm i fgn-breadcrumbs
```

In Pug Template:
```js

- let Data = [{ 
  name: "Como Solicitar", 
  href: "#" 
}, { 
  name: "Cartão de crédito", 
  href: "#" 
}, { 
  name: "Nubank", 
  href: "#" 
}]

+breadcrumb(Data)
```

Mixin Doc:
```js
- let BreadcrumbList = 'http://schema.org/BreadcrumbList'
- let ListItem = 'http://schema.org/ListItem'

/** return breadcrumb component
 ** @param {object} props - object w/ {name: "", href: ""}
 **/
mixin breadcrumb(props)
  ol.c-breadcrumb.o-list(itemscope itemtype=BreadcrumbList)
    each prop, index in props
      - let position = index

      li.c-breadcrumb__item(itemprop="itemListElement" itemscope itemtype=ListItem)
        a.c-breadcrumb__anchor(itemprop="item" href=prop.href)
          span(itemprop="name")=prop.name
          meta(itemprop="position" content=(++position))
```