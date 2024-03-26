
``` html
<!DOCTYPE html>
<html>
<head>
<meta name="viewport" content="width=device-width, initial-scale=1">
<style>
body, html {
  height: 100%;
  margin: 0;
  font-family: Arial, Helvetica, sans-serif;
}

.hero-image {
  background-image: linear-gradient(rgba(0, 0, 0, 0.5), rgba(0, 0, 0, 0.5)), url("photographer.jpg");
  height: 50%;
  background-position: center;
  background-repeat: no-repeat;
  background-size: cover;
  position: relative;
}

.hero-text {
  text-align: center;
  position: absolute;
  top: 50%;
  left: 50%;
  transform: translate(-50%, -50%);
  color: white;
}

.hero-text button {
  border: none;
  outline: 0;
  display: inline-block;
  padding: 10px 25px;
  color: black;
  background-color: #ddd;
  text-align: center;
  cursor: pointer;
}

.hero-text button:hover {
  background-color: #555;
  color: white;
}
</style>
</head>
<body>

<div class="hero-image">
  <div class="hero-text">
    <h1 style="font-size:50px">I am John Doe</h1>
    <p>And I'm a Photographer</p>
    <button>Hire me</button>
  </div>
</div>

<p>Page Content..</p>

</body>
</html>

```
##### Flexbox Hero Image
``` css
body, html {
    height: 100%;
    margin: 0;
    font-family: Arial;
}
      
.hero-image {
    display: flex;
    flex-direction: column;
    background-image: linear-gradient(rgba(0, 0, 0, 0.5), rgba(0, 0, 0, 0.5)), url("https://images.pexels.com/photos/2234006/pexels-photo-2234006.jpeg?auto=compress&cs=tinysrgb&dpr=2&h=750&w=1260");
    min-height: 15em;
    height: 50%;
    align-self: center;
    background-repeat: no-repeat;
    background-size: cover;
    background-attachment: fixed;
    align-items: center;
    justify-content: center;
}
      
.hero-text {
    text-align: center;
    color: white;
}

.hero-header{
    align-self: center;
    font-size:50px;
}
```

``` html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <meta http-equiv="X-UA-Compatible" content="ie=edge">
    <link rel="stylesheet" href="flexHero.css">
    <title>Sliding Hero Image using Flexbox</title>
</head>
<body>
        <div class="hero-image">
                <div class="hero-text">
                  <h1 class="hero-header">bloom</h1>
                  <p>inner and outer self-care</p>
                </div>
        </div>
</body>
</html>
```