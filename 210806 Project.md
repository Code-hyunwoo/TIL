# :boom: Project

---



### Media Quety

> 단말기의 유형과 어떤 특성이나 수치에 따라 웹 사이트나 앱의 스타일을 수정할 때 유용



#### Movie html page

```html
<nav class="navbar navbar-expand-lg navbar-dark bg-dark fixed-top py-0">
    <div class="container-fluid d-flex">
      <!-- logo -->
      <a class="navbar-brand" href="02_home.html">
        <img src="images/logo.png" alt="Logo Image" style="width: 200px;">
      </a>
      <div>
      <!-- button -->
      <button class="navbar-toggler"  type="button" data-bs-toggle="collapse" data-bs-target="#navbarNav" aria-controls="navbarNav" aria-expanded="false" aria-label="Toggle navigation">
        <span class="navbar-toggler-icon"></span>
      </button>

      <!-- nav list -->
      <div class="collapse navbar-collapse" id="navbarNav">
        <ul class="navbar-nav">
          <li class="nav-item">
            <a class="nav-link active" aria-current="page" href="02_home.html" class="text-decoration-none text-white fw-bold">Home</a>
          </li>
          <li class="nav-item">
            <a class="nav-link" href="03_community.html" class="text-decoration-none text-white">Community</a>
          </li>
          <li class="nav-item">
            <a class="nav-link" href="#" data-bs-toggle="modal" data-bs-target="#loginModal" class="text-decoration-none text-white">Login</a>
          </li>
        </ul>
         </div>
       </div>
    </div>
  </nav>
            <!-- modal(form) -->
            <div class="modal fade" id="loginModal" tabindex="-1" aria-labelledby="loginModalLabel" aria-hidden="true" >
              <div class="modal-dialog">
                <div class="modal-content">
                  <!-- Modal-header -->
                  <div class="modal-header">
                    <h5 class="modal-title fw-bold" id="loginModalLabel">Login</h5>
                    <button type="button" class="btn-close" data-bs-dismiss="modal" aria-label="Close"></button>
                  </div>
                  <!-- Modal-body -->
                  <div class="modal-body">
                    <form class="row g-3 d-flex flex-column">
                      <div>
                        <label for="inputUserName" class="form-label"> UserName</label>
                        <input type="email" class="form-control" placeholder="Enter your email">
                      </div>
                      <div>
                        <label for="inputPassword" class="form-label"> Password</label>
                        <input type="password" class="form-control" placeholder="Enter your password">
                      </div>
                      <div>
                        <div class="form-check">
                          <input class="form-check-input" type="checkbox" id="gridCheck">
                          <label class="form-check-label" for="gridCheck"> Check me out.</label>
                      </div>
                    </form>
                  </div>
                  <!-- Modal-Footer -->
                  <div class="modal-footer">
                    <button type="button" class="btn btn-secondary" data-bs-dismiss="modal">Close</button>
                    <button type="button" class="btn btn-primary">Submit</button>
                  </div>
                </div>
              </div>
            </div>
          </div>
  
  <!-- 02_home.html -->
  <header>
    <div id="carouselExampleControls" class="carousel slide" data-bs-ride="carousel">
      <div class="carousel-inner">
        <div class="carousel-item active">
          <img src="images/header1.jpg" class="d-block w-100" alt="...">
        </div>
        <div class="carousel-item">
          <img src="images/header2.jpg" class="d-block w-100" alt="...">
        </div>
        <div class="carousel-item">
          <img src="images/header3.jpg" class="d-block w-100" alt="...">
        </div>
      </div>
      <button class="carousel-control-prev" type="button" data-bs-target="#carouselExampleControls" data-bs-slide="prev">
        <span class="carousel-control-prev-icon" aria-hidden="true"></span>
        <span class="visually-hidden">Previous</span>
      </button>
      <button class="carousel-control-next" type="button" data-bs-target="#carouselExampleControls" data-bs-slide="next">
        <span class="carousel-control-next-icon" aria-hidden="true"></span>
        <span class="visually-hidden">Next</span>
      </button>
    </div>
  </header>

  <h1 class="text-center fw-bold my-4">Boxoffice</h1>

  <section>
    <div class="row row-cols-1 row-cols-sm-2 row-cols-md-3 g-2">
      <div class="col">
        <div class="card">
          <img src="images/movie1.jpg" class="card-img-top" alt="...">
          <div class="card-body">
            <h5 class="card-title">BREAKING BAD</h5>
            <p class="card-text">This is a longer card with supporting text below as a natural lead-in to additional content. This content is a little bit longer.</p>
          </div>
        </div>
      </div>
      <div class="col">
        <div class="card">
          <img src="images/movie2.jpg" class="card-img-top" alt="...">
          <div class="card-body">
            <h5 class="card-title">Kaafiron Ki Namaaz</h5>
            <p class="card-text">This is a longer card with supporting text below as a natural lead-in to additional content. This content is a little bit longer.</p>
          </div>
        </div>
      </div>
      <div class="col">
        <div class="card">
          <img src="images/movie3.jpg" class="card-img-top" alt="...">
          <div class="card-body">
            <h5 class="card-title">INSUROENT</h5>
            <p class="card-text">This is a longer card with supporting text below as a natural lead-in to additional content.</p>
          </div>
        </div>
      </div>
      <div class="col">
        <div class="card">
          <img src="images/movie4.jpg" class="card-img-top" alt="...">
          <div class="card-body">
            <h5 class="card-title">FIGHT CLUB</h5>
            <p class="card-text">This is a longer card with supporting text below as a natural lead-in to additional content. This content is a little bit longer.</p>
          </div>
        </div>
      </div>
      <div class="col">
        <div class="card">
          <img src="images/movie5.jpg" class="card-img-top" alt="...">
          <div class="card-body">
            <h5 class="card-title">LEON</h5>
            <p class="card-text">This is a longer card with supporting text below as a natural lead-in to additional content. This content is a little bit longer.</p>
          </div>
        </div>
      </div>
      <div class="col">
        <div class="card">
          <img src="images/movie6.jpg" class="card-img-top" alt="...">
          <div class="card-body">
            <h5 class="card-title">Joker</h5>
            <p class="card-text">This is a longer card with supporting text below as a natural lead-in to additional content. This content is a little bit longer.</p>
          </div>
        </div>
      </div>
    </div>
  </section>
 <!-- 03_community.html -->
    <div class="container">
      <div class="main row">
        <h1 class="text-center mt-5 mb-3 fw-bold"> Community </h1>

    <!-- Sidebar -->
    <aside class="col-12 col-lg-2">
        <ul class="list-group">
          <li class="list-group-item list-group-item-action active" aria-current="true"><a href="" class="text-decoration-none text-white text-center">Boxoffice</a></li>
          <li class="list-group-item list-group-item-action"><a href="" class="text-decoration-none text-center">Movies</a></li>
          <li class="list-group-item list-group-item-action"><a href="" class="text-decoration-none text-center">Genres</a></li>
          <li class="list-group-item list-group-item-action"><a href="" class="text-decoration-none text-center">Actors</a></li>
        </ul>
    </aside>

    <!-- Board -->
    <section class="col-lg-10 col-0">
      <div>
          <table class="table table-striped d-none d-lg-table">
            <thead>
              <tr class="table-dark text-white text-center">
                <th scope="col">영화제목</th>
                <th scope="col">글 제목</th>
                <th scope="col">작성자</th>
                <th scope="col">작성시간</th>
              </tr>
            </thead>
            <tbody class="text-center">
              <tr>
                <th scope="row">Movie1</th>
                <td>Funny</td>
                <td>Hyunwoo</td>
                <td>1 days ago</td>
              </tr>
              <tr>
                <th scope="row">Movie2</th>
                <td>Game</td>
                <td>Mark</td>
                <td>2 days ago</td>
              </tr>
              <tr>
                <th scope="row">Movie3</th>
                <td>HI</td>
                <td>Thornton</td>
                <td>3 days ago</td>
              </tr>
              <tr>
                <th scope="row">Movie4</th>
                <td>Hello</td>
                <td>Tom</td>
                <td>4 days ago</td>
              </tr>
              <tr>
                <th scope="row">Movie5</th>
                <td>Hello</td>
                <td>Jane</td>
                <td>5 days ago</td>
              </tr>
              <tr>
                <th scope="row">Movie6</th>
                <td>Hello</td>
                <td>Tom</td>
                <td>6 days ago</td>
              </tr>
            </tbody>
          </table>
          <div class="list-group d-lg-none">
            <a href="#" class="list-group-item list-group-item-action">
              <div class="d-flex w-100 justify-content-between">
                <h5 class="mb-1">Best Movie Ever</h5>
                <small>user</small>
              </div>
              <p class="mb-1">Great Movie title</p>
              <small>1 minutes ago</small>
            </a>
            <a href="#" class="list-group-item list-group-item-action">
              <div class="d-flex w-100 justify-content-between">
                <h5 class="mb-1">Movie Test1</h5>
                <small class="text-muted">user</small>
              </div>
              <p class="mb-1">Great Movie title</p>
              <small class="text-muted">10 minutes ago</small>
            </a>
            <a href="#" class="list-group-item list-group-item-action">
              <div class="d-flex w-100 justify-content-between">
                <h5 class="mb-1">Movie Test2</h5>
                <small class="text-muted">user</small>
              </div>
              <p class="mb-1">Great Movie title</p>
              <small class="text-muted">60 minutes ago</small>
            </a>
          </a>
          <a href="#" class="list-group-item list-group-item-action">
            <div class="d-flex w-100 justify-content-between">
              <h5 class="mb-1">Movie Test3</h5>
              <small class="text-muted">user</small>
            </div>
            <p class="mb-1">Great Movie title</p>
            <small class="text-muted">1 minutes ago</small>
          </a>
          </div>
        </div>
        <div>
          <nav aria-label="Page navigation example">
            <ul class="pagination justify-content-center align-items-center my-4">
              <li class="page-item"><a class="page-link" href="#">Previous</a></li>
              <li class="page-item"><a class="page-link" href="#">1</a></li>
              <li class="page-item"><a class="page-link" href="#">2</a></li>
              <li class="page-item"><a class="page-link" href="#">3</a></li>
              <li class="page-item"><a class="page-link" href="#">4</a></li>
              <li class="page-item"><a class="page-link" href="#">Next</a></li>
            </ul>
          </nav>
        </div>
      </section>
    </div>
    </div>
	<footer class="d-flex justify-content-center align-items-center fixed-bottom">
    <p class="mb-0 fw-bold"> Web-Bootstrap PJT, Created by 이현우</p>
  </footer>
```

