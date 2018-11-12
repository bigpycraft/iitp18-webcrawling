
# Industry 4.0 의 중심, BigData

<div align='right'><font size=2 color='gray'>Data Processing Based Python @ <font color='blue'><a href='https://www.facebook.com/jskim.kr'>FB / jskim.kr</a></font>, [김진수](bigpycraft@gmail.com)</font></div>
<hr>

## <font color='#CC3333'>TextBook. 파이썬을 이용한 웹크롤링과 스크레이핑 </font>
> <font color='#CC3333'>데이터 수집과 분석을 위한 실전 가이드
<br/>
<font color='#FF5555'>
<b>INDEX. </b>
<br/>
<select name="index">
    <option value="CH00"> 파이썬을 이용한 웹크롤링과 스크레이핑, 데이터 수집과 분석을 위한 실전 가이드 </option>
    <option value="CH00"> ------------------------------------------------------------------------------------------------------------------ </option>
    <option value="CH01"> 01.크롤링과 스크레이핑이란?                      </option>
    <option value="CH02" selected> 02.파이썬으로 시작하는 크롤링/스크레이핑         </option>
    <option value="CH03"> 03.주요 라이브러리 활용                          </option>
    <option value="CH04"> 04.크롤러를 사용할 때 기억해야 하는 것           </option>
    <option value="CH05"> 05.크롤링/스크레이핑 실전과 데이터 활용          </option>
    <option value="CH06"> 06.Scrapy 프레임워크                             </option>
    <option value="CH07"> 07.크롤러의 지속적 운용과 관리                   </option>
</select>
<br/><br/>
<b>APPENDIX </b>
<br/>
<select name="appendix">
    <option value="A00"> 부록: 베이그런트로 개발 환경 구축하기 </option>
    <option value="A00"> ------------------------------------------------------------------------------------------------------------------ </option>
    <option value="A01"> A.1 버추얼박스와 베이그런트             </option>
    <option value="A02"> A.2 CPU 가상화 지원 기능 활성화하기     </option>
    <option value="A03"> A.3 버추얼박스 설치하기                 </option>
    <option value="A04"> A.4 베이그런트 설치하기                 </option>
    <option value="A05"> A.5 가상 머신 실행하기                  </option>
    <option value="A06"> A.6 게스트 OS에 SSH 접속하기            </option>
    <option value="A07"> A.7 리눅스 기본 조작                    </option>
    <option value="A07"> A.8 베이그런트의 가상 머신 조작 명령어  </option>
</select>

<br/>
<hr>

## <font color='#FF5555'>파이썬으로 시작하는 크롤링/스크레이핑 </font>
>   
<font color='#CC3333'>
- 파이썬 기초 지식
- 웹 페이지 추출
- 웹 페이지에서 데이터 추출
- 데이터 저장
- 파이썬으로 스크레이핑하는 흐름

<hr>
### <font color='blue'>  가상환경 사용법
> 
- 가상환경 생성
<br/> \> python -m venv 디렉토리명(myvenv)
<br/> \> .\scraping\Scripts\activate
<br/> \(myvenv) > python --version 
<br/><br/> 
- 가상환경 종료
<br/> \(myvenv) > .\scraping\Scripts\deactivate
<br/> \> dir/w


```python
import os
from os.path import exists

def make_dir(dir_name):
    ''' 디렉토리 생성 '''
    
    if not exists(dir_name):
        os.mkdir(dir_name)
        msg = "{} 디렉토리를 생성하였습니다!".format(dir_name)
    else:
        msg = "{} 디렉토리가 이미 존재합니다!".format(dir_name)
        
    return msg
```

<hr>
### <font color='blue'> 웹 페이지 추출

### <font color='#0000CC'> c2-09_urlopen_encoding
> ** HTTP 헤더에서 인코딩 방식 추출 **
- text/html
- text/html; charset=UTF-8
- text/html; charset=EUC-KR

cf. 연관함수 : HTTPMessage.info().get_content_charset()


```python
import sys
from urllib.request import urlopen
```


```python
f = urlopen('http://www.hanbit.co.kr/store/books/full_book_list.html')

# HTTP 헤더를 기반으로 인코딩 방식을 추출합니다
# (명시돼 있지 않을 경우 utf-8을 사용하게 합니다).
encoding = f.info().get_content_charset(failobj="utf-8")

# 인코딩 방식을 표준 오류에 출력합니다.
print('encoding:', encoding, file=sys.stderr)

```

    encoding: utf-8
    


```python
# 추출한 인코딩 방식으로 디코딩합니다.
text = f.read().decode(encoding)
# 웹 페이지의 내용을 표준 출력에 출력합니다.
text
```




    '<!DOCTYPE html>\r\n<html lang="ko">\r\n<head>\r\n<!--[if lte IE 8]>\r\n<script>\r\n  location.replace(\'/support/explorer_upgrade.html\');\r\n</script>\r\n<![endif]-->\r\n<!-- Google Tag Manager -->\r\n<script>(function(w,d,s,l,i){w[l]=w[l]||[];w[l].push({\'gtm.start\':\r\nnew Date().getTime(),event:\'gtm.js\'});var f=d.getElementsByTagName(s)[0],\r\nj=d.createElement(s),dl=l!=\'dataLayer\'?\'&l=\'+l:\'\';j.async=true;j.src=\r\n\'https://www.googletagmanager.com/gtm.js?id=\'+i+dl;f.parentNode.insertBefore(j,f);\r\n})(window,document,\'script\',\'dataLayer\',\'GTM-W9D5PM3\');</script>\r\n<!-- End Google Tag Manager -->\r\n<meta charset="utf-8"/>\r\n<title>한빛출판네트워크</title>\r\n<link rel="shortcut icon" href="http://www.hanbit.co.kr/images/common/hanbit.ico"> \r\n<meta http-equiv="X-UA-Compatible" content="IE=Edge" />\r\n<meta property="og:type" content="website"/>\r\n<meta property="og:title" content="한빛출판네트워크"/>\r\n<meta property="og:description" content="출판사, IT전문서, 대학교재, 경제경영, 어린이/유아, MAKE, 실용/여행, 전자책, 인터넷 강의"/>\r\n<meta property="og:image" content="http://www.hanbit.co.kr/images/hanbitpubnet_logo.jpg" />\r\n<meta property="og:url" content="http://www.hanbit.co.kr/store/books/full_book_list.html"/>\r\n<link rel="canonical" href="http://www.hanbit.co.kr/store/books/full_book_list.html" />\r\n<meta name="keywords" content="책,전자책,ebook,출판사,동영상,콘텐츠,강의,자격증,대학교재" />\r\n<meta name="description" content="출판사, IT전문서, 대학교재, 경제경영, 어린이/유아, MAKE, 실용/여행, 전자책, 인터넷 강의" />\r\n<meta name="viewport" content="width=device-width,initial-scale=1.0,minimum-scale=1.0,maximum-scale=1.0">\r\n<meta name="viewport" content="width=1260">\r\n<meta name="apple-mobile-web-app-capable" content="yes" />\r\n<meta name="naver-site-verification" content="823ff8b8e7e3eb396c310703c2bbd731f48c1d9b"/>\r\n<link rel="stylesheet" href="/css/common.css" />\r\n<link href="/css/hover.css" rel="stylesheet" media="all">\r\n<link rel="stylesheet" href="/js/jquery.raty.css" />\r\n<script type="text/javascript" src="/js/jquery-latest.js"></script>\r\n<script type="text/javascript" src="/js/jquery-ui.js"></script>\r\n<script type="text/javascript" src="/js/jquery.event.drag-1.5.min.js"></script>\r\n<script type="text/javascript" src="/js/jquery.touchSlider.js"></script>\r\n<script type="text/javascript" src="/js/jquery.raty.js"></script>\r\n<script type="text/javascript" src="/js/main.js"></script>\r\n<script type="text/javascript" src="/lib/cheditor/cheditor.js"></script>\r\n<script type="text/javascript" src="/js/jquery.ui.datepicker-ko.js"></script>\r\n<script type="text/javascript" src="/js/engine.js"></script>\r\n\r\n<!-- Google Analytics -->\r\n<script>\r\n(function(i,s,o,g,r,a,m){i[\'GoogleAnalyticsObject\']=r;i[r]=i[r]||function(){\r\n(i[r].q=i[r].q||[]).push(arguments)},i[r].l=1*new Date();a=s.createElement(o),\r\nm=s.getElementsByTagName(o)[0];a.async=1;a.src=g;m.parentNode.insertBefore(a,m)\r\n})(window,document,\'script\',\'//www.google-analytics.com/analytics.js\',\'ga\');\r\nga(\'create\', \'UA-47080738-1\', \'hanbit.co.kr\');\r\nga(\'require\', \'linkid\', \'linkid.js\');\r\nga(\'send\', \'pageview\');\r\n</script>\r\n<!-- Google Analytics -->\r\n\r\n<!-- Facebook Pixel Code -->\r\n<script>\r\n!function(f,b,e,v,n,t,s)\r\n{if(f.fbq)return;n=f.fbq=function(){n.callMethod?\r\nn.callMethod.apply(n,arguments):n.queue.push(arguments)};\r\nif(!f._fbq)f._fbq=n;n.push=n;n.loaded=!0;n.version=\'2.0\';\r\nn.queue=[];t=b.createElement(e);t.async=!0;\r\nt.src=v;s=b.getElementsByTagName(e)[0];\r\ns.parentNode.insertBefore(t,s)}(window,document,\'script\',\r\n\'https://connect.facebook.net/en_US/fbevents.js\');\r\n fbq(\'init\', \'1816595558587562\'); \r\nfbq(\'track\', \'PageView\');\r\n</script>\r\n<noscript>\r\n <img height="1" width="1" \r\nsrc="https://www.facebook.com/tr?id=1816595558587562&ev=PageView\r\n&noscript=1"/>\r\n</noscript>\r\n<!-- End Facebook Pixel Code -->\r\n</head>\r\n<body>\r\n<!-- Google Tag Manager (noscript) -->\r\n<noscript><iframe src="https://www.googletagmanager.com/ns.html?id=GTM-W9D5PM3"\r\nheight="0" width="0" style="display:none;visibility:hidden"></iframe></noscript>\r\n<!-- End Google Tag Manager (noscript) --><link rel="stylesheet" href="/css/layout-hanbit.css" />\r\n<link rel="stylesheet" href="/css/layout-member.css" />\r\n<link rel="stylesheet" href="/css/layout-network.css" />\r\n<link rel="stylesheet" href="/css/layout-store.css" />\r\n<link rel="stylesheet" href="/css/layout-myhanbit.css" />\r\n<link rel="stylesheet" href="/css/layout-event.css" />\r\n<!-- 메뉴 바로가기 -->\r\n<div id="quick_skip_menu">\r\n  <a href="#gnb" onclick="document.getElementById(\'gnb\').tabIndex = -1;document.getElementById(\'gnb\').focus();return false;"><span>메뉴 바로가기</span></a>\r\n  <a href="#top_search" onclick="view_hover(\'main_search_area\',\'\',\'show\'), document.getElementById(\'top_search\').tabIndex = -1;document.getElementById(\'top_search\').focus();return false;"><span>검색 및 카테고리 바로가기</span></a>\r\n    <a href="#container" onclick="document.getElementById(\'container\').tabIndex = -1;document.getElementById(\'container\').focus();return false;"><span>본문 바로가기</span></a>\r\n  </div>\r\n<!-- //메뉴 바로가기 -->\r\n\r\n<!-- header -->\r\n<header>\r\n  <!-- top menu -->\r\n  \t<nav>\r\n\t\t<div id="wrap_nav">\r\n\t\t\t<ul class="top_brand">\r\n\t\t\t\t<li><a href="http://www.hanbit.co.kr/index.html" name="hanbit_network"><span>HOME</span></a></li>\r\n\t\t\t\t<li><a href="http://www.hanbit.co.kr/media/">한빛미디어</a></li>\r\n\t\t\t\t<li><a href="http://www.hanbit.co.kr/academy/">한빛아카데미</a></li>\r\n\t\t\t\t<li><a href="http://www.hanbit.co.kr/biz/">한빛비즈</a></li>\r\n\t\t\t\t<li><a href="http://www.hanbit.co.kr/life/">한빛라이프</a></li>\r\n\t\t\t\t<li><a href="http://www.hanbit.co.kr/edu/">한빛에듀</a></li>\r\n\t\t\t\t<li><a href="http://www.hanbit.co.kr/realtime/">리얼타임</a></li>\r\n\t\t\t\t<li><a href="http://www.hanbit.co.kr/textbook/" target="_blank">한빛정보교과서</a></li>\r\n        <li><a href="http://www.hanbit.co.kr/rent/" target="_blank">한빛대관서비스</a></li>\r\n\t\t\t</ul>\r\n\t\t\t\r\n\t\t\t<ul class="top_menu">\r\n                        \t<li><a href="http://www.hanbit.co.kr/member/login.html" class="login">로그인</a></li>\r\n\t\t\t\t<li><a href="http://www.hanbit.co.kr/member/member_agree.html" class="join">회원가입</a></li>\r\n\t\t\t\t<li><a href="http://www.hanbit.co.kr/myhanbit/myhanbit.html" class="myhanbit">마이한빛</a></li>\r\n\t\t\t\t<li><a href="http://www.hanbit.co.kr/myhanbit/cart.html" class="cart">장바구니</a></li>\r\n            \t\t\t\t<!-- <li class="top_menu_store"><a href="http://www.hanbit.co.kr/store/store_submain.html">STORE</a></li> -->\r\n\t\t\t</ul>\r\n\t\t</div>\r\n\t</nav>  <!-- //top menu -->\r\n\r\n  <div id="wrap_gnb">\r\n    <!-- logo -->\r\n    <h1><a href="http://www.hanbit.co.kr/index.html">한빛출판네트워크</a></h1>\r\n    <!-- //logo -->\r\n\r\n    <!-- Menu -->\r\n    <div id="gnb" name="gnb">\r\n      <ul>\r\n        <li><a href="http://www.hanbit.co.kr/brand/brand_submain.html" class="">BRAND</a></li>\r\n        <li><a href="http://www.hanbit.co.kr/channel/channel_submain.html" class="">Channel.H</a></li>\r\n        <li><a href="http://www.hanbit.co.kr/store/store_submain.html" class="curr">STORE</a></li>\r\n        <li><a href="http://www.hanbit.co.kr/support/help_info.html" class="">SUPPORT</a></li>\r\n        <li><a href="http://www.hanbit.co.kr/event/current/current_event_list.html" class="">EVENT</a></li>\r\n        \r\n        <li id="top_search" class="search"><a href="javascript:;" onClick="view_hover(\'main_search_area\',\'\',\'show\'); $(\'#keyword_str\').focus();"><span>SERACH</span></a></li>\r\n      </ul>\r\n    </div>\r\n    <!-- //Menu -->\r\n    \r\n    <!-- lnb -->\r\n    <div class="lnb" style="top:92px;">\r\n      <div class="lnb_area">\r\n      <!-- BRAND -->\r\n            <ul class="lnb_depth1_category">\r\n        <li onmouseover="view_hover(\'category_store\',\'\',\'show\')" onMouseOut="view_hover(\'category_store\',\'\',\'hide\')"><a href="#" onFocus="view_hover(\'category_store\',\'\',\'show\')" class="gnb_category">카테고리</a>\r\n          <ul id="category_store">\r\n\r\n                          <li onmouseover="view_hover(\'category_store1\',\'\',\'show\')" onMouseOut="view_hover(\'category_store1\',\'\',\'hide\')"><a href="/store/books/category_list.html?cate_cd=001" onFocus="view_hover(\'category_store1\',\'\',\'show\')">IT/모바일</a>\r\n                <ul id="category_store1">\r\n                              <li><a href="/store/books/category_list.html?cate_cd=001001">프로그래밍</a></li>      \r\n                              <li><a href="/store/books/category_list.html?cate_cd=001002">웹</a></li>      \r\n                              <li><a href="/store/books/category_list.html?cate_cd=001003">모바일/스마트기기</a></li>      \r\n                              <li><a href="/store/books/category_list.html?cate_cd=001013">데이터베이스</a></li>      \r\n                              <li><a href="/store/books/category_list.html?cate_cd=001005">운영체제</a></li>      \r\n                              <li><a href="/store/books/category_list.html?cate_cd=001014">하드웨어</a></li>      \r\n                              <li><a href="/store/books/category_list.html?cate_cd=001015">시스템/네트워크</a></li>      \r\n                              <li><a href="/store/books/category_list.html?cate_cd=001016">보안</a></li>      \r\n                              <li><a href="/store/books/category_list.html?cate_cd=001009">비즈니스/문화</a></li>      \r\n                              <li><a href="/store/books/category_list.html?cate_cd=001010">게임</a></li>      \r\n                              <li><a href="/store/books/category_list.html?cate_cd=001017">IT에세이</a></li>      \r\n                              <li><a href="/store/books/category_list.html?cate_cd=001012">자격증</a></li>      \r\n              </ul></li>              <li onmouseover="view_hover(\'category_store2\',\'\',\'show\')" onMouseOut="view_hover(\'category_store2\',\'\',\'hide\')"><a href="/store/books/category_list.html?cate_cd=002" onFocus="view_hover(\'category_store2\',\'\',\'show\')">MAKE</a>\r\n                <ul id="category_store2">\r\n                              <li><a href="/store/books/category_list.html?cate_cd=002001">Make 매거진</a></li>      \r\n                              <li><a href="/store/books/category_list.html?cate_cd=002002">Make 프로젝트 북</a></li>      \r\n              </ul></li>              <li onmouseover="view_hover(\'category_store3\',\'\',\'show\')" onMouseOut="view_hover(\'category_store3\',\'\',\'hide\')"><a href="/store/books/category_list.html?cate_cd=003" onFocus="view_hover(\'category_store3\',\'\',\'show\')">IT활용</a>\r\n                <ul id="category_store3">\r\n                              <li><a href="/store/books/category_list.html?cate_cd=003001">오피스/OA</a></li>      \r\n                              <li><a href="/store/books/category_list.html?cate_cd=003002">그래픽/멀티미디어</a></li>      \r\n                              <li><a href="/store/books/category_list.html?cate_cd=003003">사진/예술</a></li>      \r\n                              <li><a href="/store/books/category_list.html?cate_cd=003004">컴퓨터입문/IT교양</a></li>      \r\n              </ul></li>              <li onmouseover="view_hover(\'category_store4\',\'\',\'show\')" onMouseOut="view_hover(\'category_store4\',\'\',\'hide\')"><a href="/store/books/category_list.html?cate_cd=004" onFocus="view_hover(\'category_store4\',\'\',\'show\')">대학교재</a>\r\n                <ul id="category_store4">\r\n                              <li><a href="/store/books/category_list.html?cate_cd=004007">컴퓨터공학</a></li>      \r\n                              <li><a href="/store/books/category_list.html?cate_cd=004008">정보통신/전기/전자</a></li>      \r\n                              <li><a href="/store/books/category_list.html?cate_cd=004003">수학/과학/공학</a></li>      \r\n                              <li><a href="/store/books/category_list.html?cate_cd=004004">프로그래밍/웹</a></li>      \r\n                              <li><a href="/store/books/category_list.html?cate_cd=004005">그래픽/디자인</a></li>      \r\n                              <li><a href="/store/books/category_list.html?cate_cd=004006">OA/활용</a></li>      \r\n              </ul></li>              <li onmouseover="view_hover(\'category_store5\',\'\',\'show\')" onMouseOut="view_hover(\'category_store5\',\'\',\'hide\')"><a href="/store/books/category_list.html?cate_cd=005" onFocus="view_hover(\'category_store5\',\'\',\'show\')">수험서</a>\r\n                <ul id="category_store5">\r\n                              <li><a href="/store/books/category_list.html?cate_cd=005005">전기기본서</a></li>      \r\n                              <li><a href="/store/books/category_list.html?cate_cd=005001">전기기사</a></li>      \r\n                              <li><a href="/store/books/category_list.html?cate_cd=005002">전기산업기사</a></li>      \r\n                              <li><a href="/store/books/category_list.html?cate_cd=005003">전기공사기사</a></li>      \r\n                              <li><a href="/store/books/category_list.html?cate_cd=005004">전기공사산업기사</a></li>      \r\n              </ul></li>              <li onmouseover="view_hover(\'category_store6\',\'\',\'show\')" onMouseOut="view_hover(\'category_store6\',\'\',\'hide\')"><a href="/store/books/category_list.html?cate_cd=006" onFocus="view_hover(\'category_store6\',\'\',\'show\')">실용서</a>\r\n                <ul id="category_store6">\r\n                              <li><a href="/store/books/category_list.html?cate_cd=006001">취미/실용</a></li>      \r\n                              <li><a href="/store/books/category_list.html?cate_cd=006002">여행</a></li>      \r\n                              <li><a href="/store/books/category_list.html?cate_cd=006003">건강</a></li>      \r\n                              <li><a href="/store/books/category_list.html?cate_cd=006004">유아/육아</a></li>      \r\n              </ul></li>              <li onmouseover="view_hover(\'category_store7\',\'\',\'show\')" onMouseOut="view_hover(\'category_store7\',\'\',\'hide\')"><a href="/store/books/category_list.html?cate_cd=007" onFocus="view_hover(\'category_store7\',\'\',\'show\')">경제/경영/인문</a>\r\n                <ul id="category_store7">\r\n                              <li><a href="/store/books/category_list.html?cate_cd=007001">경제/경영</a></li>      \r\n                              <li><a href="/store/books/category_list.html?cate_cd=007002">자기계발</a></li>      \r\n                              <li><a href="/store/books/category_list.html?cate_cd=007003">인문/교양</a></li>      \r\n                              <li><a href="/store/books/category_list.html?cate_cd=007004">마케팅</a></li>      \r\n                              <li><a href="/store/books/category_list.html?cate_cd=007005">에세이</a></li>      \r\n              </ul></li>              <li onmouseover="view_hover(\'category_store8\',\'\',\'show\')" onMouseOut="view_hover(\'category_store8\',\'\',\'hide\')"><a href="/store/books/category_list.html?cate_cd=008" onFocus="view_hover(\'category_store8\',\'\',\'show\')">유아/어린이/초등</a>\r\n                <ul id="category_store8">\r\n                              <li><a href="/store/books/category_list.html?cate_cd=008001">4~6세</a></li>      \r\n                              <li><a href="/store/books/category_list.html?cate_cd=008002">5~7세</a></li>      \r\n                              <li><a href="/store/books/category_list.html?cate_cd=008003">예비초등</a></li>      \r\n                              <li><a href="/store/books/category_list.html?cate_cd=008004">초등교과연계 1~12영역</a></li>      \r\n                              <li><a href="/store/books/category_list.html?cate_cd=008005">초등 전학년</a></li>      \r\n              </ul></li>            \r\n          <!-- 항상 노출 메뉴 -->          \r\n          <li class="gnb_category_series"><a href="http://www.hanbit.co.kr/store/books/series_list.html">시리즈</a></li>\r\n          <li class="gnb_category_reservations"><a href="http://www.hanbit.co.kr/store/books/reservations_list.html">예약도서</a></li>\r\n          <!--\r\n          <li class="gnb_category_full"><a href="http://www.hanbit.co.kr/store/books/full_book_list.html">전체도서목록</a></li>\r\n          -->\r\n          <!--/li-->\r\n        </ul>\r\n      </ul>\r\n      <!--/li-->        \r\n      <!--/ul-->\r\n\r\n      <ul class="lnb_depth1">\r\n        <li><a href="http://www.hanbit.co.kr/store/books/new_book_list.html">새로나온 책</a></li><span>l</span>\r\n        <li><a href="http://www.hanbit.co.kr/store/books/bestseller_list.html">베스트셀러</a></li><span>l</span>\r\n        <li><a href="http://www.hanbit.co.kr/store/books/full_book_list.html">전체도서목록</a></li><span>l</span>\r\n        <li><a href="http://www.hanbit.co.kr/store/education/edu_list.html">교육</a></li><span>l</span>\r\n        <li><a href="http://www.hanbit.co.kr/store/item/item_list.html">Item &amp; Maker Shed</a></li>\r\n      </ul>\r\n      \r\n      <!-- SUPPORT -->\r\n          </div>\r\n    </div>\r\n    <!--// lnb -->\r\n  </div>\r\n</header>\r\n<!-- //header -->\r\n\r\n<!-- 메인 검색 및 카테고리 영역 -->\r\n<div id="main_search_area" class="fixed" style="display:none;">\r\n\t<div class="msa_wrap">\r\n\t\t<div class="msa_wrap_btn"><a href="javascript:;" onClick="view_hover(\'main_search_area\',\'\',\'hide\')">닫기</a></div>\r\n\t\t\r\n\t\t<!-- [S]카테고리 -->\r\n\t\t<div class="msa_wrap_l">\t\t\t\t\t\t\t\t\r\n\t\t\t<!-- 카테고리 노출 -->\r\n\t\t\t<p class="tit">카테고리</p>\t\t\t\t\t\t\t\t\r\n\t\t\t<ul class="cate_1depth" id="cate1_depth"></ul>\t\t\t\t\t\t\t\r\n\t\t\t<ul class="cate_3depth" id="cate2_depth"></ul>\t\t\t\t\t\t\t\t\t\t\t\t\r\n\t\t</div>\r\n\t\t<!-- [E]//카테고리 -->\r\n\r\n\r\n\t\t<!-- [S]검색 -->\r\n\t\t<div class="msa_wrap_r">\r\n\t\t\t<p class="txt">제목, 저자, ISBN으로 검색이 가능합니다.</p>\r\n\t\t\t<!-- 검색창 -->\r\n\t\t\t<form name="gnbsearchfrm" id="gnbsearchfrm" method="get" onload="form.keyword_str.focus;">\r\n\t\t\t\r\n\t\t\t\t\t\t\t<!-- 선택 카테고리 결과값 -->\t\t\t\t\t\t\r\n\t\t\t\t<div class="msa_wrap_r_srch">\r\n\t\t\t\t\t<fieldset>\r\n\t\t\t\t\t\t<legend>검색영역</legend>\r\n\t\t\t\t\t\t<input title="검색어" class="srch_keyword" accesskey="s" type="text" name="keyword_str" id="keyword_str">\t\t\t\t\t\r\n\t\t\t\t\t\t<input type="submit" alt="" class="srch_btn" onclick="sch_smit();" style="cursor:pointer;">\r\n\t\t\t\t\t</fieldset>\r\n\t\t\t\t</div>\t\t\t\t\r\n\t\t\t</form>\t\t\t\r\n\t\t\t<!-- //검색창 -->\r\n\t\t\t\r\n\t\t</div>\r\n\t\t<!-- [E]//검색 -->\r\n\t\t\r\n\t</div>\r\n</div>\r\n\r\n<style>\r\n\t.normal_css{ font-weight:normal;}\r\n\t.bold_css{  font-weight:bold;}\r\n</style>\r\n\r\n\r\n<script type="text/javascript">\t\r\n\t//[뎁스1] 브랜드 리스트\r\n\t$(document).ready(function() { \t\t\t\t\r\n\t\tdepth_list("cate1");\t\t\t\t\r\n\t});\t\r\n\t\r\n\t// 카테고리 리스트\t\r\n\tfunction depth_list(str , cate_cd){\t\t\t\t\t\r\n\t\tvar cate_str;\t\t\t\r\n\t\t\t\t\t\t\r\n\t\tif(str=="cate1")cate_str = "cate2";\r\n\t\telse cate_str = "choice";\t\r\n\r\n\t\t\t\t\r\n\t\t//카테고리1 선택\t\t\t\r\n\t\tif(str == "cate2"){\t\t\t\t\t\t\t\t\t\t\r\n\t\t\t$("li[name=\'cate1\']").removeClass("bold_css");\t\t\t\t\t\t\t\r\n\t\t\t$( "#"+cate_cd ).addClass("bold_css");\t\t\t\t\t\t\t\t\t\t\t\t\r\n\t\t\t$("#sch_cate1").val(cate_cd); \r\n\t\t\t$("#sch_cate2").val("");\t\t\t\t\r\n\t\t}\t\t\t\t\r\n\t\t\r\n\t\t//카테고리2 선택\t\t\t\r\n\t\tif(str == "choice"){ \t\t\t\t\t\r\n\t\t\t$("li[name=\'cate2\']").removeClass("bold_css");\t\t\t\t\t\t\t\r\n\t\t\t$( "#"+cate_cd ).addClass("bold_css");\t\t\t\t\t\t\r\n\t\t\t$("#sch_cate2").val(cate_cd); \t\t\t\t\t\t\r\n\t\t}\t\r\n\t\r\n\t\t\t\t\t\t\r\n\t\t//카테고리선택 >> 하위카테고리 데이터 정보\t\t\t\r\n\t\tvar depth_html = ""; \t\t\t\t\t\t\t\t\t\t\t\t\t\t\t\t\t\t\t\t\t\t\t\t\r\n\t\t$.ajax({\r\n\t\t\ttype:"post",\r\n\t\t\turl: "/inc/common_top_search_ajax.php",\r\n\t\t\tdata: { depth_attr : str,cate_cd : cate_cd},\r\n\t\t\tdataType : "json",\t\t\t\t\t\t\t\t\r\n\t\t\tsuccess: function(response){\t\t\t\t\t\t\t\t\t\r\n\t\t\t\r\n\t\t\t\tresponse = JSON.stringify(response);\t\t\t\t\t\t\t\t\t\t\t\t\t\t \r\n\t\t\t\t$.each($.parseJSON(response), function(idx, obj) {\t\t\t\t\t\r\n\t\t\t\t\tdepth_html\t+= \'<li id="\'+obj.cate_cd+\'" name="\'+str+\'" onMouseOver="javascript:depth_list(\\\'\'+cate_str+\'\\\', \\\'\'+obj.cate_cd+\'\\\',\\\'\\\');"><a href="/store/books/category_list.html?cate_cd=\'+obj.cate_cd+\'">\'+obj.cate_nm+\'</a></li>\';\t\t\t\t\t\t\t\t\t\t\t\t\t\t\t\t\t\t\t\t\t\r\n\t\t\t\t});\t\t\t\t\t\t\t\t\t\t\t\t\t\t\t\t\t\t\t\t\r\n\t\t\t\t$("#"+str+"_depth").html("");\t\t\t\t\t\t\r\n\t\t\t\t$("#"+str+"_depth").html(depth_html);\t\t\t\t\r\n\t\t\t}\t \t\t\t\r\n\t\t});\t\t\t\t\t\t\t\t\t\t\t\t\t\t\t\r\n\t}\r\n\t\r\n\t// 검색 리스트\t\r\n\tfunction sch_smit(){\t\t\t\t\t\t\r\n\t\r\n\t\tif(!$.trim($("#keyword_str").val()).length) {\r\n\t\t\talert("검색어를 입력해주세요");\r\n\t\t\t$("#keyword_str").focus();\r\n\t\t\treturn false;\r\n\t\t}else{\r\n\t\t\t$("#gnbsearchfrm").attr("action","/search/search_list.html");\r\n\t\t\t$("#gnbsearchfrm").submit(); \r\n\t\t}\t\t\t\t\t\t\t\t\t\t\t\t\t\t\t\t\t\t\t\t\t\t\t\r\n\t}\t\t\t\t\t\t\t\t\r\n\r\n</script>\r\n<!-- //메인 검색 및 카테고리 영역 -->\r\n<!-- Contents -->\r\n<div id="container">\r\n\t<div class="docu_title">\r\n\t\t<h2>전체도서목록</h2>\r\n\t</div>\r\n\t\r\n\t<!-- 전체도서목록 wrap -->\r\n\t<div class="full_book_list_wrap">\r\n\t\t<!-- 브랜드 정렬 버튼 -->\r\n\t\t\r\n        <div class="btn_brand_area">       \r\n\t\t\t<ul>\r\n\t\t\t\t<li class="curr">\r\n                \t<a href="/store/books/full_book_list.html">\r\n                    \t                    <span class="name_full">전체</span>\r\n                                        </a>\r\n                    \r\n                </li>\r\n\t\t\t\t<li >\r\n\t\t\t\t\t<a href="/store/books/full_book_list.html?brand=HM">\r\n                                        \t<span class="name_abbr">M</span>\r\n                    \t\t\t\t\t</a>\r\n\t\t\t\t</li>\r\n\r\n\t\t\t\t<li >\r\n                \t<a href="/store/books/full_book_list.html?brand=HA">\r\n                                        \t<span class="name_abbr">A</span>\r\n                    \t\t\t\t\t</a>\r\n                </li>\r\n\t\t\t\t<li >\r\n                \t<a href="/store/books/full_book_list.html?brand=HB">\r\n                                        \t<span class="name_abbr">B</span>\r\n                    \t\t\t\t\t</a>\r\n                </li>\r\n\t\t\t\t<li >\r\n                \t<a href="/store/books/full_book_list.html?brand=HL">\r\n                                        \t<span class="name_abbr">L</span>\r\n                    \t\t\t\t\t</a>\r\n                </li>\r\n\t\t\t\t<li >\r\n                \t<a href="/store/books/full_book_list.html?brand=HE">\r\n                                        \t<span class="name_abbr">E</span>\r\n                    \t\t\t\t\t</a>\r\n                </li>\r\n\t\t\t\t<li >\r\n                \t<a href="/store/books/full_book_list.html?brand=HR">\r\n                                        \t<span class="name_abbr">R</span>\r\n                    \t\t\t\t\t</a>\r\n                </li>\r\n\t\t\t\t<li >\r\n                \t<a href="/store/books/full_book_list.html?brand=MK">\r\n                                        \t<span class="name_abbr">MK</span>\r\n                    \t\t\t\t\t</a>\r\n                </li>\r\n\t\t\t\t\r\n\t\t\t</ul>\r\n\t\t</div>\r\n\r\n\r\n\r\n\t\t<!-- //브랜드 정렬 버튼 -->\r\n\t\t\r\n\t\t<!-- 출간일/도서명 순-->\r\n\t\t<div class="series_lineup">\r\n\t\t\t<ul>\r\n\t\t\t\t<li><a href="/store/books/full_book_list.html?srt=p_pub_date&brand="  class="curr" >출간일 순</a></li>\r\n\t\t\t\t<li><a href="/store/books/full_book_list.html?srt=p_title&brand=" >도서명 순</a></li>\r\n\t\t\t</ul>\r\n\t\t</div>\r\n\t\t<!-- //출간일/도서명 순-->\r\n\t\t\r\n\t\t<!-- 전체 목록 다운로드 버튼-->\r\n\t\t<div class="btn_full_list"><a href="javascript:document.frm.submit();">전체 목록 다운로드</a></div>\r\n\t\t\r\n\t\t<!-- 책 리스트 -->\r\n\t\t<div class="table_area">\r\n\t\t\t<table class="tbl_type_list" border="0" cellspacing="0" summary="전체목록 리스트 테이블">\r\n\t\t\t\t<caption>전체목록 리스트</caption>\r\n\t\t\t\t<colgroup>\r\n\t\t\t\t<col width="180px">\r\n\t\t\t\t<col width="">\r\n\t\t\t\t<col width="160px">\r\n\t\t\t\t<col width="134px">\r\n\t\t\t\t<col width="130px">\r\n\t\t\t\t</colgroup>\r\n\t\t\t\t<thead>\r\n\t\t\t\t\t<tr>\r\n\t\t\t\t\t\t<th scope="col">브랜드</th>\r\n\t\t\t\t\t\t<th scope="col">도서명</th>\r\n\t\t\t\t\t\t<th scope="col">저자</th>\r\n\t\t\t\t\t\t<th scope="col">발행일</th>\r\n\t\t\t\t\t\t<th scope="col">정가</th>\r\n\t\t\t\t\t</tr>\r\n\t\t\t\t</thead>\r\n\t\t\t\t<tbody>\r\n\t\t\t\t\t\t\t\t\t<tr>\r\n\t\t\t\t\t\t<td class="brd_e">한빛에듀</td>\r\n\t\t\t\t\t\t<td class="left"><a href="/store/books/look.php?p_code=B6994299591">재미있고 빠른 한글 2권 : 기본 자음과 쌍자음</a></td>\r\n\t\t\t\t\t\t\t\t\t\t\t\t\t<td class="left">이도한글교육연구회 김두섭(대표 저자)   </td>\r\n\t\t\t\t\t\t\t\t\t\t\t\t<td>2018-12-01</td>\r\n\t\t\t\t\t\t<td class="right">7,000원</td>\r\n\t\t\t\t\t</tr>\r\n\r\n\t\t\t\t\t\t\t\t\t\t<tr>\r\n\t\t\t\t\t\t<td class="brd_e">한빛에듀</td>\r\n\t\t\t\t\t\t<td class="left"><a href="/store/books/look.php?p_code=B8463831992">재미있고 빠른 한글 4권 : 복잡한 모음</a></td>\r\n\t\t\t\t\t\t\t\t\t\t\t\t\t<td class="left">이도한글교육연구회 김두섭(대표 저자)   </td>\r\n\t\t\t\t\t\t\t\t\t\t\t\t<td>2018-12-01</td>\r\n\t\t\t\t\t\t<td class="right">7,000원</td>\r\n\t\t\t\t\t</tr>\r\n\r\n\t\t\t\t\t\t\t\t\t\t<tr>\r\n\t\t\t\t\t\t<td class="brd_a">한빛아카데미</td>\r\n\t\t\t\t\t\t<td class="left"><a href="/store/books/look.php?p_code=B3283906872">IT CookBook, 시스템 해킹과 보안&#40;3판&#41;</a></td>\r\n\t\t\t\t\t\t\t\t\t\t\t\t\t<td class="left">양대일   </td>\r\n\t\t\t\t\t\t\t\t\t\t\t\t<td>2018-11-12</td>\r\n\t\t\t\t\t\t<td class="right">27,000원</td>\r\n\t\t\t\t\t</tr>\r\n\r\n\t\t\t\t\t\t\t\t\t\t<tr>\r\n\t\t\t\t\t\t<td class="brd_m">한빛미디어</td>\r\n\t\t\t\t\t\t<td class="left"><a href="/store/books/look.php?p_code=B8608817158">IT 트렌드 스페셜 리포트 2019</a></td>\r\n\t\t\t\t\t\t\t\t\t\t\t\t\t<td class="left">김석기외 4명  </td>\r\n\t\t\t\t\t\t\t\t\t\t\t\t<td>2018-11-05</td>\r\n\t\t\t\t\t\t<td class="right">17,800원</td>\r\n\t\t\t\t\t</tr>\r\n\r\n\t\t\t\t\t\t\t\t\t\t<tr>\r\n\t\t\t\t\t\t<td class="brd_m">한빛미디어</td>\r\n\t\t\t\t\t\t<td class="left"><a href="/store/books/look.php?p_code=B4851649517">Accelerated C++</a></td>\r\n\t\t\t\t\t\t\t\t\t\t\t\t\t<td class="left">앤드루 쾨니히(Andrew Koenig) 외 1명  </td>\r\n\t\t\t\t\t\t\t\t\t\t\t\t<td>2018-11-05</td>\r\n\t\t\t\t\t\t<td class="right">30,000원</td>\r\n\t\t\t\t\t</tr>\r\n\r\n\t\t\t\t\t\t\t\t\t\t<tr>\r\n\t\t\t\t\t\t<td class="brd_m">한빛미디어</td>\r\n\t\t\t\t\t\t<td class="left"><a href="/store/books/look.php?p_code=B1266184916">한 권으로 끝내는 딥러닝 텐서플로</a></td>\r\n\t\t\t\t\t\t\t\t\t\t\t\t\t<td class="left">바라스 람순다르 Bharath Ramsundar 외 1명  </td>\r\n\t\t\t\t\t\t\t\t\t\t\t\t<td>2018-11-05</td>\r\n\t\t\t\t\t\t<td class="right">24,000원</td>\r\n\t\t\t\t\t</tr>\r\n\r\n\t\t\t\t\t\t\t\t\t\t<tr>\r\n\t\t\t\t\t\t<td class="brd_m">한빛미디어</td>\r\n\t\t\t\t\t\t<td class="left"><a href="/store/books/look.php?p_code=B8718279503">파이썬으로 배우는 머신러닝의 교과서</a></td>\r\n\t\t\t\t\t\t\t\t\t\t\t\t\t<td class="left">이토 마코토   </td>\r\n\t\t\t\t\t\t\t\t\t\t\t\t<td>2018-11-01</td>\r\n\t\t\t\t\t\t<td class="right">29,000원</td>\r\n\t\t\t\t\t</tr>\r\n\r\n\t\t\t\t\t\t\t\t\t\t<tr>\r\n\t\t\t\t\t\t<td class="brd_m">한빛미디어</td>\r\n\t\t\t\t\t\t<td class="left"><a href="/store/books/look.php?p_code=B5331040931">좋은 사진을 만드는 ZAKO의 여행 사진 잘 찍는 법</a></td>\r\n\t\t\t\t\t\t\t\t\t\t\t\t\t<td class="left">ZAKO   </td>\r\n\t\t\t\t\t\t\t\t\t\t\t\t<td>2018-10-31</td>\r\n\t\t\t\t\t\t<td class="right">22,000원</td>\r\n\t\t\t\t\t</tr>\r\n\r\n\t\t\t\t\t\t\t\t\t\t<tr>\r\n\t\t\t\t\t\t<td class="brd_a">한빛아카데미</td>\r\n\t\t\t\t\t\t<td class="left"><a href="/store/books/look.php?p_code=B3696148245">2019 전기기사 필기 7개년 기출문제</a></td>\r\n\t\t\t\t\t\t\t\t\t\t\t\t\t<td class="left">김상훈   </td>\r\n\t\t\t\t\t\t\t\t\t\t\t\t<td>2018-10-31</td>\r\n\t\t\t\t\t\t<td class="right">22,000원</td>\r\n\t\t\t\t\t</tr>\r\n\r\n\t\t\t\t\t\t\t\t\t\t<tr>\r\n\t\t\t\t\t\t<td class="brd_a">한빛아카데미</td>\r\n\t\t\t\t\t\t<td class="left"><a href="/store/books/look.php?p_code=B6727651495">2019 전기산업기사 필기 7개년 기출문제</a></td>\r\n\t\t\t\t\t\t\t\t\t\t\t\t\t<td class="left">김상훈   </td>\r\n\t\t\t\t\t\t\t\t\t\t\t\t<td>2018-10-31</td>\r\n\t\t\t\t\t\t<td class="right">22,000원</td>\r\n\t\t\t\t\t</tr>\r\n\r\n\t\t\t\t\t\t\t\t\t\t<tr>\r\n\t\t\t\t\t\t<td class="brd_a">한빛아카데미</td>\r\n\t\t\t\t\t\t<td class="left"><a href="/store/books/look.php?p_code=B9796997266">&#40;무료동영상&#41; 2019 전기산업기사 필기</a></td>\r\n\t\t\t\t\t\t\t\t\t\t\t\t\t<td class="left">김상훈   </td>\r\n\t\t\t\t\t\t\t\t\t\t\t\t<td>2018-10-26</td>\r\n\t\t\t\t\t\t<td class="right">36,000원</td>\r\n\t\t\t\t\t</tr>\r\n\r\n\t\t\t\t\t\t\t\t\t\t<tr>\r\n\t\t\t\t\t\t<td class="brd_a">한빛아카데미</td>\r\n\t\t\t\t\t\t<td class="left"><a href="/store/books/look.php?p_code=B1401258166">&#40;무료동영상&#41; 2019 전기기사 필기</a></td>\r\n\t\t\t\t\t\t\t\t\t\t\t\t\t<td class="left">김상훈   </td>\r\n\t\t\t\t\t\t\t\t\t\t\t\t<td>2018-10-26</td>\r\n\t\t\t\t\t\t<td class="right">36,000원</td>\r\n\t\t\t\t\t</tr>\r\n\r\n\t\t\t\t\t\t\t\t\t\t<tr>\r\n\t\t\t\t\t\t<td class="brd_l">한빛라이프</td>\r\n\t\t\t\t\t\t<td class="left"><a href="/store/books/look.php?p_code=B4559886540">리얼 블라디보스톡  PLUS 우수리스크 [2019~2020년 최신판]</a></td>\r\n\t\t\t\t\t\t\t\t\t\t\t\t\t<td class="left">강한나   </td>\r\n\t\t\t\t\t\t\t\t\t\t\t\t<td>2018-10-22</td>\r\n\t\t\t\t\t\t<td class="right">13,500원</td>\r\n\t\t\t\t\t</tr>\r\n\r\n\t\t\t\t\t\t\t\t\t\t<tr>\r\n\t\t\t\t\t\t<td class="brd_b">한빛비즈</td>\r\n\t\t\t\t\t\t<td class="left"><a href="/store/books/look.php?p_code=B1052483362">프라이드</a></td>\r\n\t\t\t\t\t\t\t\t\t\t\t\t\t<td class="left">박준기   </td>\r\n\t\t\t\t\t\t\t\t\t\t\t\t<td>2018-10-15</td>\r\n\t\t\t\t\t\t<td class="right">17,000원</td>\r\n\t\t\t\t\t</tr>\r\n\r\n\t\t\t\t\t\t\t\t\t\t<tr>\r\n\t\t\t\t\t\t<td class="brd_b">한빛비즈</td>\r\n\t\t\t\t\t\t<td class="left"><a href="/store/books/look.php?p_code=B3202466252">퇴근길 인문학 수업 : 전진</a></td>\r\n\t\t\t\t\t\t\t\t\t\t\t\t\t<td class="left">백상경제연구원   </td>\r\n\t\t\t\t\t\t\t\t\t\t\t\t<td>2018-10-15</td>\r\n\t\t\t\t\t\t<td class="right">17,000원</td>\r\n\t\t\t\t\t</tr>\r\n\r\n\t\t\t\t\t\t\t\t\t\t<tr>\r\n\t\t\t\t\t\t<td class="brd_b">한빛비즈</td>\r\n\t\t\t\t\t\t<td class="left"><a href="/store/books/look.php?p_code=B7076585695">만화로 배우는 곤충의 진화</a></td>\r\n\t\t\t\t\t\t\t\t\t\t\t\t\t<td class="left">김도윤(갈로아)   </td>\r\n\t\t\t\t\t\t\t\t\t\t\t\t<td>2018-10-15</td>\r\n\t\t\t\t\t\t<td class="right">17,800원</td>\r\n\t\t\t\t\t</tr>\r\n\r\n\t\t\t\t\t\t\t\t\t\t<tr>\r\n\t\t\t\t\t\t<td class="brd_m">한빛미디어</td>\r\n\t\t\t\t\t\t<td class="left"><a href="/store/books/look.php?p_code=B7473583156">맥 쓰는 사람들의 macOS 모하비</a></td>\r\n\t\t\t\t\t\t\t\t\t\t\t\t\t<td class="left">고래돌이   </td>\r\n\t\t\t\t\t\t\t\t\t\t\t\t<td>2018-10-10</td>\r\n\t\t\t\t\t\t<td class="right">22,000원</td>\r\n\t\t\t\t\t</tr>\r\n\r\n\t\t\t\t\t\t\t\t\t\t<tr>\r\n\t\t\t\t\t\t<td class="brd_a">한빛아카데미</td>\r\n\t\t\t\t\t\t<td class="left"><a href="/store/books/look.php?p_code=B7883656935">IT CookBook, 쉽게 배우는 JSP 웹 프로그래밍</a></td>\r\n\t\t\t\t\t\t\t\t\t\t\t\t\t<td class="left">송미영   </td>\r\n\t\t\t\t\t\t\t\t\t\t\t\t<td>2018-10-08</td>\r\n\t\t\t\t\t\t<td class="right">27,000원</td>\r\n\t\t\t\t\t</tr>\r\n\r\n\t\t\t\t\t\t\t\t\t\t<tr>\r\n\t\t\t\t\t\t<td class="brd_m">한빛미디어</td>\r\n\t\t\t\t\t\t<td class="left"><a href="/store/books/look.php?p_code=B6952054209">처음 시작하는 R 데이터 분석</a></td>\r\n\t\t\t\t\t\t\t\t\t\t\t\t\t<td class="left">강전희 외 1명  </td>\r\n\t\t\t\t\t\t\t\t\t\t\t\t<td>2018-10-05</td>\r\n\t\t\t\t\t\t<td class="right">19,800원</td>\r\n\t\t\t\t\t</tr>\r\n\r\n\t\t\t\t\t\t\t\t\t\t<tr>\r\n\t\t\t\t\t\t<td class="brd_a">한빛아카데미</td>\r\n\t\t\t\t\t\t<td class="left"><a href="/store/books/look.php?p_code=B4743554662">NCS를 기반으로 한 직무 기초수학</a></td>\r\n\t\t\t\t\t\t\t\t\t\t\t\t\t<td class="left">이광연 외 2명  </td>\r\n\t\t\t\t\t\t\t\t\t\t\t\t<td>2018-10-05</td>\r\n\t\t\t\t\t\t<td class="right">22,000원</td>\r\n\t\t\t\t\t</tr>\r\n\r\n\t\t\t\t\t\t\t\t\t\t<tr>\r\n\t\t\t\t\t\t<td class="brd_m">한빛미디어</td>\r\n\t\t\t\t\t\t<td class="left"><a href="/store/books/look.php?p_code=B2845507407">데이터 과학을 위한 통계</a></td>\r\n\t\t\t\t\t\t\t\t\t\t\t\t\t<td class="left">피터 브루스 외 1명  </td>\r\n\t\t\t\t\t\t\t\t\t\t\t\t<td>2018-10-02</td>\r\n\t\t\t\t\t\t<td class="right">32,000원</td>\r\n\t\t\t\t\t</tr>\r\n\r\n\t\t\t\t\t\t\t\t\t\t<tr>\r\n\t\t\t\t\t\t<td class="brd_m">한빛미디어</td>\r\n\t\t\t\t\t\t<td class="left"><a href="/store/books/look.php?p_code=B6910482773">오준석의 안드로이드 생존코딩&#40;코틀린 편&#41;</a></td>\r\n\t\t\t\t\t\t\t\t\t\t\t\t\t<td class="left">오준석   </td>\r\n\t\t\t\t\t\t\t\t\t\t\t\t<td>2018-10-01</td>\r\n\t\t\t\t\t\t<td class="right">32,000원</td>\r\n\t\t\t\t\t</tr>\r\n\r\n\t\t\t\t\t\t\t\t\t\t<tr>\r\n\t\t\t\t\t\t<td class="brd_m">한빛미디어</td>\r\n\t\t\t\t\t\t<td class="left"><a href="/store/books/look.php?p_code=B4458049183">처음 배우는 스프링 부트 2</a></td>\r\n\t\t\t\t\t\t\t\t\t\t\t\t\t<td class="left">김영재   </td>\r\n\t\t\t\t\t\t\t\t\t\t\t\t<td>2018-10-01</td>\r\n\t\t\t\t\t\t<td class="right">22,000원</td>\r\n\t\t\t\t\t</tr>\r\n\r\n\t\t\t\t\t\t\t\t\t\t<tr>\r\n\t\t\t\t\t\t<td class="brd_b">한빛비즈</td>\r\n\t\t\t\t\t\t<td class="left"><a href="/store/books/look.php?p_code=B3730970900">퇴근길 인문학 수업 : 전환</a></td>\r\n\t\t\t\t\t\t\t\t\t\t\t\t\t<td class="left">백상경제연구원   </td>\r\n\t\t\t\t\t\t\t\t\t\t\t\t<td>2018-09-28</td>\r\n\t\t\t\t\t\t<td class="right">17,000원</td>\r\n\t\t\t\t\t</tr>\r\n\r\n\t\t\t\t\t\t\t\t\t\t<tr>\r\n\t\t\t\t\t\t<td class="brd_a">한빛아카데미</td>\r\n\t\t\t\t\t\t<td class="left"><a href="/store/books/look.php?p_code=B2985687596">수치해석학 바이블</a></td>\r\n\t\t\t\t\t\t\t\t\t\t\t\t\t<td class="left">Ward Cheney 외 1명  </td>\r\n\t\t\t\t\t\t\t\t\t\t\t\t<td>2018-09-28</td>\r\n\t\t\t\t\t\t<td class="right">32,000원</td>\r\n\t\t\t\t\t</tr>\r\n\r\n\t\t\t\t\t\t\t\t\t\t<tr>\r\n\t\t\t\t\t\t<td class="brd_b">한빛비즈</td>\r\n\t\t\t\t\t\t<td class="left"><a href="/store/books/look.php?p_code=B3043718990">돈의 마법</a></td>\r\n\t\t\t\t\t\t\t\t\t\t\t\t\t<td class="left">고경호   </td>\r\n\t\t\t\t\t\t\t\t\t\t\t\t<td>2018-09-21</td>\r\n\t\t\t\t\t\t<td class="right">13,800원</td>\r\n\t\t\t\t\t</tr>\r\n\r\n\t\t\t\t\t\t\t\t\t\t<tr>\r\n\t\t\t\t\t\t<td class="brd_e">한빛에듀</td>\r\n\t\t\t\t\t\t<td class="left"><a href="/store/books/look.php?p_code=B5099518814">퀴즈 그림 찾기</a></td>\r\n\t\t\t\t\t\t\t\t\t\t\t\t\t<td class="left">모이라 버터필드   </td>\r\n\t\t\t\t\t\t\t\t\t\t\t\t<td>2018-09-19</td>\r\n\t\t\t\t\t\t<td class="right">6,000원</td>\r\n\t\t\t\t\t</tr>\r\n\r\n\t\t\t\t\t\t\t\t\t\t<tr>\r\n\t\t\t\t\t\t<td class="brd_e">한빛에듀</td>\r\n\t\t\t\t\t\t<td class="left"><a href="/store/books/look.php?p_code=B3155316207">하나 다른 그림 찾기</a></td>\r\n\t\t\t\t\t\t\t\t\t\t\t\t\t<td class="left">조이 포터   </td>\r\n\t\t\t\t\t\t\t\t\t\t\t\t<td>2018-09-19</td>\r\n\t\t\t\t\t\t<td class="right">6,000원</td>\r\n\t\t\t\t\t</tr>\r\n\r\n\t\t\t\t\t\t\t\t\t\t<tr>\r\n\t\t\t\t\t\t<td class="brd_e">한빛에듀</td>\r\n\t\t\t\t\t\t<td class="left"><a href="/store/books/look.php?p_code=B8338535067">다른 그림 찾기</a></td>\r\n\t\t\t\t\t\t\t\t\t\t\t\t\t<td class="left">엘리자베스 골딩   </td>\r\n\t\t\t\t\t\t\t\t\t\t\t\t<td>2018-09-19</td>\r\n\t\t\t\t\t\t<td class="right">6,000원</td>\r\n\t\t\t\t\t</tr>\r\n\r\n\t\t\t\t\t\t\t\r\n\t\t\t\t\t<tr class="sold_out">\r\n\t\t\t\t\t\t<td class="brd_m sold_out">한빛미디어</td>\r\n\t\t\t\t\t\t<td class="left sold_out"><img src="/images/store/icon_soldout.png" alt="품절" class="ic_soldout" /><a href="/store/books/look.php?p_code=B8635373198">회사에서 바로 통하는 실무 엑셀+파워포인트+워드&한글</a></td>\r\n\t\t\t\t\t\t\t\t\t\t\t\t\t<td class="sold_out left">전미진 외 2명  </td>\r\n\t\t\t\t\t\t\t\t\t\t\t\t<td class="sold_out">2018-09-17</td>\r\n\t\t\t\t\t\t<td class="sold_out right">22,000원</td>\r\n\t\t\t\t\t</tr>\t\t\t\t\t\t\t\t\t\t\r\n\t\t\t\t\t\t\t\t\t\t<tr>\r\n\t\t\t\t\t\t<td class="brd_b">한빛비즈</td>\r\n\t\t\t\t\t\t<td class="left"><a href="/store/books/look.php?p_code=B8533961758">퇴근길 인문학 수업 : 멈춤</a></td>\r\n\t\t\t\t\t\t\t\t\t\t\t\t\t<td class="left">백상경제연구원   </td>\r\n\t\t\t\t\t\t\t\t\t\t\t\t<td>2018-09-11</td>\r\n\t\t\t\t\t\t<td class="right">17,000원</td>\r\n\t\t\t\t\t</tr>\r\n\r\n\t\t\t\t\t\t\t\t\t\t<tr>\r\n\t\t\t\t\t\t<td class="brd_m">한빛미디어</td>\r\n\t\t\t\t\t\t<td class="left"><a href="/store/books/look.php?p_code=B2578596304">RxJS 프로그래밍: 75가지 핵심 문법과 예제로 익히는 RxJS 기초</a></td>\r\n\t\t\t\t\t\t\t\t\t\t\t\t\t<td class="left">이종욱 외 1명  </td>\r\n\t\t\t\t\t\t\t\t\t\t\t\t<td>2018-09-10</td>\r\n\t\t\t\t\t\t<td class="right">32,000원</td>\r\n\t\t\t\t\t</tr>\r\n\r\n\t\t\t\t\t\t\t\t\t\t<tr>\r\n\t\t\t\t\t\t<td class="brd_l">한빛라이프</td>\r\n\t\t\t\t\t\t<td class="left"><a href="/store/books/look.php?p_code=B1984493876">리얼 후쿠오카 PLUS 벳푸 · 유후인 [2018~2019년 최신판]</a></td>\r\n\t\t\t\t\t\t\t\t\t\t\t\t\t<td class="left">나보영   </td>\r\n\t\t\t\t\t\t\t\t\t\t\t\t<td>2018-09-05</td>\r\n\t\t\t\t\t\t<td class="right">15,000원</td>\r\n\t\t\t\t\t</tr>\r\n\r\n\t\t\t\t\t\t\t\t\t\t<tr>\r\n\t\t\t\t\t\t<td class="brd_m">한빛미디어</td>\r\n\t\t\t\t\t\t<td class="left"><a href="/store/books/look.php?p_code=B3859466837">스프링 5 레시피&#40;4판&#41;</a></td>\r\n\t\t\t\t\t\t\t\t\t\t\t\t\t<td class="left">마틴 데니엄(Marten Deinum) 외 2명  </td>\r\n\t\t\t\t\t\t\t\t\t\t\t\t<td>2018-09-01</td>\r\n\t\t\t\t\t\t<td class="right">60,000원</td>\r\n\t\t\t\t\t</tr>\r\n\r\n\t\t\t\t\t\t\t\t\t\t<tr>\r\n\t\t\t\t\t\t<td class="brd_m">한빛미디어</td>\r\n\t\t\t\t\t\t<td class="left"><a href="/store/books/look.php?p_code=B4774300045">자바를 활용한 딥러닝</a></td>\r\n\t\t\t\t\t\t\t\t\t\t\t\t\t<td class="left">조시 패터슨(Josh Patterson) 외 1명  </td>\r\n\t\t\t\t\t\t\t\t\t\t\t\t<td>2018-09-01</td>\r\n\t\t\t\t\t\t<td class="right">38,000원</td>\r\n\t\t\t\t\t</tr>\r\n\r\n\t\t\t\t\t\t\t\t\t\t<tr>\r\n\t\t\t\t\t\t<td class="brd_m">한빛미디어</td>\r\n\t\t\t\t\t\t<td class="left"><a href="/store/books/look.php?p_code=B6320134176">회사에서 바로 통하는 엑셀 실무 강의</a></td>\r\n\t\t\t\t\t\t\t\t\t\t\t\t\t<td class="left">전미진   </td>\r\n\t\t\t\t\t\t\t\t\t\t\t\t<td>2018-08-30</td>\r\n\t\t\t\t\t\t<td class="right">21,000원</td>\r\n\t\t\t\t\t</tr>\r\n\r\n\t\t\t\t\t\t\t\t\t\t<tr>\r\n\t\t\t\t\t\t<td class="brd_b">한빛비즈</td>\r\n\t\t\t\t\t\t<td class="left"><a href="/store/books/look.php?p_code=B4534892648">아마추어</a></td>\r\n\t\t\t\t\t\t\t\t\t\t\t\t\t<td class="left">앤디 메리필드   </td>\r\n\t\t\t\t\t\t\t\t\t\t\t\t<td>2018-08-30</td>\r\n\t\t\t\t\t\t<td class="right">17,000원</td>\r\n\t\t\t\t\t</tr>\r\n\r\n\t\t\t\t\t\t\t\t\t\t<tr>\r\n\t\t\t\t\t\t<td class="brd_b">한빛비즈</td>\r\n\t\t\t\t\t\t<td class="left"><a href="/store/books/look.php?p_code=B7534117022">우주에도 우리처럼</a></td>\r\n\t\t\t\t\t\t\t\t\t\t\t\t\t<td class="left">아베 유타카 외 1명  </td>\r\n\t\t\t\t\t\t\t\t\t\t\t\t<td>2018-08-30</td>\r\n\t\t\t\t\t\t<td class="right">16,000원</td>\r\n\t\t\t\t\t</tr>\r\n\r\n\t\t\t\t\t\t\t\t\t\t<tr>\r\n\t\t\t\t\t\t<td class="brd_l">한빛라이프</td>\r\n\t\t\t\t\t\t<td class="left"><a href="/store/books/look.php?p_code=B6370742670">“사랑해”를 쓰는 40가지 방법</a></td>\r\n\t\t\t\t\t\t\t\t\t\t\t\t\t<td class="left">라나 휴즈(Lana Hughes)   </td>\r\n\t\t\t\t\t\t\t\t\t\t\t\t<td>2018-08-27</td>\r\n\t\t\t\t\t\t<td class="right">13,500원</td>\r\n\t\t\t\t\t</tr>\r\n\r\n\t\t\t\t\t\t\t\t\t\t<tr>\r\n\t\t\t\t\t\t<td class="brd_m">한빛미디어</td>\r\n\t\t\t\t\t\t<td class="left"><a href="/store/books/look.php?p_code=B1211451725">모던 스타트업</a></td>\r\n\t\t\t\t\t\t\t\t\t\t\t\t\t<td class="left">이기곤   </td>\r\n\t\t\t\t\t\t\t\t\t\t\t\t<td>2018-08-20</td>\r\n\t\t\t\t\t\t<td class="right">20,000원</td>\r\n\t\t\t\t\t</tr>\r\n\r\n\t\t\t\t\t\t\t\t\t\t<tr>\r\n\t\t\t\t\t\t<td class="brd_m">한빛미디어</td>\r\n\t\t\t\t\t\t<td class="left"><a href="/store/books/look.php?p_code=B4329597070">파이썬 웹 프로그래밍&#40;개정판&#41;</a></td>\r\n\t\t\t\t\t\t\t\t\t\t\t\t\t<td class="left">김석훈   </td>\r\n\t\t\t\t\t\t\t\t\t\t\t\t<td>2018-08-17</td>\r\n\t\t\t\t\t\t<td class="right">22,000원</td>\r\n\t\t\t\t\t</tr>\r\n\r\n\t\t\t\t\t\t\t\t\t\t<tr>\r\n\t\t\t\t\t\t<td class="brd_b">한빛비즈</td>\r\n\t\t\t\t\t\t<td class="left"><a href="/store/books/look.php?p_code=B2680149100">이젠 내 시간표대로 살겠습니다</a></td>\r\n\t\t\t\t\t\t\t\t\t\t\t\t\t<td class="left">미카엘라 청   </td>\r\n\t\t\t\t\t\t\t\t\t\t\t\t<td>2018-08-16</td>\r\n\t\t\t\t\t\t<td class="right">15,000원</td>\r\n\t\t\t\t\t</tr>\r\n\r\n\t\t\t\t\t\t\t\t\t\t<tr>\r\n\t\t\t\t\t\t<td class="brd_m">한빛미디어</td>\r\n\t\t\t\t\t\t<td class="left"><a href="/store/books/look.php?p_code=B3409534326">피, 땀, 픽셀 : 트리플 A 게임은 어떻게 만들어지는가</a></td>\r\n\t\t\t\t\t\t\t\t\t\t\t\t\t<td class="left">제이슨 슈라이어   </td>\r\n\t\t\t\t\t\t\t\t\t\t\t\t<td>2018-08-03</td>\r\n\t\t\t\t\t\t<td class="right">18,000원</td>\r\n\t\t\t\t\t</tr>\r\n\r\n\t\t\t\t\t\t\t\t\t\t<tr>\r\n\t\t\t\t\t\t<td class="brd_m">한빛미디어</td>\r\n\t\t\t\t\t\t<td class="left"><a href="/store/books/look.php?p_code=B6142075412">엔트리, 피지컬 컴퓨팅을 만나다</a></td>\r\n\t\t\t\t\t\t\t\t\t\t\t\t\t<td class="left">최현종 외 2명  </td>\r\n\t\t\t\t\t\t\t\t\t\t\t\t<td>2018-08-03</td>\r\n\t\t\t\t\t\t<td class="right">18,000원</td>\r\n\t\t\t\t\t</tr>\r\n\r\n\t\t\t\t\t\t\t\t\t\t<tr>\r\n\t\t\t\t\t\t<td class="brd_m">한빛미디어</td>\r\n\t\t\t\t\t\t<td class="left"><a href="/store/books/look.php?p_code=B8627769894">회사에서 바로 통하는 오토캐드 2019</a></td>\r\n\t\t\t\t\t\t\t\t\t\t\t\t\t<td class="left">심미현   </td>\r\n\t\t\t\t\t\t\t\t\t\t\t\t<td>2018-08-03</td>\r\n\t\t\t\t\t\t<td class="right">28,000원</td>\r\n\t\t\t\t\t</tr>\r\n\r\n\t\t\t\t\t\t\t\t\t\t<tr>\r\n\t\t\t\t\t\t<td class="brd_m">한빛미디어</td>\r\n\t\t\t\t\t\t<td class="left"><a href="/store/books/look.php?p_code=B1184560899">맛있는 디자인 프리미어 프로&애프터 이펙트 CC 2018</a></td>\r\n\t\t\t\t\t\t\t\t\t\t\t\t\t<td class="left">김덕영 외 2명  </td>\r\n\t\t\t\t\t\t\t\t\t\t\t\t<td>2018-08-03</td>\r\n\t\t\t\t\t\t<td class="right">24,000원</td>\r\n\t\t\t\t\t</tr>\r\n\r\n\t\t\t\t\t\t\t\t\t\t<tr>\r\n\t\t\t\t\t\t<td class="brd_m">한빛미디어</td>\r\n\t\t\t\t\t\t<td class="left"><a href="/store/books/look.php?p_code=B1131615065">맛있는 디자인 포토샵&인디자인 CC 2018</a></td>\r\n\t\t\t\t\t\t\t\t\t\t\t\t\t<td class="left">박효근 외 2명  </td>\r\n\t\t\t\t\t\t\t\t\t\t\t\t<td>2018-08-03</td>\r\n\t\t\t\t\t\t<td class="right">24,000원</td>\r\n\t\t\t\t\t</tr>\r\n\r\n\t\t\t\t\t\t\t\t\t\t<tr>\r\n\t\t\t\t\t\t<td class="brd_m">한빛미디어</td>\r\n\t\t\t\t\t\t<td class="left"><a href="/store/books/look.php?p_code=B5821607640">만들면서 배우는 워드프레스&#40;개정판&#41;</a></td>\r\n\t\t\t\t\t\t\t\t\t\t\t\t\t<td class="left">박현우   </td>\r\n\t\t\t\t\t\t\t\t\t\t\t\t<td>2018-07-25</td>\r\n\t\t\t\t\t\t<td class="right">26,000원</td>\r\n\t\t\t\t\t</tr>\r\n\r\n\t\t\t\t\t\t\t\t\t\t<tr>\r\n\t\t\t\t\t\t<td class="brd_m">한빛미디어</td>\r\n\t\t\t\t\t\t<td class="left"><a href="/store/books/look.php?p_code=B3633028491">처음 배우는 암호화</a></td>\r\n\t\t\t\t\t\t\t\t\t\t\t\t\t<td class="left">장필리프 오마송   </td>\r\n\t\t\t\t\t\t\t\t\t\t\t\t<td>2018-07-20</td>\r\n\t\t\t\t\t\t<td class="right">29,000원</td>\r\n\t\t\t\t\t</tr>\r\n\r\n\t\t\t\t\t\t\t\t\t\t<tr>\r\n\t\t\t\t\t\t<td class="brd_a">한빛아카데미</td>\r\n\t\t\t\t\t\t<td class="left"><a href="/store/books/look.php?p_code=B9631702376">MATLAB으로 배우는 공학 수치해석&#40;개정판&#41;</a></td>\r\n\t\t\t\t\t\t\t\t\t\t\t\t\t<td class="left">방성완   </td>\r\n\t\t\t\t\t\t\t\t\t\t\t\t<td>2018-07-20</td>\r\n\t\t\t\t\t\t<td class="right">24,000원</td>\r\n\t\t\t\t\t</tr>\r\n\r\n\t\t\t\t\t\t\t\t\t\r\n\t\t\t\t</tbody>\r\n\t\t\t</table>\r\n\t\t</div>\r\n\t\t<!-- //책 리스트 -->\r\n\t\t\r\n\t\t<!-- 페이징 -->\r\n\t\t<div class="paginate bdr_no">\r\n\t\t\t<strong>1</strong>\n<a href="/store/books/full_book_list.html?page=2&srt=p_pub_date&brand=">2</a>\n<a href="/store/books/full_book_list.html?page=3&srt=p_pub_date&brand=">3</a>\n<a href="/store/books/full_book_list.html?page=4&srt=p_pub_date&brand=">4</a>\n<a href="/store/books/full_book_list.html?page=5&srt=p_pub_date&brand=">5</a>\n<a href="/store/books/full_book_list.html?page=6&srt=p_pub_date&brand=">6</a>\n<a href="/store/books/full_book_list.html?page=7&srt=p_pub_date&brand=">7</a>\n<a href="/store/books/full_book_list.html?page=8&srt=p_pub_date&brand=">8</a>\n<a href="/store/books/full_book_list.html?page=9&srt=p_pub_date&brand=">9</a>\n<a href="/store/books/full_book_list.html?page=10&srt=p_pub_date&brand=">10</a>\n<a href="/store/books/full_book_list.html?page=11&srt=p_pub_date&brand=" class="next"><span>&gt;</span></a>\n\t\t</div>\r\n\t\t<!-- //페이징 -->\r\n\t\t\r\n\t\t<!-- 전체 목록 다운로드 버튼-->\r\n\t\t<div class="btn_full_list mt40"><a href="javascript:document.frm.submit();">전체 목록 다운로드</a></div>\r\n\t\r\n\t</div>\r\n\t<!-- //전체도서목록 wrap -->\t\r\n\t\r\n</div>\r\n<!-- //Contents -->\r\n<form name="frm" id="frm" method="post" action="./full_book_list_down.php">\r\n<input type="hidden" name="brand" id="brand" value="">\r\n<input type="hidden" name="srt" id="srt" value="p_pub_date">\r\n</form>\r\n<!-- 푸터 -->\r\n<footer>\r\n  <!-- 공지사항 -->\r\n  <div class="foot_notice">\r\n      </div>\r\n  <!-- //공지사항 -->\r\n  \r\n  <div class="foot_contents">\r\n    <!-- 하단 메뉴 -->\r\n    <div class="foot_menu">\r\n      <!-- added by coffin -->\r\n            <ul>\r\n        <li><a href="http://www.hanbit.co.kr/publisher/index.html" target="_blank">회사소개</a>(<a href="http://www.hanbit.co.kr/publisher/index.html" target="_blank">KOR</a> | <a href="http://www.hanbit.co.kr/publisher/index.html?lang=e" target="_blank">ENG</a>) &#149; <a href="http://www.hanbit.co.kr/publisher/contact.html?lang=k" target="_blank">약도</a></li>\r\n        <li><a href="http://www.hanbit.co.kr/publisher/write.html" target="_blank">기획 및 원고 모집</a></li>\r\n        <li><a href="http://www.hanbit.co.kr/member/use_agreement.html">이용약관</a></li>\r\n        <li><a href="http://www.hanbit.co.kr/member/privacy_policy.html"><strong>개인정보취급방침</strong></a></li>\r\n        <li><a href="http://www.hanbit.co.kr/sitemap/sitemap.html">사이트맵</a></li>\r\n      </ul>\r\n          </div>\r\n    <!-- //하단 메뉴 -->\r\n\r\n    <!-- SNS -->\r\n    <div class="foot_sns">\r\n    \r\n      \r\n            \r\n      <ul>\r\n        <li class="foot_facebook"><a href="https://www.facebook.com/hanbitmedia" target="_blank"><span>페이스북</span></a></li>\r\n        <li class="foot_googleplus"><a href="https://plus.google.com/u/0/+HanbitCoKr/posts" target="_blank"><span>구글플러스</span></a></li>\r\n        <li class="foot_twitter"><a href="https://twitter.com/hanbit" target="_blank"><span>트위터</span></a></li>\r\n        <li class="foot_youtube"><a href="https://www.youtube.com/user/HanbitMedia93" target="_blank"><span>유튜브</span></a></li>\r\n        <li class="foot_bolg"><a href="http://blog.hanbit.co.kr/" target="_blank"><span>블로그</span></a></li>\r\n      </ul>\r\n      \r\n            \r\n\r\n        <fieldset class="foot_srch">\r\n          <legend>하단 검색영역</legend>\r\n          <input title="검색어" class="foot_srch_keyword" accesskey="s" type="text" value=""  id="foot_keyword_str" style="font-size:16px;">\r\n          <input type="button" alt="" class="foot_srch_btn" onclick="foot_sch_smit();" style="cursor: pointer;">\r\n          <!--input type="image" alt="" class="foot_srch_btn" -->\r\n        </fieldset>\r\n\r\n      \r\n      <script>\r\n        // 검색 리스트  \r\n        $(document).ready(function() {       \r\n          $(\'#foot_keyword_str\').keyup(function(e) {\r\n            if (e.keyCode == 13) \r\n              foot_sch_smit();\r\n          });        \r\n        });\r\n\r\n        function foot_sch_smit(){            \r\n          var foot_keyword_str = $("#foot_keyword_str").val();      \r\n          var searchUrl = "/search/search_list.html?foot_keyword_str="+foot_keyword_str;\r\n\r\n          if(!foot_keyword_str){\r\n            alert("검색어를 입력해주세요");\r\n            $("#foot_keyword_str").focus();\r\n          }else{\r\n            location.href = searchUrl;\r\n          }                                              \r\n        }          \r\n      </script>  \r\n      \r\n    </div>\r\n    <!-- //SNS -->\r\n    \r\n    <!-- 한빛 정보 -->\r\n    <div class="foot_about">\r\n      <div class="foot_about_area">\r\n        \r\n\r\n        <p><strong>한빛미디어㈜ &#149; 한빛아카데미㈜ &#149; 한빛비즈㈜</strong></p>\r\n        <p>(03785) 서울 서대문구 연희로2길 62</p>\r\n        <p>TEL : 02-325-0384 / FAX : 02-325-9697</p>\r\n        <p>EMAIL : support@hanbit.co.kr</p>\r\n        <p>대표이사 : 김태헌</p>\r\n        <p>사업자등록번호 : 220-81-05665 <a href="http://www.ftc.go.kr/bizCommPop.do?wrkr_no=2208105665" target="_blank">[확인]</a></p>\r\n        <p>통신판매업신고 : 2017-서울서대문-0671호</p>\r\n        <p>호스팅제공자 : (주)누리호스팅</p>\r\n        \r\n\r\n      </div>\r\n    </div>\r\n    <!-- //한빛 정보 -->\r\n  </div>\r\n  \r\n  <div class="copyright">&copy;1993-2018 Hanbit Publishing Network, Inc. All rights reserved.</div>\r\n</footer>\r\n<!-- //푸터 -->\r\n<div class="foot_download_btn"><a href="/support/supplement_list.html">자료실</a></div>\r\n\r\n<!-- 공통 JS 호출 -->\r\n<script type="text/javascript" src="/js/common.js"></script>\r\n<!-- //공통 JS 호출 -->\r\n\r\n</body>\r\n</html>\r\n'



### <font color='#0000CC'> c2-10_urlopen_meta
> ** meta 태그에서 인코딩 방식 추출 **
<br/>Content-Type 헤더의 값고 실제 사용되고 있는 인코딩 형식이 다를 수 있다.
<br/> 디코딩 처리때 ** UnicodeDecodeError가 발생 ** 한다면 이러한 처리를 모방해서 구현하면 해결할 수 있다.
- < meta charset="utf-8" >
- < meta http-equiv="Content-Type" content="text/html; charset="EUC-KR" >
 
cf. 연관함수 : HTTPMessage.info().get_content_charset()


```python
import re
import sys
from urllib.request import urlopen

```


```python
f = urlopen('http://www.hanbit.co.kr/store/books/full_book_list.html')
# bytes 자료형의 응답 본문을 일단 변수에 저장합니다.
bytes_content = f.read()  

type(bytes_content), bytes_content[:2**10]
```




    (bytes,
     b'<!DOCTYPE html>\r\n<html lang="ko">\r\n<head>\r\n<!--[if lte IE 8]>\r\n<script>\r\n  location.replace(\'/support/explorer_upgrade.html\');\r\n</script>\r\n<![endif]-->\r\n<!-- Google Tag Manager -->\r\n<script>(function(w,d,s,l,i){w[l]=w[l]||[];w[l].push({\'gtm.start\':\r\nnew Date().getTime(),event:\'gtm.js\'});var f=d.getElementsByTagName(s)[0],\r\nj=d.createElement(s),dl=l!=\'dataLayer\'?\'&l=\'+l:\'\';j.async=true;j.src=\r\n\'https://www.googletagmanager.com/gtm.js?id=\'+i+dl;f.parentNode.insertBefore(j,f);\r\n})(window,document,\'script\',\'dataLayer\',\'GTM-W9D5PM3\');</script>\r\n<!-- End Google Tag Manager -->\r\n<meta charset="utf-8"/>\r\n<title>\xed\x95\x9c\xeb\xb9\x9b\xec\xb6\x9c\xed\x8c\x90\xeb\x84\xa4\xed\x8a\xb8\xec\x9b\x8c\xed\x81\xac</title>\r\n<link rel="shortcut icon" href="http://www.hanbit.co.kr/images/common/hanbit.ico"> \r\n<meta http-equiv="X-UA-Compatible" content="IE=Edge" />\r\n<meta property="og:type" content="website"/>\r\n<meta property="og:title" content="\xed\x95\x9c\xeb\xb9\x9b\xec\xb6\x9c\xed\x8c\x90\xeb\x84\xa4\xed\x8a\xb8\xec\x9b\x8c\xed\x81\xac"/>\r\n<meta property="og:description" content="\xec\xb6\x9c\xed\x8c\x90\xec\x82\xac, IT\xec\xa0\x84\xeb\xac\xb8\xec\x84\x9c, \xeb\x8c\x80\xed\x95\x99\xea\xb5\x90\xec\x9e\xac, \xea\xb2\xbd\xec\xa0\x9c\xea\xb2\xbd\xec\x98\x81, \xec\x96\xb4\xeb\xa6\xb0\xec\x9d\xb4/\xec\x9c\xa0\xec\x95\x84, MAKE, \xec\x8b\xa4\xec\x9a\xa9/\xec\x97\xac')




```python
# charset은 HTML의 앞부분에 적혀 있는 경우가 많으므로
# 응답 본문의 앞부분 1024바이트를 ASCII 문자로 디코딩해 둡니다.
# ASCII 범위 이위의 문자는 U+FFFD(REPLACEMENT CHARACTER)로 변환되어 예외가 발생하지 않습니다.
scanned_text = bytes_content[:2**10].decode('ascii', errors='replace')

type(scanned_text), scanned_text
```




    (str,
     '<!DOCTYPE html>\r\n<html lang="ko">\r\n<head>\r\n<!--[if lte IE 8]>\r\n<script>\r\n  location.replace(\'/support/explorer_upgrade.html\');\r\n</script>\r\n<![endif]-->\r\n<!-- Google Tag Manager -->\r\n<script>(function(w,d,s,l,i){w[l]=w[l]||[];w[l].push({\'gtm.start\':\r\nnew Date().getTime(),event:\'gtm.js\'});var f=d.getElementsByTagName(s)[0],\r\nj=d.createElement(s),dl=l!=\'dataLayer\'?\'&l=\'+l:\'\';j.async=true;j.src=\r\n\'https://www.googletagmanager.com/gtm.js?id=\'+i+dl;f.parentNode.insertBefore(j,f);\r\n})(window,document,\'script\',\'dataLayer\',\'GTM-W9D5PM3\');</script>\r\n<!-- End Google Tag Manager -->\r\n<meta charset="utf-8"/>\r\n<title>������������������������</title>\r\n<link rel="shortcut icon" href="http://www.hanbit.co.kr/images/common/hanbit.ico"> \r\n<meta http-equiv="X-UA-Compatible" content="IE=Edge" />\r\n<meta property="og:type" content="website"/>\r\n<meta property="og:title" content="������������������������"/>\r\n<meta property="og:description" content="���������, IT���������, ������������, ������������, ���������/������, MAKE, ������/���')




```python
scanned_text = bytes_content[:2**10].decode('utf-8', errors='replace')

type(scanned_text), scanned_text
```




    (str,
     '<!DOCTYPE html>\r\n<html lang="ko">\r\n<head>\r\n<!--[if lte IE 8]>\r\n<script>\r\n  location.replace(\'/support/explorer_upgrade.html\');\r\n</script>\r\n<![endif]-->\r\n<!-- Google Tag Manager -->\r\n<script>(function(w,d,s,l,i){w[l]=w[l]||[];w[l].push({\'gtm.start\':\r\nnew Date().getTime(),event:\'gtm.js\'});var f=d.getElementsByTagName(s)[0],\r\nj=d.createElement(s),dl=l!=\'dataLayer\'?\'&l=\'+l:\'\';j.async=true;j.src=\r\n\'https://www.googletagmanager.com/gtm.js?id=\'+i+dl;f.parentNode.insertBefore(j,f);\r\n})(window,document,\'script\',\'dataLayer\',\'GTM-W9D5PM3\');</script>\r\n<!-- End Google Tag Manager -->\r\n<meta charset="utf-8"/>\r\n<title>한빛출판네트워크</title>\r\n<link rel="shortcut icon" href="http://www.hanbit.co.kr/images/common/hanbit.ico"> \r\n<meta http-equiv="X-UA-Compatible" content="IE=Edge" />\r\n<meta property="og:type" content="website"/>\r\n<meta property="og:title" content="한빛출판네트워크"/>\r\n<meta property="og:description" content="출판사, IT전문서, 대학교재, 경제경영, 어린이/유아, MAKE, 실용/여')




```python
# 디코딩한 문자열에서 정규 표현식으로 charset 값을 추출합니다.
match = re.search(r'charset=["\']?([\w-]+)', scanned_text)
if match:
    encoding = match.group(1)
else:
    # charset이 명시돼 있지 않으면 UTF-8을 사용합니다.
    encoding = 'utf-8'

# 추출한 인코딩을 표준 오류에 출력합니다.
print('encoding:', encoding, file=sys.stderr)

```

    encoding: utf-8
    


```python
# 추출한 인코딩으로 다시 디코딩합니다.
text = bytes_content.decode(encoding)

# 응답 본문을 표준 출력에 출력합니다.
print(text[:2**10])
```

    <!DOCTYPE html>
    <html lang="ko">
    <head>
    <!--[if lte IE 8]>
    <script>
      location.replace('/support/explorer_upgrade.html');
    </script>
    <![endif]-->
    <!-- Google Tag Manager -->
    <script>(function(w,d,s,l,i){w[l]=w[l]||[];w[l].push({'gtm.start':
    new Date().getTime(),event:'gtm.js'});var f=d.getElementsByTagName(s)[0],
    j=d.createElement(s),dl=l!='dataLayer'?'&l='+l:'';j.async=true;j.src=
    'https://www.googletagmanager.com/gtm.js?id='+i+dl;f.parentNode.insertBefore(j,f);
    })(window,document,'script','dataLayer','GTM-W9D5PM3');</script>
    <!-- End Google Tag Manager -->
    <meta charset="utf-8"/>
    <title>한빛출판네트워크</title>
    <link rel="shortcut icon" href="http://www.hanbit.co.kr/images/common/hanbit.ico"> 
    <meta http-equiv="X-UA-Compatible" content="IE=Edge" />
    <meta property="og:type" content="website"/>
    <meta property="og:title" content="한빛출판네트워크"/>
    <meta property="og:description" content="출판사, IT전문서, 대학교재, 경제경영, 어린이/유아, MAKE, 실용/여행, 전자책, 인터넷 강의"/>
    <meta property="og:image" content="http://www.hanbit.co.k
    

<hr>
### <font color='blue'> 웹 페이지에서 데이터 추출
> 
- Regular Expression
- XML Parser

### <font color='#0000CC'>  c2-11_scrape_re
> 정규표현식으로 스크레이핑


```python
! wget http://www.hanbit.co.kr/store/books/full_book_list.html
```

    --2018-11-12 23:10:41--  http://www.hanbit.co.kr/store/books/full_book_list.html
    Resolving www.hanbit.co.kr (www.hanbit.co.kr)... 218.38.58.195
    Connecting to www.hanbit.co.kr (www.hanbit.co.kr)|218.38.58.195|:80... connected.
    HTTP request sent, awaiting response... 200 OK
    Length: unspecified [text/html]
    Saving to: 'full_book_list.html'
    
         0K .......... .......... .......... .......... .....      64.6K=0.7s
    
    2018-11-12 23:10:42 (64.6 KB/s) - 'full_book_list.html' saved [46441]
    
    


```python
! dir *.html
```

     C 드라이브의 볼륨에는 이름이 없습니다.
     볼륨 일련 번호: 3CBD-1374
    
     C:\Users\user\Dropbox\sect_tech\src_anaconda\P1810_IITP_Multicampus\tb10-web-crawling 디렉터리
    
    2018-11-12  오후 11:10            46,441 full_book_list.html
                   1개 파일              46,441 바이트
                   0개 디렉터리  24,773,201,920 바이트 남음
    


```python
# ! mkdir data
make_dir('data')
```




    'data 디렉토리를 생성하였습니다!'




```python
! dir data
```

     C 드라이브의 볼륨에는 이름이 없습니다.
     볼륨 일련 번호: 3CBD-1374
    
     C:\Users\user\Dropbox\sect_tech\src_anaconda\P1810_IITP_Multicampus\tb10-web-crawling\data 디렉터리
    
    2018-11-12  오후 11:10    <DIR>          .
    2018-11-12  오후 11:10    <DIR>          ..
                   0개 파일                   0 바이트
                   2개 디렉터리  24,773,185,536 바이트 남음
    


```python
! ren full_book_list.html dp.html
! move dp.html data
```

            1개 파일을 이동했습니다.
    


```python
! dir data\*.html
```

     C 드라이브의 볼륨에는 이름이 없습니다.
     볼륨 일련 번호: 3CBD-1374
    
     C:\Users\user\Dropbox\sect_tech\src_anaconda\P1810_IITP_Multicampus\tb10-web-crawling\data 디렉터리
    
    2018-11-12  오후 11:10            46,441 dp.html
                   1개 파일              46,441 바이트
                   0개 디렉터리  24,773,185,536 바이트 남음
    


```python
import re
from html import unescape

# 이전 절에서 다운로드한 파일을 열고 html이라는 변수에 저장합니다.
with open('./data/dp.html', encoding='utf-8') as f:
    html = f.read()

# re.findall()을 사용해 도서 하나에 해당하는 HTML을 추출합니다.
print('check')
for partial_html in re.findall(r'<td class="left"><a.*?</td>', html, re.DOTALL):
    # 도서의 URL을 추출합니다.
    url = re.search(r'<a href="(.*?)">', partial_html).group(1)
    url = 'http://www.hanbit.co.kr' + url
    # 태그를 제거해서 도서의 제목을 추출합니다.
    title = re.sub(r'<.*?>', '', partial_html)
    title = unescape(title)
    print('url:', url)
    print('title:', title)
    print('---')
```

    check
    url: http://www.hanbit.co.kr/store/books/look.php?p_code=B6994299591
    title: 재미있고 빠른 한글 2권 : 기본 자음과 쌍자음
    ---
    url: http://www.hanbit.co.kr/store/books/look.php?p_code=B8463831992
    title: 재미있고 빠른 한글 4권 : 복잡한 모음
    ---
    url: http://www.hanbit.co.kr/store/books/look.php?p_code=B3283906872
    title: IT CookBook, 시스템 해킹과 보안(3판)
    ---
    url: http://www.hanbit.co.kr/store/books/look.php?p_code=B8608817158
    title: IT 트렌드 스페셜 리포트 2019
    ---
    url: http://www.hanbit.co.kr/store/books/look.php?p_code=B4851649517
    title: Accelerated C++
    ---
    url: http://www.hanbit.co.kr/store/books/look.php?p_code=B1266184916
    title: 한 권으로 끝내는 딥러닝 텐서플로
    ---
    url: http://www.hanbit.co.kr/store/books/look.php?p_code=B8718279503
    title: 파이썬으로 배우는 머신러닝의 교과서
    ---
    url: http://www.hanbit.co.kr/store/books/look.php?p_code=B5331040931
    title: 좋은 사진을 만드는 ZAKO의 여행 사진 잘 찍는 법
    ---
    url: http://www.hanbit.co.kr/store/books/look.php?p_code=B3696148245
    title: 2019 전기기사 필기 7개년 기출문제
    ---
    url: http://www.hanbit.co.kr/store/books/look.php?p_code=B6727651495
    title: 2019 전기산업기사 필기 7개년 기출문제
    ---
    url: http://www.hanbit.co.kr/store/books/look.php?p_code=B9796997266
    title: (무료동영상) 2019 전기산업기사 필기
    ---
    url: http://www.hanbit.co.kr/store/books/look.php?p_code=B1401258166
    title: (무료동영상) 2019 전기기사 필기
    ---
    url: http://www.hanbit.co.kr/store/books/look.php?p_code=B4559886540
    title: 리얼 블라디보스톡  PLUS 우수리스크 [2019~2020년 최신판]
    ---
    url: http://www.hanbit.co.kr/store/books/look.php?p_code=B1052483362
    title: 프라이드
    ---
    url: http://www.hanbit.co.kr/store/books/look.php?p_code=B3202466252
    title: 퇴근길 인문학 수업 : 전진
    ---
    url: http://www.hanbit.co.kr/store/books/look.php?p_code=B7076585695
    title: 만화로 배우는 곤충의 진화
    ---
    url: http://www.hanbit.co.kr/store/books/look.php?p_code=B7473583156
    title: 맥 쓰는 사람들의 macOS 모하비
    ---
    url: http://www.hanbit.co.kr/store/books/look.php?p_code=B7883656935
    title: IT CookBook, 쉽게 배우는 JSP 웹 프로그래밍
    ---
    url: http://www.hanbit.co.kr/store/books/look.php?p_code=B6952054209
    title: 처음 시작하는 R 데이터 분석
    ---
    url: http://www.hanbit.co.kr/store/books/look.php?p_code=B4743554662
    title: NCS를 기반으로 한 직무 기초수학
    ---
    url: http://www.hanbit.co.kr/store/books/look.php?p_code=B2845507407
    title: 데이터 과학을 위한 통계
    ---
    url: http://www.hanbit.co.kr/store/books/look.php?p_code=B6910482773
    title: 오준석의 안드로이드 생존코딩(코틀린 편)
    ---
    url: http://www.hanbit.co.kr/store/books/look.php?p_code=B4458049183
    title: 처음 배우는 스프링 부트 2
    ---
    url: http://www.hanbit.co.kr/store/books/look.php?p_code=B3730970900
    title: 퇴근길 인문학 수업 : 전환
    ---
    url: http://www.hanbit.co.kr/store/books/look.php?p_code=B2985687596
    title: 수치해석학 바이블
    ---
    url: http://www.hanbit.co.kr/store/books/look.php?p_code=B3043718990
    title: 돈의 마법
    ---
    url: http://www.hanbit.co.kr/store/books/look.php?p_code=B5099518814
    title: 퀴즈 그림 찾기
    ---
    url: http://www.hanbit.co.kr/store/books/look.php?p_code=B3155316207
    title: 하나 다른 그림 찾기
    ---
    url: http://www.hanbit.co.kr/store/books/look.php?p_code=B8338535067
    title: 다른 그림 찾기
    ---
    url: http://www.hanbit.co.kr/store/books/look.php?p_code=B8533961758
    title: 퇴근길 인문학 수업 : 멈춤
    ---
    url: http://www.hanbit.co.kr/store/books/look.php?p_code=B2578596304
    title: RxJS 프로그래밍: 75가지 핵심 문법과 예제로 익히는 RxJS 기초
    ---
    url: http://www.hanbit.co.kr/store/books/look.php?p_code=B1984493876
    title: 리얼 후쿠오카 PLUS 벳푸 · 유후인 [2018~2019년 최신판]
    ---
    url: http://www.hanbit.co.kr/store/books/look.php?p_code=B3859466837
    title: 스프링 5 레시피(4판)
    ---
    url: http://www.hanbit.co.kr/store/books/look.php?p_code=B4774300045
    title: 자바를 활용한 딥러닝
    ---
    url: http://www.hanbit.co.kr/store/books/look.php?p_code=B6320134176
    title: 회사에서 바로 통하는 엑셀 실무 강의
    ---
    url: http://www.hanbit.co.kr/store/books/look.php?p_code=B4534892648
    title: 아마추어
    ---
    url: http://www.hanbit.co.kr/store/books/look.php?p_code=B7534117022
    title: 우주에도 우리처럼
    ---
    url: http://www.hanbit.co.kr/store/books/look.php?p_code=B6370742670
    title: “사랑해”를 쓰는 40가지 방법
    ---
    url: http://www.hanbit.co.kr/store/books/look.php?p_code=B1211451725
    title: 모던 스타트업
    ---
    url: http://www.hanbit.co.kr/store/books/look.php?p_code=B4329597070
    title: 파이썬 웹 프로그래밍(개정판)
    ---
    url: http://www.hanbit.co.kr/store/books/look.php?p_code=B2680149100
    title: 이젠 내 시간표대로 살겠습니다
    ---
    url: http://www.hanbit.co.kr/store/books/look.php?p_code=B3409534326
    title: 피, 땀, 픽셀 : 트리플 A 게임은 어떻게 만들어지는가
    ---
    url: http://www.hanbit.co.kr/store/books/look.php?p_code=B6142075412
    title: 엔트리, 피지컬 컴퓨팅을 만나다
    ---
    url: http://www.hanbit.co.kr/store/books/look.php?p_code=B8627769894
    title: 회사에서 바로 통하는 오토캐드 2019
    ---
    url: http://www.hanbit.co.kr/store/books/look.php?p_code=B1184560899
    title: 맛있는 디자인 프리미어 프로&애프터 이펙트 CC 2018
    ---
    url: http://www.hanbit.co.kr/store/books/look.php?p_code=B1131615065
    title: 맛있는 디자인 포토샵&인디자인 CC 2018
    ---
    url: http://www.hanbit.co.kr/store/books/look.php?p_code=B5821607640
    title: 만들면서 배우는 워드프레스(개정판)
    ---
    url: http://www.hanbit.co.kr/store/books/look.php?p_code=B3633028491
    title: 처음 배우는 암호화
    ---
    url: http://www.hanbit.co.kr/store/books/look.php?p_code=B9631702376
    title: MATLAB으로 배우는 공학 수치해석(개정판)
    ---
    

### <font color='#0000CC'> c2-12 : rss.xml
> RSS 파싱하기
- 서울/경기도 지역의 날씨 받기
- http://www.weather.go.kr/weather/forecast/mid-term-rss3.jsp?stnId=109


```python
! wget http://www.weather.go.kr/weather/forecast/mid-term-rss3.jsp?stnId=109
```

    --2018-11-12 23:10:42--  http://www.weather.go.kr/weather/forecast/mid-term-rss3.jsp?stnId=109
    Resolving www.weather.go.kr (www.weather.go.kr)... 121.78.77.90
    Connecting to www.weather.go.kr (www.weather.go.kr)|121.78.77.90|:80... connected.
    HTTP request sent, awaiting response... 200 OK
    Length: 96044 (94K) [text/xml]
    Saving to: 'mid-term-rss3.jsp@stnId=109'
    
         0K .......... .......... .......... .......... .......... 53% 2.09M 0s
        50K .......... .......... .......... .......... ...       100% 4.62M=0.03s
    
    2018-11-12 23:10:42 (2.81 MB/s) - 'mid-term-rss3.jsp@stnId=109' saved [96044/96044]
    
    


```python
! dir
```

     C 드라이브의 볼륨에는 이름이 없습니다.
     볼륨 일련 번호: 3CBD-1374
    
     C:\Users\user\Dropbox\sect_tech\src_anaconda\P1810_IITP_Multicampus\tb10-web-crawling 디렉터리
    
    2018-11-12  오후 11:10    <DIR>          .
    2018-11-12  오후 11:10    <DIR>          ..
    2018-11-12  오후 09:37    <DIR>          .ipynb_checkpoints
    2018-11-12  오후 11:10    <DIR>          data
    2018-11-12  오전 01:30    <DIR>          download
    2018-11-12  오후 11:10            96,044 mid-term-rss3.jsp@stnId=109
    2018-11-12  오후 02:51             4,669 packages.txt
    2018-11-12  오후 10:45           196,995 WCS01_Wget_크롤링.ipynb
    2018-10-24  오전 01:24             4,477 WCS02_크롤링과_스크랩핑_ver2.1.ipynb
    2018-10-31  오후 05:08           215,348 WCS02_크롤링과_스크랩핑_ver2.2.ipynb
    2018-11-12  오후 11:10           161,469 WCS02_크롤링과_스크랩핑_ver2.4.ipynb
    2018-11-12  오후 10:25            10,925 _readme.txt
                   7개 파일             689,927 바이트
                   5개 디렉터리  24,773,103,616 바이트 남음
    

<hr>

``` wget
wget --help 
wget link -O file.ext 
```


```python
! wget --help
```

    GNU Wget 1.19.4, a non-interactive network retriever.
    Usage: wget [OPTION]... [URL]...
    
    Mandatory arguments to long options are mandatory for short options too.
    
    Startup:
      -V,  --version                   display the version of Wget and exit
      -h,  --help                      print this help
      -b,  --background                go to background after startup
      -e,  --execute=COMMAND           execute a `.wgetrc'-style command
    
    Logging and input file:
      -o,  --output-file=FILE          log messages to FILE
      -a,  --append-output=FILE        append messages to FILE
      -d,  --debug                     print lots of debugging information
      -q,  --quiet                     quiet (no output)
      -v,  --verbose                   be verbose (this is the default)
      -nv, --no-verbose                turn off verboseness, without being quiet
           --report-speed=TYPE         output bandwidth as TYPE.  TYPE can be bits
      -i,  --input-file=FILE           download URLs found in local or external FILE
           --input-metalink=FILE       download files covered in local Metalink FILE
      -F,  --force-html                treat input file as HTML
      -B,  --base=URL                  resolves HTML input-file links (-i -F)
                                         relative to URL
           --config=FILE               specify config file to use
           --no-config                 do not read any config file
           --rejected-log=FILE         log reasons for URL rejection to FILE
    
    Download:
      -t,  --tries=NUMBER              set number of retries to NUMBER (0 unlimits)
           --retry-connrefused         retry even if connection is refused
      -O,  --output-document=FILE      write documents to FILE
      -nc, --no-clobber                skip downloads that would download to
                                         existing files (overwriting them)
           --no-netrc                  don't try to obtain credentials from .netrc
      -c,  --continue                  resume getting a partially-downloaded file
           --start-pos=OFFSET          start downloading from zero-based position OFFSET
           --progress=TYPE             select progress gauge type
           --show-progress             display the progress bar in any verbosity mode
      -N,  --timestamping              don't re-retrieve files unless newer than
                                         local
           --no-if-modified-since      don't use conditional if-modified-since get
                                         requests in timestamping mode
           --no-use-server-timestamps  don't set the local file's timestamp by
                                         the one on the server
      -S,  --server-response           print server response
           --spider                    don't download anything
      -T,  --timeout=SECONDS           set all timeout values to SECONDS
           --dns-timeout=SECS          set the DNS lookup timeout to SECS
           --connect-timeout=SECS      set the connect timeout to SECS
           --read-timeout=SECS         set the read timeout to SECS
      -w,  --wait=SECONDS              wait SECONDS between retrievals
           --waitretry=SECONDS         wait 1..SECONDS between retries of a retrieval
           --random-wait               wait from 0.5*WAIT...1.5*WAIT secs between retrievals
           --no-proxy                  explicitly turn off proxy
      -Q,  --quota=NUMBER              set retrieval quota to NUMBER
           --bind-address=ADDRESS      bind to ADDRESS (hostname or IP) on local host
           --limit-rate=RATE           limit download rate to RATE
           --no-dns-cache              disable caching DNS lookups
           --restrict-file-names=OS    restrict chars in file names to ones OS allows
           --ignore-case               ignore case when matching files/directories
      -4,  --inet4-only                connect only to IPv4 addresses
      -6,  --inet6-only                connect only to IPv6 addresses
           --prefer-family=FAMILY      connect first to addresses of specified family,
                                         one of IPv6, IPv4, or none
           --user=USER                 set both ftp and http user to USER
           --password=PASS             set both ftp and http password to PASS
           --ask-password              prompt for passwords
           --use-askpass=COMMAND       specify credential handler for requesting 
                                         username and password.  If no COMMAND is 
                                         specified the WGET_ASKPASS or the SSH_ASKPASS 
                                         environment variable is used.
           --no-iri                    turn off IRI support
           --local-encoding=ENC        use ENC as the local encoding for IRIs
           --remote-encoding=ENC       use ENC as the default remote encoding
           --unlink                    remove file before clobber
           --keep-badhash              keep files with checksum mismatch (append .badhash)
           --metalink-index=NUMBER     Metalink application/metalink4+xml metaurl ordinal NUMBER
           --metalink-over-http        use Metalink metadata from HTTP response headers
           --preferred-location        preferred location for Metalink resources
    
    Directories:
      -nd, --no-directories            don't create directories
      -x,  --force-directories         force creation of directories
      -nH, --no-host-directories       don't create host directories
           --protocol-directories      use protocol name in directories
      -P,  --directory-prefix=PREFIX   save files to PREFIX/..
           --cut-dirs=NUMBER           ignore NUMBER remote directory components
    
    HTTP options:
           --http-user=USER            set http user to USER
           --http-password=PASS        set http password to PASS
           --no-cache                  disallow server-cached data
           --default-page=NAME         change the default page name (normally
                                         this is 'index.html'.)
      -E,  --adjust-extension          save HTML/CSS documents with proper extensions
           --ignore-length             ignore 'Content-Length' header field
           --header=STRING             insert STRING among the headers
           --compression=TYPE          choose compression, one of auto, gzip and none. (default: none)
           --max-redirect              maximum redirections allowed per page
           --proxy-user=USER           set USER as proxy username
           --proxy-password=PASS       set PASS as proxy password
           --referer=URL               include 'Referer: URL' header in HTTP request
           --save-headers              save the HTTP headers to file
      -U,  --user-agent=AGENT          identify as AGENT instead of Wget/VERSION
           --no-http-keep-alive        disable HTTP keep-alive (persistent connections)
           --no-cookies                don't use cookies
           --load-cookies=FILE         load cookies from FILE before session
           --save-cookies=FILE         save cookies to FILE after session
           --keep-session-cookies      load and save session (non-permanent) cookies
           --post-data=STRING          use the POST method; send STRING as the data
           --post-file=FILE            use the POST method; send contents of FILE
           --method=HTTPMethod         use method "HTTPMethod" in the request
           --body-data=STRING          send STRING as data. --method MUST be set
           --body-file=FILE            send contents of FILE. --method MUST be set
           --content-disposition       honor the Content-Disposition header when
                                         choosing local file names (EXPERIMENTAL)
           --content-on-error          output the received content on server errors
           --auth-no-challenge         send Basic HTTP authentication information
                                         without first waiting for the server's
                                         challenge
    
    HTTPS (SSL/TLS) options:
           --secure-protocol=PR        choose secure protocol, one of auto, SSLv2,
                                         SSLv3, TLSv1, TLSv1_1, TLSv1_2 and PFS
           --https-only                only follow secure HTTPS links
           --no-check-certificate      don't validate the server's certificate
           --certificate=FILE          client certificate file
           --certificate-type=TYPE     client certificate type, PEM or DER
           --private-key=FILE          private key file
           --private-key-type=TYPE     private key type, PEM or DER
           --ca-certificate=FILE       file with the bundle of CAs
           --ca-directory=DIR          directory where hash list of CAs is stored
           --crl-file=FILE             file with bundle of CRLs
           --pinnedpubkey=FILE/HASHES  Public key (PEM/DER) file, or any number
                                       of base64 encoded sha256 hashes preceded by
                                       'sha256//' and separated by ';', to verify
                                       peer against
           --random-file=FILE          file with random data for seeding the SSL PRNG
    
    HSTS options:
           --no-hsts                   disable HSTS
           --hsts-file                 path of HSTS database (will override default)
    
    FTP options:
           --ftp-user=USER             set ftp user to USER
           --ftp-password=PASS         set ftp password to PASS
           --no-remove-listing         don't remove '.listing' files
           --no-glob                   turn off FTP file name globbing
           --no-passive-ftp            disable the "passive" transfer mode
           --preserve-permissions      preserve remote file permissions
           --retr-symlinks             when recursing, get linked-to files (not dir)
    
    FTPS options:
           --ftps-implicit                 use implicit FTPS (default port is 990)
           --ftps-resume-ssl               resume the SSL/TLS session started in the control connection when
                                             opening a data connection
           --ftps-clear-data-connection    cipher the control channel only; all the data will be in plaintext
           --ftps-fallback-to-ftp          fall back to FTP if FTPS is not supported in the target server
    WARC options:
           --warc-file=FILENAME        save request/response data to a .warc.gz file
           --warc-header=STRING        insert STRING into the warcinfo record
           --warc-max-size=NUMBER      set maximum size of WARC files to NUMBER
           --warc-cdx                  write CDX index files
           --warc-dedup=FILENAME       do not store records listed in this CDX file
           --no-warc-compression       do not compress WARC files with GZIP
           --no-warc-digests           do not calculate SHA1 digests
           --no-warc-keep-log          do not store the log file in a WARC record
           --warc-tempdir=DIRECTORY    location for temporary files created by the
                                         WARC writer
    
    Recursive download:
      -r,  --recursive                 specify recursive download
      -l,  --level=NUMBER              maximum recursion depth (inf or 0 for infinite)
           --delete-after              delete files locally after downloading them
      -k,  --convert-links             make links in downloaded HTML or CSS point to
                                         local files
           --convert-file-only         convert the file part of the URLs only (usually known as the basename)
           --backups=N                 before writing file X, rotate up to N backup files
      -K,  --backup-converted          before converting file X, back up as X.orig
      -m,  --mirror                    shortcut for -N -r -l inf --no-remove-listing
      -p,  --page-requisites           get all images, etc. needed to display HTML page
           --strict-comments           turn on strict (SGML) handling of HTML comments
    
    Recursive accept/reject:
      -A,  --accept=LIST               comma-separated list of accepted extensions
      -R,  --reject=LIST               comma-separated list of rejected extensions
           --accept-regex=REGEX        regex matching accepted URLs
           --reject-regex=REGEX        regex matching rejected URLs
           --regex-type=TYPE           regex type (posix)
      -D,  --domains=LIST              comma-separated list of accepted domains
           --exclude-domains=LIST      comma-separated list of rejected domains
           --follow-ftp                follow FTP links from HTML documents
           --follow-tags=LIST          comma-separated list of followed HTML tags
           --ignore-tags=LIST          comma-separated list of ignored HTML tags
      -H,  --span-hosts                go to foreign hosts when recursive
      -L,  --relative                  follow relative links only
      -I,  --include-directories=LIST  list of allowed directories
           --trust-server-names        use the name specified by the redirection
                                         URL's last component
      -X,  --exclude-directories=LIST  list of excluded directories
      -np, --no-parent                 don't ascend to the parent directory
    
    Mail bug reports and suggestions to <bug-wget@gnu.org>
    


```python
# rss 데이터 저장
! wget rss.xml http://www.weather.go.kr/weather/forecast/mid-term-rss3.jsp?stnId=109 -O ./data/rss.xml
```

    --2018-11-12 23:10:42--  http://rss.xml/
    Resolving rss.xml (rss.xml)... failed: 알려진 호스트가 없습니다. .
    wget: unable to resolve host address 'rss.xml'
    --2018-11-12 23:10:42--  http://www.weather.go.kr/weather/forecast/mid-term-rss3.jsp?stnId=109
    Resolving www.weather.go.kr (www.weather.go.kr)... 121.78.77.90
    Connecting to www.weather.go.kr (www.weather.go.kr)|121.78.77.90|:80... connected.
    HTTP request sent, awaiting response... 200 OK
    Length: 96044 (94K) [text/xml]
    Saving to: './data/rss.xml'
    
         0K .......... .......... .......... .......... .......... 53% 1.74M 0s
        50K .......... .......... .......... .......... ...       100% 2.13M=0.05s
    
    2018-11-12 23:10:43 (1.90 MB/s) - './data/rss.xml' saved [96044/96044]
    
    FINISHED --2018-11-12 23:10:43--
    Total wall clock time: 0.2s
    Downloaded: 1 files, 94K in 0.05s (1.90 MB/s)
    


```python
! dir data\*.xml
```

     C 드라이브의 볼륨에는 이름이 없습니다.
     볼륨 일련 번호: 3CBD-1374
    
     C:\Users\user\Dropbox\sect_tech\src_anaconda\P1810_IITP_Multicampus\tb10-web-crawling\data 디렉터리
    
    2018-11-12  오후 11:10            96,044 rss.xml
                   1개 파일              96,044 바이트
                   0개 디렉터리  24,773,005,312 바이트 남음
    

### <font color='#0000CC'> c2-13_scrape_rss
> ElementTree 모듈을 사용해 RSS 파싱


```python
# ElementTree 모듈을 읽어 들입니다.
from xml.etree import ElementTree

# parse() 함수로 파일을 읽어 들이고 ElementTree 객체를 만듭니다.
tree = ElementTree.parse('./data/rss.xml')

# getroot() 메서드로 XML의 루트 요소를 추출합니다.
root = tree.getroot()

```


```python
msg = " - tree : {} \n - root : {}".format(tree, root)
print(msg)
```

     - tree : <xml.etree.ElementTree.ElementTree object at 0x00000203DF1DDCC0> 
     - root : <Element 'rss' at 0x00000203DF1E13B8>
    


```python
find_data = root.findall('channel/item/description/body/location/data')
len(find_data), find_data[0]
```




    (455, <Element 'data' at 0x00000203DF238598>)




```python
# findall() 메서드로 요소 목록을 추출합니다.
# 태그를 찾습니다(자세한 내용은 RSS를 열어 참고해주세요).
for item in root.findall('channel/item/description/body/location/data'):
    # find() 메서드로 요소를 찾고 text 속성으로 값을 추출합니다.
    tm_ef = item.find('tmEf').text
    tmn   = item.find('tmn').text
    tmx   = item.find('tmx').text
    wf    = item.find('wf').text
    print(tm_ef, tmn, tmx, wf) # 출력합니다.

```

    2018-11-15 00:00 4 14 구름조금
    2018-11-15 12:00 4 14 구름조금
    2018-11-16 00:00 4 14 구름조금
    2018-11-16 12:00 4 14 구름조금
    2018-11-17 00:00 4 12 구름많음
    2018-11-17 12:00 4 12 구름많음
    2018-11-18 00:00 3 10 구름많음
    2018-11-18 12:00 3 10 구름많음
    2018-11-19 00:00 0 9 구름조금
    2018-11-19 12:00 0 9 구름조금
    2018-11-20 00:00 0 9 구름조금
    2018-11-21 00:00 1 10 구름많음
    2018-11-22 00:00 0 9 구름조금
    2018-11-15 00:00 6 13 구름조금
    2018-11-15 12:00 6 13 구름조금
    2018-11-16 00:00 6 13 구름조금
    2018-11-16 12:00 6 13 구름조금
    2018-11-17 00:00 5 11 구름많음
    2018-11-17 12:00 5 11 구름많음
    2018-11-18 00:00 3 10 구름많음
    2018-11-18 12:00 3 10 구름많음
    2018-11-19 00:00 2 8 구름조금
    2018-11-19 12:00 2 8 구름조금
    2018-11-20 00:00 1 8 구름조금
    2018-11-21 00:00 2 8 구름많음
    2018-11-22 00:00 2 8 구름조금
    2018-11-15 00:00 3 14 구름조금
    2018-11-15 12:00 3 14 구름조금
    2018-11-16 00:00 3 14 구름조금
    2018-11-16 12:00 3 14 구름조금
    2018-11-17 00:00 3 12 구름많음
    2018-11-17 12:00 3 12 구름많음
    2018-11-18 00:00 2 11 구름많음
    2018-11-18 12:00 2 11 구름많음
    2018-11-19 00:00 0 9 구름조금
    2018-11-19 12:00 0 9 구름조금
    2018-11-20 00:00 0 9 구름조금
    2018-11-21 00:00 1 10 구름많음
    2018-11-22 00:00 0 9 구름조금
    2018-11-15 00:00 -1 14 구름조금
    2018-11-15 12:00 -1 14 구름조금
    2018-11-16 00:00 0 13 구름조금
    2018-11-16 12:00 0 13 구름조금
    2018-11-17 00:00 0 11 구름많음
    2018-11-17 12:00 0 11 구름많음
    2018-11-18 00:00 -1 9 구름많음
    2018-11-18 12:00 -1 9 구름많음
    2018-11-19 00:00 -4 8 구름조금
    2018-11-19 12:00 -4 8 구름조금
    2018-11-20 00:00 -4 8 구름조금
    2018-11-21 00:00 -4 8 구름많음
    2018-11-22 00:00 -5 8 구름조금
    2018-11-15 00:00 1 15 구름조금
    2018-11-15 12:00 1 15 구름조금
    2018-11-16 00:00 1 14 구름조금
    2018-11-16 12:00 1 14 구름조금
    2018-11-17 00:00 1 12 구름많음
    2018-11-17 12:00 1 12 구름많음
    2018-11-18 00:00 0 11 구름많음
    2018-11-18 12:00 0 11 구름많음
    2018-11-19 00:00 -2 9 구름조금
    2018-11-19 12:00 -2 9 구름조금
    2018-11-20 00:00 -2 9 구름조금
    2018-11-21 00:00 -1 10 구름많음
    2018-11-22 00:00 -2 9 구름조금
    2018-11-15 00:00 3 14 구름조금
    2018-11-15 12:00 3 14 구름조금
    2018-11-16 00:00 3 14 구름조금
    2018-11-16 12:00 3 14 구름조금
    2018-11-17 00:00 3 12 구름많음
    2018-11-17 12:00 3 12 구름많음
    2018-11-18 00:00 2 10 구름많음
    2018-11-18 12:00 2 10 구름많음
    2018-11-19 00:00 0 9 구름조금
    2018-11-19 12:00 0 9 구름조금
    2018-11-20 00:00 0 9 구름조금
    2018-11-21 00:00 1 10 구름많음
    2018-11-22 00:00 1 9 구름조금
    2018-11-15 00:00 7 12 구름조금
    2018-11-15 12:00 7 12 구름조금
    2018-11-16 00:00 7 10 구름조금
    2018-11-16 12:00 7 10 구름조금
    2018-11-17 00:00 5 8 구름많음
    2018-11-17 12:00 5 8 구름많음
    2018-11-18 00:00 7 11 구름많음
    2018-11-18 12:00 7 11 구름많음
    2018-11-19 00:00 5 9 구름조금
    2018-11-19 12:00 5 9 구름조금
    2018-11-20 00:00 4 10 구름조금
    2018-11-21 00:00 4 8 구름많음
    2018-11-22 00:00 2 11 구름조금
    2018-11-15 00:00 2 14 구름조금
    2018-11-15 12:00 2 14 구름조금
    2018-11-16 00:00 4 13 구름조금
    2018-11-16 12:00 4 13 구름조금
    2018-11-17 00:00 2 10 구름많음
    2018-11-17 12:00 2 10 구름많음
    2018-11-18 00:00 1 10 구름많음
    2018-11-18 12:00 1 10 구름많음
    2018-11-19 00:00 2 10 구름조금
    2018-11-19 12:00 2 10 구름조금
    2018-11-20 00:00 -1 8 구름조금
    2018-11-21 00:00 0 9 구름많음
    2018-11-22 00:00 -2 8 구름조금
    2018-11-15 00:00 6 15 구름조금
    2018-11-15 12:00 6 15 구름조금
    2018-11-16 00:00 7 14 구름조금
    2018-11-16 12:00 7 14 구름조금
    2018-11-17 00:00 4 10 구름많음
    2018-11-17 12:00 4 10 구름많음
    2018-11-18 00:00 3 11 구름많음
    2018-11-18 12:00 3 11 구름많음
    2018-11-19 00:00 4 10 구름조금
    2018-11-19 12:00 4 10 구름조금
    2018-11-20 00:00 1 9 구름조금
    2018-11-21 00:00 3 9 구름많음
    2018-11-22 00:00 0 8 구름조금
    2018-11-15 00:00 2 14 구름조금
    2018-11-15 12:00 2 14 구름조금
    2018-11-16 00:00 4 13 구름조금
    2018-11-16 12:00 4 13 구름조금
    2018-11-17 00:00 1 9 구름많음
    2018-11-17 12:00 1 9 구름많음
    2018-11-18 00:00 -1 10 구름많음
    2018-11-18 12:00 -1 10 구름많음
    2018-11-19 00:00 2 9 구름조금
    2018-11-19 12:00 2 9 구름조금
    2018-11-20 00:00 -3 7 구름조금
    2018-11-21 00:00 -1 7 구름많음
    2018-11-22 00:00 -2 8 구름조금
    2018-11-15 00:00 3 13 구름조금
    2018-11-15 12:00 3 13 구름조금
    2018-11-16 00:00 4 13 구름조금
    2018-11-16 12:00 4 13 구름조금
    2018-11-17 00:00 2 9 구름많음
    2018-11-17 12:00 2 9 구름많음
    2018-11-18 00:00 -1 10 구름많음
    2018-11-18 12:00 -1 10 구름많음
    2018-11-19 00:00 1 8 구름조금
    2018-11-19 12:00 1 8 구름조금
    2018-11-20 00:00 -1 8 구름조금
    2018-11-21 00:00 0 8 구름많음
    2018-11-22 00:00 -1 6 구름조금
    2018-11-15 00:00 3 15 구름조금
    2018-11-15 12:00 3 15 구름조금
    2018-11-16 00:00 5 14 구름조금
    2018-11-16 12:00 5 14 구름조금
    2018-11-17 00:00 2 10 구름많음
    2018-11-17 12:00 2 10 구름많음
    2018-11-18 00:00 0 11 구름많음
    2018-11-18 12:00 0 11 구름많음
    2018-11-19 00:00 3 11 구름조금
    2018-11-19 12:00 3 11 구름조금
    2018-11-20 00:00 0 9 구름조금
    2018-11-21 00:00 0 9 구름많음
    2018-11-22 00:00 -1 9 구름조금
    2018-11-15 00:00 3 15 구름조금
    2018-11-15 12:00 3 15 구름조금
    2018-11-16 00:00 5 14 구름조금
    2018-11-16 12:00 5 14 구름조금
    2018-11-17 00:00 2 10 구름많음
    2018-11-17 12:00 2 10 구름많음
    2018-11-18 00:00 0 11 구름많음
    2018-11-18 12:00 0 11 구름많음
    2018-11-19 00:00 3 10 구름조금
    2018-11-19 12:00 3 10 구름조금
    2018-11-20 00:00 -1 9 구름조금
    2018-11-21 00:00 1 10 구름많음
    2018-11-22 00:00 -2 9 구름조금
    2018-11-15 00:00 3 14 구름조금
    2018-11-15 12:00 3 14 구름조금
    2018-11-16 00:00 5 13 구름조금
    2018-11-16 12:00 5 13 구름조금
    2018-11-17 00:00 3 9 구름많음
    2018-11-17 12:00 3 9 구름많음
    2018-11-18 00:00 1 11 구름많음
    2018-11-18 12:00 1 11 구름많음
    2018-11-19 00:00 2 9 구름조금
    2018-11-19 12:00 2 9 구름조금
    2018-11-20 00:00 0 8 구름조금
    2018-11-21 00:00 1 8 구름많음
    2018-11-22 00:00 0 7 구름조금
    2018-11-15 00:00 0 14 구름조금
    2018-11-15 12:00 0 14 구름조금
    2018-11-16 00:00 2 13 구름조금
    2018-11-16 12:00 2 13 구름조금
    2018-11-17 00:00 0 10 구름많음
    2018-11-17 12:00 0 10 구름많음
    2018-11-18 00:00 -2 10 구름많음
    2018-11-18 12:00 -2 10 구름많음
    2018-11-19 00:00 0 9 구름조금
    2018-11-19 12:00 0 9 구름조금
    2018-11-20 00:00 -3 8 구름조금
    2018-11-21 00:00 -1 9 구름많음
    2018-11-22 00:00 -3 9 구름조금
    2018-11-15 00:00 3 15 구름조금
    2018-11-15 12:00 3 15 구름조금
    2018-11-16 00:00 4 13 구름조금
    2018-11-16 12:00 4 13 구름조금
    2018-11-17 00:00 1 10 구름많음
    2018-11-17 12:00 1 10 구름많음
    2018-11-18 00:00 -1 11 구름많음
    2018-11-18 12:00 -1 11 구름많음
    2018-11-19 00:00 2 10 구름조금
    2018-11-19 12:00 2 10 구름조금
    2018-11-20 00:00 -2 8 구름조금
    2018-11-21 00:00 0 8 구름많음
    2018-11-22 00:00 -3 8 구름조금
    2018-11-15 00:00 -1 14 구름조금
    2018-11-15 12:00 -1 14 구름조금
    2018-11-16 00:00 1 13 구름조금
    2018-11-16 12:00 1 13 구름조금
    2018-11-17 00:00 -1 10 구름많음
    2018-11-17 12:00 -1 10 구름많음
    2018-11-18 00:00 -3 10 구름많음
    2018-11-18 12:00 -3 10 구름많음
    2018-11-19 00:00 -1 9 구름조금
    2018-11-19 12:00 -1 9 구름조금
    2018-11-20 00:00 -5 7 구름조금
    2018-11-21 00:00 -3 8 구름많음
    2018-11-22 00:00 -5 8 구름조금
    2018-11-15 00:00 0 14 구름조금
    2018-11-15 12:00 0 14 구름조금
    2018-11-16 00:00 2 13 구름조금
    2018-11-16 12:00 2 13 구름조금
    2018-11-17 00:00 -1 9 구름많음
    2018-11-17 12:00 -1 9 구름많음
    2018-11-18 00:00 -3 10 구름많음
    2018-11-18 12:00 -3 10 구름많음
    2018-11-19 00:00 0 9 구름조금
    2018-11-19 12:00 0 9 구름조금
    2018-11-20 00:00 -4 8 구름조금
    2018-11-21 00:00 -3 7 구름많음
    2018-11-22 00:00 -4 9 구름조금
    2018-11-15 00:00 -1 13 구름조금
    2018-11-15 12:00 -1 13 구름조금
    2018-11-16 00:00 1 12 구름조금
    2018-11-16 12:00 1 12 구름조금
    2018-11-17 00:00 -2 9 구름많음
    2018-11-17 12:00 -2 9 구름많음
    2018-11-18 00:00 -3 11 구름많음
    2018-11-18 12:00 -3 11 구름많음
    2018-11-19 00:00 -2 9 구름조금
    2018-11-19 12:00 -2 9 구름조금
    2018-11-20 00:00 -5 7 구름조금
    2018-11-21 00:00 -2 8 구름많음
    2018-11-22 00:00 -5 7 구름조금
    2018-11-15 00:00 1 13 구름조금
    2018-11-15 12:00 1 13 구름조금
    2018-11-16 00:00 2 13 구름조금
    2018-11-16 12:00 2 13 구름조금
    2018-11-17 00:00 -1 9 구름많음
    2018-11-17 12:00 -1 9 구름많음
    2018-11-18 00:00 -3 10 구름많음
    2018-11-18 12:00 -3 10 구름많음
    2018-11-19 00:00 0 9 구름조금
    2018-11-19 12:00 0 9 구름조금
    2018-11-20 00:00 -4 7 구름조금
    2018-11-21 00:00 -2 7 구름많음
    2018-11-22 00:00 -4 7 구름조금
    2018-11-15 00:00 -1 14 구름조금
    2018-11-15 12:00 -1 14 구름조금
    2018-11-16 00:00 1 13 구름조금
    2018-11-16 12:00 1 13 구름조금
    2018-11-17 00:00 0 10 구름많음
    2018-11-17 12:00 0 10 구름많음
    2018-11-18 00:00 -3 10 구름많음
    2018-11-18 12:00 -3 10 구름많음
    2018-11-19 00:00 -1 10 구름조금
    2018-11-19 12:00 -1 10 구름조금
    2018-11-20 00:00 -4 7 구름조금
    2018-11-21 00:00 -3 7 구름많음
    2018-11-22 00:00 -5 7 구름조금
    2018-11-15 00:00 3 14 구름조금
    2018-11-15 12:00 3 14 구름조금
    2018-11-16 00:00 4 13 구름조금
    2018-11-16 12:00 4 13 구름조금
    2018-11-17 00:00 3 10 구름많음
    2018-11-17 12:00 3 10 구름많음
    2018-11-18 00:00 0 10 구름많음
    2018-11-18 12:00 0 10 구름많음
    2018-11-19 00:00 2 10 구름조금
    2018-11-19 12:00 2 10 구름조금
    2018-11-20 00:00 -1 8 구름조금
    2018-11-21 00:00 0 9 구름많음
    2018-11-22 00:00 -3 8 구름조금
    2018-11-15 00:00 1 14 구름조금
    2018-11-15 12:00 1 14 구름조금
    2018-11-16 00:00 3 13 구름조금
    2018-11-16 12:00 3 13 구름조금
    2018-11-17 00:00 0 10 구름많음
    2018-11-17 12:00 0 10 구름많음
    2018-11-18 00:00 -2 10 구름많음
    2018-11-18 12:00 -2 10 구름많음
    2018-11-19 00:00 0 9 구름조금
    2018-11-19 12:00 0 9 구름조금
    2018-11-20 00:00 -3 8 구름조금
    2018-11-21 00:00 -2 9 구름많음
    2018-11-22 00:00 -4 10 구름조금
    2018-11-15 00:00 3 14 구름조금
    2018-11-15 12:00 3 14 구름조금
    2018-11-16 00:00 3 13 구름조금
    2018-11-16 12:00 3 13 구름조금
    2018-11-17 00:00 2 11 구름많음
    2018-11-17 12:00 2 11 구름많음
    2018-11-18 00:00 -1 11 구름많음
    2018-11-18 12:00 -1 11 구름많음
    2018-11-19 00:00 0 10 구름조금
    2018-11-19 12:00 0 10 구름조금
    2018-11-20 00:00 -3 8 구름조금
    2018-11-21 00:00 -3 8 구름많음
    2018-11-22 00:00 -3 9 구름조금
    2018-11-15 00:00 2 14 구름조금
    2018-11-15 12:00 2 14 구름조금
    2018-11-16 00:00 3 13 구름조금
    2018-11-16 12:00 3 13 구름조금
    2018-11-17 00:00 1 10 구름많음
    2018-11-17 12:00 1 10 구름많음
    2018-11-18 00:00 0 10 구름많음
    2018-11-18 12:00 0 10 구름많음
    2018-11-19 00:00 2 11 구름조금
    2018-11-19 12:00 2 11 구름조금
    2018-11-20 00:00 -2 7 구름조금
    2018-11-21 00:00 -1 8 구름많음
    2018-11-22 00:00 -4 8 구름조금
    2018-11-15 00:00 3 14 구름조금
    2018-11-15 12:00 3 14 구름조금
    2018-11-16 00:00 4 13 구름조금
    2018-11-16 12:00 4 13 구름조금
    2018-11-17 00:00 2 10 구름많음
    2018-11-17 12:00 2 10 구름많음
    2018-11-18 00:00 1 10 구름많음
    2018-11-18 12:00 1 10 구름많음
    2018-11-19 00:00 2 10 구름조금
    2018-11-19 12:00 2 10 구름조금
    2018-11-20 00:00 -1 8 구름조금
    2018-11-21 00:00 0 9 구름많음
    2018-11-22 00:00 -2 8 구름조금
    2018-11-15 00:00 4 14 구름조금
    2018-11-15 12:00 4 14 구름조금
    2018-11-16 00:00 4 14 구름조금
    2018-11-16 12:00 4 14 구름조금
    2018-11-17 00:00 2 11 구름많음
    2018-11-17 12:00 2 11 구름많음
    2018-11-18 00:00 1 10 구름많음
    2018-11-18 12:00 1 10 구름많음
    2018-11-19 00:00 1 9 구름조금
    2018-11-19 12:00 1 9 구름조금
    2018-11-20 00:00 -1 9 구름조금
    2018-11-21 00:00 1 10 구름많음
    2018-11-22 00:00 -1 8 구름조금
    2018-11-15 00:00 3 15 구름조금
    2018-11-15 12:00 3 15 구름조금
    2018-11-16 00:00 5 14 구름조금
    2018-11-16 12:00 5 14 구름조금
    2018-11-17 00:00 2 10 구름많음
    2018-11-17 12:00 2 10 구름많음
    2018-11-18 00:00 0 10 구름많음
    2018-11-18 12:00 0 10 구름많음
    2018-11-19 00:00 3 10 구름조금
    2018-11-19 12:00 3 10 구름조금
    2018-11-20 00:00 -1 9 구름조금
    2018-11-21 00:00 1 9 구름많음
    2018-11-22 00:00 -1 9 구름조금
    2018-11-15 00:00 3 15 구름조금
    2018-11-15 12:00 3 15 구름조금
    2018-11-16 00:00 4 14 구름조금
    2018-11-16 12:00 4 14 구름조금
    2018-11-17 00:00 3 11 구름많음
    2018-11-17 12:00 3 11 구름많음
    2018-11-18 00:00 0 11 구름많음
    2018-11-18 12:00 0 11 구름많음
    2018-11-19 00:00 3 10 구름조금
    2018-11-19 12:00 3 10 구름조금
    2018-11-20 00:00 0 9 구름조금
    2018-11-21 00:00 0 9 구름많음
    2018-11-22 00:00 -1 9 구름조금
    2018-11-15 00:00 4 15 구름조금
    2018-11-15 12:00 4 15 구름조금
    2018-11-16 00:00 5 14 구름조금
    2018-11-16 12:00 5 14 구름조금
    2018-11-17 00:00 3 11 구름많음
    2018-11-17 12:00 3 11 구름많음
    2018-11-18 00:00 2 11 구름많음
    2018-11-18 12:00 2 11 구름많음
    2018-11-19 00:00 3 10 구름조금
    2018-11-19 12:00 3 10 구름조금
    2018-11-20 00:00 0 9 구름조금
    2018-11-21 00:00 1 9 구름많음
    2018-11-22 00:00 -1 9 구름조금
    2018-11-15 00:00 5 15 구름조금
    2018-11-15 12:00 5 15 구름조금
    2018-11-16 00:00 5 14 구름조금
    2018-11-16 12:00 5 14 구름조금
    2018-11-17 00:00 3 10 구름많음
    2018-11-17 12:00 3 10 구름많음
    2018-11-18 00:00 1 10 구름많음
    2018-11-18 12:00 1 10 구름많음
    2018-11-19 00:00 3 10 구름조금
    2018-11-19 12:00 3 10 구름조금
    2018-11-20 00:00 0 9 구름조금
    2018-11-21 00:00 1 10 구름많음
    2018-11-22 00:00 -1 9 구름조금
    2018-11-15 00:00 1 15 구름조금
    2018-11-15 12:00 1 15 구름조금
    2018-11-16 00:00 2 14 구름조금
    2018-11-16 12:00 2 14 구름조금
    2018-11-17 00:00 2 9 구름많음
    2018-11-17 12:00 2 9 구름많음
    2018-11-18 00:00 -1 11 구름많음
    2018-11-18 12:00 -1 11 구름많음
    2018-11-19 00:00 2 11 구름조금
    2018-11-19 12:00 2 11 구름조금
    2018-11-20 00:00 -2 9 구름조금
    2018-11-21 00:00 -1 10 구름많음
    2018-11-22 00:00 -3 10 구름조금
    2018-11-15 00:00 2 14 구름조금
    2018-11-15 12:00 2 14 구름조금
    2018-11-16 00:00 3 13 구름조금
    2018-11-16 12:00 3 13 구름조금
    2018-11-17 00:00 1 10 구름많음
    2018-11-17 12:00 1 10 구름많음
    2018-11-18 00:00 -1 10 구름많음
    2018-11-18 12:00 -1 10 구름많음
    2018-11-19 00:00 1 10 구름조금
    2018-11-19 12:00 1 10 구름조금
    2018-11-20 00:00 -2 8 구름조금
    2018-11-21 00:00 -1 8 구름많음
    2018-11-22 00:00 -3 9 구름조금
    2018-11-15 00:00 2 14 구름조금
    2018-11-15 12:00 2 14 구름조금
    2018-11-16 00:00 3 14 구름조금
    2018-11-16 12:00 3 14 구름조금
    2018-11-17 00:00 1 10 구름많음
    2018-11-17 12:00 1 10 구름많음
    2018-11-18 00:00 -1 11 구름많음
    2018-11-18 12:00 -1 11 구름많음
    2018-11-19 00:00 1 11 구름조금
    2018-11-19 12:00 1 11 구름조금
    2018-11-20 00:00 -2 7 구름조금
    2018-11-21 00:00 -2 8 구름많음
    2018-11-22 00:00 -4 9 구름조금
    2018-11-15 00:00 1 13 구름조금
    2018-11-15 12:00 1 13 구름조금
    2018-11-16 00:00 2 13 구름조금
    2018-11-16 12:00 2 13 구름조금
    2018-11-17 00:00 1 9 구름많음
    2018-11-17 12:00 1 9 구름많음
    2018-11-18 00:00 -1 11 구름많음
    2018-11-18 12:00 -1 11 구름많음
    2018-11-19 00:00 0 9 구름조금
    2018-11-19 12:00 0 9 구름조금
    2018-11-20 00:00 -2 8 구름조금
    2018-11-21 00:00 -2 8 구름많음
    2018-11-22 00:00 -4 8 구름조금
    

<hr>
### <font color='blue'> 데이터 저장
> 
- TEXT파일로 저장 : CSV/TSV 형식, JSON 형식
- DataBase에 저장 : SQLite3, MySQL, Oracle, MongoDB 

### <font color='#0000CC'> c2-14_save_csv_join
> CSV(Comma-Seperated Values) 형식으로 저장
- str.join() 메소드 사용
- (venb) $ python OOO.py > OOO.csv


```python
# 첫 번째 줄에 헤더를 작성합니다.
print('rank,city,population')  

```

    rank,city,population
    


```python
# join() 메서드의 매개변수로 전달한 list는 str이어야 하므로 주의해 주세요.
print(','.join(['1', '상하이', '24150000']))
print(','.join(['2', '카라치', '23500000']))
print(','.join(['3', '베이징', '21516000']))
print(','.join(['4', '텐진', '14722100']))
print(','.join(['5', '이스탄불', '14160467']))
```

    1,상하이,24150000
    2,카라치,23500000
    3,베이징,21516000
    4,텐진,14722100
    5,이스탄불,14160467
    

### <font color='#0000CC'> c2-15_save_csv
> CSV(Comma-Seperated Values) 형식으로 저장


```python
import csv

# 파일을 엽니다. newline=''으로 줄바꿈 코드의 자동 변환을 제어합니다.
csv_file = './data/top_cities_1.csv'

with open(csv_file, 'w', newline='') as f:
    # csv.writer는 파일 객체를 매개변수로 지정합니다.
    writer = csv.writer(f)  
    # 첫 번째 줄에는 헤더를 작성합니다.
    writer.writerow(['rank', 'city', 'population'])  
    # writerows()에 리스트를 전달하면 여러 개의 값을 출력합니다.
    writer.writerows([
        [1, '상하이', 24150000],
        [2, '카라치', 23500000],
        [3, '베이징', 21516000],
        [4, '텐진', 14722100],
        [5, '이스탄불', 14160467],
    ])
```


```python
# 확인
with open(csv_file, 'r') as f:
    data = f.read()

print(data)
```

    rank,city,population
    1,상하이,24150000
    2,카라치,23500000
    3,베이징,21516000
    4,텐진,14722100
    5,이스탄불,14160467
    
    

### <font color='#0000CC'>  c2-16_save_csv_dict
> 딕셔너리 형식으로 저장


```python
import csv

csv_file = './data/top_cities_2.csv'
with open(csv_file, 'w', newline='') as f:
    # 첫 번째 매개변수에 파일 객체
    # 두 번째 매개변수에 필드 이름 리스트를 지정합니다.
    writer = csv.DictWriter(f, ['rank', 'city', 'population'])
      # 첫 번째 줄에 헤더를 입력합니다.
    writer.writeheader()
    # writerows()로 여러 개의 데이터를 딕셔너리 형태로 작성합니다.
    writer.writerows([
        {'rank': 1,  'city': '상하이',   'population': 24150000},
        {'rank': 2,  'city': '카라치',   'population': 23500000},
        {'rank': 3,  'city': '베이징',   'population': 21516000},
        {'rank': 4,  'city': '텐진',     'population': 14722100},
        {'rank': 5,  'city': '이스탄불', 'population': 14160467},
    ])
```


```python
# 확인
with open(csv_file, 'r') as f:
    data = f.readlines()
    
for idx in range(len(data)):    
    print(data[idx], end='')
    if idx==0:
        print('-'*20)
    
```

    rank,city,population
    --------------------
    1,상하이,24150000
    2,카라치,23500000
    3,베이징,21516000
    4,텐진,14722100
    5,이스탄불,14160467
    

### <font color='#0000CC'> c2-17_save_json
> JSON 형식으로 저장


```python
import json

cities = [
    {'rank': 1,  'city': '상하이',   'population': 24150000},
    {'rank': 2,  'city': '카라치',   'population': 23500000},
    {'rank': 3,  'city': '베이징',   'population': 21516000},
    {'rank': 4,  'city': '텐진',     'population': 14722100},
    {'rank': 5,  'city': '이스탄불', 'population': 14160467},
]

print(json.dumps(cities))
```

    [{"rank": 1, "city": "\uc0c1\ud558\uc774", "population": 24150000}, {"rank": 2, "city": "\uce74\ub77c\uce58", "population": 23500000}, {"rank": 3, "city": "\ubca0\uc774\uc9d5", "population": 21516000}, {"rank": 4, "city": "\ud150\uc9c4", "population": 14722100}, {"rank": 5, "city": "\uc774\uc2a4\ud0c4\ubd88", "population": 14160467}]
    


```python
print(json.dumps(cities, ensure_ascii=False, indent=4))
```

    [
        {
            "rank": 1,
            "city": "상하이",
            "population": 24150000
        },
        {
            "rank": 2,
            "city": "카라치",
            "population": 23500000
        },
        {
            "rank": 3,
            "city": "베이징",
            "population": 21516000
        },
        {
            "rank": 4,
            "city": "텐진",
            "population": 14722100
        },
        {
            "rank": 5,
            "city": "이스탄불",
            "population": 14160467
        }
    ]
    

### <font color='#0000CC'> c2-18_save_sqlite3
> 데이터베이스(SQLite3)에 저장
- SQLite3 는 파일기반의 간단한 관계형 데이터베이스
- SQL 구문을 사용해 데이터를 읽고 쓰기

``` python
import sqlite3

# top_cities.db 파일을 열고 연결을 변수에 저장합니다.
conn = sqlite3.connect('./database/top_cities.db')

# 커서를 추출합니다.
c = conn.cursor()

# execute() 메서드로 SQL 구문을 실행합니다.
# 스크립트를 여러 번 사용해도 같은 결과를 출력할 수 있게 cities 테이블이 존재하는 경우 제거합니다.
c.execute('DROP TABLE IF EXISTS cities')

# cities 테이블을 생성합니다.
c.execute('''
    CREATE TABLE cities (
        rank integer,
        city text,
        population integer
    )
''')

# execute() 메서드의 두 번째 매개변수에는 파라미터를 지정할 수 있습니다.
# SQL 내부에서 파라미터로 변경할 부분(플레이스홀더)은 ?로 지정합니다.
c.execute('INSERT INTO cities VALUES (?, ?, ?)', (1, '상하이', 24150000))

# 파라미터가 딕셔너리일 때는 플레이스홀더를 :<이름> 형태로 지정합니다.
c.execute('INSERT INTO cities VALUES (:rank, :city, :population)',
          {'rank': 2, 'city': '카라치', 'population': 23500000})

# executemany() 메서드를 사용하면 여러 개의 파라미터를 리스트로 지정해서
# 여러 개(현재 예제에서는 3개)의 SQL 구문을 실행할 수 있습니다.
c.executemany('INSERT INTO cities VALUES (:rank, :city, :population)', [
    {'rank': 3,  'city': '베이징',   'population': 21516000},
    {'rank': 4,  'city': '텐진',     'population': 14722100},
    {'rank': 5,  'city': '이스탄불', 'population': 14160467},
])

# 변경사항을 커밋(저장)합니다.
conn.commit()

# 저장한 데이터를 추출합니다.
c.execute('SELECT * FROM cities')

# 쿼리의 결과는 fetchall() 메서드로 추출할 수 있습니다.
for row in c.fetchall():
    # 추출한 데이터를 출력합니다.
    print(row)

# 연결을 닫습니다.
conn.close()
```

<hr>


```python
# ! mkdir database
make_dir('database')
```




    'database 디렉토리를 생성하였습니다!'




```python
import sqlite3

# top_cities.db 파일을 열고 연결을 변수에 저장합니다.
db_path = './database/top_cities.db'
conn = sqlite3.connect(db_path)

# 커서를 추출합니다.
c = conn.cursor()

# execute() 메서드로 SQL 구문을 실행합니다.
# 스크립트를 여러 번 사용해도 같은 결과를 출력할 수 있게 cities 테이블이 존재하는 경우 제거합니다.
c.execute('DROP TABLE IF EXISTS cities')

# cities 테이블을 생성합니다.
c.execute('''
    CREATE TABLE cities (
        rank integer,
        city text,
        population integer
    )
''')

```




    <sqlite3.Cursor at 0x203df1f86c0>




```python
# execute() 메서드의 두 번째 매개변수에는 파라미터를 지정할 수 있습니다.
# SQL 내부에서 파라미터로 변경할 부분(플레이스홀더)은 ?로 지정합니다.
c.execute('INSERT INTO cities VALUES (?, ?, ?)', (1, '상하이', 24150000))

```




    <sqlite3.Cursor at 0x203df1f86c0>




```python
# 파라미터가 딕셔너리일 때는 플레이스홀더를 :<이름> 형태로 지정합니다.
c.execute('INSERT INTO cities VALUES (:rank, :city, :population)',
          {'rank': 2, 'city': '카라치', 'population': 23500000}) 

```




    <sqlite3.Cursor at 0x203df1f86c0>




```python
# executemany() 메서드를 사용하면 여러 개의 파라미터를 리스트로 지정해서
# 여러 개(현재 예제에서는 3개)의 SQL 구문을 실행할 수 있습니다.
c.executemany('INSERT INTO cities VALUES (:rank, :city, :population)', [
    {'rank': 3, 'city': '베이징', 'population': 21516000},
    {'rank': 4, 'city': '텐진', 'population': 14722100},
    {'rank': 5, 'city': '이스탄불', 'population': 14160467},
])

```




    <sqlite3.Cursor at 0x203df1f86c0>




```python
# 변경사항을 커밋(저장)합니다.
conn.commit()

```


```python
# 저장한 데이터를 추출합니다.
c.execute('SELECT * FROM cities')

# 쿼리의 결과는 fetchall() 메서드로 추출할 수 있습니다.
for row in c.fetchall():
    # 추출한 데이터를 출력합니다.
    print(row)

# 연결을 닫습니다.
conn.close()
```

    (1, '상하이', 24150000)
    (2, '카라치', 23500000)
    (3, '베이징', 21516000)
    (4, '텐진', 14722100)
    (5, '이스탄불', 14160467)
    

### <font color="#0000CC"> c2-19_python_scraper
> 파이썬으로 스크레이핑하는 프로세스
- 웹 페이지를 추출
- 스크레이핑
- 데이터를 저장

### main( ) 함수에서 차례대로 호출
- fetch(url) : 매개변수로 url을 받고 지정한 URL의 웹 페이지를 추출
- scrape(html) : 매개변수로 html을 받고, 정규표현식을 사용해 HTML에서 도서 정보를 추출
- save(db_path, books) : 매개변수로 books라는 도서 목록을 받고, SQLite 데이터베이스에 저장

``` python
# python_scraper.py 

import re
import sqlite3
from urllib.request import urlopen
from html import unescape

def main():
    """
    메인 처리입니다.
    fetch(), scrape(), save() 함수를 호출합니다.
    """
    
    url = 'http://www.hanbit.co.kr/store/books/full_book_list.html'
    db_path = './database/books.db'
    
    html = fetch(url)
    books = scrape(html)
    save(db_path, books)


def fetch(url):
    """
    매개변수로 전달받을 url을 기반으로 웹 페이지를 추출합니다.
    웹 페이지의 인코딩 형식은 Content-Type 헤더를 기반으로 알아냅니다.
    반환값: str 자료형의 HTML
    """
    f = urlopen(url)
    
    # HTTP 헤더를 기반으로 인코딩 형식을 추출합니다.
    encoding = f.info().get_content_charset(failobj="utf-8")
    
    # 추출한 인코딩 형식을 기반으로 문자열을 디코딩합니다.
    html = f.read().decode(encoding)
    return html


def scrape(html):
    """
    매개변수 html로 받은 HTML을 기반으로 정규 표현식을 사용해 도서 정보를 추출합니다.
    반환값: 도서(dict) 리스트
    """
    books = []
    
    # re.findall()을 사용해 도서 하나에 해당하는 HTML을 추출합니다.
    for partial_html in re.findall(r'<td class="left"><a.*?</td>', html, re.DOTALL):
        # 도서의 URL을 추출합니다.
        url = re.search(r'<a href="(.*?)">', partial_html).group(1)
        url = 'http://www.hanbit.co.kr' + url
        
        # 태그를 제거해서 도서의 제목을 추출합니다.
        title = re.sub(r'<.*?>', '', partial_html)
        title = unescape(title)
        books.append({'url': url, 'title': title})
    
    return books


def save(db_path, books):
    """
    매개변수 books로 전달된 도서 목록을 SQLite 데이터베이스에 저장합니다.
    데이터베이스의 경로는 매개변수 dp_path로 지정합니다.
    반환값: None(없음)
    """
    # 데이터베이스를 열고 연결을 확립합니다.
    conn = sqlite3.connect(db_path)
    
    # 커서를 추출합니다.
    c = conn.cursor()
    
    # execute() 메서드로 SQL을 실행합니다.
    # 스크립트를 여러 번 실행할 수 있으므로 기존의 books 테이블을 제거합니다.
    c.execute('DROP TABLE IF EXISTS books')
    
    # books 테이블을 생성합니다.
    c.execute('''
        CREATE TABLE books (
            title text,
            url text
        )
    ''')
    
    # executemany() 메서드를 사용하면 매개변수로 리스트를 지정할 수 있습니다.
    c.executemany('INSERT INTO books VALUES (:title, :url)', books)
    
    # 변경사항을 커밋(저장)합니다.
    conn.commit()
    
    # 연결을 종료합니다.
    conn.close()


# python 명령어로 실행한 경우 main() 함수를 호출합니다.
# 이는 모듈로써 다른 파일에서 읽어 들였을 때 main() 함수가 호출되지 않게 하는 것입니다.
# 파이썬 프로그램의 일반적인 작성 방식입니다.
if __name__ == '__main__':
    main()
    
```

<br/>
<hr>


```python
# ! mkdir modules
make_dir('modules')
```




    'modules 디렉토리를 생성하였습니다!'




```python
%%writefile  ./modules/python_scraper.py 

import re
import sqlite3
from urllib.request import urlopen
from html import unescape

def main():
    """
    메인 처리입니다.
    fetch(), scrape(), save() 함수를 호출합니다.
    """
    
    url = 'http://www.hanbit.co.kr/store/books/full_book_list.html'
    db_path = './database/books.db'
    
    html = fetch(url)
    books = scrape(html)
    save(db_path, books)


def fetch(url):
    """
    매개변수로 전달받을 url을 기반으로 웹 페이지를 추출합니다.
    웹 페이지의 인코딩 형식은 Content-Type 헤더를 기반으로 알아냅니다.
    반환값: str 자료형의 HTML
    """
    f = urlopen(url)
    # HTTP 헤더를 기반으로 인코딩 형식을 추출합니다.
    encoding = f.info().get_content_charset(failobj="utf-8")
    # 추출한 인코딩 형식을 기반으로 문자열을 디코딩합니다.
    html = f.read().decode(encoding)
    return html


def scrape(html):
    """
    매개변수 html로 받은 HTML을 기반으로 정규 표현식을 사용해 도서 정보를 추출합니다.
    반환값: 도서(dict) 리스트
    """
    books = []
    # re.findall()을 사용해 도서 하나에 해당하는 HTML을 추출합니다.
    for partial_html in re.findall(r'<td class="left"><a.*?</td>', html, re.DOTALL):
        # 도서의 URL을 추출합니다.
        url = re.search(r'<a href="(.*?)">', partial_html).group(1)
        url = 'http://www.hanbit.co.kr' + url
        # 태그를 제거해서 도서의 제목을 추출합니다.
        title = re.sub(r'<.*?>', '', partial_html)
        title = unescape(title)
        books.append({'url': url, 'title': title})
    
    return books


def save(db_path, books):
    """
    매개변수 books로 전달된 도서 목록을 SQLite 데이터베이스에 저장합니다.
    데이터베이스의 경로는 매개변수 dp_path로 지정합니다.
    반환값: None(없음)
    """
    # 데이터베이스를 열고 연결을 확립합니다.
    conn = sqlite3.connect(db_path)
    
    # 커서를 추출합니다.
    c = conn.cursor()
    
    # execute() 메서드로 SQL을 실행합니다.
    # 스크립트를 여러 번 실행할 수 있으므로 기존의 books 테이블을 제거합니다.
    c.execute('DROP TABLE IF EXISTS books')
    
    # books 테이블을 생성합니다.
    c.execute('''
        CREATE TABLE books (
            title text,
            url text
        )
    ''')
    
    # executemany() 메서드를 사용하면 매개변수로 리스트를 지정할 수 있습니다.
    c.executemany('INSERT INTO books VALUES (:title, :url)', books)
    
    # 변경사항을 커밋(저장)합니다.
    conn.commit()
    
    # 연결을 종료합니다.
    conn.close()

# python 명령어로 실행한 경우 main() 함수를 호출합니다.
# 이는 모듈로써 다른 파일에서 읽어 들였을 때 main() 함수가 호출되지 않게 하는 것입니다.
# 파이썬 프로그램의 일반적인 작성 방식입니다.
if __name__ == '__main__':
    main()
    
```

    Writing ./modules/python_scraper.py
    


```python
! dir/w modules\*.py
```

     C 드라이브의 볼륨에는 이름이 없습니다.
     볼륨 일련 번호: 3CBD-1374
    
     C:\Users\user\Dropbox\sect_tech\src_anaconda\P1810_IITP_Multicampus\tb10-web-crawling\modules 디렉터리
    
    python_scraper.py   
                   1개 파일               3,155 바이트
                   0개 디렉터리  24,772,972,544 바이트 남음
    


```python
# 파이썬 실행1
% run modules/python_scraper.py 
```


```python
# # 파이썬 실행2
! python modules/python_scraper.py 
```


```python
! dir database
```

     C 드라이브의 볼륨에는 이름이 없습니다.
     볼륨 일련 번호: 3CBD-1374
    
     C:\Users\user\Dropbox\sect_tech\src_anaconda\P1810_IITP_Multicampus\tb10-web-crawling\database 디렉터리
    
    2018-11-12  오후 11:10    <DIR>          .
    2018-11-12  오후 11:10    <DIR>          ..
    2018-11-12  오후 11:10            16,384 books.db
    2018-11-12  오후 11:10             8,192 top_cities.db
                   2개 파일              24,576 바이트
                   2개 디렉터리  24,772,952,064 바이트 남음
    


```python
# ! sqlite3 ./database/books.db
```

<hr>
<marquee><font size=3 color='brown'>The BigpyCraft find the information to design valuable society with Technology & Craft.</font></marquee>
<div align='right'><font size=2 color='gray'> &lt; The End &gt; </font></div>
