# CSS?

Cascading Style Sheets 는 콘텐츠의 글꼴, 색상, 크기 및 간격을 조정하거나 여러 열로 분할하거나 애니메이션 및 기타 장식 기능을 추가하는 웹 페이지 스타일 및 레이아웃에 사용됩니다.

### CSS 적용 방식

CSS 의 적용방식에는 총 3가지가 있습니다. External stylesheet, Internal Stylesheet, InlineStyleSheet 이 있습니다.

### External stylesheet

```html
<!DOCTYPE html>
<html>
  <head>
    <meta charset="utf-8">
    <title>My CSS experiment</title>
    <link rel="stylesheet" href="styles.css">
  </head>
  <body>
    <h1>Hello World!</h1>
    <p>This is my first CSS example</p>
  </body>
</html>
```

- 우리가 현재 HTML 에 원하는 CSS 를 적용하기 위해서는 <link> 의 href 을 통해서 파일시스템에서 참조할 파일을 찾아야 합니다.

### Internal stylesheet

```html
<!DOCTYPE html>
<html>
  <head>
    <meta charset="utf-8">
    <title>My CSS experiment</title>
    <style>
      h1 {
        color: blue;
        background-color: yellow;
        border: 1px solid black;
      }

      p {
        color: red;
      }
    </style>
  </head>
  <body>
    <h1>Hello World!</h1>
    <p>This is my first CSS example</p>
  </body>
</html>
```

- Intenal 은 내부에 <style> 태그로 속성을 넣어주어 사용합니다. 

### Inline styles

```html
<!DOCTYPE html>
<html>
  <head>
    <meta charset="utf-8">
    <title>My CSS experiment</title>
  </head>
  <body>
    <h1 style="color: blue;background-color: yellow;border: 1px solid black;">Hello World!</h1>
    <p style="color:red;">This is my first CSS example</p>
  </body>
</html>
```

- Inline styles 는 해당 속성에 넣어주는 방법인데, 재사용성도 좋지않아서 안티패턴중 하나입니다.

