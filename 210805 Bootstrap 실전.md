# :boom:Bootstrap 실전

---



## Workshop

```html
<!DOCTYPE html>
<html lang="ko">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <link rel="stylesheet" href="style.css">
  <title>Document</title>
  <link href="https://cdn.jsdelivr.net/npm/bootstrap@5.1.0/dist/css/bootstrap.min.css" rel="stylesheet" integrity="sha384-KyZXEAg3QhqLMpG8r+8fhAXLRk2vvoC2f3B09zVXn8CA5QIVfZOJ3BCsw2P0p/We" crossorigin="anonymous">
</head>
<body>
  <!-- 1. Nav -->
  <nav class="navbar navbar-dark bg-dark sticky-top pt-0">
    <a href="#">
      <img src="images/logo.png" alt="Logo Image">
    </a>
    <ul class="d-flex list-unstyled mb-0">
      <li class="px-3"><a href="#" class="text-decoration-none text-white fw-bold">Home</a></li>
      <li class="px-3"><a href="#" class="text-decoration-none text-white fw-bold">Community</a></li>
      <li class="px-3"><a href="#" class="text-decoration-none text-white fw-bold">Login</a></li>
    </ul>
  </nav>

  <!-- 2. Header -->
  <header class="display-2 text-white fw-bold d-flex justify-content-center align-items-center flex-column">
      <div>Cinema</div>
      <div>Community</div>
      <button type="button" class="btn btn-primary btn-lg mt-5">Let's go</button>
  </header>

  <!-- 3. Section -->
  <section class="mt-4">
    <h2 class="text-center mb-4">Used Skills</h2>
    <article class="d-flex justify-content-evenly align-items-center text-center fw-bold">
      <div>
        <img src="images/web.png" alt="Web Image">
        <p>Web</p>
      </div>
      <div>
        <img src="images/html5.png" alt="HTML5 Image">
        <p>HTML5</p>
      </div>
      <div>
        <img src="images/css3.png" alt="CSS3 Image">
        <p>CSS3</p>
      </div>
    </article>
  </section>

  <!-- 4. Footer -->
  <footer class="d-flex justify-content-center align-items-center fixed-bottom bg-primary">
    <p class="mb-0 text-white">HTML & CSS project. Created by 이현우</p>
  </footer>
  <script src="https://cdn.jsdelivr.net/npm/bootstrap@5.1.0/dist/js/bootstrap.bundle.min.js" integrity="sha384-U1DAWAznBHeqEIlVSCgzq+c9gqGAJn5c/t99JyeKa9xxaYpSvHU5awsuZVVFIhvj" crossorigin="anonymous"></script>
</body>
</html>

```

​																

## Shop

```html
    <!-- section -->
    <section>
      <img src="images/main.png" alt="main" class="img-fluid mt-5">
    </section>

    <!-- article -->
    <article>
      <h4 class="text-center fw-bold my-5">Our New Products</h4>
      <div class="row row-cols-1 row-cols-md-2 row-cols-lg-4 g-4 text-center">
        <div class="col">
          <div class="card">
            <img src="images/buds.jpg" class="card-img-top" alt="...">
            <div class="card-body">
              <h5 class="card-title">Buds</h5>
              <p class="card-text">179,000</p>
            </div>
          </div>
        </div>
        <div class="col">
          <div class="card">
            <img src="images/buds.jpg" class="card-img-top" alt="...">
            <div class="card-body">
              <h5 class="card-title">Buds</h5>
              <p class="card-text">179,000</p>
            </div>
          </div>
        </div>
        <div class="col">
          <div class="card">
            <img src="images/buds.jpg" class="card-img-top" alt="...">
            <div class="card-body">
              <h5 class="card-title">Buds</h5>
              <p class="card-text">179,000</p>
            </div>
          </div>
        </div>
        <div class="col">
          <div class="card">
            <img src="images/buds.jpg" class="card-img-top" alt="...">
            <div class="card-body">
              <h5 class="card-title">Buds</h5>
              <p class="card-text">179,000</p>
            </div>
          </div>
        </div>
      </div>
    </article>

    <!-- footer -->
    <footer class="d-flex justify-content-center my-5">
      <a href="https://www.insatgram.com/" class="mx-2">
        <img src="images/instagram.png" alt="" style="width:50px;">
      </a>
      <a href="https://www.facebook.com/" class="mx-2">
        <img src="images/facebook.png" alt="" style="width:50px;">
      </a>
      <a href="https://www.twitter.com/" class="mx-2">
        <img src="images/twitter.png" alt="" style="width:50px;">
      </a>
    </footer>
```

​																										