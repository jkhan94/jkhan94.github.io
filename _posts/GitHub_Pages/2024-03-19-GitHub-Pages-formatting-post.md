---
layout: post
title:  "깃허브 포스팅"
date:   2024-03-19
categories: GitHub_Pages
---

1. 헤더 <br>
# 헤더1
## 헤더2
### 헤더3
#### 헤더4
##### 헤더5
###### 헤더6 
<br>

2. 수평선 <br>
  &ensp; 페이지 나눌 때 사용 <br>
  &ensp; 이전 라인을 비워둬야 수평선으로 인식 <br>
  &ensp; 기호 뒤에 태그 붙이지 않아야 수평선으로 인식. eg) ___&lt;br&gt;은 언더바 3개로 인식. <br>
  언더바 3개 <br>
  
  ___ 
  줄표 3개 <br>
  
  ---
  
  <br><br>

3. Indentation(들여쓰기) <br>
  &ensp; 엔터 키나 스페이스로 해도 된다지만 가독성도 떨어지고, 제대로 적용되지 않을 때가 많아 코드로 작성한다.<br>
  &nbsp; &amp;nbsp; 1칸 <br> 
  &ensp; &amp;ensp; 2칸 <br>
  &emsp; &amp;emsp; 3칸 <br><br>


4. New Line(개행, 줄바꿈) <br>
  &lt;br&gt; <br><br>


5. 강조 <br>
  &ensp;이탤릭 &emsp; *Italic star* &emsp; _italic underbar_ <br>
  &ensp;굵게 &emsp; **Bold star** &emsp; __Bold underbar__ <br>
  &ensp;취소선 &emsp; ~~Cancel~~ <br>
  &ensp;굵은 이탤릭 취소선 &emsp; *Italic **bold** ~~cancel~~ star* <br><br>
  

6. URL <br>
   [https://theorydb.github.io/envops/2019/05/22/envops-blog-how-to-use-md/](https://theorydb.github.io/envops/2019/05/22/envops-blog-how-to-use-md/) <br>
   [https://inpa.tistory.com/entry/MarkDown-%F0%9F%93%9A-%EB%A7%88%ED%81%AC%EB%8B%A4%EC%9A%B4-%EB%AC%B8%EB%B2%95-%F0%9F%92%AF-%EC%A0%95%EB%A6%AC#headers_%ED%97%A4%EB%8D%94](https://inpa.tistory.com/entry/MarkDown-%F0%9F%93%9A-%EB%A7%88%ED%81%AC%EB%8B%A4%EC%9A%B4-%EB%AC%B8%EB%B2%95-%F0%9F%92%AF-%EC%A0%95%EB%A6%AC#headers_%ED%97%A4%EB%8D%94) <br><br>


7. 인용구 <br>
   누군가 말하길
   > 잔디는 미리미리 심어야 하고
   > > 되도록이면 해 지기 전에 다 심어야
   > > > 수면시간을 확보할 수 있다고 한다.
   > ###### 헤더도 넣을 수 있고
   > *list
   > 'textbox'      
   <br><br>

8. 리스트 <br>
   Unordered List
   * 기호는 * + - 3가지
     - 리스트 작성할 때는 br 태그 조심
       - 탭으로 미는 게 편함.

   Ordered List
   1. 1번부터 순서대로 숫자 매김
   3. 2 대신 3을 써도 2번으로 출력
      1. 탭으로 밀어넣으면 새 리스트 시작
         3. 그런데 새 리스트 시작할 때는 1로 시작해야 리스트가 제대로 인식되는 듯.
