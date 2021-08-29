<!DOCTYPE html>
<html lang="ko">
<head>
    <title>방방곡곡</title>
    <link rel="stylesheet" type="text/css" href="css/color1.css" />
    <link rel="stylesheet" type="text/css" href="css/style.css" />
</head>
<body style="margin-left:300px;">
    <a href="login_end.html"><h1 style= "font-size: 50px;">방방곡곡</h1></a>
    <!-- <div style="width:723px; height:30px;text-align: right;">
        <label for="area" style ="font-size: 31px;">지역 선택</label>
        <select name="area" id="area">
            <option value="1"; >인천.서울.경기</option>
            <option value="2";>강원도</option>
            <option value="3";>경북.대구</option>
            <option value="4";>충남.대전</option>
            <option value="5";>충북.세종</option>
            <option value="6";>경남.부산.울산</option>
            <option value="7";>전라북도</option>
            <option value="8";>전남.광주</option>
            <option value="9";>제주도</option>
            <option value="10";>울릉도.독도</option>
        </select>
    </div> -->
    
<div>
        <tr>
            <td><b style= "font-size:28px">작성자 : </b><b id="userName" style="font-size:30px"></b></td> 
            <!-- 로그인시 작성자의 아이디를 불러와 p태그로 입력 기존 폼은 삭제 예정 -->
        </tr>
    </br>
        <tr>
            <td><input type="text" id="title" name="title" placeholder="제목"></td>
        </tr>
    </br>
        <tr>
            <td><textarea rows="15" cols="100" type="text" id="contents" name="contents" placeholder="내용을 입력하세요."></textarea>
              </tr>
              <br/>
        <input type="text" id="srcimg" placeholder="이미지 주소를 입력하세요."><br/>
            </br>
            <div class="image-cont" style="padding:10px; height: 250px; width: 400px;" >
                <img style="height: auto; width: 250px;" id="prev_img" src="no.PNG";>
                <input style="display: block; height:max-content;" type="file" accept="image/*" id="input_image" name="input_image" >
            </div>
            <p id="demo"></p>
        <div style="width:723px; text-align: right;">
            <!-- <div style="width:100%; text-align: right;"> -->
                 <button onclick="window.history.back()">취소</button>
                 <button onclick="save()">수정</button>
         </div>
</div>
</div> 
    </body>
<script>
  helloUser()
    function helloUser(){
        let user = document.querySelector('#userName');
        let span = document.createElement("span");
        var usr = JSON.parse(sessionStorage.getItem('__login__'));
        console.log(usr.pw, usr.id);

        user.appendChild(span);
        span.innerText = usr.id;      
    }

    function readImage(input) {
        var img= document.getElementById("input_image").src;
        document.getElementById("demo").innerHTML = img;

    if(input.files && input.files[0]) {
        const reader = new FileReader()
        reader.onload = e => {
            const previewImage = document.getElementById("prev_img")
            previewImage.src = e.target.result
        }
        reader.readAsDataURL(input.files[0])

    }
}
    const inputImage = document.getElementById("input_image")
    inputImage.addEventListener("change", e => {
    readImage(e.target)
})
    getContents();
    function getContents() {
    var contents = JSON.parse(localStorage.getItem("contents"+getParameterByName('area')));
    if (!contents) {
      contents = [];
    }
    var content = contents  [getParameterByName('no')-1];
    document.getElementById('title').value = content.title;
    document.getElementById('srcimg').value = content.srcimg ? content.srcimg  : '';
    // document.getElementById('writer').value = content.writer;
    document.getElementById('contents').value = content.contents;
  }

  function getParameterByName(name) { 
    name = name.replace(/[\[]/, "\\[").replace(/[\]]/, "\\]"); 
    var regex = new RegExp("[\\?&]" + name + "=([^&#]*)"), results = regex.exec(location.search); 
    return results == null ? "" : decodeURIComponent(results[1].replace(/\+/g, " ")); }
    function goList(){
        location.href='list.html?area=' + getParameterByName('area');
        }

    function save() {
      if (!confirm('수정하시겠습니까?')) {
        return;
      }

        var nolist = JSON.parse(localStorage.getItem("contents" + getParameterByName("area")));
        var area = getParameterByName('area');
        var content = nolist[getParameterByName("no") - 1];
        var no = content.no;
        
        var contents = JSON.parse(localStorage.getItem("contents"+area));
      if (!contents) {
          contents = [];
        }
      var srcimg = document.getElementById('srcimg').value;
      var title = document.getElementById('title').value;
      // var writer = document.getElementById('writer').value;
      var content = document.getElementById('contents').value;

      contents[getParameterByName('no')-1]={no:no
        , srcimg:srcimg
        , area:area
        , title:title
        // , writer:writer
        , contents:content
        , write_date:new Date()};
      localStorage.setItem("contents"+area, JSON.stringify(contents));
  
      alert('수정되었습니다.');
      goList();
    }
  </script>
</html>
