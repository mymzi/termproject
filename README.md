# termproject
<방방곡곡>
프로젝트 개요 
: 본 프로젝트는 여행자들의 여행 기록 작성 및 공유 서비스 수행을 위한 여행 기록 시스템 통합구축프로젝트로서, 다른 사용자와의 기록을 공유하여 여행지 선별에 있어 편리함을 추구함
수행기간 
: 2021년 8월 23일 ~ 2021년 8월 27일 (5일간)
수행 방안
: 개인으로 추진하되, 페이지 병합 후 팀 활동
  - 개인 페이지 구축
  - 페이지 병합 후 서식 통일
  - 검토 및 수정
세부 기간
  - 개인 페이지 구축 : 2021. 08. 23 ~2021. 08. 25 (3일)
  - 페이지 병합 후 서식 통일 : 2021. 08. 25 ~ 2021. 08.26 (2일)
  - 검토 및 수정 : 2021. 08.26 ~ 2021. 08.27 (2일)
프로젝트 배경 및 목표
: 본 프로젝트 목표는 코로나로 인해 국민들의 국내여행에 관한 관심도가 높아져 국내 여행에 관한 정보를 제공하기 위해 게시판 서비스를 운영하는 것
전체 프로젝트 범위
: 여행기록 시스템 통합구축 프로젝트는 HTML, JAVASCRIPT, CSS를 활용하여 기본적인 시스템과 안정적인 서비스를 제공하는 것임
메인 홈페이지 구축
- 전국8도 오버 인터페이스 그축 
  -남녀노소 접근하기 쉬운 방향으로 마우스 오버 인터페이스 적용
- 안목을 끄는 UI 구축
  - 경쟁력을 높이기 위함
  - 이용자들의 재방문율 상승
로그인, 회원가입 기능 구현
- 로그인 팝업
  - 팝업창 로그인을 통해 페이지 이동없는 게시판 진입가능
- 신뢰도 향상
  -로그인을 통해 무분별한 게시판 난입을 방지
유저 커뮤니티 구현
 - 회원제 운영
   - 경험기반 지식을 통한 회원간 추천가능
   - 회원제로 운영함으로써 정보의 신뢰도 향상
지역별 여행 정보 서비스 제공
 - 지역별 정보 제공
   - 전국 시, 도별 여행 정보를 제공함으로써 여행 정보에 관한 궁금증 해소
 - 사진 첨부 가능
   - 사진을 통한 여행지에 관한 사실적인 정보
![flow chart](https://user-images.githubusercontent.com/89428396/130538537-a4b70a53-3e72-4976-aa7d-ba0f3e49b7ae.JPG)

<상세내용 페이지>
<!DOCTYPE html>
<html>
    <head>
        <meta charset="UTF-8">
        <title>문단 정렬</title>
        <style>
            h1{text-align:center;}
            h2{text-align:left;}
            p{text-align:left}
        </style>
    </head>
    <body>
        <h1>방방곡곡</h1>
        <h2>전라남도 순천시 - 순천만 국가정원</h2>
        <p>작성자 :</p>
        <p>작성일 :</p>
    </body>
    <body>
        <img src="순천만.jpg">
        <div style="border:1px dashed #BDBDBD;width: 900px; height: 285px; float: right;">글내용</div>
        <p>
            주소 : 전남 순천시 국가정원1호길 47
        </p>    
    </body>
    <form action = 'login_page.php'>
        <input type = 'button'
               value = '목록'
               outlick = 'alert("목록으로가시겠습니까?")'/>
               &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;
               <button type="button" class="btn btn-info" style="margin-right: 2%;">수정</button>
               <button type="button" class="btn btn-info" style="margin-right: 2%;">삭제</button>
    </form>
  
</html>
