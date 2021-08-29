<!DOCTYPE html>
<html>
<title>자유게시판 글작성</title>
<link rel="stylesheet" type="text/css" href="css/color2.css" />
<link rel="stylesheet" type="text/css" href="css/style.css" />
<!-- <body style="
margin-left: 470px;
margin-top: 200px;
width: 400px;
height: 400px;"
> -->

<body>

  <div style="width: 500px;margin: 0 auto;">
    <a href="login_end.html"><h1 style="font-family: 'Dongle-Regular'; font-size:55px;">방방곡곡</h1></a>
  </div>
<div style="width: 500px;  border:3px solid rgb(110, 33, 33);margin: 0 auto;">
  <table>
  <tr>
    <th style="width:80px;font-family: 'Dongle-Regular'; font-size:22px;">제목 :</th>
    <td><p id="title"></p></td>
  </tr>
  <tr>
    <th  style="font-family: 'Dongle-Regular'; font-size:22px;">작성자 :</th>
    <td><p id="userName"></p></td>
  </tr>
  <tr>
    <th style="font-family: 'Dongle-Regular'; font-size:22px;">작성일 :</th>
    <td><p id="write_date"></p></td>
  </tr>
  <tr>
    <th  style="font-family: 'Dongle-Regular'; font-size:22px;"> 내용 :</th>
    <td>
      <pre id=contents></pre>
    </td>   
  </tr>
  <tr>
    <th  style="font-family: 'Dongle-Regular'; font-size:22px;"> 이미지 :</th>
    <td>
      <img id="viewimg" width="100%"/>
    </td>   
  </tr>


</table>
</div>

<div style="width: 500px; margin: 0 auto; padding-top:20px">
  <input button type="button" value='목록' onClick="goList()">
  <div style='width:80px;float: right;'>
    <button onclick="removeContent()">삭제</button>
  </div>
  <div style='width:50px;float: right;'>
    <button onclick="modify()">수정</button>
  </div>
</div>
 
</body>

 

<script>
  helloUser();
    
    function helloUser(){
        let user = document.querySelector('#userName');
        let span = document.createElement("span");
        var usr = JSON.parse(sessionStorage.getItem('__login__'));
        console.log(usr.pw, usr.id);

        user.appendChild(span);
        span.innerText = usr.id;      
    }

  function goList(){
    location.href='list.html?area=' + getParameterByName('area');
  }
  
  getContents();
  function getContents() {
  var contents = JSON.parse(
    localStorage.getItem("contents" + getParameterByName("area"))
  );
  console.log("contents: ", contents);
  if (!contents) {
    contents = [];
  }
  var content = contents[getParameterByName("no") - 1];
  console.log("content: ", content);
  console.log("content: ", content.title);
  console.log("content: ", content.writer);

  const title = document.getElementById("title");
  title.innerText = content.title;
  // document.getElementById("writer").innerText = content.writer;
  document.getElementById("contents").innerText = content.contents;
  var write_date = content.write_date;
  var date = write_date.substr(0, 10);
  document.getElementById("write_date").innerText = date;
  document.getElementById("viewimg").src=content.srcimg;
}
  function modify() {
      if (confirm('수정하시겠습니까?')) {
      location.href = 'modify.html?area=' + getParameterByName('area') + '&no='+getParameterByName('no');
    } else{
      return;
    }
  }
  function removeContent() {
    if (!confirm('삭제하시겠습니까?')){

      return;
    }
    var contents = JSON.parse(localStorage.getItem("contents"+getParameterByName('area')));
    contents.splice(getParameterByName('no')-1,1);
    localStorage.setItem("contents"+getParameterByName('area') , JSON.stringify(contents));
    location.href = 'list.html';
  }
  function getParameterByName(name) { 
    name = name.replace(/[\[]/, "\\[").replace(/[\]]/, "\\]"); 
    var regex = new RegExp("[\\?&]" + name + "=([^&#]*)"), results = regex.exec(location.search); 
    return results == null ? "" : decodeURIComponent(results[1].replace(/\+/g, " ")); }
</script>
</html>
