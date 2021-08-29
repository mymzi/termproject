<!DOCTYPE html>
<html lang="ko">
<head>
<meta charset="UTF-8">
<title>회원가입</title>
<link rel="stylesheet" type="text/css" href="css/color2.css" />
<link rel="stylesheet" type="text/css" href="css/style.css" />
</head>
<body>
    <div style="height:500px;width: 500px;margin-left: 300px;margin-top: 100px;padding-left: 150px;border:3px solid rgb(70, 12, 12)">
        <div>
         <h4 style="font-family:'Recipekorea'; font-size: 40px;">회원가입</h4>
        </div>
        <div style="font-family:'ONE-Mobile-POP';font-size:15px;">
    <label for="user_id">사용할 아이디 : </label>
        <input type="text" id="id" placeholder="영문/숫자 혼합"/><button onclick="checkId()">중복체크</button>
    </br>
    </br>
        <label for="user_name">이름 : </label>
        <input type="text" id="name" placeholder="홍길동">
    </br>
    </br>
        <label for="user_name">이메일 </label>
        <input type="text" id="ml" placeholder="for@example.com">

    </br>
    </br>
    
        <label for="user_pw">사용할 비밀번호 : </label>
        <input type="password" name="wUserPW" id="pw" placeholder="비밀번호" onchange="isSame()">
    </br>
    </br>
        <label for="user_pw">비밀번호 확인 : </label>
        <input type="password" name="wUserPWConfirm" id="pw_chk" placeholder="비밀번호 확인" onchange="isSame()">&nbsp;&nbsp;<span id="same"></span></td>
    </br>
    </br>
    </br>
    </div>
        <button id="btnJoin" onclick="join()" style="margin-left: 216px;" disabled >회원가입</button>
    </div>

</body>
<script>
    /*
    0.회원가입 버튼 클릭

    1.입력값 가져오기
     - document.getElementById('id').value

    2.입력값을 로컬스토리지에 저장
     - document.setElementById('id').value

    3.아이디 중복체크 하고

    4.비밀번호 확인 일치해야

    5.로컬스토리지에 저장
    */
    var _userkey = '__user__' ;

    function join() {
       var id = document.getElementById('id').value;
       var name = document.getElementById('name').value;
       var pw = document.getElementById('pw').value;
       var pw_chk = document.getElementById('pw_chk').value;
       var ml= document.getElementById('ml').value;

       console.log(id, name, pw, pw_chk,ml);

       var userInfo = {
           id:id,
           name:name,
           pw:pw,
           pw_chk:pw_chk,
           ml:ml
       }

       localStorage.setItem(_userkey+id, JSON.stringify(userInfo));
       alert('회원가입이 완료되었습니다.')
        location.replace("main.html");  
    }

    function checkId() {
    document.getElementById('btnJoin').disabled = true;
    var id = document.getElementById('id').value;
    var userInfo = localStorage.getItem(_userkey+id);
    if (userInfo) {
      alert('중복된 아이디입니다.');
      document.getElementById('id').value = null;
      return;
    }
    alert('사용할 수 있는 아이디 입니다.');
    document.getElementById('btnJoin').disabled = false;
    }
   
   function isSame() {
    var pw = document.getElementById('pw').value;    
    var pw_chk = document.getElementById('pw_chk').value;
    if (pw.length < 6 || pw.length > 12) {
        window.alert('비밀번호는 6글자 이상, 12글자 이하만 이용 가능합니다.');
        document.getElementById('pw').value=document.getElementById('pw_chk').value='';
        document.getElementById('same').innerHTML='';
    }
    if(document.getElementById('pw').value!='' && document.getElementById('pw_chk').value!='') {
        if(document.getElementById('pw').value==document.getElementById('pw_chk').value) {
            document.getElementById('same').innerHTML='비밀번호가 일치합니다.';
            document.getElementById('same').style.color='blue';
        }
        else {
            document.getElementById('same').innerHTML='비밀번호가 일치하지 않습니다!!';
            document.getElementById('same').style.color='red';
        }
        
    }
}

    // 비밀번호 체크
 
    
    // 아이디 중복체크
</script>
</html>
