---
layout: post
title: WebRookie_sparta - week01
date: 2024-03-26
category: WebRookie_sparta
---

Get designs from bootstrap. <br>
[Bootstrap](https://getbootstrap.com/docs/5.3/getting-started/introduction/) <br><br>

Fonts can be found here. <br>
[Google fonts](https://fonts.google.com/) <br><br>


## tags.html
Basic tags to use when designing web page by html.
```html
<!DOCTYPE html>
<html lang="en">

<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>스파르타코딩클럽 | HTML 기초</title>
</head>

<body>
    <!-- 구역을 나누는 태그들 -->
    <div>나는 구역을 나누죠</div>
    <p>나는 문단이에요</p>
    <ul>
        <li> bullet point!1 </li>
        <li> bullet point!2 </li>
    </ul>

    <!-- 구역 내 콘텐츠 태그들 -->
    <h1>h1은 제목을 나타내는 태그입니다. 페이지마다 하나씩 꼭 써주는 게 좋아요. 그래야 구글 검색이 잘 되거든요.</h1>
    <h2>h2는 소제목입니다.</h2>
    <h3>h3~h6도 각자의 역할이 있죠. 비중은 작지만..</h3>
    <hr>
    span 태그입니다: 특정 <span style="color:red">글자</span>를 꾸밀 때 써요
    <hr>
    a 태그입니다: <a href="http://naver.com/"> 하이퍼링크 </a>
    <hr>
    img 태그입니다: <img src="https://www.google.com/images/branding/googlelogo/1x/googlelogo_color_272x92dp.png" />
    <hr>
    input 태그입니다: <input type="text" />
    <hr>
    button 태그입니다: <button> 버튼입니다</button>
    <hr>
    textarea 태그입니다: <textarea>나는 무엇일까요?</textarea>
</body>

</html>
```
### <ins>Result</ins>
![file:///C:/0325_sparta/frontend/tags.html](https://github.com/jkhan94/assests_images_issue/assets/163835909/312d39fd-96ff-4bde-9a60-ced6a9781294 "result"){: width="50%"}

<br>

## login.html
Get Id, PW from the user. <br>
```html
<!DOCTYPE html>
<html lang="en">

<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Login</title>
    <style>
        @import url('https://fonts.googleapis.com/css2?family=Nanum+Pen+Script&display=swap');

        * {
            font-family: "Nanum Pen Script", cursive;
            font-size: large;
        }

        .mytitle {
            width: 300px;
            height: 200px;
            /* background-color: green; */
            /* padding-top: 30px; */
            padding: 30px 0px 0px 0px;
            border-radius: 8px;

            /* 배경 이미지 넣기*/
            background-image: url('https://www.ancient-origins.net/sites/default/files/field/image/Agesilaus-II-cover.jpg');
            background-position: center;
            background-size: cover;

            color: white;
            text-align: center;
        }

        .mytitle > button {
            border-radius: 15px;
        }

        .wrap {
            /* background-color: green; */
            /* div는 가로 전체 구역.
            옮길 것들을 div로 묶은 뒤 가로 길이를 줘야 그것만 위치 벼녁 가능.
            auto는 끝까지 민다.*/
            width: 300px;
            /* margin: auto; */
            margin: 20px auto 0px auto;
        }
    </style>
</head>

<body>
    <div class="wrap">
        <div class="mytitle">
            <h1>로그인 페이지</h1>
            <h5>아이디, 비밀번호를 입력해주세요</h5>
        </div>

        <p>ID: <input type="text" /></p>
        <p>PW: <input type="text" /> </p>
        <button>로그인하기</button>
    </div>
</body>

</html>
```
### <ins>Result</ins>
![file:///C:/0325_sparta/frontend/login.html](https://github.com/jkhan94/assests_images_issue/assets/163835909/7857edf8-6749-4246-a565-0bd83e269501)

<br>

## index.html
Album layout.<br>
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

        .mypostingbox{
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
        .mybtn>button{
            margin-right: 5px;
        }
        .mycards {
            width: 1200px;
            margin: 30px auto 0px auto;
        }
    </style>
</head>

<body>
    <div class="mytitle">
        <h1>나만의 추억앨범</h1>
        <button>추억 저장하기</button>
    </div>
    <div class="mypostingbox">
        <div class="form-floating mb-3">
            <input type="email" class="form-control" id="floatingInput" placeholder="앨범 이미지">
            <label for="floatingInput">앨범 이미지</label>
        </div>
        <div class="form-floating mb-3">
            <input type="email" class="form-control" id="floatingInput" placeholder="앨범 제목">
            <label for="floatingInput">앨범 제목</label>
        </div>
        <div class="form-floating mb-3">
            <input type="email" class="form-control" id="floatingInput" placeholder="앨범 내용">
            <label for="floatingInput">앨범 내용</label>
        </div>
        <div class="form-floating mb-3">
            <input type="email" class="form-control" id="floatingInput" placeholder="앨범 날짜">
            <label for="floatingInput">앨범 날짜</label>
        </div>
        <div class="mybtn">
            <button type="button" class="btn btn-primary">기록하기</button>
            <button type="button" class="btn btn-outline-primary">닫기</button>
        </div>
    </div>
    <div class="mycards">
        <div class="row row-cols-1 row-cols-md-4 g-4">
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
![file:///C:/0325_sparta/album/index.html](https://github.com/jkhan94/assests_images_issue/assets/163835909/cf6cff3a-6e94-4b6c-8989-694925b828ce)
