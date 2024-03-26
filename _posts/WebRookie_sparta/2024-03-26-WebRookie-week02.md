---
layout: post
title: WebRookie_sparta - week02
date: 2024-03-26
category: WebRookie_sparta
---
# Spartaflix
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
    <link rel="stylesheet" href="https://maxcdn.bootstrapcdn.com/bootstrap/4.5.2/css/bootstrap.min.css">s

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
            <button type="button" class="btn btn-outline-light">영화 기록하기</button>
            <button type="button" class="btn btn-outline-light">상세정보</button>
        </div>
    </div>

    <div class="mypostingbox">
        <div class="form-floating mb-3">
            <input type="email" class="form-control" id="floatingInput" placeholder="영화 이미지 주소">
            <label for="floatingInput">영화 이미지 주소</label>
        </div>
        <div class="form-floating mb-3">
            <input type="email" class="form-control" id="floatingInput" placeholder="영화 제목">
            <label for="floatingInput">영화 제목</label>
        </div>
        <div class="input-group mb-3">
            <label class="input-group-text" for="inputGroupSelect01">별점</label>
            <select class="form-select">
                <option selected>별점선택</option>
                <option value="1">⭐</option>
                <option value="2">⭐⭐</option>
                <option value="3">⭐⭐⭐</option>
                <option value="4">⭐⭐⭐⭐</option>
                <option value="5">⭐⭐⭐⭐⭐</option>
            </select>
        </div>
        <div class="form-floating mb-3">
            <input type="email" class="form-control" id="floatingInput" placeholder="추천 이유">
            <label for="floatingInput">추천 이유</label>
        </div>
        <button type="button" class="btn btn-danger">기록하기</button>
    </div>

    <div class="mycards">
        <div class="row row-cols-1 row-cols-md-4 g-4">
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
![file:///C:/0325_sparta/spartaflix/index.html](https://github.com/jkhan94/assests_images_issue/assets/163835909/0a229918-4344-45a5-ae55-31db1c9768bc)

<br>

## javascript.html
Variable declaration in javascript. <br>
Array and dictionary, if and foreach statements. <br>
```javascript
<!DOCTYPE html>
<html lang="en">

<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Javascript</title>

    <!-- 자바 스크립트 -->
    <script>
        // let: 변수 선언
        // console.log(): 웹페이지 우클릭 > 검사 > 콘솔 탭에 출력
        let a = 'hello'
        let b = 'javascript'
        console.log(a)
        console.log(b)
        console.log(a + " " + b)

        let c = 3, d = 5
        console.log(c + d)
        console.log(c + '' + d)
        console.log(" ")

        // let list = [] : 리스트 선언
        // list.length : 리스트 길이
        let list = ['사과', '수박', '딸기', '감']
        console.log(list[1]) // 수박
        console.log(list[0]) // 사과
        console.log(list.length) //4
        // let a_dict = {} : 딕셔너리 선언     
        let dict = { 'name': 'Bob', 'age': 27, 'height': 150 }
        console.log(dict)
        console.log(dict['name']) // 영수
        console.log(dict['age']) // 27
        // 리스트와 딕셔너리 혼용
        // 딕셔너리 고객별로 정보를 묶을 수 있음.
        // 리스트는 묶인 정보(딕셔너리)를 한번에 관리할 수 있음.
        let listd = [
            { 'name': '영수', 'phone': '010-1234-1234' },
            { 'name': '철수', 'phone': '010-4321-4321' },
            { 'name': '영희', 'phone': '010-5678-5678' }
        ]
        console.log(listd[0]['name']) //영수
        console.log(listd[1]['phone']) //010-4321-4321
        console.log(" ")

        // 배열 요소 출력
        console.log("원본")
        listd.forEach((ele) => {
            console.log(ele)
        })
        console.log(" ")
        // 배열에 요소 추가
        // 배열명.push(요소) : 배열 끝에 요소 추가
        // 배열명.unshift(요소) : 배열 앞에 요소 추가
        // 배열명.splice(인덱스,0,요소1,요소2,...) : '인덱스'번으로 요소 추가. 배열 인덱스는 0부터 시작.
        console.log("3개 추가")
        listd.push({ 'name': 'Aria', 'phone': '010-1111-1111' })
        listd.unshift({ 'name': 'Granada', 'phone': '010-2222-2222' })
        listd.splice(3, 0, { 'name': '철수 뒤', 'phone': '010-3333-3333' })
        listd.forEach((ele) => {
            console.log(ele)
        })
        console.log(" ")
        // 배열 요소 삭제        
        // 배열명.pop(요소) : 배열 마지막 요소 제거
        // 배열명.shift(요소) : 배열 첫번째 요소 제거
        // 배열명.splice(인덱스,n) : 인덱스부터 n개의 요소 제거
        // listd.pop() // 함수 쓸 때마다 요소가 삭제됨.
        console.log("추가한 3개 삭제")
        console.log(listd.pop())
        element = listd.shift()
        console.log(element);
        listd.splice(2, 1)
        console.log("원본과 동일한지 확인")
        console.log(listd)
        console.log(" ")

        // split: 특정 문자로 문자열 나누기
        let myemail = 'sparta@gmail.com'
        let result = myemail.split('@') // ['sparta','gmail.com']
        console.log(result[0]) // sparta
        console.log(result[1]) // gmail.com
        let result2 = result[1].split('.') // ['gmail','com']
        console.log(result2[0]) // gmail -> 우리가 알고 싶었던 것!
        console.log(result2[1]) // com
        myemail.split('@')[1].split('.')[0] // gmail 
        console.log(" ")

        //반복문
        let fruits = ['사과', '배', '감', '귤']
        fruits.forEach((a) => {
            console.log(a)
        })
        // 조건문
        let age = 24
        if (age > 20) {
            console.log('성인입니다')
        } else {
            console.log('청소년입니다')
        }
        // 반복문 + 조건문
        let ages = [12, 15, 20, 25, 17, 37, 24]
        ages.forEach((a) => {
            if (a > 20) {
                console.log("성인입니다.")
            }
            else {
                if ((a == 20)) {
                    console.log("20살입니다.")
                } else {
                    console.log("청소년입니다.")
                }
            }
        })

    </script>
</head>

<body>
    자바스크립트 연습
</body>

</html>
```
### <ins>Result</ins>
![1](https://github.com/jkhan94/assests_images_issue/assets/163835909/eaec4889-1905-4097-8e8a-1bd028f44c7c)
![2](https://github.com/jkhan94/assests_images_issue/assets/163835909/b441229e-3992-4d10-ab13-d476f9415d0d)
![3](https://github.com/jkhan94/assests_images_issue/assets/163835909/f39ca3ec-6f36-43e6-8f70-90237ae4a12c)
![4](https://github.com/jkhan94/assests_images_issue/assets/163835909/606f6dc0-7acc-4e13-85dd-4b56ab775e5c)
![5](https://github.com/jkhan94/assests_images_issue/assets/163835909/d2e1be9d-07af-4ffb-afe8-9e858fb1bc4a)


## javascriptDOM.html
Functions in javascript.<br>
```html
<!DOCTYPE html>
<html lang="en">

<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Javascript DOM</title>

    <link href="https://cdn.jsdelivr.net/npm/bootstrap@5.0.2/dist/css/bootstrap.min.css" rel="stylesheet"
        integrity="sha384-EVSTQN3/azprG1Anm3QDgpJLIm9Nao0Yz1ztcQTwFspd3yD65VohhpuuCOmLASjC" crossorigin="anonymous">

    <style>
        .total {
            width: max-content;
            margin: 10px 0px 0px 10px;
        }

        .total>button{
            width: 100%;
        }

        .wrap {
            margin: 20px 0px 0px 0px;
        }
    </style>
    <script>
        function hey() {
            alert('안녕!');
        }

        function changeBlue() {
            document.getElementById('title').style.color = 'blue';
        }

        function changeBlack() {
            document.getElementById('title').style.color = 'black';
        }
    </script>
</head>

<body>
    <div class="total">
        <h1 id="title">자바스크립트 DOM</h1>       

        <button type="button" class="btn btn-primary" onclick="hey()">hey</button>

        <div class="wrap">            
            <button type="button" class="btn btn-info" onclick="changeBlue()">제목색 파랑으로 변경</button>
            <button type="button" class="btn btn-dark" onclick="changeBlack()">제목색 검정으로 변경</button>
        </div>
    </div>
</body>

</html>
```
### <ins>Result</ins>
![main](https://github.com/jkhan94/assests_images_issue/assets/163835909/353e6f44-fed5-444b-9cb6-37f141c612b6)
![alert](https://github.com/jkhan94/assests_images_issue/assets/163835909/c3ed292c-e988-40f5-9280-48441340cc1e)
![blue](https://github.com/jkhan94/assests_images_issue/assets/163835909/7c3602b2-0f75-42c0-8288-5a9cb3b85313)
![black](https://github.com/jkhan94/assests_images_issue/assets/163835909/1c43c8e3-dbbb-4f64-a8cd-f1b72ce9f4ac)


## jQuery.html
```html
<!DOCTYPE html>
<html lang="en">

<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>JQuery</title>

    <!-- 부트스트랩 -->
    <link href="https://cdn.jsdelivr.net/npm/bootstrap@5.0.2/dist/css/bootstrap.min.css" rel="stylesheet"
        integrity="sha384-EVSTQN3/azprG1Anm3QDgpJLIm9Nao0Yz1ztcQTwFspd3yD65VohhpuuCOmLASjC" crossorigin="anonymous">

    <!-- 제이쿼리 -->
    <script src="https://ajax.googleapis.com/ajax/libs/jquery/3.5.1/jquery.min.js"></script>

    <style>
        .total {
            width: max-content;
            margin: 10px 0px 0px 10px;
        }

        .total>button {
            width: 100%;
        }

        .wrap {
            margin: 20px 0px 0px 0px;
        }
    </style>

    <script>
        function hey() {
            $('#title').text('나는 제목이다')
        }

    </script>
</head>

<body>
    <div class="total">
        <h1 id="title">제이쿼리</h1>

        <button type="button" class="btn btn-primary" onclick="hey()">제목 변경</button>
    </div>
</body>

</html>
```
### <ins>Result</ins>
![original](https://github.com/jkhan94/assests_images_issue/assets/163835909/c1d46ba7-fd14-4347-bfeb-f50f9ecfd45d)
![change](https://github.com/jkhan94/assests_images_issue/assets/163835909/235f53a8-fe0b-4109-8c96-21345d731807)


## prac1.html
```html
<!DOCTYPE html>
<html>

<head>
    <title>자바스크립트 문법 연습하기!</title>
    <script src="https://ajax.googleapis.com/ajax/libs/jquery/3.4.1/jquery.min.js"></script>
</head>
<style>
    .button-part {
        display: flex;
        height: 50px;
    }
</style>
<script>
    // 리스트 헤드 밑에 텍스트 추가
    function checkResult() {
        // text는 마지막에 입력된 인수만 출력.
        $('#q1').text('나는 제목이다');

        let a = ['사과', '배', '감', '귤']
        $('#q1').text(a[2]);

        let b = { 'name': '영수', 'age': 30 }
        $('#q2').text(b['name']);

        let c = [
            { 'name': '영수', 'age': 30 },
            { 'name': '철수', 'age': 35 }
        ]
        $('#q3').text(c[1]['name']);
    }
</script>
<script>

</script>

<body>
    <div class="top-part">
        <h1>자바스크립트 문법 연습하기!</h1>
    </div>
    <hr />
    <br>
    <h2>1. 함수</h2>
    <div class="button-part">
        <button onclick="checkResult()">결과 확인하기!</button>
    </div>
    <div class="list-part">
        <h2>2. 리스트</h2>
        <div id="q1"></div>
    </div>
    <div class="dict-part">
        <h2>3. 딕셔너리</h2>
        <div id="q2"></div>
    </div>
    <div>
        <h2>4. 리스트 딕셔너리</h2>
        <div id="q3"></div>
    </div>
</body>

</html>
```
### <ins>Result</ins>
![1](https://github.com/jkhan94/assests_images_issue/assets/163835909/2540b913-aabe-4920-b3ac-82242dd65c6d)


## prac2.html
```html
<!DOCTYPE html>
<html>

<head>
    <title>자바스크립트 문법 연습하기!</title>
    <script src="https://ajax.googleapis.com/ajax/libs/jquery/3.4.1/jquery.min.js"></script>
</head>
<script>
    function checkResult() {
        let fruits = ['사과', '배', '감', '귤', '수박']
        // 작성된 내용 삭제
        $('#q1').empty();

        // append: 이어서 출력됨. text는 마지막 데이터만 출력.
        // temp_html: 변수명
        // `: 백틱 (물결무늬). 문자와 변수를 함께 써줄 수 있도록 하는 특수기호
        let temp_html1 = `<p>감자</p>`
        $('#q1').append(temp_html1)

        // 배열의 요소 1개만 출력
        let b = fruits[0]
        let temp_html3 = `<p>${b}</p>`
        $('#q1').append(temp_html3)

        // 배열의 요소를 한줄로 출력
        let temp_html2 = `<p>${fruits}</p>`
        $('#q1').append(temp_html2)

        // 배열의 요소를 줄바꿔서 출력
        fruits.forEach((a) => {
            let temp_html = `<p>${a}</p>`
            $('#q1').append(temp_html)
        })


        let people = [
            { 'name': '서영', 'age': 24 },
            { 'name': '현아', 'age': 30 },
            { 'name': '영환', 'age': 12 },
            { 'name': '서연', 'age': 15 },
            { 'name': '지용', 'age': 18 },
            { 'name': '예지', 'age': 36 }
        ]
        $('#q2').empty()
        people.forEach((a) => {
            //     이렇게 쓰면 [Object object]가 출력됨.
            //     let temp_html = `<p>${a}</p>`
            // $('#q2').append(temp_html)
            let name = a['name']
            let age = a['age']
            let temp_html = `<p>${name}는 ${age}살</p>`
            $('#q2').append(temp_html)
        })

        let people2 = [
            { 'name': '서영', 'height': 165 },
            { 'name': '현아', 'height': 170 },
            { 'name': '영환', 'height': 175 },
            { 'name': '서연', 'height': 162 },
            { 'name': '지용', 'height': 190 },
            { 'name': '예지', 'height': 168 }
        ]
        people2.forEach((a)=>{
            let name = a['name']
            let height = a['height']
            let temp_html = `<p>${name}는 ${height}cm 입니다.</p>`
            $('#q3').append(temp_html)
        })

    }
</script>

<body>
    <div class="top-part">
        <h1>자바스크립트 문법 연습하기!</h1>
    </div>
    <hr />
    <br>
    <h2>1. 함수</h2>
    <div class="button-part">
        <button onclick="checkResult()">결과 확인하기!</button>
    </div>
    <div class="list-part">
        <h2>2. 붙이기</h2>
        <div id="q1">
            <p>사과</p>
            <p>귤</p>
            <p>감</p>
        </div>
    </div>
    <div class="list-part">
        <h2>3. 붙이기</h2>
        <div id="q2">
            <p>영수는 24살입니다.</p>
            <p>세종은 30살입니다.</p>
            <p>수영은 20살입니다.</p>
        </div>
    </div>
    <div class="list-part">
        <h2>4. 붙이기</h2>
        <div id="q3">
        </div>
    </div>
</body>

</html>
```
### <ins>Result</ins>
![original](https://github.com/jkhan94/assests_images_issue/assets/163835909/4cedf985-a9ae-4261-8902-9eeb4bc8fa29)
![function](https://github.com/jkhan94/assests_images_issue/assets/163835909/52842a2a-9a23-4ef0-82df-5afb1b3f05b6)
![people](https://github.com/jkhan94/assests_images_issue/assets/163835909/15dad82c-0eb6-4ed9-9fbe-b630a9f28f99)
![height](https://github.com/jkhan94/assests_images_issue/assets/163835909/5b528184-d471-4672-a6d0-b5201a2321a3)



