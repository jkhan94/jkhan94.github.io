---
layout: post
title: WebRookie_sparta - week04
date: 2024-04-01
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
    <script type="module">
        // Firebase SDK 라이브러리 가져오기
        import { initializeApp } from "https://www.gstatic.com/firebasejs/9.22.0/firebase-app.js";
        import { getFirestore } from "https://www.gstatic.com/firebasejs/9.22.0/firebase-firestore.js";
        import { collection, addDoc } from "https://www.gstatic.com/firebasejs/9.22.0/firebase-firestore.js";
        import { getDocs } from "https://www.gstatic.com/firebasejs/9.22.0/firebase-firestore.js";

        // Firebase 구성 정보 설정
        // 프로젝트 개요 옆 톱니바퀴 > 프로젝트 설정 > SDK 설정 및 구성에서 구성 > 해당 코드 복사해서 붙여넣기.
        // For Firebase JS SDK v7.20.0 and later, measurementId is optional
        const firebaseConfig = {
            파이어스토어 프로젝트 설젇 > 일반 > SDK 구성 > 구성에 있는 값
        };

        // Firebase 인스턴스 초기화
        const app = initializeApp(firebaseConfig);
        const db = getFirestore(app);

        // 디비에 데이터 추가
        $("#postingbtn").click(async function () {
            let image = $('#image').val()
            let title = $('#title').val()
            let content = $('#content').val()
            let date = $('#date').val()

            let doc = {
                // 'name':"Bob", 'age':30
                'image': image,
                'title': title,
                'content': content,
                'date': date
            };
            await addDoc(collection(db, "albums"), doc);
            // 팝업으로 등록완료 알림
            alert('추억앨범 등록 완료!')
            // 화면 새로고침
            window.location.reload();
        })

        // 디비 데이터 불러오기
        // function makecard()와 동일한 작업.
        let docs = await getDocs(collection(db, "albums"));
        docs.forEach((doc) => {
            let row = doc.data();
            // console.log(row);

            let image = row['image']
            let title = row['title']
            let content = row['content']
            let date = row['date']

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
        });

        ///////////////////////////////////////////////
        // script에 module이 지정되면 가장 마지막에 실행됨. 따라서 아래 함수 불필요.
        // $(document).ready(function () {})
        let url = "http://spartacodingclub.shop/sparta_api/seoulair";
        fetch(url).then(res => res.json()).then(data => {
            let mise = data['RealtimeCityAir']['row'][0]['IDEX_NM']
            $('#msg').text(mise)
        })

        // script에 module이 지정되면 onclick 안 됨. 그래서 버튼을 동적으로 만들어야 함. 
        // 동적으로 만든다 = 코딩한다.
        // openclose()
        $("#savebtn").click(async function () {
            $('#mypostingbox').toggle();
        })
    </script>
</head>

<body>
    <div class="mytitle">
        <h1>나만의 추억앨범</h1>
        <!-- span: p 태그 내 글자 묶음. -->
        <p>현재 서울의 미세먼지 : <span id="msg"></span></p>
        <button id="savebtn">추억 저장하기</button>
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
            <button id="postingbtn" type="button" class="btn btn-primary" onclick="makecard()">기록하기</button>
            <button type="button" class="btn btn-outline-primary">닫기</button>
        </div>
    </div>
    <!-- 디비에 저장된 카드만 출력 -->
    <div class="mycards">
        <div id="card" class="row row-cols-1 row-cols-md-4 g-4">
            
        </div>
    </div>
</body>

</html>
```
### <ins>Result</ins>
![firestoreAlbum](https://github.com/jkhan94/assests_images_issue/assets/163835909/5f874cbe-518e-4df7-a654-f72afd138171){: width="60%"}

___


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

    <script type="module">
        // Firebase SDK 라이브러리 가져오기
        import { initializeApp } from "https://www.gstatic.com/firebasejs/9.22.0/firebase-app.js";
        import { getFirestore } from "https://www.gstatic.com/firebasejs/9.22.0/firebase-firestore.js";
        import { collection, addDoc } from "https://www.gstatic.com/firebasejs/9.22.0/firebase-firestore.js";
        import { getDocs } from "https://www.gstatic.com/firebasejs/9.22.0/firebase-firestore.js";

        // Firebase 구성 정보 설정
        const firebaseConfig = {
            파이어베이스 구성 정보
        };

        // Firebase 인스턴스 초기화
        const app = initializeApp(firebaseConfig);
        const db = getFirestore(app);

        // 디비에 데이터 추가
        $("#postingbtn").click(async function () {
            let image = $('#image').val()
            let title = $('#title').val()
            let star = $('#star').val()
            let comment = $('#comment').val()

            let doc = {
                'image': image,
                'title': title,
                'star': star,
                'comment': comment
            };
            await addDoc(collection(db, "spartaflix"), doc);
            // 팝업으로 등록완료 알림
            alert('영화 등록 완료!')
            // 화면 새로고침
            window.location.reload();
        })

        // 디비 데이터 불러오기
        // function makecard()와 동일한 작업.
        let docs = await getDocs(collection(db, "spartaflix"));
        docs.forEach((doc) => {
            let row = doc.data();
            // console.log(row);

            let image = row['image']
            let title = row['title']
            let star = row['star']
            let comment = row['comment']

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
        });

        ////////////////////////////////////////////
        // $(document).ready(function () { })
        let url = "http://spartacodingclub.shop/sparta_api/weather/seoul"
        fetch(url).then(res => res.json()).then(data => {
            let temper = data['temp']
            // $('#msg').text(temper);

            let over = "더워요"
            let under = "추워요"
            if (temper > 20) {
                $('#msg').text(over)
            } else {
                $('#msg').text(under)
            }
        })

        // openClose()
        $("#savebtn").click(async function () {
            $('#mypostingbox').toggle();
        })
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
            <button id="savebtn" type="button" class="btn btn-outline-light">영화 기록하기</button>
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
        <button id="postingbtn" type="button" class="btn btn-danger">기록하기</button>
    </div>

    <div class="mycards">
        <div id="cards" class="row row-cols-1 row-cols-md-4 g-4">

        </div>
    </div>
</body>

</html>
```
### <ins>Result</ins>
![firestoreSpartaflix](https://github.com/jkhan94/assests_images_issue/assets/163835909/5069daca-189e-4e49-9c98-ccdd127487aa){: width="60%"}
<br>
![DB](https://github.com/jkhan94/assests_images_issue/assets/163835909/24fbc1bd-c301-4608-9900-fce170ddb645){: width="60%"}
