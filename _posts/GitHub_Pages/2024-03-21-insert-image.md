---
layout: post
title:  "깃허브 페이지에 이미지 삽입"
date:   2024-03-21
categories: GitHub_Pages
---

### 1. &lt;img&gt;태그, 로컬 이미지
assets/images에 저장. <br>
저장소에 개별로 저장해야 해서 용량 차지함.<br>
&lt;img src="/assets/images/mango.png" width="10%" height="10%" title="Array" alt="아무거나"/&gt; <br>
<img src="/assets/images/mango.png" width="10%" height="10%" title="Array" alt="아무거나"/> 

<br>

### 2. 마크다운 문법, https://~.png
"이미지 주소 복사"가 가능하면 사용할 수 있음.<br>
링크 복사하면 이미지가 뜨지 않음.<br>
크기는 전체 공간에서 몇 % 차지할지 또는 길이만 써서 px 단위로 작성 가능.
![이름](URL]{: width="300" height="300"}{: .center}*캡션*<br>
![test](https://cdn-icons-png.flaticon.com/128/13879/13879378.png){: width="300" height="300"}{: .center}*pixel* <br>
![test](https://cdn-icons-png.flaticon.com/128/13879/13879378.png){: width="30%" height="30%"}{: .center}*percentage*

<br>

### 3. 마크다운 문법, 이미지 복사
"이미지 복사' 가능하거나 캠처본이라서 주소가 없을 경우 이미지의 주소를 생성해서 첨부하면 저장공간을 아낄 수 있다. <br>
임의의 레포지토리 > issues > new issues > 텍스트 박스에 이미지 복사 누른 거 붙여넣기 > 잠시 기다리면 마크다운 문법으로 이미지 형식 뜸.
![banana](https://github.com/jkhan94/assests_images_issue/assets/163835909/a1be2a90-0723-4b7c-819b-26f5f378be0f)

<br><br>
<ins>**참고**</ins>
[이슈, 이미지 정렬, 사이즈 조절](https://hyeonjiwon.github.io/blog/markdown_img/) <br>
[이미지 캡션](https://blog.jaeyoon.io/2017/12/jekyll-image.html) <br>
[이슈, 이미지 삽입, 링크 삽입](https://velog.io/@uzchu/Github-%EB%B8%94%EB%A1%9C%EA%B7%B8-image-%EC%82%BD%EC%9E%85%ED%95%98%EA%B8%B0) <br>
[이미지 사이즈 조절](https://blog.yena.io/studynote/2017/11/23/Github-resize-image.html) <br>
[이미지 캠션](https://mohitto55.github.io/gitblog/%EB%A7%88%ED%81%AC%EB%8B%A4%EC%9A%B4-%EC%9D%B4%EB%AF%B8%EC%A7%80-%EC%BA%A1%EC%85%98/)
