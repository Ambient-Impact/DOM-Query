DOM Query Component
=====================

The purpose of this component is to provide a jQuery-like interface for crawling XML and HTML documents.

Example use :

```php
$H = \PowerTools\DOM_Query::loadHTML(file_get_contents($path));

$data = array(
   'meta' => json_decode(file_get_contents('meta.json')),
   'menu' => Menu::build(),
   'content' => Page::content()
);

$H->select('head')
  ->append(
     $H->select('<link rel="shortcut icon" type="image/x-icon">')
       ->attr(array('href' => $data['meta']->favicon)))
  ->append(
     $H->select('<title />')
       ->text($data['meta']->title))
  ->append(
     $H->select('<meta  name="description" />')
       ->attr(array('content' => $data['meta']->description)))
  ->append(
     $H->select('<meta />')
       ->attr(array('charset' => $data['meta']->charset)))
  ->append(
     $H->select('<meta  name="viewport" />')
       ->attr(array('content' => $data['meta']->viewport)));

$H->select('body')
  ->append(
     $H->select('<div class="menu" />')
       ->text($data['menu']))
  ->append(
     $H->select('<div class="content" />')
       ->text($data['content']));

echo $H;
```

## Author

| [![twitter/johnslegers](https://en.gravatar.com/avatar/bf4cc94221382810233575862875e687?s=70)](http://twitter.com/johnslegers "Follow @johnslegers on Twitter") |
|---|
| [John slegers](http://www.johnslegers.com/) |
