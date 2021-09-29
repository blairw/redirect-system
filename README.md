# redirect-system

## Introduction

This is a very simple code sample that helps you set up a redirect system on your web server.

There is an implementation in PHP (if you are running a LAMP system), and also an implementation in JavaScript (if you are only able to host static content, e.g., on a Content Distribution Network).

I, [Blair Wang](https://www.blair.wang/), release this work to the public domain. I consider this a very trivial code sample and do not seek to profit from it in any way. You may use this code sample for any purposes. This work is dedicated to the many students who have studied programming with me over the years, it has been a privilege teaching all of you.

## PHP implementation

```php
<?php
    if ($_GET["key"] == "Wikipedia-Cats")
    {
        header('Location: https://en.wikipedia.org/wiki/Cats');
    }
    else if ($_GET["key"] == "DigitalNomad-Map")
    {
        header('Location: https://blair.wang/nomadsmap/');
    }
    else
    {
        echo 'Resource not found.';
    }
?>
```

## JavaScript implementation

```html
<!DOCTYPE html>
<html>
<head>
<meta charset="UTF-8">
<title>Redirect System</title>
<style>
p {
	margin: 0 auto;
	text-align: center;
	padding-top: 1rem;
	font-family: "Helvetica Neue", "Helvetica", sans-serif;
}
</style>
<script>
function bodyDidLoad()
{
	var key = window.location.search.replace("?key=", "");

	if (key == "Wikipedia-Cats")
	{
		window.location.replace("https://en.wikipedia.org/wiki/Cats");
		document.getElementById("status").innerHTML = "Now loading <strong>" + key + "</strong>";
	}
	else
	if (key == "DigitalNomad-Map")
	{
		window.location.replace("https://blair.wang/nomadsmap/");
		document.getElementById("status").innerHTML = "Now loading <strong>" + key + "</strong>";
	}
	else
	{
		document.getElementById("status").innerHTML = "Resource not found.";
	}
}
</script>
</head>
<body onload="bodyDidLoad()">
<p id="status">
	Loading ...
</p>
</body>
</html>
```
