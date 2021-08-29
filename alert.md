<!DOCTYPE html>
<html lang="ko">
<head>
<meta charset="UTF-8">
<title></title>
</head>
<body>
</body>
<script>
    /*
    1.로그인된 사용자인지 확인한다.
        - 로그인이 안되었으면 로그인 페이지로 이동한다.
    2.로그인된 사용자 이름을 보여준다
    */
    loginCheck();
    setUserName();

    function loginCheck() {
      var userName =  sessionStorage.getItem('__login_user_');
      if(!userName) {
          alert('로그인 후 이용하세요.')
          location.replace('login.html');
      }
      _user = JSON.parse(userName);
    }
</script>
</html>
