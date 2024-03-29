---
layout: post
title: WebRookie_sparta - week03
date: 2024-03-29
category: WebRookie_sparta
---

## index.html
```html
<!DOCTYPE html>
<html lang="en">

<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>나만의 추억앨범</title>
    <!-- 부트스트랩 -->
    <link href="https://cdn.jsdelivr.net/npm/bootstrap@5.0.2/dist/css/bootstrap.min.css" rel="stylesheet"
        integrity="sha384-EVSTQN3/azprG1Anm3QDgpJLIm9Nao0Yz1ztcQTwFspd3yD65VohhpuuCOmLASjC" crossorigin="anonymous">

    <script src="https://ajax.googleapis.com/ajax/libs/jquery/3.5.1/jquery.min.js"></script>

    <style>
        @import url('https://fonts.googleapis.com/css2?family=Nanum+Pen+Script&display=swap');

        * {
            font-family: "Nanum Pen Script", cursive;
            font-size: large;
        }

        .mytitle {
            height: 250px;
            background-image: url('https://images.unsplash.com/photo-1511992243105-2992b3fd0410?ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D&auto=format&fit=crop&w=1470&q=80');
            background-position: center;
            background-size: cover;

            color: white;

            /* 아이템 중앙 정렬. 
            flex-direction은 아이템을 가로로 배열할지, 세로로 배열할지. */
            display: flex;
            flex-direction: column;
            align-items: center;
            justify-content: center;
        }

        /* mytitle 내의 버튼을 꾸민다. */
        .mytitle>button {
            width: 150px;
            height: 50px;
            background-color: transparent;

            color: white;
            border: 1px solid white;
            border-radius: 5px;

            margin-top: 20px;
        }

        .mypostingbox {
            width: 500px;
            margin: 30px auto 0px auto;
            padding: 20px;

            /* 그림자 넣기 */
            box-shadow: 0px 0px 3px 0px blue;
            border-radius: 5px;
        }

        .mybtn {
            display: flex;
            flex-direction: row;
            align-items: center;
            justify-content: center;
        }

        .mybtn>button {
            margin-right: 5px;
        }

        .mycards {
            width: 1200px;
            margin: 30px auto 0px auto;
        }
    </style>
    <script>
        function openclose() {
            // alert("안녕");
            $('#mypostingbox').toggle();
        }

        function makecard() {
            // alert("버튼과 함수가 연결됐는지 확인")          

            // $('#아이디').val(): 아이디가 가리키는 부분에 저장된 값 불러오기.
            let image = $('#image').val()
            let title = $('#title').val()
            let content = $('#content').val()
            let date = $('#date').val()

            // 백틱. temp_html은 문자열.
            let temp_html= `
            <div class="col">
                <div class="card h-100">
                    <img src="${image}"
                        class="card-img-top" alt="...">
                    <div class="card-body">
                        <h5 class="card-title">${title}</h5>
                        <p class="card-text">${content}</p>
                    </div>
                    <div class="card-footer">
                        <small class="text-body-secondary">${date}</small>
                    </div>
                </div>
            </div>`

            $('#card').append(temp_html);
        }
    </script>
</head>

<body>
    <div class="mytitle">
        <h1>나만의 추억앨범</h1>
        <button onclick="openclose()">추억 저장하기</button>
    </div>
    <div class="mypostingbox" id="mypostingbox">
        <div class="form-floating mb-3">
            <input type="email" class="form-control" id="image" placeholder="앨범 이미지">
            <label for="floatingInput">앨범 이미지</label>
        </div>
        <div class="form-floating mb-3">
            <input type="email" class="form-control" id="title" placeholder="앨범 제목">
            <label for="floatingInput">앨범 제목</label>
        </div>
        <div class="form-floating mb-3">
            <input type="email" class="form-control" id="content" placeholder="앨범 내용">
            <label for="floatingInput">앨범 내용</label>
        </div>
        <div class="form-floating mb-3">
            <input type="email" class="form-control" id="date" placeholder="앨범 날짜">
            <label for="floatingInput">앨범 날짜</label>
        </div>
        <div class="mybtn">
            <button type="button" class="btn btn-primary" onclick="makecard()">기록하기</button>
            <button type="button" class="btn btn-outline-primary">닫기</button>
        </div>
    </div>
    <div class="mycards">
        <div id="card" class="row row-cols-1 row-cols-md-4 g-4">
            <div class="col">
                <div class="card h-100">
                    <img src="https://images.unsplash.com/photo-1446768500601-ac47e5ec3719?ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D&auto=format&fit=crop&w=1446&q=80"
                        class="card-img-top" alt="...">
                    <div class="card-body">
                        <h5 class="card-title">앨범 제목</h5>
                        <p class="card-text">앨범 내용</p>
                    </div>
                    <div class="card-footer">
                        <small class="text-body-secondary">앨범 날짜</small>
                    </div>
                </div>
            </div>
            <div class="col">
                <div class="card h-100">
                    <img src="https://images.unsplash.com/photo-1446768500601-ac47e5ec3719?ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D&auto=format&fit=crop&w=1446&q=80"
                        class="card-img-top" alt="...">
                    <div class="card-body">
                        <h5 class="card-title">앨범 제목</h5>
                        <p class="card-text">앨범 내용</p>
                    </div>
                    <div class="card-footer">
                        <small class="text-body-secondary">앨범 날짜</small>
                    </div>
                </div>
            </div>
            <div class="col">
                <div class="card h-100">
                    <img src="https://images.unsplash.com/photo-1446768500601-ac47e5ec3719?ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D&auto=format&fit=crop&w=1446&q=80"
                        class="card-img-top" alt="...">
                    <div class="card-body">
                        <h5 class="card-title">앨범 제목</h5>
                        <p class="card-text">앨범 내용</p>
                    </div>
                    <div class="card-footer">
                        <small class="text-body-secondary">앨범 날짜</small>
                    </div>
                </div>
            </div>
            <div class="col">
                <div class="card h-100">
                    <img src="https://images.unsplash.com/photo-1446768500601-ac47e5ec3719?ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D&auto=format&fit=crop&w=1446&q=80"
                        class="card-img-top" alt="...">
                    <div class="card-body">
                        <h5 class="card-title">앨범 제목</h5>
                        <p class="card-text">앨범 내용</p>
                    </div>
                    <div class="card-footer">
                        <small class="text-body-secondary">앨범 날짜</small>
                    </div>
                </div>
            </div>
        </div>

    </div>
</body>

</html>
```
### <ins>Result</ins>
![toggle](https://github.com/jkhan94/assests_images_issue/assets/163835909/17ae5236-6dc2-42f2-a2fd-26f2139c0d02){: width="60%"}
![makeCard](https://github.com/jkhan94/assests_images_issue/assets/163835909/7351f89f-a7cd-4deb-be1b-1b7cf07a6058){: width="60%"}


## index.html
```html
<!DOCTYPE html>
<html lang="en">

<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>스파르타플릭스</title>

    <link href="https://cdn.jsdelivr.net/npm/bootstrap@5.0.2/dist/css/bootstrap.min.css" rel="stylesheet"
        integrity="sha384-EVSTQN3/azprG1Anm3QDgpJLIm9Nao0Yz1ztcQTwFspd3yD65VohhpuuCOmLASjC" crossorigin="anonymous">
    <script src="https://ajax.googleapis.com/ajax/libs/jquery/3.5.1/jquery.min.js"></script>

    <style>
        @import url('https://fonts.googleapis.com/css2?family=Gowun+Dodum&display=swap');

        * {
            font-family: 'Gowun Dodum', sans-serif;
        }

        .main {
            color: white;

            background-image: url('https://occ-0-1123-1217.1.nflxso.net/dnm/api/v6/6AYY37jfdO6hpXcMjf9Yu5cnmO0/AAAABeIfo7VL_VDyKnljV66IkR-4XLb6xpZqhpLSo3JUtbivnEW4s60PD27muH1mdaANM_8rGpgbm6L2oDgA_iELHZLZ2IQjG5lvp5d2.jpg?r=e6e.jpg');
            background-position: center;
            background-size: cover;
        }

        body {
            background-color: black;
        }

        .mypostingbox {
            width: 500px;
            margin: 20px auto 20px auto;

            border: 1px solid white;
            padding: 20px;
            border-radius: 5px;
        }

        .form-floating>input {
            background-color: transparent;
            color: white;
        }

        .form-floating>label {
            color: white;
        }

        .input-group>label {
            background-color: transparent;
            color: white;
        }

        .mypostingbox>button {
            width: 100%;
        }

        .mycards {
            width: 1200px;
            /* background-color: green; */
            margin: 20px auto 20px auto;
        }
    </style>

    <script>
        function openClose() {
            $('#mypostingbox').toggle();
        }

        function makeCard() {
            let image = $('#image').val();
            let title = $('#title').val();
            // select칸 옵션의 value를 받아옴
            let star = $('#star').val();
            let comment = $('#comment').val();

            let html_temp = `<div class="col">
                <div class="card h-100">
                    <img src="${image}"
                        class="card-img-top" alt="...">
                    <div class="card-body">
                        <h5 class="card-title">${title}</h5>
                        <p class="card-text">${star}</p>
                        <p class="card-text">${comment}</p>
                    </div>
                </div>
            </div>`
            $('#cards').append(html_temp)
        }
    </script>
</head>

<body>
    <header class="p-3 text-bg-dark">
        <div class="container">
            <div class="d-flex flex-wrap align-items-center justify-content-center justify-content-lg-start">
                <a href="/" class="d-flex align-items-center mb-2 mb-lg-0 text-white text-decoration-none">
                    <svg class="bi me-2" width="40" height="32" role="img" aria-label="Bootstrap">
                        <use xlink:href="#bootstrap"></use>
                    </svg>
                </a>

                <ul class="nav col-12 col-lg-auto me-lg-auto mb-2 justify-content-center mb-md-0">
                    <li><a href="#" class="nav-link px-2 text-danger">spartaflix</a></li>
                    <li><a href="#" class="nav-link px-2 text-white">홈</a></li>
                    <li><a href="#" class="nav-link px-2 text-white">시리즈</a></li>
                    <li><a href="#" class="nav-link px-2 text-white">영화</a></li>
                    <li><a href="#" class="nav-link px-2 text-white">내가 찜한 콘텐츠</a></li>
                </ul>

                <form class="col-12 col-lg-auto mb-3 mb-lg-0 me-lg-3" role="search">
                    <input type="search" class="form-control form-control-dark text-bg-dark" placeholder="Search..."
                        aria-label="Search">
                </form>

                <div class="text-end">
                    <button type="button" class="btn btn-outline-light me-2">Login</button>
                    <button type="button" class="btn btn-danger">Sign-up</button>
                </div>
            </div>
        </div>
    </header>

    <div class="main">
        <div class="container-fluid py-5">
            <h1 class="display-5 fw-bold">킹덤</h1>
            <p class="col-md-8 fs-4">병든 왕을 둘러싸고 흉흉한 소문이 떠돈다. 어둠에 뒤덮인 조선, 기이한 역병에 신음하는 산하. 정체 모를 악에 맞서 백성을 구원할 희망은 오직
                세자뿐이다.</p>
            <button type="button" class="btn btn-outline-light" onclick="openClose()">영화 기록하기</button>
            <button type="button" class="btn btn-outline-light">상세정보</button>
        </div>
    </div>

    <div id="mypostingbox" class="mypostingbox">
        <div class="form-floating mb-3">
            <input type="email" class="form-control" id="image" placeholder="영화 이미지 주소">
            <label for="floatingInput">영화 이미지 주소</label>
        </div>
        <div class="form-floating mb-3">
            <input type="email" class="form-control" id="title" placeholder="영화 제목">
            <label for="floatingInput">영화 제목</label>
        </div>
        <div class="input-group mb-3">
            <label class="input-group-text" for="inputGroupSelect01">별점</label>
            <select class="form-select" id="star">
                <option selected>별점선택</option>
                <option value="⭐">⭐</option>
                <option value="⭐⭐">⭐⭐</option>
                <option value="⭐⭐⭐">⭐⭐⭐</option>
                <option value="⭐⭐⭐⭐">⭐⭐⭐⭐</option>
                <option value="⭐⭐⭐⭐⭐">⭐⭐⭐⭐⭐</option>
            </select>
        </div>
        <div class="form-floating mb-3">
            <input type="email" class="form-control" id="comment" placeholder="추천 이유">
            <label for="floatingInput">추천 이유</label>
        </div>
        <button type="button" class="btn btn-danger" onclick="makeCard()">기록하기</button>
    </div>

    <div class="mycards">
        <div id="cards" class="row row-cols-1 row-cols-md-4 g-4">
            <div class="col">
                <div class="card h-100">
                    <img src="https://movie-phinf.pstatic.net/20210728_221/1627440327667GyoYj_JPEG/movie_image.jpg"
                        class="card-img-top" alt="...">
                    <div class="card-body">
                        <h5 class="card-title">영화 제목</h5>
                        <p class="card-text">⭐⭐⭐</p>
                        <p class="card-text">영화 코멘트</p>
                    </div>
                </div>
            </div>
            <div class="col">
                <div class="card h-100">
                    <img src="https://movie-phinf.pstatic.net/20210728_221/1627440327667GyoYj_JPEG/movie_image.jpg"
                        class="card-img-top" alt="...">
                    <div class="card-body">
                        <h5 class="card-title">영화 제목</h5>
                        <p class="card-text">⭐⭐⭐</p>
                        <p class="card-text">영화 코멘트</p>
                    </div>
                </div>
            </div>
            <div class="col">
                <div class="card h-100">
                    <img src="https://movie-phinf.pstatic.net/20210728_221/1627440327667GyoYj_JPEG/movie_image.jpg"
                        class="card-img-top" alt="...">
                    <div class="card-body">
                        <h5 class="card-title">영화 제목</h5>
                        <p class="card-text">⭐⭐⭐</p>
                        <p class="card-text">영화 코멘트</p>
                    </div>
                </div>
            </div>
            <div class="col">
                <div class="card h-100">
                    <img src="https://movie-phinf.pstatic.net/20210728_221/1627440327667GyoYj_JPEG/movie_image.jpg"
                        class="card-img-top" alt="...">
                    <div class="card-body">
                        <h5 class="card-title">영화 제목</h5>
                        <p class="card-text">⭐⭐⭐</p>
                        <p class="card-text">영화 코멘트</p>
                    </div>
                </div>
            </div>
        </div>
    </div>
</body>

</html>
```
### <ins>Result</ins>
![toggle2](https://github.com/jkhan94/assests_images_issue/assets/163835909/d744177d-7986-48bb-b263-227a5c93b050){: width="60%"}
![makeCard2](https://github.com/jkhan94/assests_images_issue/assets/163835909/0d61888a-872c-4bde-a4da-b0360b260ea2){: width="60%"}

___


## prac_fetch.html
```html
<!doctype html>
<html lang="ko">

<head>
    <meta charset="UTF-8">
    <title>Fetch 시작하기</title>
    <script src="https://ajax.googleapis.com/ajax/libs/jquery/3.5.1/jquery.min.js"></script>
    <script>
        function hey() {
            // alert('연결완료');

            let url = 'http://spartacodingclub.shop/sparta_api/seoulair'
            fetch(url).then(res => res.json()).then(data => {
                // 전체 데이터 출력      
                console.log(data)

                // 첫번째 데이터만 출력
                console.log(data['RealtimeCityAir']['row'][0])

                // 반복문 사용해서 요소를 개별적으로 출력
                let rows = data['RealtimeCityAir']['row']
                rows.forEach((a) => {
                    // 미세먼지 데이터 리스트의 길이만큼 반복해서 하나씩 개발자 도구에서 보기
                    console.log(a)
                })

                rows.forEach((a) => {
                    // 구 이름과 미세먼지만 출력
                    let gu_name = a['MSRSTE_NM']
                    let gu_mise = a['IDEX_MVL']
                    console.log(gu_name, gu_mise)
                })
            })
        }
    </script>
</head>

<body>
    <button onclick="hey()">fetch 연습!</button>
</body>

</html>
```
### <ins>Result</ins>
![a](https://github.com/jkhan94/assests_images_issue/assets/163835909/a6a3f403-9856-401f-8adb-e22c53fa4ee7)
<br>
![indiv](https://github.com/jkhan94/assests_images_issue/assets/163835909/129fd7ac-0bb7-40b5-9f92-e69c8c9a059b)
<br>
![2items](https://github.com/jkhan94/assests_images_issue/assets/163835909/27533bbb-e2c4-4055-b04d-8299bde1133a)
<br><br>


## prac_fetch2.html
```html
<!doctype html>
<html lang="ko">

<head>
    <meta charset="UTF-8">
    <title>미세먼지 API로Fetch 연습하고 가기!</title>

    <script src="https://ajax.googleapis.com/ajax/libs/jquery/3.5.1/jquery.min.js"></script>

    <style type="text/css">
        div.question-box {
            margin: 10px 0 20px 0;
        }

        .bad {
            color: red;
        }
    </style>

    <script>
        function q1() {
            // alert('연결완료');

            let url = 'http://spartacodingclub.shop/sparta_api/seoulair'

            // 기존에 받은 데이터를 초기화
            $('#names-q1').empty()

            fetch(url).then(res => res.json()).then(data => {
                let rows = data['RealtimeCityAir']['row']
                rows.forEach((a) => {
                    // 구 이름과 미세먼지만 출력
                    let gu_name = a['MSRSTE_NM']
                    let gu_mise = a['IDEX_MVL']

                    let temp_html = ``;
                    if (gu_mise > 40) {
                        temp_html = `<li class="bad">${gu_name} : ${gu_mise}</li>`
                    } else {
                        temp_html = `<li>${gu_name} : ${gu_mise}</li>`
                    }
                    $('#names-q1').append(temp_html)
                })
            })
        }
    </script>

</head>

<body>
    <h1>Fetch 연습하자!</h1>

    <hr />

    <div class="question-box">
        <h2>1. 서울시 OpenAPI(실시간 미세먼지 상태)를 이용하기</h2>
        <p>모든 구의 미세먼지를 표기해주세요</p>
        <p>업데이트 버튼을 누를 때마다 지웠다 새로 씌여져야 합니다.</p>
        <button onclick="q1()">업데이트</button>
        <ul id="names-q1">
        </ul>
    </div>
</body>

</html>
```
### <ins>Result</ins>
![original](https://github.com/jkhan94/assests_images_issue/assets/163835909/8a48161c-4fa8-42c4-9da8-e50f5220e3bf){: width="60%"}
&ensp;
![fetch](https://github.com/jkhan94/assests_images_issue/assets/163835909/5d6364da-8ebd-4e48-9afe-cab9464fc2ca){: width="60%"}


## index.html
```html
<!DOCTYPE html>
<html lang="en">

<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>나만의 추억앨범</title>
    <!-- 부트스트랩 -->
    <link href="https://cdn.jsdelivr.net/npm/bootstrap@5.0.2/dist/css/bootstrap.min.css" rel="stylesheet"
        integrity="sha384-EVSTQN3/azprG1Anm3QDgpJLIm9Nao0Yz1ztcQTwFspd3yD65VohhpuuCOmLASjC" crossorigin="anonymous">

    <script src="https://ajax.googleapis.com/ajax/libs/jquery/3.5.1/jquery.min.js"></script>

    <style>
        @import url('https://fonts.googleapis.com/css2?family=Nanum+Pen+Script&display=swap');

        * {
            font-family: "Nanum Pen Script", cursive;
            font-size: large;
        }

        .mytitle {
            height: 250px;
            background-image: url('https://images.unsplash.com/photo-1511992243105-2992b3fd0410?ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D&auto=format&fit=crop&w=1470&q=80');
            background-position: center;
            background-size: cover;

            color: white;

            /* 아이템 중앙 정렬. 
            flex-direction은 아이템을 가로로 배열할지, 세로로 배열할지. */
            display: flex;
            flex-direction: column;
            align-items: center;
            justify-content: center;
        }

        /* mytitle 내의 버튼을 꾸민다. */
        .mytitle>button {
            width: 150px;
            height: 50px;
            background-color: transparent;

            color: white;
            border: 1px solid white;
            border-radius: 5px;

            margin-top: 20px;
        }

        .mypostingbox {
            width: 500px;
            margin: 30px auto 0px auto;
            padding: 20px;

            /* 그림자 넣기 */
            box-shadow: 0px 0px 3px 0px blue;
            border-radius: 5px;
        }

        .mybtn {
            display: flex;
            flex-direction: row;
            align-items: center;
            justify-content: center;
        }

        .mybtn>button {
            margin-right: 5px;
        }

        .mycards {
            width: 1200px;
            margin: 30px auto 0px auto;
        }
    </style>
    <script>
        $(document).ready(function () {
            let url = "http://spartacodingclub.shop/sparta_api/seoulair";
            fetch(url).then(res => res.json()).then(data => {
                let mise = data['RealtimeCityAir']['row'][0]['IDEX_NM']
                $('#msg').text(mise)
            })
        })

        function openclose() {
            // alert("안녕");
            $('#mypostingbox').toggle();
        }

        function makecard() {
            // alert("버튼과 함수가 연결됐는지 확인")          

            // $('#아이디').val(): 아이디가 가리키는 부분에 저장된 값 불러오기.
            let image = $('#image').val()
            let title = $('#title').val()
            let content = $('#content').val()
            let date = $('#date').val()

            // 백틱. temp_html은 문자열.
            let temp_html = `
            <div class="col">
                <div class="card h-100">
                    <img src="${image}"
                        class="card-img-top" alt="...">
                    <div class="card-body">
                        <h5 class="card-title">${title}</h5>
                        <p class="card-text">${content}</p>
                    </div>
                    <div class="card-footer">
                        <small class="text-body-secondary">${date}</small>
                    </div>
                </div>
            </div>`

            $('#card').append(temp_html);
        }
    </script>
</head>

<body>
    <div class="mytitle">
        <h1>나만의 추억앨범</h1>
        <!-- span: p 태그 내 글자 묶음. -->
        <p>현재 서울의 미세먼지 : <span id="msg"></span></p>
        <button onclick="openclose()">추억 저장하기</button>
    </div>
    <div class="mypostingbox" id="mypostingbox">
        <div class="form-floating mb-3">
            <input type="email" class="form-control" id="image" placeholder="앨범 이미지">
            <label for="floatingInput">앨범 이미지</label>
        </div>
        <div class="form-floating mb-3">
            <input type="email" class="form-control" id="title" placeholder="앨범 제목">
            <label for="floatingInput">앨범 제목</label>
        </div>
        <div class="form-floating mb-3">
            <input type="email" class="form-control" id="content" placeholder="앨범 내용">
            <label for="floatingInput">앨범 내용</label>
        </div>
        <div class="form-floating mb-3">
            <input type="email" class="form-control" id="date" placeholder="앨범 날짜">
            <label for="floatingInput">앨범 날짜</label>
        </div>
        <div class="mybtn">
            <button type="button" class="btn btn-primary" onclick="makecard()">기록하기</button>
            <button type="button" class="btn btn-outline-primary">닫기</button>
        </div>
    </div>
    <div class="mycards">
        <div id="card" class="row row-cols-1 row-cols-md-4 g-4">
            <div class="col">
                <div class="card h-100">
                    <img src="https://images.unsplash.com/photo-1446768500601-ac47e5ec3719?ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D&auto=format&fit=crop&w=1446&q=80"
                        class="card-img-top" alt="...">
                    <div class="card-body">
                        <h5 class="card-title">앨범 제목</h5>
                        <p class="card-text">앨범 내용</p>
                    </div>
                    <div class="card-footer">
                        <small class="text-body-secondary">앨범 날짜</small>
                    </div>
                </div>
            </div>
            <div class="col">
                <div class="card h-100">
                    <img src="https://images.unsplash.com/photo-1446768500601-ac47e5ec3719?ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D&auto=format&fit=crop&w=1446&q=80"
                        class="card-img-top" alt="...">
                    <div class="card-body">
                        <h5 class="card-title">앨범 제목</h5>
                        <p class="card-text">앨범 내용</p>
                    </div>
                    <div class="card-footer">
                        <small class="text-body-secondary">앨범 날짜</small>
                    </div>
                </div>
            </div>
            <div class="col">
                <div class="card h-100">
                    <img src="https://images.unsplash.com/photo-1446768500601-ac47e5ec3719?ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D&auto=format&fit=crop&w=1446&q=80"
                        class="card-img-top" alt="...">
                    <div class="card-body">
                        <h5 class="card-title">앨범 제목</h5>
                        <p class="card-text">앨범 내용</p>
                    </div>
                    <div class="card-footer">
                        <small class="text-body-secondary">앨범 날짜</small>
                    </div>
                </div>
            </div>
            <div class="col">
                <div class="card h-100">
                    <img src="https://images.unsplash.com/photo-1446768500601-ac47e5ec3719?ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D&auto=format&fit=crop&w=1446&q=80"
                        class="card-img-top" alt="...">
                    <div class="card-body">
                        <h5 class="card-title">앨범 제목</h5>
                        <p class="card-text">앨범 내용</p>
                    </div>
                    <div class="card-footer">
                        <small class="text-body-secondary">앨범 날짜</small>
                    </div>
                </div>
            </div>
        </div>

    </div>
</body>

</html>
```
### <ins>Result</ins>
![album](https://github.com/jkhan94/assests_images_issue/assets/163835909/13ca03c8-78fe-4573-a246-b98ff6427f37){: width="60%"}
<br><br>

## index.html
```html
<!DOCTYPE html>
<html lang="en">

<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>스파르타플릭스</title>

    <link href="https://cdn.jsdelivr.net/npm/bootstrap@5.0.2/dist/css/bootstrap.min.css" rel="stylesheet"
        integrity="sha384-EVSTQN3/azprG1Anm3QDgpJLIm9Nao0Yz1ztcQTwFspd3yD65VohhpuuCOmLASjC" crossorigin="anonymous">
    <script src="https://ajax.googleapis.com/ajax/libs/jquery/3.5.1/jquery.min.js"></script>

    <style>
        @import url('https://fonts.googleapis.com/css2?family=Gowun+Dodum&display=swap');

        * {
            font-family: 'Gowun Dodum', sans-serif;
        }

        .main {
            color: white;

            background-image: url('https://occ-0-1123-1217.1.nflxso.net/dnm/api/v6/6AYY37jfdO6hpXcMjf9Yu5cnmO0/AAAABeIfo7VL_VDyKnljV66IkR-4XLb6xpZqhpLSo3JUtbivnEW4s60PD27muH1mdaANM_8rGpgbm6L2oDgA_iELHZLZ2IQjG5lvp5d2.jpg?r=e6e.jpg');
            background-position: center;
            background-size: cover;
        }

        body {
            background-color: black;
        }

        .mypostingbox {
            width: 500px;
            margin: 20px auto 20px auto;

            border: 1px solid white;
            padding: 20px;
            border-radius: 5px;
        }

        .form-floating>input {
            background-color: transparent;
            color: white;
        }

        .form-floating>label {
            color: white;
        }

        .input-group>label {
            background-color: transparent;
            color: white;
        }

        .mypostingbox>button {
            width: 100%;
        }

        .mycards {
            width: 1200px;
            /* background-color: green; */
            margin: 20px auto 20px auto;
        }
    </style>

    <script>
        $(document).ready(function(){
            let url="http://spartacodingclub.shop/sparta_api/weather/seoul"
            fetch(url).then(res => res.json()).then(data => {
                let temper = data['temp']
                $('#msg').text(temper);
            })
        })

        function openClose() {
            $('#mypostingbox').toggle();
        }

        function makeCard() {
            let image = $('#image').val();
            let title = $('#title').val();
            // select칸 옵션의 value를 받아옴
            let star = $('#star').val();
            let comment = $('#comment').val();

            let html_temp = `<div class="col">
                <div class="card h-100">
                    <img src="${image}"
                        class="card-img-top" alt="...">
                    <div class="card-body">
                        <h5 class="card-title">${title}</h5>
                        <p class="card-text">${star}</p>
                        <p class="card-text">${comment}</p>
                    </div>
                </div>
            </div>`
            $('#cards').append(html_temp)
        }
    </script>
</head>

<body>
    <header class="p-3 text-bg-dark">
        <div class="container">
            <div class="d-flex flex-wrap align-items-center justify-content-center justify-content-lg-start">
                <a href="/" class="d-flex align-items-center mb-2 mb-lg-0 text-white text-decoration-none">
                    <svg class="bi me-2" width="40" height="32" role="img" aria-label="Bootstrap">
                        <use xlink:href="#bootstrap"></use>
                    </svg>
                </a>

                <ul class="nav col-12 col-lg-auto me-lg-auto mb-2 justify-content-center mb-md-0">
                    <li><a href="#" class="nav-link px-2 text-danger">spartaflix</a></li>
                    <li><a href="#" class="nav-link px-2 text-white">홈</a></li>
                    <li><a href="#" class="nav-link px-2 text-white">시리즈</a></li>
                    <li><a href="#" class="nav-link px-2 text-white">영화</a></li>
                    <li><a href="#" class="nav-link px-2 text-white">내가 찜한 콘텐츠</a></li>
                    <li><a href="#" class="nav-link px-2 text-white">현재 서울의 날씨: <span id="msg"></span>도</a></li>
                </ul>

                <form class="col-12 col-lg-auto mb-3 mb-lg-0 me-lg-3" role="search">
                    <input type="search" class="form-control form-control-dark text-bg-dark" placeholder="Search..."
                        aria-label="Search">
                </form>

                <div class="text-end">
                    <button type="button" class="btn btn-outline-light me-2">Login</button>
                    <button type="button" class="btn btn-danger">Sign-up</button>
                </div>
            </div>
        </div>
    </header>

    <div class="main">
        <div class="container-fluid py-5">
            <h1 class="display-5 fw-bold">킹덤</h1>
            <p class="col-md-8 fs-4">병든 왕을 둘러싸고 흉흉한 소문이 떠돈다. 어둠에 뒤덮인 조선, 기이한 역병에 신음하는 산하. 정체 모를 악에 맞서 백성을 구원할 희망은 오직
                세자뿐이다.</p>
            <button type="button" class="btn btn-outline-light" onclick="openClose()">영화 기록하기</button>
            <button type="button" class="btn btn-outline-light">상세정보</button>
        </div>
    </div>

    <div id="mypostingbox" class="mypostingbox">
        <div class="form-floating mb-3">
            <input type="email" class="form-control" id="image" placeholder="영화 이미지 주소">
            <label for="floatingInput">영화 이미지 주소</label>
        </div>
        <div class="form-floating mb-3">
            <input type="email" class="form-control" id="title" placeholder="영화 제목">
            <label for="floatingInput">영화 제목</label>
        </div>
        <div class="input-group mb-3">
            <label class="input-group-text" for="inputGroupSelect01">별점</label>
            <select class="form-select" id="star">
                <option selected>별점선택</option>
                <option value="⭐">⭐</option>
                <option value="⭐⭐">⭐⭐</option>
                <option value="⭐⭐⭐">⭐⭐⭐</option>
                <option value="⭐⭐⭐⭐">⭐⭐⭐⭐</option>
                <option value="⭐⭐⭐⭐⭐">⭐⭐⭐⭐⭐</option>
            </select>
        </div>
        <div class="form-floating mb-3">
            <input type="email" class="form-control" id="comment" placeholder="추천 이유">
            <label for="floatingInput">추천 이유</label>
        </div>
        <button type="button" class="btn btn-danger" onclick="makeCard()">기록하기</button>
    </div>

    <div class="mycards">
        <div id="cards" class="row row-cols-1 row-cols-md-4 g-4">
            <div class="col">
                <div class="card h-100">
                    <img src="https://movie-phinf.pstatic.net/20210728_221/1627440327667GyoYj_JPEG/movie_image.jpg"
                        class="card-img-top" alt="...">
                    <div class="card-body">
                        <h5 class="card-title">영화 제목</h5>
                        <p class="card-text">⭐⭐⭐</p>
                        <p class="card-text">영화 코멘트</p>
                    </div>
                </div>
            </div>
            <div class="col">
                <div class="card h-100">
                    <img src="https://movie-phinf.pstatic.net/20210728_221/1627440327667GyoYj_JPEG/movie_image.jpg"
                        class="card-img-top" alt="...">
                    <div class="card-body">
                        <h5 class="card-title">영화 제목</h5>
                        <p class="card-text">⭐⭐⭐</p>
                        <p class="card-text">영화 코멘트</p>
                    </div>
                </div>
            </div>
            <div class="col">
                <div class="card h-100">
                    <img src="https://movie-phinf.pstatic.net/20210728_221/1627440327667GyoYj_JPEG/movie_image.jpg"
                        class="card-img-top" alt="...">
                    <div class="card-body">
                        <h5 class="card-title">영화 제목</h5>
                        <p class="card-text">⭐⭐⭐</p>
                        <p class="card-text">영화 코멘트</p>
                    </div>
                </div>
            </div>
            <div class="col">
                <div class="card h-100">
                    <img src="https://movie-phinf.pstatic.net/20210728_221/1627440327667GyoYj_JPEG/movie_image.jpg"
                        class="card-img-top" alt="...">
                    <div class="card-body">
                        <h5 class="card-title">영화 제목</h5>
                        <p class="card-text">⭐⭐⭐</p>
                        <p class="card-text">영화 코멘트</p>
                    </div>
                </div>
            </div>
        </div>
    </div>
</body>

</html>
```
### <ins>Result</ins>
![flix](https://github.com/jkhan94/assests_images_issue/assets/163835909/0a33bf8d-55a4-4929-bfb2-7ac95079fa17){: width="60%"}
<br><br>

## index.html
```html
<!DOCTYPE html>
<html lang="en">

<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>스파르타플릭스</title>

    <link href="https://cdn.jsdelivr.net/npm/bootstrap@5.0.2/dist/css/bootstrap.min.css" rel="stylesheet"
        integrity="sha384-EVSTQN3/azprG1Anm3QDgpJLIm9Nao0Yz1ztcQTwFspd3yD65VohhpuuCOmLASjC" crossorigin="anonymous">
    <script src="https://ajax.googleapis.com/ajax/libs/jquery/3.5.1/jquery.min.js"></script>

    <style>
        @import url('https://fonts.googleapis.com/css2?family=Gowun+Dodum&display=swap');

        * {
            font-family: 'Gowun Dodum', sans-serif;
        }

        .main {
            color: white;

            background-image: url('https://occ-0-1123-1217.1.nflxso.net/dnm/api/v6/6AYY37jfdO6hpXcMjf9Yu5cnmO0/AAAABeIfo7VL_VDyKnljV66IkR-4XLb6xpZqhpLSo3JUtbivnEW4s60PD27muH1mdaANM_8rGpgbm6L2oDgA_iELHZLZ2IQjG5lvp5d2.jpg?r=e6e.jpg');
            background-position: center;
            background-size: cover;
        }

        body {
            background-color: black;
        }

        .mypostingbox {
            width: 500px;
            margin: 20px auto 20px auto;

            border: 1px solid white;
            padding: 20px;
            border-radius: 5px;
        }

        .form-floating>input {
            background-color: transparent;
            color: white;
        }

        .form-floating>label {
            color: white;
        }

        .input-group>label {
            background-color: transparent;
            color: white;
        }

        .mypostingbox>button {
            width: 100%;
        }

        .mycards {
            width: 1200px;
            /* background-color: green; */
            margin: 20px auto 20px auto;
        }
    </style>

    <script>
        $(document).ready(function(){
            let url="http://spartacodingclub.shop/sparta_api/weather/seoul"
            fetch(url).then(res => res.json()).then(data => {
                let temper = data['temp']
                // $('#msg').text(temper);

                let over = "더워요"
                let under = "추워요"
                if(temper>20){
                    $('#msg').text(over)
                }else{
                    $('#msg').text(under)
                }

            })
        })

        function openClose() {
            $('#mypostingbox').toggle();
        }

        function makeCard() {
            let image = $('#image').val();
            let title = $('#title').val();
            // select칸 옵션의 value를 받아옴
            let star = $('#star').val();
            let comment = $('#comment').val();

            let html_temp = `<div class="col">
                <div class="card h-100">
                    <img src="${image}"
                        class="card-img-top" alt="...">
                    <div class="card-body">
                        <h5 class="card-title">${title}</h5>
                        <p class="card-text">${star}</p>
                        <p class="card-text">${comment}</p>
                    </div>
                </div>
            </div>`
            $('#cards').append(html_temp)
        }
    </script>
</head>

<body>
    <header class="p-3 text-bg-dark">
        <div class="container">
            <div class="d-flex flex-wrap align-items-center justify-content-center justify-content-lg-start">
                <a href="/" class="d-flex align-items-center mb-2 mb-lg-0 text-white text-decoration-none">
                    <svg class="bi me-2" width="40" height="32" role="img" aria-label="Bootstrap">
                        <use xlink:href="#bootstrap"></use>
                    </svg>
                </a>

                <ul class="nav col-12 col-lg-auto me-lg-auto mb-2 justify-content-center mb-md-0">
                    <li><a href="#" class="nav-link px-2 text-danger">spartaflix</a></li>
                    <li><a href="#" class="nav-link px-2 text-white">홈</a></li>
                    <li><a href="#" class="nav-link px-2 text-white">시리즈</a></li>
                    <li><a href="#" class="nav-link px-2 text-white">영화</a></li>
                    <li><a href="#" class="nav-link px-2 text-white">내가 찜한 콘텐츠</a></li>
                    <li><a href="#" class="nav-link px-2 text-white">현재 서울의 날씨: <span id="msg"></span></a></li>
                </ul>

                <form class="col-12 col-lg-auto mb-3 mb-lg-0 me-lg-3" role="search">
                    <input type="search" class="form-control form-control-dark text-bg-dark" placeholder="Search..."
                        aria-label="Search">
                </form>

                <div class="text-end">
                    <button type="button" class="btn btn-outline-light me-2">Login</button>
                    <button type="button" class="btn btn-danger">Sign-up</button>
                </div>
            </div>
        </div>
    </header>

    <div class="main">
        <div class="container-fluid py-5">
            <h1 class="display-5 fw-bold">킹덤</h1>
            <p class="col-md-8 fs-4">병든 왕을 둘러싸고 흉흉한 소문이 떠돈다. 어둠에 뒤덮인 조선, 기이한 역병에 신음하는 산하. 정체 모를 악에 맞서 백성을 구원할 희망은 오직
                세자뿐이다.</p>
            <button type="button" class="btn btn-outline-light" onclick="openClose()">영화 기록하기</button>
            <button type="button" class="btn btn-outline-light">상세정보</button>
        </div>
    </div>

    <div id="mypostingbox" class="mypostingbox">
        <div class="form-floating mb-3">
            <input type="email" class="form-control" id="image" placeholder="영화 이미지 주소">
            <label for="floatingInput">영화 이미지 주소</label>
        </div>
        <div class="form-floating mb-3">
            <input type="email" class="form-control" id="title" placeholder="영화 제목">
            <label for="floatingInput">영화 제목</label>
        </div>
        <div class="input-group mb-3">
            <label class="input-group-text" for="inputGroupSelect01">별점</label>
            <select class="form-select" id="star">
                <option selected>별점선택</option>
                <option value="⭐">⭐</option>
                <option value="⭐⭐">⭐⭐</option>
                <option value="⭐⭐⭐">⭐⭐⭐</option>
                <option value="⭐⭐⭐⭐">⭐⭐⭐⭐</option>
                <option value="⭐⭐⭐⭐⭐">⭐⭐⭐⭐⭐</option>
            </select>
        </div>
        <div class="form-floating mb-3">
            <input type="email" class="form-control" id="comment" placeholder="추천 이유">
            <label for="floatingInput">추천 이유</label>
        </div>
        <button type="button" class="btn btn-danger" onclick="makeCard()">기록하기</button>
    </div>

    <div class="mycards">
        <div id="cards" class="row row-cols-1 row-cols-md-4 g-4">
            <div class="col">
                <div class="card h-100">
                    <img src="https://movie-phinf.pstatic.net/20210728_221/1627440327667GyoYj_JPEG/movie_image.jpg"
                        class="card-img-top" alt="...">
                    <div class="card-body">
                        <h5 class="card-title">영화 제목</h5>
                        <p class="card-text">⭐⭐⭐</p>
                        <p class="card-text">영화 코멘트</p>
                    </div>
                </div>
            </div>
            <div class="col">
                <div class="card h-100">
                    <img src="https://movie-phinf.pstatic.net/20210728_221/1627440327667GyoYj_JPEG/movie_image.jpg"
                        class="card-img-top" alt="...">
                    <div class="card-body">
                        <h5 class="card-title">영화 제목</h5>
                        <p class="card-text">⭐⭐⭐</p>
                        <p class="card-text">영화 코멘트</p>
                    </div>
                </div>
            </div>
            <div class="col">
                <div class="card h-100">
                    <img src="https://movie-phinf.pstatic.net/20210728_221/1627440327667GyoYj_JPEG/movie_image.jpg"
                        class="card-img-top" alt="...">
                    <div class="card-body">
                        <h5 class="card-title">영화 제목</h5>
                        <p class="card-text">⭐⭐⭐</p>
                        <p class="card-text">영화 코멘트</p>
                    </div>
                </div>
            </div>
            <div class="col">
                <div class="card h-100">
                    <img src="https://movie-phinf.pstatic.net/20210728_221/1627440327667GyoYj_JPEG/movie_image.jpg"
                        class="card-img-top" alt="...">
                    <div class="card-body">
                        <h5 class="card-title">영화 제목</h5>
                        <p class="card-text">⭐⭐⭐</p>
                        <p class="card-text">영화 코멘트</p>
                    </div>
                </div>
            </div>
        </div>
    </div>
</body>

</html>
```
### <ins>Result</ins>
![flixIF](https://github.com/jkhan94/assests_images_issue/assets/163835909/2cf9a29f-1afa-476d-9d60-c69c787fd06a){: width="60%"}
