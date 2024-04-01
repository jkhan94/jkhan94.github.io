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
            apiKey: "AIzaSyBwtFDCTPr-T6H_wo5kQAq4mURnAz6wdRA",
            authDomain: "sparta-19da5.firebaseapp.com",
            projectId: "sparta-19da5",
            storageBucket: "sparta-19da5.appspot.com",
            messagingSenderId: "476640655491",
            appId: "1:476640655491:web:78923f4071fef7a7ffc3b6",
            measurementId: "G-1YJMLSQFLJ"
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
```
### <ins>Result</ins>
![firestoreSpartaflix](https://github.com/jkhan94/assests_images_issue/assets/163835909/5069daca-189e-4e49-9c98-ccdd127487aa){: width="60%"}
<br>
![DB](https://github.com/jkhan94/assests_images_issue/assets/163835909/24fbc1bd-c301-4608-9900-fce170ddb645){: width="60%"}
