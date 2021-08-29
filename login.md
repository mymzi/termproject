<!DOCTYPE html>
<html lang="ko">
<head>
<meta charset="UTF-8">
<title>login</title>
<link rel="stylesheet" type="text/css" href="css/color2.css" />
<link rel="stylesheet" type="text/css" href="css/style.css" />
</head>
<body>
    <div style="width: 350px; height: 300px;margin-left: 400px;margin-top: 100px; padding-left: 100px;border:3px solid rgb(78, 19, 19)">
    <h4 style="font-family: 'Recipekorea'; font-size:40px;">로그인 하기</h4>
    <div style="font-family: 'ONE-Mobile-POP'; font-size:15px;">
        <div>
            <label for="user_id">아이디 :</label>
            <input type="text" id="id">
    </div>
    <div>
            <label for="user_pw">비밀번호 : </label>
            <input type="password" id="pw">
    </div>
            <button onclick="login()">로그인</button>
        <div>
            <p >혹시 회원이 아니신가요?
            <a href="join.html" style="font-family: Recipekorea; font-size: 15px;">회원가입</a></p>
        </div>
    </div>
</body>
<script>
    /*
    0.로그인 버튼 클릭
     - onclick.

    1.input 값과 스토리지에 저장되어있는 값이 같다면
     - if(id input값 정보 == 스토리지 id){
         if(pw input값 정보 == 스토리지 pw){
             로그인 성공!
         } else {
           로그인 실패!
         }}

    2.로그인 성공! 메인화면으로 이동
     - location.href =

    3.실패시 로그인에 (경고)실패하였습니다.
     - alert
    */
    //localStorage.setItem("id", "pw");
    var _login="__login__";

    function moveJoin() {
        location.replace = "join.html";
        self.close();
    }

    function login() {
        var id = document.getElementById('id').value;
        var pw = document.getElementById('pw').value;
        var  _userMat= {
           id:id,
           pw:pw,
          }
        
        //브라우저가 바뀌게 되면 회원가입 홈페이지에 저장하고 있던 변수는 잃어버리게 된다.
        var userInfo = JSON.parse(localStorage.getItem('__user__' + id));
        

        //이중 if문으로 구현 -id 값이랑 pw값 불러와서 비교
        if (id == userInfo.id){
            if (pw == userInfo.pw){
                self.close();
                location.href = 'login_end.html';
            } 
                else {
                alert("로그인 정보를 확인해주세요!");
            }
        } else {
            alert("로그인 실패");
        }
        sessionStorage.setItem(_login, JSON.stringify(_userMat));
    }
</script>
</html>
