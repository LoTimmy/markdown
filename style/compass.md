- http://rubyinstaller.org/downloads/

![](https://cdn.rubyinstaller.org/images/logo.png)


```console
shell> gem update --system
shell> gem install compass

shell> compass create
shell> compass create <myproject>
shell> compass version

shell> cd /path/to/project
shell> compass watch

shell> compass compile [path/to/project]
shell> compass watch [path/to/project]

shell> compass compile --production
```

---

```
css_dir = "stylesheets"
javascripts_dir = "javascripts"
output_style = :expanded
line_comments = 
sass_dir = "sass"
images_path = "images"
```
### :books: 參考網站：
- http://compass-style.org/help/documentation/configuration-reference/

---

```
<head>
  <link href="/stylesheets/screen.css" media="screen, projection" rel="stylesheet" type="text/css" />
  <link href="/stylesheets/print.css" media="print" rel="stylesheet" type="text/css" />
  <!--[if IE]>
      <link href="/stylesheets/ie.css" media="screen, projection" rel="stylesheet" type="text/css" />
  <![endif]-->
</head>
```


---

```
@import "compass/css3";
@import "compass/support"
@import "compass/layout"
```

```
.simple   { @include border-radius(4px, 4px); }
.compound { @include border-radius(2px 5px, 3px 6px); }
.crazy    { @include border-radius(1px 3px 5px 7px, 2px 4px 6px 8px)}
```

- http://compass-style.org/reference/compass/css3/border_radius/

---

### :books: 參考網站：
- http://compass-style.org/install/
