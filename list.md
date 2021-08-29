
<!DOCTYPE html>
<html>
  <header>
    <title>방방곡곡</title>
<link rel="stylesheet" type="text/css" href="css/color1.css" />
<link rel="stylesheet" type="text/css" href="css/style.css" />
<style>
  td, th {
          border:solid 1px;
          font-size:22px;
        } 
  table {border-collapse: collapse;}
</style>
<div style="text-align:center;font-size:30px">
  <a href="login_end.html"><h1>방방곡곡</h1></a>
</div>
</header>

<body style="
width: 1000px;
margin-left: 140px;
margin-top: 50px;
">
  <label for="area" style= "font-size:28px;">지역 선택</label>
  <select id="area" onchange="changeLocal()">
      <option value="1">인천.서울.경기</option>
      <option value="2">강원도</option>
      <option value="3">경북.대구</option>
      <option value="4">충남.대전</option>
      <option value="5">충북.세종</option>
      <option value="6">경남.부산.울산</option>
      <option value="7">전라북도</option>
      <option value="8">전남.광주</option>
      <option value="9">제주도</option>
      <option value="10">울릉도.독도</option>
  </select>
  <div style="width:100%; text-align: right;">
    <button onclick="moveForm()">글쓰기</button>
  </div>
<table style="width:100%">
  <tr>
    <th>번호</th>
    <th>제목</th>
    <th>작성자</th>
    <th>작성일</th>
  </tr>
  <tbody id="rows">
      <tr>
          <th>번호</th>
          <th>제목</th>
          <th>작성자</th>
          <th>작성일</th>
        </tr>
        <tr>
            <th>번호</th>
            <th>제목</th>
            <th>작성자</th>
            <th>작성일</th>
          </tr>
  </tbody>
</table>


</body>
<script>
  const url = new URL(location.href);
  
  const urlParams = url.searchParams;

  var sel = document.getElementById("area");
    for(var i=0; i<sel.length; i++){
      if(sel[i].value==urlParams.get('area')){
            sel[i].selected = true;
        }
    }

    changeLocal();

// URLSearchParams.get()
  var area = document.getElementById('area').value;
  console.log(area)
  var contentList = JSON.parse(localStorage.getItem("contents"+area));

  drawRows();
  function moveForm() {
    location.href = 'write.html'
  }

  function drawRows() {
    var templates = '';
    var body = document.getElementById('rows');

    if (contentList) {
      for (var i=contentList.length-1; 0<=i; i--) {
        var content  = contentList[i];
        console.log(content);
        templates += '<tr onclick="moveView('+content.area+','+i+')">';
        templates += '<td style="text-align:center">'+(i+1)+'</td>';
        templates += '<td style="text-align:center">' +content.title+'</td>';
        templates += '<td style="text-align:center" id="userName"></td>';
        templates += '<td style="text-align:center">'+toStringByFormatting(new Date(content.write_date))+'</td>';
        templates += '</tr>';
      }
    }

    body.innerHTML = templates;
  }
   helloUser()


    function helloUser(){
        var user = document.querySelector('#userName');
        var span = document.createElement("span");
        var usr = JSON.parse(sessionStorage.getItem('__login__'));
        console.log(usr.pw, usr.id);

        user.appendChild(span);
        span.innerText = usr.id;      
    }

    // function getUserId(){


    // }
  function moveView(area, contentNo) {
    location.href = 'view.html?area=' + area + '&no='+(contentNo+1);
  }

  function changeLocal() {
    var area = document.getElementById('area').value;
    
    contentList = JSON.parse(localStorage.getItem("contents"+area));
    drawRows();
  }

  function leftPad(value) { if (value >= 10) { return value; } 
  return `0${value}`; } 
  function toStringByFormatting(source, delimiter = '-') {
    const year = source.getFullYear();
    const month = leftPad(source.getMonth() + 1);
    const day = leftPad(source.getDate());
    return [year, month, day].join(delimiter); }
</script>
</html>
