
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
    <option value="CH01" selected> 01.크롤링과 스크레이핑이란?                      </option>
    <option value="CH02"> 02.파이썬으로 시작하는 크롤링/스크레이핑         </option>
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

## <font color='#FF5555'>크롤링과 스크레이핑 이란? </font>
>  
<font color='#CC3333'>
- 크롤링과 스크레이핑 개념
- Wget으로 크롤링
- UNIX / LINUX 명령어 


```python
! python --version
```

    Python 3.6.3 :: Anaconda custom (64-bit)
    

### <font color='blue'> 크롤링과 스크레이핑
* 크롤링 
<br/> - 웹 페이지의 하이퍼링크를 순회하면서 웹 페이지를 다운로드하는 작업
<br/><br/>
* 스크레이핑
<br/> - 다운로드한 웹 페이지에서 필요한 정보를 추출하는 작업

### <font color='blue'> Wget으로 크롤링
> GNU Wget : HTTP통신 또는 FTP 통신을 사용해 서버에서 파일 또는 콘텐츠를 다운로드할 때 사용하는 소프트웨어
* wget for windows : https://eternallybored.org/misc/wget/
* 사용법
<br/> - url 페이지 크롤링 : 화면에 출력, 파일에 저장
<br/> - wget option  ::  cf. 10page
<br/> - tree



```python
! wget --version
```

    GNU Wget 1.19.4 built on mingw32.
    
    -cares +digest +gpgme +https +ipv6 +iri +large-file +metalink -nls 
    +ntlm +opie -psl +ssl/openssl 
    
    Wgetrc: 
        /win32dev/misc/wget/out64/etc/wgetrc (system)
    Compile: 
        x86_64-w64-mingw32-gcc -DHAVE_CONFIG_H 
        -DSYSTEM_WGETRC="/win32dev/misc/wget/out64/etc/wgetrc" 
        -DLOCALEDIR="/win32dev/misc/wget/out64/share/locale" -I. -I../lib 
        -I../lib -I/win32dev/misc/wget/out64/include 
        -I/win32dev/misc/wget/out64/include 
        -I/win32dev/misc/wget/out64/include 
        -I/win32dev/misc/wget/out64/include -DHAVE_LIBSSL 
        -I/win32dev/misc/wget/out64/include -DNDEBUG 
    Link: 
        x86_64-w64-mingw32-gcc -I/win32dev/misc/wget/out64/include 
        -I/win32dev/misc/wget/out64/include 
        -I/win32dev/misc/wget/out64/include -DHAVE_LIBSSL 
        -I/win32dev/misc/wget/out64/include -DNDEBUG 
        -L/win32dev/misc/wget/out64/lib -lidn2 
        -L/win32dev/misc/wget/out64/lib -lgpgme -lassuan -lws2_32 
        -lgpg-error -L/win32dev/misc/wget/out64/lib -lmetalink -lunistring 
        -liconv -L/win32dev/misc/wget/out64/lib -lssl -lcrypto 
        -L/win32dev/misc/wget/out64/lib -lz -lws2_32 -lole32 -lcrypt32 
        -lexpat ftp-opie.o mswindows.o openssl.o http-ntlm.o 
        ../lib/libgnu.a -lws2_32 -lws2_32 -lws2_32 -lws2_32 
        /win32dev/misc/wget/out64/lib/libiconv.a 
        /win32dev/misc/wget/out64/lib/libunistring.a -lws2_32 
    
    Copyright (C) 2015 Free Software Foundation, Inc.
    License GPLv3+: GNU GPL version 3 or later
    <http://www.gnu.org/licenses/gpl.html>.
    This is free software: you are free to change and redistribute it.
    There is NO WARRANTY, to the extent permitted by law.
    
    Originally written by Hrvoje Niksic <hniksic@xemacs.org>.
    Please send bug reports and questions to <bug-wget@gnu.org>.
    


```python
# ! mkdir download
# 파일명에 -(하이픈)을 지정하면 파일로 저장하지 않고 표준 출력에 출력
! wget https://movie.naver.com/ -q -O -
```

    
    
    
    
    
    
    
    
    <!DOCTYPE html>
    <html lang="ko">
    <head>
    <meta charset="utf-8">
    <meta http-equiv="X-UA-Compatible" content="IE=edge">
    <meta http-equiv="imagetoolbar" content="no">
    <meta property="og:title" content="�꽕�씠踰� �쁺�솕"/>
    <meta property="og:description" content="�쁺�솕�뿉 ����븳 紐⑤뱺 寃�"/>
    <meta property="og:image" content="https://ssl.pstatic.net/static/m/movie/icons/OG_270_270.png"/>
    <meta property="og:type" content="article"/>
    <meta property="og:url" content="https://movie.naver.com"/>
    <title>�꽕�씠踰� �쁺�솕</title>
    
    
    
    	
    	
    	
    	
    		<link rel="shortcut icon" href="https://ssl.pstatic.net/static/m/movie/icons/naver_movie_favicon.ico" type="image/x-icon">
    			
    
    
    
    <link rel="stylesheet" type="text/css" href="/css/deploy/movie.all.css?20181107154553" />
    
    <script type="text/javascript" src="/js/deploy/movie.home.js?20181107154553"></script>
    </head>
    
    <body >
    <div id="wrap" class="basic">
    
    	<!-- GNB -->
    	
    
    
    
    <script type="text/javascript">
    function delayed_submit(object) {
    	if (navigator.userAgent.indexOf('MSIE') == -1) {
    		var b = c = new Date();
          	while ((b.getTime() - c.getTime()) < 100) {
    			b = new Date();
          	}
    	} 
    }
    </script>
    
    <script type="text/javascript">
    	var gnb_service = "movie";
    	var gnb_logout = "http://movie.naver.com/index.nhn";
    	var gnb_template = "gnb_utf8";
    	var gnb_brightness=3;
    	var gnb_response = true;
    	
    	jindo.$Fn(function(){
    		getGNB();
    	}).attach(window, "load");
    	
    	jindo.$Fn(function(oEvent){ var welSource = jindo.$Element(oEvent.element);
    			if (!welSource.isChildOf(jindo.$Element("gnb"))) {
    				gnbAllLayerClose();
    			}
    	}).attach(document, 'click');
    </script>
     <!-- skip navigation -->
    <div id="u_skip">
             <a href="#header" onclick="document.getElementById('header').tabIndex=-1;document.getElementById('header').focus();return false;"><span>硫붿씤 硫붾돱濡� 諛붾줈媛�湲�</span></a>
             <a href="#content" id="gnb_goContent" onclick="document.getElementById('content').tabIndex=-1;document.getElementById('content').focus();return false;"><span>蹂몃Ц�쑝濡� 諛붾줈媛�湲�</span></a>
    </div>
    <!-- //skip navigation -->
    <div class="gnb_container">
    	<div class="gnb_content">
    		<div class="gnb_box">
    			<div class="gnb_wrap">
    				<div id="gnb">
    				    <script type="text/javascript" charset="utf-8" src="https://ssl.pstatic.net/static.gn/templates/gnb_utf8.nhn"></script>
    				</div>
    			</div>
    			<!-- 寃��깋李� -->
    			<form id="jSearchForm" action="/movie/search/result.nhn" method="get" style="margin:0;display:none;">
    				<input type="text" name="query" maxlength="100" title="�쁺�솕寃��깋" />
    				<input type="hidden" name="section" value="all"/>
    				<input type="hidden" name="ie" value="utf8"/>
    			</form>
    			<fieldset id="jSearchArea" class="srch_area">
    				<legend><span class="blind">�쁺�솕寃��깋 �쁺�뿭</span></legend>
    				<div class="srch_field_on _view">
    					<span class="ipt_srch">
    						<label for="ipt_tx_srch" id="search_placeholder">�쁺�솕寃��깋</label>
    						<input type="text" id="ipt_tx_srch" class="ipt_tx_srch" name="query" maxlength="100" accesskey="s" style="ime-mode:active;" autocomplete="off" />
    						<span class="align"></span>
    						<span class="auto_tx"><a href="#" title="�옄�룞�셿�꽦 �렯移섍린"><img src="https://ssl.pstatic.net/static/movie/2012/06/srch_arrow_down.gif" width="7" height="4" title="�옄�룞�셿�꽦 �렯移섍린" alt="�옄�룞�셿�꽦 �렯移섍린" /></a></span>
    					</span>
    					<button type="submit" title="寃��깋" class="btn_srch" onClick="clickcr(this,'GNB.search','','',event); delayed_submit(this);"><span class="blind">寃��깋</span></button>
    					 <!-- �옄�룞 �셿�꽦 �쁺�뿭�엫 #autocomplate_template-->
    				</div>
    			</fieldset>
    			<!-- //寃��깋李� -->
    		</div>
    	</div>
    </div>
    
    	<!-- //GNB -->
    
    	<!-- header -->
    	
    
    
    
    
    
    	<div id="header">
    		<a href="#content" title="蹂몃Ц�쑝濡� �씠�룞" class="blind">蹂몃Ц 諛붾줈媛�湲�</a>
    		<h1 class="svc_name">
    			<a href="http://www.naver.com/" title="naver濡� 諛붾줈媛�湲�" class="ci_logo" id="lnb_gonaver"><img src="https://ssl.pstatic.net/static/movie/2013/07/logo_ci.png" width="62" height="13" alt="NAVER" /></a><!-- N=a:LNB.naver -->
    			<a href="/" title="�쁺�솕�꽌鍮꾩뒪�솃�쑝濡� 諛붾줈媛�湲�" class="svc_logo"><img src="https://ssl.pstatic.net/static/movie/2012/06/logo_svc.png" width="34" height="19" alt="�쁺�솕" /></a><!-- N=a:LNB.movie -->
    		</h1>
    		<div id="scrollbar" class="scrollbar scrollbar-noscript">
    			<div class="scrollbar-box">
    				<div class="scrollbar-content">
                        <div class="in_scroll">
                            <ul class="navi">
                            <li>
                                <a href="/" title="�쁺�솕�솃" class="menu01_on"><strong>�쁺�솕�솃</strong></a><!-- N=a:LNB.home -->
                            </li>
                            <li>
                                <a href="/movie/running/current.nhn" title="�긽�쁺�옉쨌�삁�젙�옉" class="menu02"><strong>�긽�쁺�옉쨌�삁�젙�옉</strong></a><!-- N=a:LNB.movies -->
                                <ul class="navi_sub" id="navi_movie" style="display:none">
                                <li><a href="/movie/running/current.nhn" title="�쁽�옱 �긽�쁺�쁺�솕" class="sub2_1"><em>�쁽�옱 �긽�쁺�쁺�솕</em></a><!-- N=a:LNB.now --></li>
                                <li><a href="/movie/running/premovie.nhn" title="媛쒕큺 �삁�젙�쁺�솕" class="sub2_2"><em>媛쒕큺 �삁�젙�쁺�솕</em></a><!-- N=a:LNB.soon --></li>
                                <li><a href="/movie/running/weekendmovie.nhn" title="TV/DVD �쁺�솕" class="sub2_3"><em>TV/DVD �쁺�솕</em></a><!-- N=a:LNB.guide --></li>
                                <li><a href="/movie/running/movieclip.nhn" title="�삁怨좏렪" class="sub2_4"><em>�삁怨좏렪</em></a><!-- N=a:LNB.tailer --></li>
                                </ul>
                            </li>
                            <li>
                                <a href="/movie/sdb/rank/rmovie.nhn" title="�쁺�솕�옲�궧" class="menu03"><strong>�쁺�솕�옲�궧</strong></a><!-- N=a:LNB.db -->
                            </li>
                            <li>
                                <a href="/movie/bi/mi/reserve.nhn" title="�삁留�" class="menu05"><strong>�삁留�</strong></a><!-- N=a:LNB.ticket -->
                            </li>
    
                            <li>
                                <a href="/movie/point/af/list.nhn" title="�룊�젏&middot由щ럭" class="menu07"><strong>�룊�젏&middot由щ럭</strong></a><!-- N=a:LNB.comm -->
                            </li>
                            <li>
                                <a href="http://nstore.naver.com/movie/home.nhn" title="�떎�슫濡쒕뱶" class="menu08" target="_blank"><strong>�떎�슫濡쒕뱶</strong></a><!-- N=a:LNB.download -->
                            </li>
    						<li class="nav_indi">
    						        <a href="http://tv.naver.com/indiecinema" title="�씤�뵒洹뱀옣" target="_blank"><strong>�씤�뵒洹뱀옣</strong></a><!-- N=a:LNB.indie -->
    						</li>                        
                            </ul>
                            
                        </div>
    				</div>
    			</div>
    			<div class="scrollbar-v">
    				<div class="scrollbar-button-up"></div>
    				<div class="scrollbar-track">
    					<div class="scrollbar-thumb"></div>
    				</div>
    				<div class="scrollbar-button-down"></div>
    			</div>
    		</div>
    	</div>
    	
    	<script type="text/javascript">
    	if ("�쁺�솕�솃" == "�긽�쁺�옉쨌�삁�젙�옉"
    			|| "�쁺�솕�솃" == "�쁽�옱 �긽�쁺�쁺�솕"
    			|| "�쁺�솕�솃" == "媛쒕큺 �삁�젙�쁺�솕"
    			|| "�쁺�솕�솃" == "TV/DVD �쁺�솕"
    			|| "�쁺�솕�솃" == "�삁怨좏렪") {
    		jindo.$Element("navi_movie").show();
    	}
    	</script>
    	<!-- //header -->
    	
    	<!-- container -->
    	<div id="container">
    			<!-- content -->
    <div id="content">
    
    	
    	<div class="article hh">
    		<!-- 臾대퉬李⑦듃 -->
    		<div class="mv_main" onmouseover="oTimer.abort();" onmouseout="movieChart.restartTimer();">
    			<div class="flick_nav">
    				<a href="#" id="flick_prev" class="btn_prev" onclick="clickcr(this, 'run.pre', '', '', event);" onfocus="oTimer.abort();" onblur="movieChart.restartTimer();" title="�씠�쟾"><em>�씠�쟾</em></a><!-- N=a:run.pre -->
    			</div>
    			<!-- flick area -->
    			<div id="mflick" class="flick_view_area flick-view">
    				<div class="flick-container" style="left: 0px; ">
    					<ul id="flick0" class="flick-ct home_list page0 flick-panel"></ul>
    					<ul id="flick1" class="flick-ct home_list page1 flick-panel blind"></ul>
    					<ul id="flick2" class="flick-ct home_list page2 flick-panel blind"></ul>
    				</div>
    			</div>
    			<!-- //flick area -->
    			<div class="flick_nav">
    				<a href="#" id="flick_next" class="btn_next" onclick="clickcr(this, 'run.next', '', '', event);" onfocus="oTimer.abort();" onblur="movieChart.restartTimer();" title="�떎�쓬"><em>�떎�쓬</em></a><!-- N=a:run.next -->
    			</div>
    		
    			<div class="running_tab">
    				<ul>
    					<li id="RESERVE_tab" class="item0 on"><a href="#" onclick="movieChart.fullSettingMovieChart(0);" onfocus="oTimer.abort();" onblur="movieChart.restartTimer();" class="flickingTab"><em>�삁留ㅼ닚</em></a><!-- N=a:run.ticket --></li>
    					<li id="CURRENT_tab" class="item1"><a href="#" onclick="movieChart.fullSettingMovieChart(1);" onfocus="oTimer.abort();" onblur="movieChart.restartTimer();" class="flickingTab"><em>�쁽�옱�긽�쁺�옉</em></a><!-- N=a:run.now --></li>
    					<li id="COMMING_tab" class="item2"><a href="#" onclick="movieChart.fullSettingMovieChart(2);" onfocus="oTimer.abort();" onblur="movieChart.restartTimer();" class="flickingTab"><em>媛쒕큺�삁�젙�옉</em></a><!-- N=a:run.coming --></li>
    					<li id="POINT_tab" class="item3"><a href="#" onclick="movieChart.fullSettingMovieChart(3);" onfocus="oTimer.abort();" onblur="movieChart.restartTimer();" class="flickingTab"><em>�룊�젏�닚</em></a><!-- N=a:run.bystar --></li>
    					<li id="BOXOFFICE_tab" class="item4"><a href="#" onclick="movieChart.fullSettingMovieChart(4);" onfocus="oTimer.abort();" onblur="movieChart.restartTimer();" class="flickingTab"><em>諛뺤뒪�삤�뵾�뒪</em></a><!-- N=a:run.box --></li>
    					<li id="DOWNLOAD_tab" class="item5"><a href="#" onclick="movieChart.fullSettingMovieChart(5);" onfocus="oTimer.abort();" onblur="movieChart.restartTimer();" class="flickingTab"><em>�떎�슫濡쒕뱶�닚</em></a><!-- N=a:run.down --></li>
    				</ul>
    				<p href="#" class="all_view_go"><a id="movieChartAllView" href="#" onclick="clickcr(this, 'run.all', '', '', event);" onfocus="oTimer.abort();" onblur="movieChart.restartTimer();" title="�쟾泥대낫湲�">�쟾泥대낫湲�</a><!-- N=a:run.all --></p>
    			</div>
    		</div>
    		<!-- //臾대퉬李⑦듃  -->
    		<div class="section_group" id="homeReview">
    			<div class="obj_section">
    				<div class="main_review">
    					
    					<div class="title_area">
    						<h4 class="hh_review"><strong class="blind">�룊�젏/由щ럭</strong></h4>
    					</div>
    					<div class="hh_review_area">
    						<div id="movieReview" class="hh_review_ct">
    							<ul class="lst_con first" data-index=0 style="display:block">
    							<!-- [D] �꽑�깮�맂 寃쎌슦 li�뿉 class="on" 異붽�� -->
    							
    							<li id="review1" data-index=0 class="_select_title">
    								<a href="/movie/bi/mi/basic.nhn?code=167638" class="thmb" onclick="clickcr(this, 'tvw.img', '167638', '1', event);"><img src="https://movie-phinf.pstatic.net/20181106_289/1541478936071tmadh_JPEG/movie_image.jpg?type=f64_91" width="64" height="91" alt="�셿踰쏀븳 ����씤" onerror="this.src='https://ssl.pstatic.net/static/movie/2012/06/dft_img64x91.png'"></a>
    								<div class="detail">
    									<a href="/movie/bi/mi/basic.nhn?code=167638" onclick="clickcr(this, 'tvw.title', '167638', '1', event);" data-index=0 class="_select_title_anchor"><strong>�셿踰쏀븳 ����씤</strong>
    										<div class="star_score">
    											
    											
    											
    												
    												
    													
    													
    													
    													<span class="st_off"><span class="st_on" style="width:88.3%">�룊�젏 - 珥� 10�젏 以�</span></span>
    													<span class="score">
    													<span class="char sc_num8"><em>8</em></span><span class="char sc_dot"><em>.</em></span><span class="char sc_num8"><em>8</em></span><span class="char sc_num3"><em>3</em></span>
    												
    											
    											</span>
    										</div>
    									</a>
    									<ul class="info">
    										
    											
    												<li><a href="/movie/bi/mi/reviewread.nhn?nid=4666476&code=167638" onclick="clickcr(this, 'tvw.list', '4666476', '1', event);"><span class="tit">�빖�뱶�룿�쓣 怨듦컻�븯硫� 紐⑤몢�쓽 鍮꾨���씠 �뱶�윭�궃�떎. �쁺�솕 &lt;�셿踰쏀븳 ����씤&gt; 蹂닿퀬 �솕�뒿�땲�떎.</span></a></li>
    											
    										
    											
    												<li><a href="/movie/bi/mi/reviewread.nhn?nid=4665211&code=167638" onclick="clickcr(this, 'tvw.list', '4665211', '2', event);"><span class="tit">�셿踰쏀븳 ����씤 [Intimate Strangers] (�뒪�룷X, 荑좏궎�쁺�긽O)</span></a></li>
    											
    										
    											
    												<li class="last"><a href="/movie/bi/mi/reviewread.nhn?nid=4666420&code=167638" onclick="clickcr(this, 'tvw.list', '4666420', '3', event);"><span class="tit">�쁺�솕 �셿踰쏀븳����씤 �넄吏곹썑湲�!!!!!!!!!</span></a></li>
    											
    										
    									</ul>
    								</div>
    							</li>
    							
    							<li id="review2" data-index=1 class="_select_title">
    								<a href="/movie/bi/mi/basic.nhn?code=164155" class="thmb" onclick="clickcr(this, 'tvw.img', '164155', '2', event);"><img src="https://movie-phinf.pstatic.net/20181001_122/153836420654806YHX_JPEG/movie_image.jpg?type=f64_91" width="64" height="91" alt="踰� �냽�뿉 �닲��� 留덈쾿�떆怨�" onerror="this.src='https://ssl.pstatic.net/static/movie/2012/06/dft_img64x91.png'"></a>
    								<div class="detail">
    									<a href="/movie/bi/mi/basic.nhn?code=164155" onclick="clickcr(this, 'tvw.title', '164155', '2', event);" data-index=1 class="_select_title_anchor"><strong>踰� �냽�뿉 �닲��� 留덈쾿�떆怨�</strong>
    										<div class="star_score">
    											
    											
    											
    												
    												
    													
    													
    													
    													<span class="st_off"><span class="st_on" style="width:64.0%">�룊�젏 - 珥� 10�젏 以�</span></span>
    													<span class="score">
    													<span class="char sc_num6"><em>6</em></span><span class="char sc_dot"><em>.</em></span><span class="char sc_num4"><em>4</em></span><span class="char sc_num0"><em>0</em></span>
    												
    											
    											</span>
    										</div>
    									</a>
    									<ul class="info">
    										
    											
    												<li><a href="/movie/bi/mi/reviewread.nhn?nid=4666313&code=164155" onclick="clickcr(this, 'tvw.list', '4666313', '1', event);"><span class="tit">踰쎌냽�뿉 �닲��� 留덈쾿�떆怨�</span></a></li>
    											
    										
    											
    												<li><a href="/movie/bi/mi/reviewread.nhn?nid=4667572&code=164155" onclick="clickcr(this, 'tvw.list', '4667572', '2', event);"><span class="tit">[�쁺�솕�씪�뒗 �씠由꾩쓽 轅�]�쑀�뀈�떆�젅 �뙋���吏��쓽 �뼢�뿰</span></a></li>
    											
    										
    											
    												<li class="last"><a href="/movie/bi/mi/reviewread.nhn?nid=4666805&code=164155" onclick="clickcr(this, 'tvw.list', '4666805', '3', event);"><span class="tit">[踰� �냽�뿉 �닲��� 留덈쾿�떆怨�] �솚�긽�쟻�씤 留덈쾿 �뙋���吏�媛� �렯爾먯쭊�떎.</span></a></li>
    											
    										
    									</ul>
    								</div>
    							</li>
    							
    							<li id="review3" data-index=2 class="_select_title">
    								<a href="/movie/bi/mi/basic.nhn?code=156464" class="thmb" onclick="clickcr(this, 'tvw.img', '156464', '3', event);"><img src="https://movie-phinf.pstatic.net/20181031_68/1540952503496fNRsF_JPEG/movie_image.jpg?type=f64_91" width="64" height="91" alt="蹂댄뿤誘몄븞 �옪�냼�뵒" onerror="this.src='https://ssl.pstatic.net/static/movie/2012/06/dft_img64x91.png'"></a>
    								<div class="detail">
    									<a href="/movie/bi/mi/basic.nhn?code=156464" onclick="clickcr(this, 'tvw.title', '156464', '3', event);" data-index=2 class="_select_title_anchor"><strong>蹂댄뿤誘몄븞 �옪�냼�뵒</strong>
    										<div class="star_score">
    											
    											
    											
    												
    												
    													
    													
    													
    													<span class="st_off"><span class="st_on" style="width:96.6%">�룊�젏 - 珥� 10�젏 以�</span></span>
    													<span class="score">
    													<span class="char sc_num9"><em>9</em></span><span class="char sc_dot"><em>.</em></span><span class="char sc_num6"><em>6</em></span><span class="char sc_num6"><em>6</em></span>
    												
    											
    											</span>
    										</div>
    									</a>
    									<ul class="info">
    										
    											
    												<li><a href="/movie/bi/mi/reviewread.nhn?nid=4664841&code=156464" onclick="clickcr(this, 'tvw.list', '4664841', '1', event);"><span class="tit">��� 洹몃━怨� �봽�젅�뵒 癒명걧由� 120遺꾩�� �굹�뿉寃� 媛먮룞�씠����떎.</span></a></li>
    											
    										
    											
    												<li><a href="/movie/bi/mi/reviewread.nhn?nid=4666759&code=156464" onclick="clickcr(this, 'tvw.list', '4666759', '2', event);"><span class="tit">蹂댄뿤誘몄븞 �옪�냼�뵒</span></a></li>
    											
    										
    											
    												<li class="last"><a href="/movie/bi/mi/reviewread.nhn?nid=4667080&code=156464" onclick="clickcr(this, 'tvw.list', '4667080', '3', event);"><span class="tit">�씠 媛��쓣 吏묒븞 媛��뱷 QUEEN�쓽 �쓬�븙�쑝濡� 梨꾩썙 �꽔寃� �븳 �쁺�솕 ��� 蹂댄뿤誘몄븞 �옪�냼�뵒 ���</span></a></li>
    											
    										
    									</ul>
    								</div>
    							</li>
    							
    							<li id="review4" data-index=3 class="_select_title">
    								<a href="/movie/bi/mi/basic.nhn?code=168058" class="thmb" onclick="clickcr(this, 'tvw.img', '168058', '4', event);"><img src="https://movie-phinf.pstatic.net/20180921_295/1537492322557T4mGt_JPEG/movie_image.jpg?type=f64_91" width="64" height="91" alt="�띁�뒪�듃留�" onerror="this.src='https://ssl.pstatic.net/static/movie/2012/06/dft_img64x91.png'"></a>
    								<div class="detail">
    									<a href="/movie/bi/mi/basic.nhn?code=168058" onclick="clickcr(this, 'tvw.title', '168058', '4', event);" data-index=3 class="_select_title_anchor"><strong>�띁�뒪�듃留�</strong>
    										<div class="star_score">
    											
    											
    											
    												
    												
    													
    													
    													
    													<span class="st_off"><span class="st_on" style="width:69.8%">�룊�젏 - 珥� 10�젏 以�</span></span>
    													<span class="score">
    													<span class="char sc_num6"><em>6</em></span><span class="char sc_dot"><em>.</em></span><span class="char sc_num9"><em>9</em></span><span class="char sc_num8"><em>8</em></span>
    												
    											
    											</span>
    										</div>
    									</a>
    									<ul class="info">
    										
    											
    												<li><a href="/movie/bi/mi/reviewread.nhn?nid=4665669&code=168058" onclick="clickcr(this, 'tvw.list', '4665669', '1', event);"><span class="tit">�띁�뒪�듃留�</span></a></li>
    											
    										
    											
    												<li><a href="/movie/bi/mi/reviewread.nhn?nid=4666569&code=168058" onclick="clickcr(this, 'tvw.list', '4666569', '2', event);"><span class="tit">[�띁�뒪�듃 留�] �슦二쇨�� �븘�땶 �븳 �씤媛꾩쓽 �쐞����븳 �뿬�젙�쓣 �븿猿� �븳�떎.</span></a></li>
    											
    										
    											
    												<li class="last"><a href="/movie/bi/mi/reviewread.nhn?nid=4664850&code=168058" onclick="clickcr(this, 'tvw.list', '4664850', '3', event);"><span class="tit">&lt;�띁�뒪�듃留�(First Man , 2018)&gt; �떖�뿉 泥� 諛쒖쓣 �궡�뵛湲곌퉴吏�.. �땺 �븫�뒪�듃濡깆쓽 �쟾湲� �쁺�솕 (�뜲�씠誘몄뼵 �뀛�젮 媛먮룆, �씪�씠�뼵 怨좎뒳留�, �겢�젅�뼱 �룷�씠, �떎�솕 �쁺�솕)</span></a></li>
    											
    										
    									</ul>
    								</div>
    							</li>
    							
    							</ul>
    						</div>
    					</div>
    				</div>
    				<div class="main_spot" id="homeSpotlight">
    					
    					<div class="section">
    						<div class="title_area">
    							<h4 class="hh_spotlight">
    								<strong class="blind">�뒪�룷�듃�씪�씠�듃</strong>
    							</h4>
    						</div>
    						<div class="hh_spot_area">
    							<a href="https://nstore.naver.com/event/details.nhn?eventNo=11724&productType=MOVIE">
    								
    								
    									
    								
    								<img src="https://movie-phinf.pstatic.net/20181102_44/1541142948715gfzLX_PNG/%BD%BA%C6%F7%C6%AE%B6%F3%C0%CC%C6%AE210X196_3.png" width="210" height="196" title="�뒪�룷�듃�씪�씠�듃 諛곕꼫" alt="�뒪�룷�듃�씪�씠�듃 �쁺�뿭 �엯�땲�떎." border="0">
    							</a>
    						</div>
    					</div>
    					
    				</div>
    			</div>
    
    			
    			<div class="obj_section" id="homeTrailer">
    				<div class="main_prv">
    					<div class="title_area">
    						<h4 class="hh_preview"><strong class="blind">�삁怨좏렪</strong></h4>
    						<a href="/movie/running/movieclip.nhn">
    							<span class="more"><span class="blind">�뜑蹂닿린</span></span>
    						</a><!-- N=a:cms.more -->
    					</div>
    					<ul class="video_thumb">
    					
    					<li>
    						<a href="/movie/bi/mi/mediaView.nhn?code=163843&mid=40551#tab" title="硫붿씤 �삁怨좏렪" class="video_obj">
    							<span class="mask">�룞�쁺�긽</span>
    							
    							<span class="video_ico first"></span>
    							<img src="https://ssl.pstatic.net/imgmovie/multimedia/MOVIECLIP/TRAILER/40551_20181109110238.jpg" width="164" height="114" alt="硫붿씤 �삁怨좏렪" onerror="this.src='https://ssl.pstatic.net/static/movie/2012/06/dft_img164x114.png'">
    						</a><!-- N=a:cms.img,r:1,i:40551 -->
    						<p class="tx_video ico_hd"><span class="blind">HD</span><a href="/movie/bi/mi/mediaView.nhn?code=163843&mid=40551#tab" title="肄쒕뱶 �뒪�궓">肄쒕뱶 �뒪�궓</a><!-- N=a:cms.title,r:1,i:40551 --></p>
    						<p class="tx_brief"><a href="/movie/bi/mi/mediaView.nhn?code=163843&mid=40551#tab" title="硫붿씤 �삁怨좏렪">硫붿씤 �삁怨좏렪</a><!-- N=a:cms.desc,r:1,i:40551 --></p>
    					</li>
    					
    					<li>
    						<a href="/movie/bi/mi/mediaView.nhn?code=162097&mid=40549#tab" title="硫붿씤 �삁怨좏렪" class="video_obj">
    							<span class="mask">�룞�쁺�긽</span>
    							
    							<span class="video_ico first"></span>
    							<img src="https://ssl.pstatic.net/imgmovie/multimedia/MOVIECLIP/TRAILER/40549_20181109104321.jpg" width="164" height="114" alt="硫붿씤 �삁怨좏렪" onerror="this.src='https://ssl.pstatic.net/static/movie/2012/06/dft_img164x114.png'">
    						</a><!-- N=a:cms.img,r:2,i:40549 -->
    						<p class="tx_video ico_hd"><span class="blind">HD</span><a href="/movie/bi/mi/mediaView.nhn?code=162097&mid=40549#tab" title="���由� �뿉�뼱">���由� �뿉�뼱</a><!-- N=a:cms.title,r:2,i:40549 --></p>
    						<p class="tx_brief"><a href="/movie/bi/mi/mediaView.nhn?code=162097&mid=40549#tab" title="硫붿씤 �삁怨좏렪">硫붿씤 �삁怨좏렪</a><!-- N=a:cms.desc,r:2,i:40549 --></p>
    					</li>
    					
    					<li>
    						<a href="/movie/bi/mi/mediaView.nhn?code=180384&mid=40552#tab" title="硫붿씤 �삁怨좏렪" class="video_obj">
    							<span class="mask">�룞�쁺�긽</span>
    							
    							<span class="video_ico first"></span>
    							<img src="https://ssl.pstatic.net/imgmovie/multimedia/MOVIECLIP/TRAILER/40552_20181109110841.jpg" width="164" height="114" alt="硫붿씤 �삁怨좏렪" onerror="this.src='https://ssl.pstatic.net/static/movie/2012/06/dft_img164x114.png'">
    						</a><!-- N=a:cms.img,r:3,i:40552 -->
    						<p class="tx_video ico_hd"><span class="blind">HD</span><a href="/movie/bi/mi/mediaView.nhn?code=180384&mid=40552#tab" title="�윴�떇留� : ���猷곕（�쓽 �뿭�뒿">�윴�떇留� : ���猷곕（�쓽 �뿭�뒿</a><!-- N=a:cms.title,r:3,i:40552 --></p>
    						<p class="tx_brief"><a href="/movie/bi/mi/mediaView.nhn?code=180384&mid=40552#tab" title="硫붿씤 �삁怨좏렪">硫붿씤 �삁怨좏렪</a><!-- N=a:cms.desc,r:3,i:40552 --></p>
    					</li>
    					
    					<li>
    						<a href="/movie/bi/mi/mediaView.nhn?code=164102&mid=40566#tab" title="�뼢湲곗쓽 �궚�꽑 �뼹援� �쁺�긽" class="video_obj">
    							<span class="mask">�룞�쁺�긽</span>
    							
    							
    							<img src="https://ssl.pstatic.net/imgmovie/multimedia/MOVIECLIP/MAKING/40566_20181109040543.jpg" width="164" height="114" alt="�뼢湲곗쓽 �궚�꽑 �뼹援� �쁺�긽" onerror="this.src='https://ssl.pstatic.net/static/movie/2012/06/dft_img164x114.png'">
    						</a><!-- N=a:cms.img,r:4,i:40566 -->
    						<p class="tx_video ico"><a href="/movie/bi/mi/mediaView.nhn?code=164102&mid=40566#tab" title="�쁺二�">�쁺二�</a><!-- N=a:cms.title,r:4,i:40566 --></p>
    						<p class="tx_brief"><a href="/movie/bi/mi/mediaView.nhn?code=164102&mid=40566#tab" title="�뼢湲곗쓽 �궚�꽑 �뼹援� �쁺�긽">�뼢湲곗쓽 �궚�꽑 �뼹援� �쁺�긽</a><!-- N=a:cms.desc,r:4,i:40566 --></p>
    					</li>
    					
    					</ul>
    				</div>
    			</div>
    		</div>
    		
    
    		
    		<div class="section_group" id="homePhoto">
    			<div class="obj_section">
    				<div class="main_photo">
    					<div class="title_area">
    						<h4 class="hh_photo"><strong class="blind">�룷�넗</strong></h4>
    					</div>
    					<ul>
    					
    					<li class="">
    						<p class="thmb">
    							<a href="/movie/bi/mi/photoView.nhn?code=179840&imageNid=6626688#tab">
    								<img src="https://movie-phinf.pstatic.net/20181001_224/1538357818245Ew1Xu_JPEG/movie_image.jpg?type=n108_108_2" width="108" height="108" alt="湲덉���맂 濡쒕㎤�뒪" onerror="this.src='https://ssl.pstatic.net/static/movie/2012/06/dft_img108x108.png'">
    								
    								
    							</a><!-- N=a:pho.img,r:1,i:6626688 -->
    						</p>
    						<a href="/movie/bi/mi/photoView.nhn?code=179840&imageNid=6626688#tab"><strong class="tit">留덊떥�떎: �솴�젣�쓽 �뿰�씤</strong></a><!-- N=a:pho.list,r:1,i:6626688 -->
    						<p class="tx_brief"><a href="/movie/bi/mi/photoView.nhn?code=179840&imageNid=6626688#tab">湲덉���맂 濡쒕㎤�뒪</a><!-- N=a:pho.tlist,r:1,i:6626688 --></p>
    					</li>
    					
    					<li class="">
    						<p class="thmb">
    							<a href="/movie/bi/mi/photoView.nhn?code=164153&imageNid=6628192#tab">
    								<img src="https://movie-phinf.pstatic.net/20181012_178/1539323686120pUbby_JPEG/movie_image.jpg?type=n108_108_2" width="108" height="108" alt="�븷留ㅻえ�샇�븳 �궓���" onerror="this.src='https://ssl.pstatic.net/static/movie/2012/06/dft_img108x108.png'">
    								
    								
    							</a><!-- N=a:pho.img,r:2,i:6628192 -->
    						</p>
    						<a href="/movie/bi/mi/photoView.nhn?code=164153&imageNid=6628192#tab"><strong class="tit">援곗궛: 嫄곗쐞瑜� �끂�옒�븯�떎</strong></a><!-- N=a:pho.list,r:2,i:6628192 -->
    						<p class="tx_brief"><a href="/movie/bi/mi/photoView.nhn?code=164153&imageNid=6628192#tab">�븷留ㅻえ�샇�븳 �궓���</a><!-- N=a:pho.tlist,r:2,i:6628192 --></p>
    					</li>
    					
    					<li class="">
    						<p class="thmb">
    							<a href="/movie/bi/mi/photoView.nhn?code=177381&imageNid=6625840#tab">
    								<img src="https://movie-phinf.pstatic.net/20180919_105/1537319605020MHRRo_JPEG/movie_image.jpg?type=n108_108_2" width="108" height="108" alt="�뙋���吏� �뼱�뱶踰ㅼ쿂" onerror="this.src='https://ssl.pstatic.net/static/movie/2012/06/dft_img108x108.png'">
    								
    								
    							</a><!-- N=a:pho.img,r:3,i:6625840 -->
    						</p>
    						<a href="/movie/bi/mi/photoView.nhn?code=177381&imageNid=6625840#tab"><strong class="tit">�렚洹� �븯�씠�썾�씠</strong></a><!-- N=a:pho.list,r:3,i:6625840 -->
    						<p class="tx_brief"><a href="/movie/bi/mi/photoView.nhn?code=177381&imageNid=6625840#tab">�뙋���吏� �뼱�뱶踰ㅼ쿂</a><!-- N=a:pho.tlist,r:3,i:6625840 --></p>
    					</li>
    					
    					<li class="">
    						<p class="thmb">
    							<a href="/movie/bi/mi/photoView.nhn?code=167374&imageNid=6627917#tab">
    								<img src="https://movie-phinf.pstatic.net/20181011_121/15392182151413vsjd_JPEG/movie_image.jpg?type=n108_108_2" width="108" height="108" alt="�닲寃⑥쭊 吏꾩떎" onerror="this.src='https://ssl.pstatic.net/static/movie/2012/06/dft_img108x108.png'">
    								
    								
    							</a><!-- N=a:pho.img,r:4,i:6627917 -->
    						</p>
    						<a href="/movie/bi/mi/photoView.nhn?code=167374&imageNid=6627917#tab"><strong class="tit">酉고떚��� �뜲�씠利�</strong></a><!-- N=a:pho.list,r:4,i:6627917 -->
    						<p class="tx_brief"><a href="/movie/bi/mi/photoView.nhn?code=167374&imageNid=6627917#tab">�닲寃⑥쭊 吏꾩떎</a><!-- N=a:pho.tlist,r:4,i:6627917 --></p>
    					</li>
    					
    					<li class="">
    						<p class="thmb">
    							<a href="/movie/bi/mi/photoView.nhn?code=144183&imageNid=6623789#tab">
    								<img src="https://movie-phinf.pstatic.net/20180910_31/1536541570879K0tpD_JPEG/movie_image.jpg?type=n108_108_2" width="108" height="108" alt="����엫�뒳由� 濡쒕㎤�뒪" onerror="this.src='https://ssl.pstatic.net/static/movie/2012/06/dft_img108x108.png'">
    								
    								
    							</a><!-- N=a:pho.img,r:5,i:6623789 -->
    						</p>
    						<a href="/movie/bi/mi/photoView.nhn?code=144183&imageNid=6623789#tab"><strong class="tit">28�꽭 誘몄꽦�뀈</strong></a><!-- N=a:pho.list,r:5,i:6623789 -->
    						<p class="tx_brief"><a href="/movie/bi/mi/photoView.nhn?code=144183&imageNid=6623789#tab">����엫�뒳由� 濡쒕㎤�뒪</a><!-- N=a:pho.tlist,r:5,i:6623789 --></p>
    					</li>
    					
    					<li class="last">
    						<p class="thmb">
    							<a href="/movie/bi/mi/photoView.nhn?code=168735&imageNid=6594170#tab">
    								<img src="https://movie-phinf.pstatic.net/20180104_281/1515048793973Wcl1z_JPEG/movie_image.jpg?type=n108_108_2" width="108" height="108" alt="理쒓퀬�쓽 �냼�꽕" onerror="this.src='https://ssl.pstatic.net/static/movie/2012/06/dft_img108x108.png'">
    								
    								
    							</a><!-- N=a:pho.img,r:6,i:6594170 -->
    						</p>
    						<a href="/movie/bi/mi/photoView.nhn?code=168735&imageNid=6594170#tab"><strong class="tit">�깉踰쎌쓽 �빟�냽</strong></a><!-- N=a:pho.list,r:6,i:6594170 -->
    						<p class="tx_brief"><a href="/movie/bi/mi/photoView.nhn?code=168735&imageNid=6594170#tab">理쒓퀬�쓽 �냼�꽕</a><!-- N=a:pho.tlist,r:6,i:6594170 --></p>
    					</li>
    					
    					</ul>
    				</div>
    			</div>
    			<div class="obj_section">
    				<div class="main_event">
    					<div class="notice">
    						<a href="/movie/other/gonggi.nhn" class="notice_more">怨듭���궗�빆 �뜑蹂닿린</a><!-- N=a:bnt.more -->
    						<div class="info"><a href="/movie/other/gonggi.nhn?docID=10000000000030662512"><em>[怨듭��]</em>&nbsp; YES24 �삁留� �꽌鍮꾩뒪 �젏寃� �븞�궡</a><!-- N=a:bnt.list --></div>
    						<p><span class="page_info">�젙蹂�</span>蹂� �럹�씠吏��뒗 �굹�닎湲�瑗댁뿉 理쒖쟻�솕 �릺�뼱�엳�뒿�땲�떎. <a href="http://hangeul.naver.com/font" target="_blank" class="font_inst">�굹�닎湲�瑗댁꽕移�<em class="arr"></em></a><!-- N=a:btm.nanumfont --></p>
    					</div>
    				</div>
    			</div>
    		</div>
    	</div>
    	<!-- [D] 留⑥쐞濡� 踰꾪듉 div id="content" 湲곗�� top:342px �씠�긽 -->
    	
    <div class="staticbanner" id="floatingTopAnchor" style="bottom:40px">
        <a href="#" title="留⑥쐞濡�"><img alt="留⑥쐞濡�" src="https://ssl.pstatic.net/static/movie/2012/08/btn_top.png" width="33" height="35"></a><!-- N=a:btm.top -->
    </div>
    <script type="text/javascript">
    jindo.$Fn(function () {
        var welTopAnchor = jindo.$Element('floatingTopAnchor');
        var welContent = jindo.$Element('content');
        var nTopMargin = 342 + welTopAnchor.height();
        var nMaxY;
        var nMinY = 61;
        var oFloatingLayer = new jindo.FloatingLayer(welTopAnchor).attach({
            beforeMove: function (oEvent) {
                // �긽�떒 limit
                nMaxY = welContent.height() - nTopMargin;
                if (oEvent.nY > nMaxY) {
                    oEvent.nY = nMaxY;
                }
    
                 // �븯�떒 limit
                if (oEvent.nY < nMinY) {
                    oEvent.nY = nMinY;
                }
            }
        });
    }).attach(window, 'load');
    </script>
    	<!-- //留⑥쐞濡� -->
    
    </div>
    <!-- //content -->
    
    <script type="text/template" id="RESERVE_template">
    {for index:movie in RESERVE}
    	<li class="item{=index +1}" data-id="{=movie.movieCode}" data-detail="{=movie.movieCode}" data-reserve="{=movie.movieCode}" onmouseover="jindo.$Element('reserveTooltip{=index+1}').show();" onmouseout="jindo.$Element('reserveTooltip{=index+1}').hide();">
    		<div class="obj_off tab4">
    			<a href="/movie/bi/mi/basic.nhn?code={=movie.movieCode}" onfocus="jindo.$Element('reserveTooltip{=index+1}').show();oTimer.abort();" onblur="jindo.$Element('reserveTooltip{=index+1}').hide();movieChart.restartTimer();"><span class="rank"><em>{=index +1}�쐞</em></span>
    				{if movie.adult}
    					<span class="ico_rating_19">泥��냼�뀈 �쑀�빐臾�</span>
    				{elseif movie.lastKoreanGrade != null}
    					{js movieChart.getGradeIcon(=movie.lastKoreanGrade.code)}
    				{/if}
    				<span class="mask"></span>
    				<img src="https://movie-phinf.pstatic.net{=movie.posterImageUrl}?type=f125" alt="{js movieChart.replaceDoubleQuotationForHTML(=movie.movieTitle)}" width="125" height="179" onerror="this.src='https://ssl.pstatic.net/static/movie/2012/06/dft_img125x179.png'">
    				<span class="baseplate r">
    					<span class="spr stic_rate l"><em>�삁留ㅼ쑉</em></span>
    					<strong class="l">{js movieChart.numberFont(=movie.formattedReserveRatio, 'rate')}<span class="char rate_pct"><em>%</em></span></strong>
    				</span>
    			</a><!-- N=a:run.da,r:{=index + 1},i:{=movie.movieCode} -->
    		</div>
    		<div  id="reserveTooltip{=index+1}" class="obj_con" style="display:none">
    			<div class="obj_on{js movieChart.tooltipLengthOver(=movie.movieTitle)} {if (index+1)%5 == 0}rt{/if}">
    				<div class="tooltip">
    					<span class="top"></span>
    					<p class="mv_title">{=movie.movieTitle}</p>
    					<span class="bottom"></span><span class="bottom_r"></span>
    				</div>
    			</div>
    		</div>
    	</li>
    {/for}
    </script>
    
    <script type="text/template" id="CURRENT_template">
    {for index:movie in CURRENT}
    	<li class="item{=index +1}" data-id="{=movie.movieCode}" data-detail="{=movie.movieCode}" data-reserve="{=movie.movieCode}" onmouseover="jindo.$Element('currentTooltip{=index+1}').show();" onmouseout="jindo.$Element('currentTooltip{=index+1}').hide();">
    		<div class="obj_off tab4">
    			<a href="/movie/bi/mi/basic.nhn?code={=movie.movieCode}" onfocus="jindo.$Element('currentTooltip{=index+1}').show();oTimer.abort();" onblur="jindo.$Element('currentTooltip{=index+1}').hide();movieChart.restartTimer();">
    				{if movie.adult}
    					<span class="ico_rating_19">泥��냼�뀈 �쑀�빐臾�</span>
    				{elseif movie.lastKoreanGrade != null}
    					{js movieChart.getGradeIcon(=movie.lastKoreanGrade.code)}
    				{/if}
    				<span class="mask"></span>
    				<img src="https://movie-phinf.pstatic.net{=movie.posterImageUrl}?type=f125" alt="{js movieChart.replaceDoubleQuotationForHTML(=movie.movieTitle)}" width="125" height="179" onerror="this.src='https://ssl.pstatic.net/static/movie/2012/06/dft_img125x179.png'">
    				<span class="baseplate r">
    					<span class="rank_star l"><span class="star_off"><em>蹂꾩젏 - 珥� 10�젏 以�</em></span><span class="star_on" style="width:{=movie.point*10}%"><em>{=movie.point} �젏</em></span></span>
    					<strong class="l">{js movieChart.numberFont(=movie.point, 'sc')}</strong>
    				</span>
    			</a><!-- N=a:run.da,r:{=index + 1},i:{=movie.movieCode} -->
    		</div>
    		<div id="currentTooltip{=index+1}" class="obj_con" style="display:none">
    			<div class="obj_on{js movieChart.tooltipLengthOver(=movie.movieTitle)} {if (index+1)%5 == 0}rt{/if}">
    				<div class="tooltip">
    					<span class="top"></span>
    					<p class="mv_title">{=movie.movieTitle}</p>
    					<span class="bottom"></span><span class="bottom_r"></span>
    				</div>
    			</div>
    		</div>
    	</li>
    {/for}
    </script>
    
    <script type="text/template" id="COMMING_template">
    {for index:movie in COMMING}
    	<li class="item{=index +1}" data-id="{=movie.movieCode}" data-detail="{=movie.movieCode}" data-reserve="{=movie.movieCode}" onmouseover="jindo.$Element('commingTooltip{=index+1}').show();" onmouseout="jindo.$Element('commingTooltip{=index+1}').hide();">
    		<div class="obj_off tab4">
    			<a href="/movie/bi/mi/basic.nhn?code={=movie.movieCode}" onfocus="jindo.$Element('commingTooltip{=index+1}').show();oTimer.abort();" onblur="jindo.$Element('commingTooltip{=index+1}').hide();movieChart.restartTimer();">
    				{if movie.adult}
    					<span class="ico_rating_19">泥��냼�뀈 �쑀�빐臾�</span>
    				{elseif movie.lastKoreanGrade != null}
    					{js movieChart.getGradeIcon(=movie.lastKoreanGrade.code)}
    				{/if}
    				<span class="mask"></span>
    				<img src="https://movie-phinf.pstatic.net{=movie.posterImageUrl}?type=f125" alt="{js movieChart.replaceDoubleQuotationForHTML(=movie.movieTitle)}" width="125" height="179" onerror="this.src='https://ssl.pstatic.net/static/movie/2012/06/dft_img125x179.png'">
    				<span class="baseplate r">
    					<strong class="l">{js movieChart.numberFont(=movie.openDate, 'rate')}</strong>{if movie.openDate != ''}<span class="spr stic_open l"><em>媛쒕큺</em>{/if}</span>
    				</span>
    			</a><!-- N=a:run.da,r:{=index + 1},i:{=movie.movieCode} -->
    		</div>
    		<div id="commingTooltip{=index+1}" class="obj_con" style="display:none">
    			<div class="obj_on{js movieChart.tooltipLengthOver(=movie.movieTitle)} {if (index+1)%5 == 0}rt{/if}">
    				<div class="tooltip">
    					<span class="top"></span>
    					<p class="mv_title">{=movie.movieTitle}</p>
    					<span class="bottom"></span><span class="bottom_r"></span>
    				</div>
    			</div>
    		</div>
    	</li>
    {/for}
    </script>
    
    <script type="text/template" id="POINT_template">
    {for index:movie in POINT}
    	<li class="item{=index +1}" data-id="{=movie.movieCode}" data-detail="{=movie.movieCode}" data-reserve="{=movie.movieCode}" onmouseover="jindo.$Element('pointTooltip{=index+1}').show();" onmouseout="jindo.$Element('pointTooltip{=index+1}').hide();">
    		<div class="obj_off tab4">
    			<a href="/movie/bi/mi/basic.nhn?code={=movie.movieCode}" onfocus="jindo.$Element('pointTooltip{=index+1}').show();oTimer.abort();" onblur="jindo.$Element('pointTooltip{=index+1}').hide();movieChart.restartTimer();"><span class="rank"><em>{=index +1}�쐞</em></span>
    				{if movie.adult}
    					<span class="ico_rating_19">泥��냼�뀈 �쑀�빐臾�</span>
    				{elseif movie.lastKoreanGrade != null}
    					{js movieChart.getGradeIcon(=movie.lastKoreanGrade.code)}
    				{/if}
    				<span class="mask"></span>
    				<img src="https://movie-phinf.pstatic.net{=movie.posterImageUrl}?type=f125" alt="{js movieChart.replaceDoubleQuotationForHTML(=movie.movieTitle)}" width="125" height="179" onerror="this.src='https://ssl.pstatic.net/static/movie/2012/06/dft_img125x179.png'">
    				<span class="baseplate r">
    					<span class="rank_star l"><span class="star_off"><em>蹂꾩젏 - 珥� 10�젏 以�</em></span><span class="star_on" style="width:{=movie.point*10}%"><em>{=movie.point} �젏</em></span></span>
    					<strong class="l">{js movieChart.numberFont(=movie.point, 'sc')}</strong>
    				</span>
    			</a><!-- N=a:run.da,r:{=index + 1},i:{=movie.movieCode} -->
    		</div>
    		<div id="pointTooltip{=index+1}" class="obj_con" style="display:none">
    			<div class="obj_on{js movieChart.tooltipLengthOver(=movie.movieTitle)} {if (index+1)%5 == 0}rt{/if}">
    				<div class="tooltip">
    					<span class="top"></span>
    					<p class="mv_title">{=movie.movieTitle}</p>
    					<span class="bottom"></span><span class="bottom_r"></span>
    				</div>
    			</div>
    		</div>
    	</li>
    {/for}
    </script>
    
    <script type="text/template" id="BOXOFFICE_template">
    {for index:movie in BOXOFFICE}
    	<li class="item{=index +1}" data-id="{=movie.movieCode}" data-detail="{=movie.movieCode}" data-reserve="{=movie.movieCode}" onmouseover="jindo.$Element('boxofficeTooltip{=index+1}').show();" onmouseout="jindo.$Element('boxofficeTooltip{=index+1}').hide();">
    		<div class="obj_off tab4">
    			<a href="/movie/bi/mi/basic.nhn?code={=movie.movieCode}" onfocus="jindo.$Element('boxofficeTooltip{=index+1}').show();oTimer.abort();" onblur="jindo.$Element('boxofficeTooltip{=index+1}').hide();movieChart.restartTimer();"><span class="rank"><em>{=index +1}�쐞</em></span>
    				{if movie.adult}
    					<span class="ico_rating_19">泥��냼�뀈 �쑀�빐臾�</span>
    				{elseif movie.lastKoreanGrade != null}
    					{js movieChart.getGradeIcon(=movie.lastKoreanGrade.code)}
    				{/if}
    				<span class="mask"></span>
    				<img src="https://movie-phinf.pstatic.net{=movie.posterImageUrl}?type=f125" alt="{js movieChart.replaceDoubleQuotationForHTML(=movie.movieTitle)}" width="125" height="179" onerror="this.src='https://ssl.pstatic.net/static/movie/2012/06/dft_img125x179.png'">
    				<span class="baseplate r">
    					<span class="spr stic_box l"><em>二쇰쭚愿�媛�</em></span>
    					<strong class="l">{js movieChart.numberFont(=movie.formattedWeekendAudience, 'cnt')}<span class="char cnt_per"><em>紐�</em></span></strong>
    				</span>
    			</a><!-- N=a:run.da,r:{=index + 1},i:{=movie.movieCode} -->
    		</div>
    		<div id="boxofficeTooltip{=index+1}" class="obj_con" style="display:none">
    			<div class="obj_on{js movieChart.tooltipLengthOver(=movie.movieTitle)} {if (index+1)%5 == 0}rt{/if}">
    				<div class="tooltip">
    					<span class="top"></span>
    					<p class="mv_title">{=movie.movieTitle}</p>
    					<span class="bottom"></span><span class="bottom_r"></span>
    				</div>
    			<div>
    		</div>
    	</li>
    {/for}
    </script>
    
    <script type="text/template" id="DOWNLOAD_template">
    {if DOWNLOAD ==  ""}
    	<li class="error_area">
             <div class="error_msg"></div>
        </li>
    {else}
    	{for index:movie in DOWNLOAD}
    		<li class="item{=index +1}" data-id="{=movie.movieCode}" data-detail="{=movie.movieCode}" data-reserve="{=movie.movieCode}" onmouseover="jindo.$Element('downloadTooltip{=index+1}').show();" onmouseout="jindo.$Element('downloadTooltip{=index+1}').hide();">
    			<div class="obj_off tab4">
    				<a href="http://nstore.naver.com/tvstore/detail.nhn?mcode={=movie.movieCode}" target="_blank"  onfocus="jindo.$Element('downloadTooltip{=index+1}').show();oTimer.abort();" onblur="jindo.$Element('downloadTooltip{=index+1}').hide();movieChart.restartTimer();"><span class="rank"><em>{=index +1}�쐞</em></span>
    					{if movie.adult}
    						<span class="ico_rating_19">泥��냼�뀈 �쑀�빐臾�</span>
    					{elseif movie.lastKoreanGrade != null}
    						{js movieChart.getGradeIcon(=movie.lastKoreanGrade.code)}
    					{/if}
    					<span class="mask"></span> {if movie.salePossibleYn == true}<span class="purchase">援щℓ</span>{/if} {if movie.lendingPossibleYn == true}<span class="rental">����뿬</span>{/if}
    					<img src="https://movie-phinf.pstatic.net{=movie.posterImageUrl}?type=f125" alt="{js movieChart.replaceDoubleQuotationForHTML(=movie.movieTitle)}" width="125" height="179" onerror="this.src='https://ssl.pstatic.net/static/movie/2012/06/dft_img125x179.png'">
    					<span class="baseplate r">
    						<span class="spr stic_down l"><em>�뙋留ㅼ쑉</em></span>
    						<strong class="l">{js movieChart.numberFont(=movie.formattedSaleRate, 'rate')}<span class="char rate_pct"><em>%</em></span></strong>
    					</span>
    				</a><!-- N=a:run.da,r:{=index + 1},i:{=movie.movieCode} -->
    			</div>
    			<div id="downloadTooltip{=index+1}" class="obj_con" style="display:none">
    				<div class="obj_on{js movieChart.tooltipLengthOver(=movie.movieTitle)} {if (index+1)%5 == 0}rt{/if}">
    					<div class="tooltip">
    						<span class="top"></span>
    						<p class="mv_title">{=movie.movieTitle}</p>
    						<span class="bottom"></span><span class="bottom_r"></span>
    					</div>
    				</div>
    			</div>
    		</li>
    	{/for}
    {/if}
    </script>
    
    
    <script type="text/javascript">
    
    
    
    
    
    var flickContents = new Array(6);
    
    
    var htInfo = jindo.m.getDeviceInfo(); 
    var bUseCss3d = jindo.m._isUseCss3d() || (htInfo.galaxyS2 && (htInfo.version >= "4.0.3"));
    var oFlicking = new jindo.m.CircularFlicking(jindo.$('mflick'),{
    	nDuration : 100,
    	bHorizontal : true,
        sClassPrefix : 'flick-',
        nFlickThreshold : 40,
        nTotalContents : 6,
        bUseCss3d : bUseCss3d
    }).attach({
    
    	// ����씠癒� �젙吏� 諛� 硫붾돱 �븯�씠�씪�씠�똿
    	'beforeFlicking' : function(oCustomEvt) {
    		oTimer.abort();
    
    		var index = oCustomEvt.nContentIndex;
    		var nextIndex = movieChart.getNextIndex(index);
    		var previousIndex = movieChart.getPreviousIndex(index);
    
    		if (oCustomEvt.bLeft) {
    			movieChart.setMenuHighlighting(nextIndex);
    		} else {
    			movieChart.setMenuHighlighting(previousIndex);
    		}
    		
    		
    		this.getPanelElement().removeClass('blind');
    		this.getRightPanelElement().removeClass('blind');
    		this.getLeftPanelElement().removeClass('blind');
    	},
    	
    	// �뵆由ы궧泥섎━ 諛� ����씠癒� �옱�떆�옉
    	'afterFlicking' : function(oCustomEvt){
    		
    		if (oCustomEvt.bLeft) {
    			var type = movieChart.movieChartTab[oCustomEvt.nContentRightIndex];
    			
    			// �뵆由ы궧 ����옣蹂��닔�뿉 �씠誘� �뜲�씠�꽣媛� �엳�떎硫� ����옣蹂��닔 �씠�슜, �뾾�쑝硫� Ajax Call.
    			if (flickContents[oCustomEvt.nContentRightIndex]) {
    				movieChart.movieChartJsonCallBack(null, flickContents[oCustomEvt.nContentRightIndex], type, oCustomEvt.nContentRightIndex, oCustomEvt.nPanelRightIndex);
    			} else {
    				movieChart.ajaxCall(movieChart.movieChartJsonUrl, type, oCustomEvt.nContentRightIndex, oCustomEvt.nPanelRightIndex);
    			}
    			
    		} else {
    			var type = movieChart.movieChartTab[oCustomEvt.nContentLeftIndex];
    			
    			// �뵆由ы궧 ����옣蹂��닔�뿉 �씠誘� �뜲�씠�꽣媛� �엳�떎硫� ����옣蹂��닔 �씠�슜, �뾾�쑝硫� Ajax Call.
    			if (flickContents[oCustomEvt.nContentLeftIndex]) {
    				movieChart.movieChartJsonCallBack(null, flickContents[oCustomEvt.nContentLeftIndex], type, oCustomEvt.nContentLeftIndex, oCustomEvt.nPanelLeftIndex);
    			} else {
    				movieChart.ajaxCall(movieChart.movieChartJsonUrl, type, oCustomEvt.nContentLeftIndex, oCustomEvt.nPanelLeftIndex);
    			}
    		}
    
    		
    		this.getRightPanelElement().addClass('blind');
    		this.getLeftPanelElement().addClass('blind');
    		
    		movieChart.restartTimer();
    	}
    });
    
    //[MOVIEOP-5993] [紐⑤컮�씪�쎒] Android 怨듯넻�뙎湲� �씠�쟾/�떎�쓬 踰꾪듉 �겢由��떆 �룷而ㅼ떛 �쑀吏�(PC �솚寃쎌뿉�꽌�뒗 Flicking �릺吏� �븡�룄濡� �닔�젙.)
    var osInfo = jindo.$Agent().os();
    if(osInfo.win || osInfo.mac || osInfo.linux) {
    	oFlicking.attach({
    		'touchStart' : function(oCustomEvt){
    			oCustomEvt.stop();
    			}
    	});
    }
    
    
    var oTimer = new jindo.Timer();
    
    
    var movieChart = {
    		
    		movieChartDefaultJsonUrl : "/movieChartDefaultJson.nhn",
    		movieChartJsonUrl : "/movieChartJson.nhn",
    		
    		movieChartTab : new Array("RESERVE", "CURRENT", "COMMING", "POINT", "BOXOFFICE", "DOWNLOAD"),
    		movieChartAllViewUrl : new Array(
    				"/movie/running/current.nhn?order=reserve",
    				"/movie/running/current.nhn",
    				"/movie/running/premovie.nhn?order=reserve",
    				"/movie/running/current.nhn?order=point",
    				"/movie/sdb/rank/rboxoffice.nhn",
    				"http://nstore.naver.com/movie/top100List.nhn?rankingTypeCode=PC_D"
    		),
    
    		// 媛쒕큺�삁�젙�옉 紐⑸줉�쓽 留덉��留� �쁺�솕�쓽 �긽�쁺愿��씠 �뾾�떎硫�, �삁留ㅼ쑉�닚 媛쒕큺�삁�젙�옉�뿉�꽌 �뜲�씠�꽣媛� 遺�議깊빐�꽌 �긽�쁺愿��씠 �뾾�뒗 �뜲�씠�꽣�룄 梨꾩썙�꽔��� 寃쎌슦�씠湲� �븣臾몄뿉 �뜑蹂닿린 留곹겕 �젣怨듯븯吏� �븡�쓬
    		hasCommingMovieAllViewUrl : true,
    		
    		// domready�떆 �닔�뻾
    		init : function() {
    			movieChart.ajaxCall(movieChart.movieChartJsonUrl, movieChart.movieChartTab[0], 0, 0);
    			movieChart.setMenuHighlighting(0);
    			movieChart.startTimer();
    		},
    		
    		// load�떆 �닔�뻾
    		load : function() {
    			movieChart.ajaxCall(movieChart.movieChartJsonUrl, movieChart.movieChartTab[1], 1, 1);
    			movieChart.ajaxCall(movieChart.movieChartJsonUrl, movieChart.movieChartTab[movieChart.movieChartTab.length-1], movieChart.movieChartTab.length-1, 2);
    		},
    		
    		// ����씠癒� �옱�떆�옉
    		restartTimer : function() {
    			
    			if (oTimer.isRunning = true) {
    				oTimer.abort();
    			}
    			
    			oTimer = new jindo.Timer();
    			movieChart.startTimer();
    		},
    		
    		// ����씠癒� �떆�옉
    		startTimer : function() {
    			oTimer.start( function() {
    				oFlicking.moveNext();
    				return true;  
    			}, 7000);
    		},
    		
    		// JSON API �샇異�
    		ajaxCall : function(url, type, index, targetAreaIndex) {
    			var ajax = new jindo.$Ajax(url, { 
    				method : "GET",
    				onload : function(response){
    					if (url == movieChart.movieChartDefaultJsonUrl) {
    						// ����꽭�똿 
    						movieChart.movieChartDefaultJsonCallBack(response, null, index);
    					} else {
    						// 媛쒕퀎�꽭�똿
    						movieChart.movieChartJsonCallBack(response, null, type, index, targetAreaIndex);
    					}
    				}
    			});
    			ajax.header("ajax", "true");
    		    ajax.request({"type":type});
    		},
    		
    		// 臾대퉬李⑦듃 ����꽭�똿 CallBack �븿�닔
    		movieChartDefaultJsonCallBack : function(response, movieChartList, index) {
    			
    			if (movieChartList == null) {
    				var jsonData = response.json();
    				movieChartList = jsonData.movieChartList;
    			}
    			
    			var nextIndex = movieChart.getNextIndex(index);
    			var previousIndex = movieChart.getPreviousIndex(index);
    
    			oFlicking.setContentIndex(index);
    			oFlicking.getPanelElement().html(jindo.$Template(movieChart.movieChartTab[index] + "_template").process(movieChartList[0]));
    			oFlicking.getRightPanelElement().html(jindo.$Template(movieChart.movieChartTab[nextIndex] + "_template").process(movieChartList[1]));
    			oFlicking.getLeftPanelElement().html(jindo.$Template(movieChart.movieChartTab[previousIndex] + "_template").process(movieChartList[2]));
    
    			flickContents[index] = movieChartList[0];
    			flickContents[nextIndex] = movieChartList[1];
    			flickContents[previousIndex] = movieChartList[2];
    			
    			if (index == 2) {
    				this.setHasCommingMovieAllViewUrl(movieChartList[0]);
    				movieChart.setMenuHighlighting(index);
    			}
    			
    			
    			oFlicking.getPanelElement().removeClass('blind');
    			oFlicking.getRightPanelElement().addClass('blind');
    			oFlicking.getLeftPanelElement().addClass('blind');
    		},
    		
    		// �뵆由ы궧 諛� 醫뚯슦 �꽕鍮꾧쾶�씠�뀡 踰꾪듉 �겢由��뿉 �뵲瑜� CallBack �븿�닔
    		movieChartJsonCallBack : function(response, movieChartList, type, index, targetAreaIndex) {
    			
    			if (movieChartList == null) {
    				var jsonData = response.json();
    				movieChartList = jsonData.movieChartList;
    			}
    			
    			jindo.$Element("flick" + targetAreaIndex).html(jindo.$Template(type + "_template").process(movieChartList));
    			flickContents[index] = movieChartList;
    			
    			if (index == 2) {
    				this.setHasCommingMovieAllViewUrl(movieChartList);
    			}
    			
    			
    			oFlicking.getPanelElement().removeClass('blind');
    			oFlicking.getRightPanelElement().addClass('blind');
    			oFlicking.getLeftPanelElement().addClass('blind');
    		},
    		
    		// 臾대퉬李⑦듃 ����꽭�똿 �샇異�
    		fullSettingMovieChart : function(index) {
    			movieChart.setMenuHighlighting(index);
    			
    			var nextIndex = movieChart.getNextIndex(index);
    			var previousIndex = movieChart.getPreviousIndex(index);
    
    			// ����옣蹂��닔�뿉 �뜲�씠�꽣媛� �씠誘� �엳�떎硫� ����옣蹂��닔 �씠�슜, �븘�땲硫� Ajax Call.
    			if (flickContents[index] && flickContents[nextIndex] && flickContents[previousIndex]) {
    				var movieChartList = new Array(flickContents[index], flickContents[nextIndex], flickContents[previousIndex]);
    				movieChart.movieChartDefaultJsonCallBack(null, movieChartList, index);
    			} else {
    				movieChart.ajaxCall(movieChart.movieChartDefaultJsonUrl, movieChart.movieChartTab[index], index);
    			}
    		},
    		
    		// 硫붾돱 �븯�씠�씪�씠�똿 泥섎━
    		setMenuHighlighting : function(index) {
    			
    			// �꺆硫붾돱 �븯�씠�씪�씠�똿
    			for (i=0; i<movieChart.movieChartTab.length; i++) {
    				jindo.$Element(movieChart.movieChartTab[i] + "_tab").removeClass("on");
    			}
    			jindo.$Element(movieChart.movieChartTab[index] + "_tab").addClass("on");
    			
    			// �쟾泥대낫湲� URL �꽭�똿
    			jindo.$("movieChartAllView").href = movieChart.movieChartAllViewUrl[index];
    			
    			// [�떎�슫濡쒕뱶�닚]�씪 寃쎌슦, �쟾泥대낫湲� �븘�씠肄섏씠 �떎瑜대떎. (�깉李�)
    			if (movieChart.movieChartTab[index] == "DOWNLOAD") {
    				jindo.$Element(jindo.$$.getSingle(".all_view_go")).show();
    				jindo.$("movieChartAllView").target = "_blank";
    				jindo.$Element(jindo.$$.getSingle(".all_view_go")).addClass("dwn");
    			}
    			// [媛쒕큺�삁�젙�옉]�씪 寃쎌슦 �삁留ㅼ쑉�닚 媛쒕큺�삁�젙�옉�뿉�꽌 �뜲�씠�꽣媛� 遺�議깊빐�꽌 梨꾩썙�꽔��� 寃쎌슦�씠硫� �쟾泥� 蹂닿린 留곹겕瑜� 蹂댁뿬二쇱�� �븡�뒗�떎. 
    			else if (movieChart.movieChartTab[index] == "COMMING" && !this.hasCommingMovieAllViewUrl) {
    				jindo.$Element(jindo.$$.getSingle(".all_view_go")).hide();
    			}
    			else {
    				jindo.$Element(jindo.$$.getSingle(".all_view_go")).show();
    				jindo.$("movieChartAllView").target = "_self";
    				jindo.$Element(jindo.$$.getSingle(".all_view_go")).removeClass("dwn");
    			}
    			
    		},		
    		
    		// �몢媛쒖쓽 �룷�넗�씤�봽�씪�룄硫붿씤�쓣 遺꾩궛�빐�꽌 �젣怨� 
    		getPhotoInfraImageDomain : function() {
    			var photoInfraImageDomains = new Array("http://movie.phinf.naver.net", "http://movie2.phinf.naver.net");
    			return photoInfraImageDomains[Math.floor((Math.random()*(2)))];
    		},
    		
    		// �뵲�샂�몴 escape 泥섎━
    		replaceDoubleQuotationForHTML : function(title) {
    			if (title == null) {
    				return null;
    			}
    
    			var result = "";
    			for (i=0; i<title.length; i++) {
    				var tmpChar = title.charAt(i);
    				if (tmpChar == "\"") {
    					result += "&quot;";
    				} else if (tmpChar == "\n" || tmpChar == "\r") {
    					result += "";
    				} else {
    					result += tmpChar;
    				}
    			}
    			return result;
    		},
    		
    		// �씠誘몄���룿�듃 �젙�쓽
    		numberFont : function(value, charName) {
    			var result = "";
    
    			if (value == 'undefined') {
    				value = "0";
    			}
    			
    			for (i=0; i<value.length; i++) {
    				var tmpChar = value.charAt(i);
    
    				result += '<span class="char ' + charName + '_';
    				if (tmpChar == ".") {
    					result += "dot";
    				} else if (tmpChar == ",") {
    					result += "comma";
    				} else {
    					result += "num" + tmpChar;
    				}
    				result += '"><em>' + tmpChar + '</em></span>';
    			}
    
    			return result;
    		},
    		
    		// �룷�뒪�꽣 �댋�똻 湲몄씠�젣�븳 �솗�씤
    		tooltipLengthOver : function(value) {
    			if (value != null && value.length > 18) {
    				return " br";
    			}
    			return "";
    		},
    		
    		// �뵆由ы궧�쁺�뿭 �떎�쓬 index瑜� �뼸�뒗�떎.
    		getNextIndex : function(index) {
    			var nextIndex = index + 1;
    			if (nextIndex > movieChart.movieChartTab.length - 1) {
    				nextIndex = 0;
    			}
    			return nextIndex;
    		},
    		
    		// �뵆由ы궧�쁺�뿭 �씠�쟾 index瑜� �뼸�뒗�떎.
    		getPreviousIndex : function(index) {
    			var previousIndex = index - 1;
    			if (previousIndex < 0) {
    				previousIndex = movieChart.movieChartTab.length - 1;
    			}
    			return previousIndex;
    		}, 
    		
    		// 媛쒕큺�삁�젙�옉�쓽 �쟾泥대낫湲� 踰꾪듉 �끂異� �뿬遺�
    		setHasCommingMovieAllViewUrl : function(movieList) {
    			if (movieList.COMMING[movieList.COMMING.length - 1].theater == 0) {
    				this.hasCommingMovieAllViewUrl = false;	
    			} else {
    				this.hasCommingMovieAllViewUrl = true;	
    			}
    		},
    
    		// �벑湲� �븘�씠肄� html�쓣 �뼸�뒗�떎.
    		getGradeIcon : function(gradeCode) {
    			var result = '<span class="ico_rating_';
    			if (gradeCode == "1001001") {
    				result += 'all">�쟾泥� 愿��엺媛�'
    			} else if (gradeCode == "1001002") {
    				result += '12">12�꽭 愿��엺媛�'
    			} else if (gradeCode == "1001003") {
    				result += '15">15�꽭 愿��엺媛�'
    			} else if (gradeCode == "1001004") {
    				result += '18">泥��냼�뀈 愿��엺遺덇��'
    			} else if (gradeCode == "1001005") {
    				result += 'restricted">�젣�븳 �긽�쁺媛�'
    			} else {
    				return "";
    			}
    
    			result += '</span>'	;
    
    			return result;
    		}
    };
    
    
    var HomeMovieReviewAccordion = jindo.$Class({
    	$init : function(sClassName) {
    		_self = this;
    		this._wel = jindo.$Element("movieReview");
    		this._welList = this._wel.query ("ul.lst_con." + sClassName);
    		
    		this._wel.delegate(
    				"mouseover",
    				"._select_title",
    				jindo.$Fn(this._onMouseOverItem, this).bind()
    		);
    		
    		jindo.$A(jindo.$ElementList('._select_title_anchor').$value()).forEach(function(element, index, array) {
    			jindo.$Fn(_self._onMouseOverItem, _self).attach(element, "focus");
    		});
    	},
    	
    	_onMouseOverItem : function (we) {
    		we.stopDefault();
    		var nIndex = Number(jindo.$Element(we.element).data('index'));
    		
    		this.openReview(nIndex);
    	},
    	
    	openReview : function (nIndex) {
    		var aEls = this._welList.queryAll("li ! li");
    		
    		// �빐�떦�븯�뒗 �빆紐⑸쭔 <li class="on">
    		for (var i = 0; i < aEls.length; i++) {
    			aEls[i].cssClass("on", nIndex == i);
    		}
    	},
    	
    	showRandomMovie : function () {
    		var randNo = Math.floor(4 * Math.random());
    		this.openReview(randNo);
    	}
    });
    
    
    
    var oFirstHomeMovieReviewAccordion = new HomeMovieReviewAccordion("first");
    
    
    jindo.$Fn(function() {oFirstHomeMovieReviewAccordion.showRandomMovie();}).attach(document, "domready");
    
    jindo.$Fn(function() {movieChart.init();}).attach(document, "domready");
    jindo.$Fn(function() {movieChart.load();}).attach(window, "load");
    jindo.$Fn(function(evt){evt.stop(); oFlicking.movePrev();}, this).attach(jindo.$("flick_prev"),"click");
    jindo.$Fn(function(evt){evt.stop(); oFlicking.moveNext();} ,this).attach(jindo.$("flick_next"),"click");
    
    var nsc = "movie.home";
    </script>
    	</div>
    	<!-- //container -->
    	
    	<!-- footer -->
    	
    
    
    
    <div id="footer">
    	<div class="in_footer">
    		<div class="foot_con">
    				<ul>
    					<li class="first"><a href="http://www.naver.com/rules/service.html" target="rules">�씠�슜�빟愿�</a><!-- N=a:fot.agreement --></li>		
    					<li><a href="http://www.naver.com/rules/privacy.html" target="rules"><strong>媛쒖씤�젙蹂댁쿂由щ갑移�</strong></a><!-- N=a:fot.privacy --></li>
    					<li><a href="http://www.naver.com/rules/disclaimer.html" target="rules">梨낆엫�쓽 �븳怨꾩�� 踰뺤쟻怨좎��</a><!-- N=a:fot.disclaimer --></li>		
    					<li><a href="https://help.naver.com/support/service/main.nhn?serviceNo=800" target="customer">�쁺�솕 怨좉컼�꽱�꽣</a><!-- N=a:fot.help --></li>
    				</ul>
    				<p class="info">蹂� 肄섑뀗痢좎쓽 ����옉沅뚯�� ����옉沅뚯옄 �삉�뒗 �젣怨듭쿂�뿉 �엳�쑝硫�, �씠瑜� 臾대떒 �씠�슜�븯�뒗 寃쎌슦 ����옉沅뚮쾿 �벑�뿉 �뵲�씪 踰뺤쟻 梨낆엫�쓣 吏� �닔 �엳�뒿�땲�떎.</p>
    				<p class="info">
    					�궗�뾽�옄�벑濡앸쾲�샇 : 220-81-62517<span>�넻�떊�뙋留ㅼ뾽 �떊怨좊쾲�샇</span> : 寃쎄린�꽦�궓 �젣 2006 - 692�샇<span>����몴�씠�궗 : �븳�꽦�닕</span><span><a href="http://www.ftc.go.kr/info/bizinfo/communicationList.jsp">�궗�뾽�옄�벑濡앹젙蹂� �솗�씤</a><!-- N=a:fot.bizinfo --></span><br>
    					二쇱냼 : 寃쎄린�룄 �꽦�궓�떆 遺꾨떦援� 遺덉젙濡� 6 �꽕�씠踰� 洹몃┛�뙥�넗由� <span>����몴�쟾�솕 : 1588-3820</span>
    				</p> 
    				<address>
    					<a href="http://www.navercorp.com/" target="_blank" class="logo"><img src="https://ssl.pstatic.net/static/movie/2013/07/logo_naver.png" width="63" height="11" alt="NAVER"></a><!-- N=a:fot.nhn -->
    					<em>Copyright 짤</em>
    					<a href="http://www.navercorp.com/" target="_blank">NAVER Corp.</a><!-- N=a:fot.corp -->
    					<span>All Rights Reserved.</span>
    				</address>
    		</div>
    	</div>
    </div>
    
    
    
    
    
    
    
    
    <script type="text/javascript">
    
    if (false) {
    	var alertType = "NONE";
    	var koreanTitle = "";
    	var movieCode = "0";
    	var userReserveCount = "0";
    	var todayDatetime = "20181112145149";
    	var endDatetimeAfterTwoDays = "00000000000000";
    	
    	
    	if (movieCode > 0) {
    		openWriteActualPointAlert (alertType, koreanTitle, movieCode, userReserveCount, todayDatetime, endDatetimeAfterTwoDays);
    	}
    }
    
    function openWriteActualPointAlert (alertType, koreanTitle, movieCode, count, today, endDate) {
    	if (alertType == "ONE") {
    		setCookieLastUserReserveDate(today, endDate);
    		if (confirm("愿��엺�븯�떊 " + koreanTitle + "�뿉\n�룊�젏 �벑濡� �떆 �꽕�씠踰꾪럹�씠 �룷�씤�듃 500�썝 �쟻由�!\n吏�湲� �룊�젏�벐湲� 硫붾돱濡� �씠�룞�븯�떆寃좎뒿�땲源�?")) {
    			top.location.href = "https://movie.naver.com/movie/bi/mi/point.nhn?code=" + movieCode;
    		}
    	} else if (alertType == "MORE") {
    		setCookieLastUserReserveDate(today, endDate);
    		if (confirm("愿��엺�븯�떊 �옉�뭹�뿉 �룊�젏�쓣 �벑濡앺빐二쇱꽭�슂\n�옉�뭹�떦 �꽕�씠踰꾪럹�씠 �룷�씤�듃 500�썝�뵫 �쟻由�!\n�룊�젏 誘몃벑濡앹옉 由ъ뒪�듃瑜� �솗�씤�븯�떆寃좎뒿�땲源�?")) {
    			top.location.href = "http://ticket.movie.naver.com/Order/OverdueList.aspx";
    		}
    	}
    }
    
    function setCookieLastUserReserveDate(today, endDate) {
    	var cookieForNotOpenActualPointPopup = jindo.$Cookie();
    	
    	
    	cookieForNotOpenActualPointPopup.remove("lastUserReserveDatetime");
    	cookieForNotOpenActualPointPopup.remove("lastUserReserveCheckDatetime");
    	
    	cookieForNotOpenActualPointPopup.set("lastUserReserveDatetime", endDate, 9999, "movie.naver.com");
    	cookieForNotOpenActualPointPopup.set("lastUserReserveCheckDatetime", today, 9999, "movie.naver.com");
    }
    
    </script>
    
    
    
    
    
    
    
    
    <script type="text/javascript">
    	
    		
    		
    		
    		
    			var alertMessage = "吏��썝�릺吏� �븡�뒗 釉뚮씪�슦���濡� �꽌鍮꾩뒪 �씠�슜�뿉 �젣�븳�씠 �엳�뒿�땲�떎.";
    		
    	
    
    	function getBrowser() {
    		var ua = navigator.userAgent;
    		if (/NAVER/.test(ua)) {
    			return "NAVER_APP";
    		} else if (/IEMobile/.test(ua)) {
    			return "INTERNET_EXPLORER_MOBILE";
    		} else if (/MSIE/.test(ua) || /Trident/.test(ua)) {
    			return "INTERNET_EXPLORER";
    		} else if (/Firefox/.test(ua)) {
    			return "FIREFOX";
    		} else if (/Opera\//.test(ua) || /OPR\//.test(ua)) {
    			return "OPERA";
    		}  else if (/Swing\//.test(ua)) {
    			return "SWING";
    		} else if (/Chrome\//.test(ua) || /CriOS\//.test(ua)) {
    			return "CHROME";
    		} else if (/BAND\//.test(ua)) {
    			return "BAND_APP";
    		} else if (/FBAN\/FBIOS/.test(ua)) {
    			return "FACEBOOK_APP";
    		} else if (/Twitter/.test(ua)) {
    			return "TWITTER_APP";
    		} else if (/KAKAOTALK/.test(ua)) {
    			return "KAKAOTALK_APP";
    		} else if (/Android/.test(ua) && /Safari/.test(ua)) {
    			return "ANDROID_INTERNET_APP";
    		} else if (/Safari/.test(ua)) {
    			return "SAFARI";
    		}
    
    		return "";
    	}
    
    	if (getBrowser() === "UNKNOWN" && jindo.$Cookie().get("notSupportBrowserAlert") != 'true') {
    		alert(alertMessage);
    		jindo.$Cookie().set("notSupportBrowserAlert", "true", "9999", "movie.naver.com");
    	}
    
    
    </script>
    
    
    	<!-- //footer -->
    </div>
    <script type="text/javascript">
    
    jindo.$Fn(function (we) {
    
    	// �긽�떒 寃��깋�쁺�뿭
    	var oSearch = new nhn.movie.Search({
    		area : "jSearchArea",
    		autosearch : "https://auto-movie.naver.com/ac?q_enc=UTF-8&st=1&r_lt=1&n_ext=1&t_koreng=1&r_format=json&r_enc=UTF-8&r_unicode=0&r_escape=1&q=",
    		movelink : "/movie/bi/mi/basic.nhn?code=",
    		peoplelink : "/movie/bi/pi/basic.nhn?code="
    	});
    
        // 醫뚯륫 LNB
        var oLNB = new nhn.movie.LNB();
    	if( typeof oViewMode != "undefined") {
    		oViewMode.attach('change', jindo.$Fn(oLNB.update, oLNB).bind());
    	}
    
        //�쁺�솕寃��깋 寃곌낵�뿉�꽌 �룷而ㅼ뒪 �븘�썐�맆 寃쎌슦, 寃��깋 寃곌낵瑜� 吏��슦�룄濡� 蹂�寃�.
        jindo.$Element("lnb_gonaver").attach("focus",function(e){
        	
        	jindo.$Element('search_placeholder').attr({
        		"style" : "display: inline;"
        	})
        	jindo.$Element('ipt_tx_srch').$value().value="";
        	if(jindo.$Element("jAutoComplate") != null){
        		jindo.$Element("jAutoComplate").hide();
        	}
        });
    }).attach(document, 'domready');
    
    //LCS
    jindo.$Fn(function() {
        try{ lcs_do(); } catch(e){}
    }).attach(window, "pageshow");
    
    
    </script>
    <script type="text/javascript">
    	//nClick 珥덇린�솕 �쁺�뿭
    	//�겢由�濡쒓렇 吏묎퀎 肄붾뱶 異붽��
    	var ccsrv="cc.naver.com";
    	var nclk_evt = 1;
    	
    	nclk_do();
    	//nClick 珥덇린�솕 �쁺�뿭 �걹
    </script>
    </body>
    </html>
    


```python
# 파일에 저장
! wget https://movie.naver.com/ -O ./download/naver_movie.html
```

    --2018-11-12 14:51:49--  https://movie.naver.com/
    Resolving movie.naver.com (movie.naver.com)... 210.89.168.33, 210.89.168.65
    Connecting to movie.naver.com (movie.naver.com)|210.89.168.33|:443... connected.
    HTTP request sent, awaiting response... 200 OK
    Length: unspecified [text/html]
    Saving to: './download/naver_movie.html'
    
         0K .......... .......... .......... .......... .......... 2.44M
        50K .......... .                                            110K=0.1s
    
    2018-11-12 14:51:49 (494 KB/s) - './download/naver_movie.html' saved [62975]
    
    


```python
! tree
```

    폴더 PATH의 목록입니다.
    볼륨 일련 번호는 3CBD-1374입니다.
    C:.
    ├─.ipynb_checkpoints
    └─download
    


```python
! type .\download\naver_movie.html
```

    
    
    
    
    
    
    
    
    <!DOCTYPE html>
    <html lang="ko">
    <head>
    <meta charset="utf-8">
    <meta http-equiv="X-UA-Compatible" content="IE=edge">
    <meta http-equiv="imagetoolbar" content="no">
    <meta property="og:title" content="�꽕�씠踰� �쁺�솕"/>
    <meta property="og:description" content="�쁺�솕�뿉 ����븳 紐⑤뱺 寃�"/>
    <meta property="og:image" content="https://ssl.pstatic.net/static/m/movie/icons/OG_270_270.png"/>
    <meta property="og:type" content="article"/>
    <meta property="og:url" content="https://movie.naver.com"/>
    <title>�꽕�씠踰� �쁺�솕</title>
    
    
    
    	
    	
    	
    	
    		<link rel="shortcut icon" href="https://ssl.pstatic.net/static/m/movie/icons/naver_movie_favicon.ico" type="image/x-icon">
    			
    
    
    
    <link rel="stylesheet" type="text/css" href="/css/deploy/movie.all.css?20181107154553" />
    
    <script type="text/javascript" src="/js/deploy/movie.home.js?20181107154553"></script>
    </head>
    
    <body >
    <div id="wrap" class="basic">
    
    	<!-- GNB -->
    	
    
    
    
    <script type="text/javascript">
    function delayed_submit(object) {
    	if (navigator.userAgent.indexOf('MSIE') == -1) {
    		var b = c = new Date();
          	while ((b.getTime() - c.getTime()) < 100) {
    			b = new Date();
          	}
    	} 
    }
    </script>
    
    <script type="text/javascript">
    	var gnb_service = "movie";
    	var gnb_logout = "http://movie.naver.com/index.nhn";
    	var gnb_template = "gnb_utf8";
    	var gnb_brightness=3;
    	var gnb_response = true;
    	
    	jindo.$Fn(function(){
    		getGNB();
    	}).attach(window, "load");
    	
    	jindo.$Fn(function(oEvent){ var welSource = jindo.$Element(oEvent.element);
    			if (!welSource.isChildOf(jindo.$Element("gnb"))) {
    				gnbAllLayerClose();
    			}
    	}).attach(document, 'click');
    </script>
     <!-- skip navigation -->
    <div id="u_skip">
             <a href="#header" onclick="document.getElementById('header').tabIndex=-1;document.getElementById('header').focus();return false;"><span>硫붿씤 硫붾돱濡� 諛붾줈媛�湲�</span></a>
             <a href="#content" id="gnb_goContent" onclick="document.getElementById('content').tabIndex=-1;document.getElementById('content').focus();return false;"><span>蹂몃Ц�쑝濡� 諛붾줈媛�湲�</span></a>
    </div>
    <!-- //skip navigation -->
    <div class="gnb_container">
    	<div class="gnb_content">
    		<div class="gnb_box">
    			<div class="gnb_wrap">
    				<div id="gnb">
    				    <script type="text/javascript" charset="utf-8" src="https://ssl.pstatic.net/static.gn/templates/gnb_utf8.nhn"></script>
    				</div>
    			</div>
    			<!-- 寃��깋李� -->
    			<form id="jSearchForm" action="/movie/search/result.nhn" method="get" style="margin:0;display:none;">
    				<input type="text" name="query" maxlength="100" title="�쁺�솕寃��깋" />
    				<input type="hidden" name="section" value="all"/>
    				<input type="hidden" name="ie" value="utf8"/>
    			</form>
    			<fieldset id="jSearchArea" class="srch_area">
    				<legend><span class="blind">�쁺�솕寃��깋 �쁺�뿭</span></legend>
    				<div class="srch_field_on _view">
    					<span class="ipt_srch">
    						<label for="ipt_tx_srch" id="search_placeholder">�쁺�솕寃��깋</label>
    						<input type="text" id="ipt_tx_srch" class="ipt_tx_srch" name="query" maxlength="100" accesskey="s" style="ime-mode:active;" autocomplete="off" />
    						<span class="align"></span>
    						<span class="auto_tx"><a href="#" title="�옄�룞�셿�꽦 �렯移섍린"><img src="https://ssl.pstatic.net/static/movie/2012/06/srch_arrow_down.gif" width="7" height="4" title="�옄�룞�셿�꽦 �렯移섍린" alt="�옄�룞�셿�꽦 �렯移섍린" /></a></span>
    					</span>
    					<button type="submit" title="寃��깋" class="btn_srch" onClick="clickcr(this,'GNB.search','','',event); delayed_submit(this);"><span class="blind">寃��깋</span></button>
    					 <!-- �옄�룞 �셿�꽦 �쁺�뿭�엫 #autocomplate_template-->
    				</div>
    			</fieldset>
    			<!-- //寃��깋李� -->
    		</div>
    	</div>
    </div>
    
    	<!-- //GNB -->
    
    	<!-- header -->
    	
    
    
    
    
    
    	<div id="header">
    		<a href="#content" title="蹂몃Ц�쑝濡� �씠�룞" class="blind">蹂몃Ц 諛붾줈媛�湲�</a>
    		<h1 class="svc_name">
    			<a href="http://www.naver.com/" title="naver濡� 諛붾줈媛�湲�" class="ci_logo" id="lnb_gonaver"><img src="https://ssl.pstatic.net/static/movie/2013/07/logo_ci.png" width="62" height="13" alt="NAVER" /></a><!-- N=a:LNB.naver -->
    			<a href="/" title="�쁺�솕�꽌鍮꾩뒪�솃�쑝濡� 諛붾줈媛�湲�" class="svc_logo"><img src="https://ssl.pstatic.net/static/movie/2012/06/logo_svc.png" width="34" height="19" alt="�쁺�솕" /></a><!-- N=a:LNB.movie -->
    		</h1>
    		<div id="scrollbar" class="scrollbar scrollbar-noscript">
    			<div class="scrollbar-box">
    				<div class="scrollbar-content">
                        <div class="in_scroll">
                            <ul class="navi">
                            <li>
                                <a href="/" title="�쁺�솕�솃" class="menu01_on"><strong>�쁺�솕�솃</strong></a><!-- N=a:LNB.home -->
                            </li>
                            <li>
                                <a href="/movie/running/current.nhn" title="�긽�쁺�옉쨌�삁�젙�옉" class="menu02"><strong>�긽�쁺�옉쨌�삁�젙�옉</strong></a><!-- N=a:LNB.movies -->
                                <ul class="navi_sub" id="navi_movie" style="display:none">
                                <li><a href="/movie/running/current.nhn" title="�쁽�옱 �긽�쁺�쁺�솕" class="sub2_1"><em>�쁽�옱 �긽�쁺�쁺�솕</em></a><!-- N=a:LNB.now --></li>
                                <li><a href="/movie/running/premovie.nhn" title="媛쒕큺 �삁�젙�쁺�솕" class="sub2_2"><em>媛쒕큺 �삁�젙�쁺�솕</em></a><!-- N=a:LNB.soon --></li>
                                <li><a href="/movie/running/weekendmovie.nhn" title="TV/DVD �쁺�솕" class="sub2_3"><em>TV/DVD �쁺�솕</em></a><!-- N=a:LNB.guide --></li>
                                <li><a href="/movie/running/movieclip.nhn" title="�삁怨좏렪" class="sub2_4"><em>�삁怨좏렪</em></a><!-- N=a:LNB.tailer --></li>
                                </ul>
                            </li>
                            <li>
                                <a href="/movie/sdb/rank/rmovie.nhn" title="�쁺�솕�옲�궧" class="menu03"><strong>�쁺�솕�옲�궧</strong></a><!-- N=a:LNB.db -->
                            </li>
                            <li>
                                <a href="/movie/bi/mi/reserve.nhn" title="�삁留�" class="menu05"><strong>�삁留�</strong></a><!-- N=a:LNB.ticket -->
                            </li>
    
                            <li>
                                <a href="/movie/point/af/list.nhn" title="�룊�젏&middot由щ럭" class="menu07"><strong>�룊�젏&middot由щ럭</strong></a><!-- N=a:LNB.comm -->
                            </li>
                            <li>
                                <a href="http://nstore.naver.com/movie/home.nhn" title="�떎�슫濡쒕뱶" class="menu08" target="_blank"><strong>�떎�슫濡쒕뱶</strong></a><!-- N=a:LNB.download -->
                            </li>
    						<li class="nav_indi">
    						        <a href="http://tv.naver.com/indiecinema" title="�씤�뵒洹뱀옣" target="_blank"><strong>�씤�뵒洹뱀옣</strong></a><!-- N=a:LNB.indie -->
    						</li>                        
                            </ul>
                            
                        </div>
    				</div>
    			</div>
    			<div class="scrollbar-v">
    				<div class="scrollbar-button-up"></div>
    				<div class="scrollbar-track">
    					<div class="scrollbar-thumb"></div>
    				</div>
    				<div class="scrollbar-button-down"></div>
    			</div>
    		</div>
    	</div>
    	
    	<script type="text/javascript">
    	if ("�쁺�솕�솃" == "�긽�쁺�옉쨌�삁�젙�옉"
    			|| "�쁺�솕�솃" == "�쁽�옱 �긽�쁺�쁺�솕"
    			|| "�쁺�솕�솃" == "媛쒕큺 �삁�젙�쁺�솕"
    			|| "�쁺�솕�솃" == "TV/DVD �쁺�솕"
    			|| "�쁺�솕�솃" == "�삁怨좏렪") {
    		jindo.$Element("navi_movie").show();
    	}
    	</script>
    	<!-- //header -->
    	
    	<!-- container -->
    	<div id="container">
    			<!-- content -->
    <div id="content">
    
    	
    	<div class="article hh">
    		<!-- 臾대퉬李⑦듃 -->
    		<div class="mv_main" onmouseover="oTimer.abort();" onmouseout="movieChart.restartTimer();">
    			<div class="flick_nav">
    				<a href="#" id="flick_prev" class="btn_prev" onclick="clickcr(this, 'run.pre', '', '', event);" onfocus="oTimer.abort();" onblur="movieChart.restartTimer();" title="�씠�쟾"><em>�씠�쟾</em></a><!-- N=a:run.pre -->
    			</div>
    			<!-- flick area -->
    			<div id="mflick" class="flick_view_area flick-view">
    				<div class="flick-container" style="left: 0px; ">
    					<ul id="flick0" class="flick-ct home_list page0 flick-panel"></ul>
    					<ul id="flick1" class="flick-ct home_list page1 flick-panel blind"></ul>
    					<ul id="flick2" class="flick-ct home_list page2 flick-panel blind"></ul>
    				</div>
    			</div>
    			<!-- //flick area -->
    			<div class="flick_nav">
    				<a href="#" id="flick_next" class="btn_next" onclick="clickcr(this, 'run.next', '', '', event);" onfocus="oTimer.abort();" onblur="movieChart.restartTimer();" title="�떎�쓬"><em>�떎�쓬</em></a><!-- N=a:run.next -->
    			</div>
    		
    			<div class="running_tab">
    				<ul>
    					<li id="RESERVE_tab" class="item0 on"><a href="#" onclick="movieChart.fullSettingMovieChart(0);" onfocus="oTimer.abort();" onblur="movieChart.restartTimer();" class="flickingTab"><em>�삁留ㅼ닚</em></a><!-- N=a:run.ticket --></li>
    					<li id="CURRENT_tab" class="item1"><a href="#" onclick="movieChart.fullSettingMovieChart(1);" onfocus="oTimer.abort();" onblur="movieChart.restartTimer();" class="flickingTab"><em>�쁽�옱�긽�쁺�옉</em></a><!-- N=a:run.now --></li>
    					<li id="COMMING_tab" class="item2"><a href="#" onclick="movieChart.fullSettingMovieChart(2);" onfocus="oTimer.abort();" onblur="movieChart.restartTimer();" class="flickingTab"><em>媛쒕큺�삁�젙�옉</em></a><!-- N=a:run.coming --></li>
    					<li id="POINT_tab" class="item3"><a href="#" onclick="movieChart.fullSettingMovieChart(3);" onfocus="oTimer.abort();" onblur="movieChart.restartTimer();" class="flickingTab"><em>�룊�젏�닚</em></a><!-- N=a:run.bystar --></li>
    					<li id="BOXOFFICE_tab" class="item4"><a href="#" onclick="movieChart.fullSettingMovieChart(4);" onfocus="oTimer.abort();" onblur="movieChart.restartTimer();" class="flickingTab"><em>諛뺤뒪�삤�뵾�뒪</em></a><!-- N=a:run.box --></li>
    					<li id="DOWNLOAD_tab" class="item5"><a href="#" onclick="movieChart.fullSettingMovieChart(5);" onfocus="oTimer.abort();" onblur="movieChart.restartTimer();" class="flickingTab"><em>�떎�슫濡쒕뱶�닚</em></a><!-- N=a:run.down --></li>
    				</ul>
    				<p href="#" class="all_view_go"><a id="movieChartAllView" href="#" onclick="clickcr(this, 'run.all', '', '', event);" onfocus="oTimer.abort();" onblur="movieChart.restartTimer();" title="�쟾泥대낫湲�">�쟾泥대낫湲�</a><!-- N=a:run.all --></p>
    			</div>
    		</div>
    		<!-- //臾대퉬李⑦듃  -->
    		<div class="section_group" id="homeReview">
    			<div class="obj_section">
    				<div class="main_review">
    					
    					<div class="title_area">
    						<h4 class="hh_review"><strong class="blind">�룊�젏/由щ럭</strong></h4>
    					</div>
    					<div class="hh_review_area">
    						<div id="movieReview" class="hh_review_ct">
    							<ul class="lst_con first" data-index=0 style="display:block">
    							<!-- [D] �꽑�깮�맂 寃쎌슦 li�뿉 class="on" 異붽�� -->
    							
    							<li id="review1" data-index=0 class="_select_title">
    								<a href="/movie/bi/mi/basic.nhn?code=167638" class="thmb" onclick="clickcr(this, 'tvw.img', '167638', '1', event);"><img src="https://movie-phinf.pstatic.net/20181106_289/1541478936071tmadh_JPEG/movie_image.jpg?type=f64_91" width="64" height="91" alt="�셿踰쏀븳 ����씤" onerror="this.src='https://ssl.pstatic.net/static/movie/2012/06/dft_img64x91.png'"></a>
    								<div class="detail">
    									<a href="/movie/bi/mi/basic.nhn?code=167638" onclick="clickcr(this, 'tvw.title', '167638', '1', event);" data-index=0 class="_select_title_anchor"><strong>�셿踰쏀븳 ����씤</strong>
    										<div class="star_score">
    											
    											
    											
    												
    												
    													
    													
    													
    													<span class="st_off"><span class="st_on" style="width:88.3%">�룊�젏 - 珥� 10�젏 以�</span></span>
    													<span class="score">
    													<span class="char sc_num8"><em>8</em></span><span class="char sc_dot"><em>.</em></span><span class="char sc_num8"><em>8</em></span><span class="char sc_num3"><em>3</em></span>
    												
    											
    											</span>
    										</div>
    									</a>
    									<ul class="info">
    										
    											
    												<li><a href="/movie/bi/mi/reviewread.nhn?nid=4666476&code=167638" onclick="clickcr(this, 'tvw.list', '4666476', '1', event);"><span class="tit">�빖�뱶�룿�쓣 怨듦컻�븯硫� 紐⑤몢�쓽 鍮꾨���씠 �뱶�윭�궃�떎. �쁺�솕 &lt;�셿踰쏀븳 ����씤&gt; 蹂닿퀬 �솕�뒿�땲�떎.</span></a></li>
    											
    										
    											
    												<li><a href="/movie/bi/mi/reviewread.nhn?nid=4665211&code=167638" onclick="clickcr(this, 'tvw.list', '4665211', '2', event);"><span class="tit">�셿踰쏀븳 ����씤 [Intimate Strangers] (�뒪�룷X, 荑좏궎�쁺�긽O)</span></a></li>
    											
    										
    											
    												<li class="last"><a href="/movie/bi/mi/reviewread.nhn?nid=4666420&code=167638" onclick="clickcr(this, 'tvw.list', '4666420', '3', event);"><span class="tit">�쁺�솕 �셿踰쏀븳����씤 �넄吏곹썑湲�!!!!!!!!!</span></a></li>
    											
    										
    									</ul>
    								</div>
    							</li>
    							
    							<li id="review2" data-index=1 class="_select_title">
    								<a href="/movie/bi/mi/basic.nhn?code=164155" class="thmb" onclick="clickcr(this, 'tvw.img', '164155', '2', event);"><img src="https://movie-phinf.pstatic.net/20181001_122/153836420654806YHX_JPEG/movie_image.jpg?type=f64_91" width="64" height="91" alt="踰� �냽�뿉 �닲��� 留덈쾿�떆怨�" onerror="this.src='https://ssl.pstatic.net/static/movie/2012/06/dft_img64x91.png'"></a>
    								<div class="detail">
    									<a href="/movie/bi/mi/basic.nhn?code=164155" onclick="clickcr(this, 'tvw.title', '164155', '2', event);" data-index=1 class="_select_title_anchor"><strong>踰� �냽�뿉 �닲��� 留덈쾿�떆怨�</strong>
    										<div class="star_score">
    											
    											
    											
    												
    												
    													
    													
    													
    													<span class="st_off"><span class="st_on" style="width:64.0%">�룊�젏 - 珥� 10�젏 以�</span></span>
    													<span class="score">
    													<span class="char sc_num6"><em>6</em></span><span class="char sc_dot"><em>.</em></span><span class="char sc_num4"><em>4</em></span><span class="char sc_num0"><em>0</em></span>
    												
    											
    											</span>
    										</div>
    									</a>
    									<ul class="info">
    										
    											
    												<li><a href="/movie/bi/mi/reviewread.nhn?nid=4666313&code=164155" onclick="clickcr(this, 'tvw.list', '4666313', '1', event);"><span class="tit">踰쎌냽�뿉 �닲��� 留덈쾿�떆怨�</span></a></li>
    											
    										
    											
    												<li><a href="/movie/bi/mi/reviewread.nhn?nid=4667572&code=164155" onclick="clickcr(this, 'tvw.list', '4667572', '2', event);"><span class="tit">[�쁺�솕�씪�뒗 �씠由꾩쓽 轅�]�쑀�뀈�떆�젅 �뙋���吏��쓽 �뼢�뿰</span></a></li>
    											
    										
    											
    												<li class="last"><a href="/movie/bi/mi/reviewread.nhn?nid=4666805&code=164155" onclick="clickcr(this, 'tvw.list', '4666805', '3', event);"><span class="tit">[踰� �냽�뿉 �닲��� 留덈쾿�떆怨�] �솚�긽�쟻�씤 留덈쾿 �뙋���吏�媛� �렯爾먯쭊�떎.</span></a></li>
    											
    										
    									</ul>
    								</div>
    							</li>
    							
    							<li id="review3" data-index=2 class="_select_title">
    								<a href="/movie/bi/mi/basic.nhn?code=156464" class="thmb" onclick="clickcr(this, 'tvw.img', '156464', '3', event);"><img src="https://movie-phinf.pstatic.net/20181031_68/1540952503496fNRsF_JPEG/movie_image.jpg?type=f64_91" width="64" height="91" alt="蹂댄뿤誘몄븞 �옪�냼�뵒" onerror="this.src='https://ssl.pstatic.net/static/movie/2012/06/dft_img64x91.png'"></a>
    								<div class="detail">
    									<a href="/movie/bi/mi/basic.nhn?code=156464" onclick="clickcr(this, 'tvw.title', '156464', '3', event);" data-index=2 class="_select_title_anchor"><strong>蹂댄뿤誘몄븞 �옪�냼�뵒</strong>
    										<div class="star_score">
    											
    											
    											
    												
    												
    													
    													
    													
    													<span class="st_off"><span class="st_on" style="width:96.6%">�룊�젏 - 珥� 10�젏 以�</span></span>
    													<span class="score">
    													<span class="char sc_num9"><em>9</em></span><span class="char sc_dot"><em>.</em></span><span class="char sc_num6"><em>6</em></span><span class="char sc_num6"><em>6</em></span>
    												
    											
    											</span>
    										</div>
    									</a>
    									<ul class="info">
    										
    											
    												<li><a href="/movie/bi/mi/reviewread.nhn?nid=4664841&code=156464" onclick="clickcr(this, 'tvw.list', '4664841', '1', event);"><span class="tit">��� 洹몃━怨� �봽�젅�뵒 癒명걧由� 120遺꾩�� �굹�뿉寃� 媛먮룞�씠����떎.</span></a></li>
    											
    										
    											
    												<li><a href="/movie/bi/mi/reviewread.nhn?nid=4666759&code=156464" onclick="clickcr(this, 'tvw.list', '4666759', '2', event);"><span class="tit">蹂댄뿤誘몄븞 �옪�냼�뵒</span></a></li>
    											
    										
    											
    												<li class="last"><a href="/movie/bi/mi/reviewread.nhn?nid=4667080&code=156464" onclick="clickcr(this, 'tvw.list', '4667080', '3', event);"><span class="tit">�씠 媛��쓣 吏묒븞 媛��뱷 QUEEN�쓽 �쓬�븙�쑝濡� 梨꾩썙 �꽔寃� �븳 �쁺�솕 ��� 蹂댄뿤誘몄븞 �옪�냼�뵒 ���</span></a></li>
    											
    										
    									</ul>
    								</div>
    							</li>
    							
    							<li id="review4" data-index=3 class="_select_title">
    								<a href="/movie/bi/mi/basic.nhn?code=168058" class="thmb" onclick="clickcr(this, 'tvw.img', '168058', '4', event);"><img src="https://movie-phinf.pstatic.net/20180921_295/1537492322557T4mGt_JPEG/movie_image.jpg?type=f64_91" width="64" height="91" alt="�띁�뒪�듃留�" onerror="this.src='https://ssl.pstatic.net/static/movie/2012/06/dft_img64x91.png'"></a>
    								<div class="detail">
    									<a href="/movie/bi/mi/basic.nhn?code=168058" onclick="clickcr(this, 'tvw.title', '168058', '4', event);" data-index=3 class="_select_title_anchor"><strong>�띁�뒪�듃留�</strong>
    										<div class="star_score">
    											
    											
    											
    												
    												
    													
    													
    													
    													<span class="st_off"><span class="st_on" style="width:69.8%">�룊�젏 - 珥� 10�젏 以�</span></span>
    													<span class="score">
    													<span class="char sc_num6"><em>6</em></span><span class="char sc_dot"><em>.</em></span><span class="char sc_num9"><em>9</em></span><span class="char sc_num8"><em>8</em></span>
    												
    											
    											</span>
    										</div>
    									</a>
    									<ul class="info">
    										
    											
    												<li><a href="/movie/bi/mi/reviewread.nhn?nid=4665669&code=168058" onclick="clickcr(this, 'tvw.list', '4665669', '1', event);"><span class="tit">�띁�뒪�듃留�</span></a></li>
    											
    										
    											
    												<li><a href="/movie/bi/mi/reviewread.nhn?nid=4666569&code=168058" onclick="clickcr(this, 'tvw.list', '4666569', '2', event);"><span class="tit">[�띁�뒪�듃 留�] �슦二쇨�� �븘�땶 �븳 �씤媛꾩쓽 �쐞����븳 �뿬�젙�쓣 �븿猿� �븳�떎.</span></a></li>
    											
    										
    											
    												<li class="last"><a href="/movie/bi/mi/reviewread.nhn?nid=4664850&code=168058" onclick="clickcr(this, 'tvw.list', '4664850', '3', event);"><span class="tit">&lt;�띁�뒪�듃留�(First Man , 2018)&gt; �떖�뿉 泥� 諛쒖쓣 �궡�뵛湲곌퉴吏�.. �땺 �븫�뒪�듃濡깆쓽 �쟾湲� �쁺�솕 (�뜲�씠誘몄뼵 �뀛�젮 媛먮룆, �씪�씠�뼵 怨좎뒳留�, �겢�젅�뼱 �룷�씠, �떎�솕 �쁺�솕)</span></a></li>
    											
    										
    									</ul>
    								</div>
    							</li>
    							
    							</ul>
    						</div>
    					</div>
    				</div>
    				<div class="main_spot" id="homeSpotlight">
    					
    					<div class="section">
    						<div class="title_area">
    							<h4 class="hh_spotlight">
    								<strong class="blind">�뒪�룷�듃�씪�씠�듃</strong>
    							</h4>
    						</div>
    						<div class="hh_spot_area">
    							<a href="https://nstore.naver.com/event/details.nhn?eventNo=11724&productType=MOVIE">
    								
    								
    									
    								
    								<img src="https://movie-phinf.pstatic.net/20181102_44/1541142948715gfzLX_PNG/%BD%BA%C6%F7%C6%AE%B6%F3%C0%CC%C6%AE210X196_3.png" width="210" height="196" title="�뒪�룷�듃�씪�씠�듃 諛곕꼫" alt="�뒪�룷�듃�씪�씠�듃 �쁺�뿭 �엯�땲�떎." border="0">
    							</a>
    						</div>
    					</div>
    					
    				</div>
    			</div>
    
    			
    			<div class="obj_section" id="homeTrailer">
    				<div class="main_prv">
    					<div class="title_area">
    						<h4 class="hh_preview"><strong class="blind">�삁怨좏렪</strong></h4>
    						<a href="/movie/running/movieclip.nhn">
    							<span class="more"><span class="blind">�뜑蹂닿린</span></span>
    						</a><!-- N=a:cms.more -->
    					</div>
    					<ul class="video_thumb">
    					
    					<li>
    						<a href="/movie/bi/mi/mediaView.nhn?code=163843&mid=40551#tab" title="硫붿씤 �삁怨좏렪" class="video_obj">
    							<span class="mask">�룞�쁺�긽</span>
    							
    							<span class="video_ico first"></span>
    							<img src="https://ssl.pstatic.net/imgmovie/multimedia/MOVIECLIP/TRAILER/40551_20181109110238.jpg" width="164" height="114" alt="硫붿씤 �삁怨좏렪" onerror="this.src='https://ssl.pstatic.net/static/movie/2012/06/dft_img164x114.png'">
    						</a><!-- N=a:cms.img,r:1,i:40551 -->
    						<p class="tx_video ico_hd"><span class="blind">HD</span><a href="/movie/bi/mi/mediaView.nhn?code=163843&mid=40551#tab" title="肄쒕뱶 �뒪�궓">肄쒕뱶 �뒪�궓</a><!-- N=a:cms.title,r:1,i:40551 --></p>
    						<p class="tx_brief"><a href="/movie/bi/mi/mediaView.nhn?code=163843&mid=40551#tab" title="硫붿씤 �삁怨좏렪">硫붿씤 �삁怨좏렪</a><!-- N=a:cms.desc,r:1,i:40551 --></p>
    					</li>
    					
    					<li>
    						<a href="/movie/bi/mi/mediaView.nhn?code=162097&mid=40549#tab" title="硫붿씤 �삁怨좏렪" class="video_obj">
    							<span class="mask">�룞�쁺�긽</span>
    							
    							<span class="video_ico first"></span>
    							<img src="https://ssl.pstatic.net/imgmovie/multimedia/MOVIECLIP/TRAILER/40549_20181109104321.jpg" width="164" height="114" alt="硫붿씤 �삁怨좏렪" onerror="this.src='https://ssl.pstatic.net/static/movie/2012/06/dft_img164x114.png'">
    						</a><!-- N=a:cms.img,r:2,i:40549 -->
    						<p class="tx_video ico_hd"><span class="blind">HD</span><a href="/movie/bi/mi/mediaView.nhn?code=162097&mid=40549#tab" title="���由� �뿉�뼱">���由� �뿉�뼱</a><!-- N=a:cms.title,r:2,i:40549 --></p>
    						<p class="tx_brief"><a href="/movie/bi/mi/mediaView.nhn?code=162097&mid=40549#tab" title="硫붿씤 �삁怨좏렪">硫붿씤 �삁怨좏렪</a><!-- N=a:cms.desc,r:2,i:40549 --></p>
    					</li>
    					
    					<li>
    						<a href="/movie/bi/mi/mediaView.nhn?code=180384&mid=40552#tab" title="硫붿씤 �삁怨좏렪" class="video_obj">
    							<span class="mask">�룞�쁺�긽</span>
    							
    							<span class="video_ico first"></span>
    							<img src="https://ssl.pstatic.net/imgmovie/multimedia/MOVIECLIP/TRAILER/40552_20181109110841.jpg" width="164" height="114" alt="硫붿씤 �삁怨좏렪" onerror="this.src='https://ssl.pstatic.net/static/movie/2012/06/dft_img164x114.png'">
    						</a><!-- N=a:cms.img,r:3,i:40552 -->
    						<p class="tx_video ico_hd"><span class="blind">HD</span><a href="/movie/bi/mi/mediaView.nhn?code=180384&mid=40552#tab" title="�윴�떇留� : ���猷곕（�쓽 �뿭�뒿">�윴�떇留� : ���猷곕（�쓽 �뿭�뒿</a><!-- N=a:cms.title,r:3,i:40552 --></p>
    						<p class="tx_brief"><a href="/movie/bi/mi/mediaView.nhn?code=180384&mid=40552#tab" title="硫붿씤 �삁怨좏렪">硫붿씤 �삁怨좏렪</a><!-- N=a:cms.desc,r:3,i:40552 --></p>
    					</li>
    					
    					<li>
    						<a href="/movie/bi/mi/mediaView.nhn?code=164102&mid=40566#tab" title="�뼢湲곗쓽 �궚�꽑 �뼹援� �쁺�긽" class="video_obj">
    							<span class="mask">�룞�쁺�긽</span>
    							
    							
    							<img src="https://ssl.pstatic.net/imgmovie/multimedia/MOVIECLIP/MAKING/40566_20181109040543.jpg" width="164" height="114" alt="�뼢湲곗쓽 �궚�꽑 �뼹援� �쁺�긽" onerror="this.src='https://ssl.pstatic.net/static/movie/2012/06/dft_img164x114.png'">
    						</a><!-- N=a:cms.img,r:4,i:40566 -->
    						<p class="tx_video ico"><a href="/movie/bi/mi/mediaView.nhn?code=164102&mid=40566#tab" title="�쁺二�">�쁺二�</a><!-- N=a:cms.title,r:4,i:40566 --></p>
    						<p class="tx_brief"><a href="/movie/bi/mi/mediaView.nhn?code=164102&mid=40566#tab" title="�뼢湲곗쓽 �궚�꽑 �뼹援� �쁺�긽">�뼢湲곗쓽 �궚�꽑 �뼹援� �쁺�긽</a><!-- N=a:cms.desc,r:4,i:40566 --></p>
    					</li>
    					
    					</ul>
    				</div>
    			</div>
    		</div>
    		
    
    		
    		<div class="section_group" id="homePhoto">
    			<div class="obj_section">
    				<div class="main_photo">
    					<div class="title_area">
    						<h4 class="hh_photo"><strong class="blind">�룷�넗</strong></h4>
    					</div>
    					<ul>
    					
    					<li class="">
    						<p class="thmb">
    							<a href="/movie/bi/mi/photoView.nhn?code=179840&imageNid=6626688#tab">
    								<img src="https://movie-phinf.pstatic.net/20181001_224/1538357818245Ew1Xu_JPEG/movie_image.jpg?type=n108_108_2" width="108" height="108" alt="湲덉���맂 濡쒕㎤�뒪" onerror="this.src='https://ssl.pstatic.net/static/movie/2012/06/dft_img108x108.png'">
    								
    								
    							</a><!-- N=a:pho.img,r:1,i:6626688 -->
    						</p>
    						<a href="/movie/bi/mi/photoView.nhn?code=179840&imageNid=6626688#tab"><strong class="tit">留덊떥�떎: �솴�젣�쓽 �뿰�씤</strong></a><!-- N=a:pho.list,r:1,i:6626688 -->
    						<p class="tx_brief"><a href="/movie/bi/mi/photoView.nhn?code=179840&imageNid=6626688#tab">湲덉���맂 濡쒕㎤�뒪</a><!-- N=a:pho.tlist,r:1,i:6626688 --></p>
    					</li>
    					
    					<li class="">
    						<p class="thmb">
    							<a href="/movie/bi/mi/photoView.nhn?code=164153&imageNid=6628192#tab">
    								<img src="https://movie-phinf.pstatic.net/20181012_178/1539323686120pUbby_JPEG/movie_image.jpg?type=n108_108_2" width="108" height="108" alt="�븷留ㅻえ�샇�븳 �궓���" onerror="this.src='https://ssl.pstatic.net/static/movie/2012/06/dft_img108x108.png'">
    								
    								
    							</a><!-- N=a:pho.img,r:2,i:6628192 -->
    						</p>
    						<a href="/movie/bi/mi/photoView.nhn?code=164153&imageNid=6628192#tab"><strong class="tit">援곗궛: 嫄곗쐞瑜� �끂�옒�븯�떎</strong></a><!-- N=a:pho.list,r:2,i:6628192 -->
    						<p class="tx_brief"><a href="/movie/bi/mi/photoView.nhn?code=164153&imageNid=6628192#tab">�븷留ㅻえ�샇�븳 �궓���</a><!-- N=a:pho.tlist,r:2,i:6628192 --></p>
    					</li>
    					
    					<li class="">
    						<p class="thmb">
    							<a href="/movie/bi/mi/photoView.nhn?code=177381&imageNid=6625840#tab">
    								<img src="https://movie-phinf.pstatic.net/20180919_105/1537319605020MHRRo_JPEG/movie_image.jpg?type=n108_108_2" width="108" height="108" alt="�뙋���吏� �뼱�뱶踰ㅼ쿂" onerror="this.src='https://ssl.pstatic.net/static/movie/2012/06/dft_img108x108.png'">
    								
    								
    							</a><!-- N=a:pho.img,r:3,i:6625840 -->
    						</p>
    						<a href="/movie/bi/mi/photoView.nhn?code=177381&imageNid=6625840#tab"><strong class="tit">�렚洹� �븯�씠�썾�씠</strong></a><!-- N=a:pho.list,r:3,i:6625840 -->
    						<p class="tx_brief"><a href="/movie/bi/mi/photoView.nhn?code=177381&imageNid=6625840#tab">�뙋���吏� �뼱�뱶踰ㅼ쿂</a><!-- N=a:pho.tlist,r:3,i:6625840 --></p>
    					</li>
    					
    					<li class="">
    						<p class="thmb">
    							<a href="/movie/bi/mi/photoView.nhn?code=167374&imageNid=6627917#tab">
    								<img src="https://movie-phinf.pstatic.net/20181011_121/15392182151413vsjd_JPEG/movie_image.jpg?type=n108_108_2" width="108" height="108" alt="�닲寃⑥쭊 吏꾩떎" onerror="this.src='https://ssl.pstatic.net/static/movie/2012/06/dft_img108x108.png'">
    								
    								
    							</a><!-- N=a:pho.img,r:4,i:6627917 -->
    						</p>
    						<a href="/movie/bi/mi/photoView.nhn?code=167374&imageNid=6627917#tab"><strong class="tit">酉고떚��� �뜲�씠利�</strong></a><!-- N=a:pho.list,r:4,i:6627917 -->
    						<p class="tx_brief"><a href="/movie/bi/mi/photoView.nhn?code=167374&imageNid=6627917#tab">�닲寃⑥쭊 吏꾩떎</a><!-- N=a:pho.tlist,r:4,i:6627917 --></p>
    					</li>
    					
    					<li class="">
    						<p class="thmb">
    							<a href="/movie/bi/mi/photoView.nhn?code=144183&imageNid=6623789#tab">
    								<img src="https://movie-phinf.pstatic.net/20180910_31/1536541570879K0tpD_JPEG/movie_image.jpg?type=n108_108_2" width="108" height="108" alt="����엫�뒳由� 濡쒕㎤�뒪" onerror="this.src='https://ssl.pstatic.net/static/movie/2012/06/dft_img108x108.png'">
    								
    								
    							</a><!-- N=a:pho.img,r:5,i:6623789 -->
    						</p>
    						<a href="/movie/bi/mi/photoView.nhn?code=144183&imageNid=6623789#tab"><strong class="tit">28�꽭 誘몄꽦�뀈</strong></a><!-- N=a:pho.list,r:5,i:6623789 -->
    						<p class="tx_brief"><a href="/movie/bi/mi/photoView.nhn?code=144183&imageNid=6623789#tab">����엫�뒳由� 濡쒕㎤�뒪</a><!-- N=a:pho.tlist,r:5,i:6623789 --></p>
    					</li>
    					
    					<li class="last">
    						<p class="thmb">
    							<a href="/movie/bi/mi/photoView.nhn?code=168735&imageNid=6594170#tab">
    								<img src="https://movie-phinf.pstatic.net/20180104_281/1515048793973Wcl1z_JPEG/movie_image.jpg?type=n108_108_2" width="108" height="108" alt="理쒓퀬�쓽 �냼�꽕" onerror="this.src='https://ssl.pstatic.net/static/movie/2012/06/dft_img108x108.png'">
    								
    								
    							</a><!-- N=a:pho.img,r:6,i:6594170 -->
    						</p>
    						<a href="/movie/bi/mi/photoView.nhn?code=168735&imageNid=6594170#tab"><strong class="tit">�깉踰쎌쓽 �빟�냽</strong></a><!-- N=a:pho.list,r:6,i:6594170 -->
    						<p class="tx_brief"><a href="/movie/bi/mi/photoView.nhn?code=168735&imageNid=6594170#tab">理쒓퀬�쓽 �냼�꽕</a><!-- N=a:pho.tlist,r:6,i:6594170 --></p>
    					</li>
    					
    					</ul>
    				</div>
    			</div>
    			<div class="obj_section">
    				<div class="main_event">
    					<div class="notice">
    						<a href="/movie/other/gonggi.nhn" class="notice_more">怨듭���궗�빆 �뜑蹂닿린</a><!-- N=a:bnt.more -->
    						<div class="info"><a href="/movie/other/gonggi.nhn?docID=10000000000030662512"><em>[怨듭��]</em>&nbsp; YES24 �삁留� �꽌鍮꾩뒪 �젏寃� �븞�궡</a><!-- N=a:bnt.list --></div>
    						<p><span class="page_info">�젙蹂�</span>蹂� �럹�씠吏��뒗 �굹�닎湲�瑗댁뿉 理쒖쟻�솕 �릺�뼱�엳�뒿�땲�떎. <a href="http://hangeul.naver.com/font" target="_blank" class="font_inst">�굹�닎湲�瑗댁꽕移�<em class="arr"></em></a><!-- N=a:btm.nanumfont --></p>
    					</div>
    				</div>
    			</div>
    		</div>
    	</div>
    	<!-- [D] 留⑥쐞濡� 踰꾪듉 div id="content" 湲곗�� top:342px �씠�긽 -->
    	
    <div class="staticbanner" id="floatingTopAnchor" style="bottom:40px">
        <a href="#" title="留⑥쐞濡�"><img alt="留⑥쐞濡�" src="https://ssl.pstatic.net/static/movie/2012/08/btn_top.png" width="33" height="35"></a><!-- N=a:btm.top -->
    </div>
    <script type="text/javascript">
    jindo.$Fn(function () {
        var welTopAnchor = jindo.$Element('floatingTopAnchor');
        var welContent = jindo.$Element('content');
        var nTopMargin = 342 + welTopAnchor.height();
        var nMaxY;
        var nMinY = 61;
        var oFloatingLayer = new jindo.FloatingLayer(welTopAnchor).attach({
            beforeMove: function (oEvent) {
                // �긽�떒 limit
                nMaxY = welContent.height() - nTopMargin;
                if (oEvent.nY > nMaxY) {
                    oEvent.nY = nMaxY;
                }
    
                 // �븯�떒 limit
                if (oEvent.nY < nMinY) {
                    oEvent.nY = nMinY;
                }
            }
        });
    }).attach(window, 'load');
    </script>
    	<!-- //留⑥쐞濡� -->
    
    </div>
    <!-- //content -->
    
    <script type="text/template" id="RESERVE_template">
    {for index:movie in RESERVE}
    	<li class="item{=index +1}" data-id="{=movie.movieCode}" data-detail="{=movie.movieCode}" data-reserve="{=movie.movieCode}" onmouseover="jindo.$Element('reserveTooltip{=index+1}').show();" onmouseout="jindo.$Element('reserveTooltip{=index+1}').hide();">
    		<div class="obj_off tab4">
    			<a href="/movie/bi/mi/basic.nhn?code={=movie.movieCode}" onfocus="jindo.$Element('reserveTooltip{=index+1}').show();oTimer.abort();" onblur="jindo.$Element('reserveTooltip{=index+1}').hide();movieChart.restartTimer();"><span class="rank"><em>{=index +1}�쐞</em></span>
    				{if movie.adult}
    					<span class="ico_rating_19">泥��냼�뀈 �쑀�빐臾�</span>
    				{elseif movie.lastKoreanGrade != null}
    					{js movieChart.getGradeIcon(=movie.lastKoreanGrade.code)}
    				{/if}
    				<span class="mask"></span>
    				<img src="https://movie-phinf.pstatic.net{=movie.posterImageUrl}?type=f125" alt="{js movieChart.replaceDoubleQuotationForHTML(=movie.movieTitle)}" width="125" height="179" onerror="this.src='https://ssl.pstatic.net/static/movie/2012/06/dft_img125x179.png'">
    				<span class="baseplate r">
    					<span class="spr stic_rate l"><em>�삁留ㅼ쑉</em></span>
    					<strong class="l">{js movieChart.numberFont(=movie.formattedReserveRatio, 'rate')}<span class="char rate_pct"><em>%</em></span></strong>
    				</span>
    			</a><!-- N=a:run.da,r:{=index + 1},i:{=movie.movieCode} -->
    		</div>
    		<div  id="reserveTooltip{=index+1}" class="obj_con" style="display:none">
    			<div class="obj_on{js movieChart.tooltipLengthOver(=movie.movieTitle)} {if (index+1)%5 == 0}rt{/if}">
    				<div class="tooltip">
    					<span class="top"></span>
    					<p class="mv_title">{=movie.movieTitle}</p>
    					<span class="bottom"></span><span class="bottom_r"></span>
    				</div>
    			</div>
    		</div>
    	</li>
    {/for}
    </script>
    
    <script type="text/template" id="CURRENT_template">
    {for index:movie in CURRENT}
    	<li class="item{=index +1}" data-id="{=movie.movieCode}" data-detail="{=movie.movieCode}" data-reserve="{=movie.movieCode}" onmouseover="jindo.$Element('currentTooltip{=index+1}').show();" onmouseout="jindo.$Element('currentTooltip{=index+1}').hide();">
    		<div class="obj_off tab4">
    			<a href="/movie/bi/mi/basic.nhn?code={=movie.movieCode}" onfocus="jindo.$Element('currentTooltip{=index+1}').show();oTimer.abort();" onblur="jindo.$Element('currentTooltip{=index+1}').hide();movieChart.restartTimer();">
    				{if movie.adult}
    					<span class="ico_rating_19">泥��냼�뀈 �쑀�빐臾�</span>
    				{elseif movie.lastKoreanGrade != null}
    					{js movieChart.getGradeIcon(=movie.lastKoreanGrade.code)}
    				{/if}
    				<span class="mask"></span>
    				<img src="https://movie-phinf.pstatic.net{=movie.posterImageUrl}?type=f125" alt="{js movieChart.replaceDoubleQuotationForHTML(=movie.movieTitle)}" width="125" height="179" onerror="this.src='https://ssl.pstatic.net/static/movie/2012/06/dft_img125x179.png'">
    				<span class="baseplate r">
    					<span class="rank_star l"><span class="star_off"><em>蹂꾩젏 - 珥� 10�젏 以�</em></span><span class="star_on" style="width:{=movie.point*10}%"><em>{=movie.point} �젏</em></span></span>
    					<strong class="l">{js movieChart.numberFont(=movie.point, 'sc')}</strong>
    				</span>
    			</a><!-- N=a:run.da,r:{=index + 1},i:{=movie.movieCode} -->
    		</div>
    		<div id="currentTooltip{=index+1}" class="obj_con" style="display:none">
    			<div class="obj_on{js movieChart.tooltipLengthOver(=movie.movieTitle)} {if (index+1)%5 == 0}rt{/if}">
    				<div class="tooltip">
    					<span class="top"></span>
    					<p class="mv_title">{=movie.movieTitle}</p>
    					<span class="bottom"></span><span class="bottom_r"></span>
    				</div>
    			</div>
    		</div>
    	</li>
    {/for}
    </script>
    
    <script type="text/template" id="COMMING_template">
    {for index:movie in COMMING}
    	<li class="item{=index +1}" data-id="{=movie.movieCode}" data-detail="{=movie.movieCode}" data-reserve="{=movie.movieCode}" onmouseover="jindo.$Element('commingTooltip{=index+1}').show();" onmouseout="jindo.$Element('commingTooltip{=index+1}').hide();">
    		<div class="obj_off tab4">
    			<a href="/movie/bi/mi/basic.nhn?code={=movie.movieCode}" onfocus="jindo.$Element('commingTooltip{=index+1}').show();oTimer.abort();" onblur="jindo.$Element('commingTooltip{=index+1}').hide();movieChart.restartTimer();">
    				{if movie.adult}
    					<span class="ico_rating_19">泥��냼�뀈 �쑀�빐臾�</span>
    				{elseif movie.lastKoreanGrade != null}
    					{js movieChart.getGradeIcon(=movie.lastKoreanGrade.code)}
    				{/if}
    				<span class="mask"></span>
    				<img src="https://movie-phinf.pstatic.net{=movie.posterImageUrl}?type=f125" alt="{js movieChart.replaceDoubleQuotationForHTML(=movie.movieTitle)}" width="125" height="179" onerror="this.src='https://ssl.pstatic.net/static/movie/2012/06/dft_img125x179.png'">
    				<span class="baseplate r">
    					<strong class="l">{js movieChart.numberFont(=movie.openDate, 'rate')}</strong>{if movie.openDate != ''}<span class="spr stic_open l"><em>媛쒕큺</em>{/if}</span>
    				</span>
    			</a><!-- N=a:run.da,r:{=index + 1},i:{=movie.movieCode} -->
    		</div>
    		<div id="commingTooltip{=index+1}" class="obj_con" style="display:none">
    			<div class="obj_on{js movieChart.tooltipLengthOver(=movie.movieTitle)} {if (index+1)%5 == 0}rt{/if}">
    				<div class="tooltip">
    					<span class="top"></span>
    					<p class="mv_title">{=movie.movieTitle}</p>
    					<span class="bottom"></span><span class="bottom_r"></span>
    				</div>
    			</div>
    		</div>
    	</li>
    {/for}
    </script>
    
    <script type="text/template" id="POINT_template">
    {for index:movie in POINT}
    	<li class="item{=index +1}" data-id="{=movie.movieCode}" data-detail="{=movie.movieCode}" data-reserve="{=movie.movieCode}" onmouseover="jindo.$Element('pointTooltip{=index+1}').show();" onmouseout="jindo.$Element('pointTooltip{=index+1}').hide();">
    		<div class="obj_off tab4">
    			<a href="/movie/bi/mi/basic.nhn?code={=movie.movieCode}" onfocus="jindo.$Element('pointTooltip{=index+1}').show();oTimer.abort();" onblur="jindo.$Element('pointTooltip{=index+1}').hide();movieChart.restartTimer();"><span class="rank"><em>{=index +1}�쐞</em></span>
    				{if movie.adult}
    					<span class="ico_rating_19">泥��냼�뀈 �쑀�빐臾�</span>
    				{elseif movie.lastKoreanGrade != null}
    					{js movieChart.getGradeIcon(=movie.lastKoreanGrade.code)}
    				{/if}
    				<span class="mask"></span>
    				<img src="https://movie-phinf.pstatic.net{=movie.posterImageUrl}?type=f125" alt="{js movieChart.replaceDoubleQuotationForHTML(=movie.movieTitle)}" width="125" height="179" onerror="this.src='https://ssl.pstatic.net/static/movie/2012/06/dft_img125x179.png'">
    				<span class="baseplate r">
    					<span class="rank_star l"><span class="star_off"><em>蹂꾩젏 - 珥� 10�젏 以�</em></span><span class="star_on" style="width:{=movie.point*10}%"><em>{=movie.point} �젏</em></span></span>
    					<strong class="l">{js movieChart.numberFont(=movie.point, 'sc')}</strong>
    				</span>
    			</a><!-- N=a:run.da,r:{=index + 1},i:{=movie.movieCode} -->
    		</div>
    		<div id="pointTooltip{=index+1}" class="obj_con" style="display:none">
    			<div class="obj_on{js movieChart.tooltipLengthOver(=movie.movieTitle)} {if (index+1)%5 == 0}rt{/if}">
    				<div class="tooltip">
    					<span class="top"></span>
    					<p class="mv_title">{=movie.movieTitle}</p>
    					<span class="bottom"></span><span class="bottom_r"></span>
    				</div>
    			</div>
    		</div>
    	</li>
    {/for}
    </script>
    
    <script type="text/template" id="BOXOFFICE_template">
    {for index:movie in BOXOFFICE}
    	<li class="item{=index +1}" data-id="{=movie.movieCode}" data-detail="{=movie.movieCode}" data-reserve="{=movie.movieCode}" onmouseover="jindo.$Element('boxofficeTooltip{=index+1}').show();" onmouseout="jindo.$Element('boxofficeTooltip{=index+1}').hide();">
    		<div class="obj_off tab4">
    			<a href="/movie/bi/mi/basic.nhn?code={=movie.movieCode}" onfocus="jindo.$Element('boxofficeTooltip{=index+1}').show();oTimer.abort();" onblur="jindo.$Element('boxofficeTooltip{=index+1}').hide();movieChart.restartTimer();"><span class="rank"><em>{=index +1}�쐞</em></span>
    				{if movie.adult}
    					<span class="ico_rating_19">泥��냼�뀈 �쑀�빐臾�</span>
    				{elseif movie.lastKoreanGrade != null}
    					{js movieChart.getGradeIcon(=movie.lastKoreanGrade.code)}
    				{/if}
    				<span class="mask"></span>
    				<img src="https://movie-phinf.pstatic.net{=movie.posterImageUrl}?type=f125" alt="{js movieChart.replaceDoubleQuotationForHTML(=movie.movieTitle)}" width="125" height="179" onerror="this.src='https://ssl.pstatic.net/static/movie/2012/06/dft_img125x179.png'">
    				<span class="baseplate r">
    					<span class="spr stic_box l"><em>二쇰쭚愿�媛�</em></span>
    					<strong class="l">{js movieChart.numberFont(=movie.formattedWeekendAudience, 'cnt')}<span class="char cnt_per"><em>紐�</em></span></strong>
    				</span>
    			</a><!-- N=a:run.da,r:{=index + 1},i:{=movie.movieCode} -->
    		</div>
    		<div id="boxofficeTooltip{=index+1}" class="obj_con" style="display:none">
    			<div class="obj_on{js movieChart.tooltipLengthOver(=movie.movieTitle)} {if (index+1)%5 == 0}rt{/if}">
    				<div class="tooltip">
    					<span class="top"></span>
    					<p class="mv_title">{=movie.movieTitle}</p>
    					<span class="bottom"></span><span class="bottom_r"></span>
    				</div>
    			<div>
    		</div>
    	</li>
    {/for}
    </script>
    
    <script type="text/template" id="DOWNLOAD_template">
    {if DOWNLOAD ==  ""}
    	<li class="error_area">
             <div class="error_msg"></div>
        </li>
    {else}
    	{for index:movie in DOWNLOAD}
    		<li class="item{=index +1}" data-id="{=movie.movieCode}" data-detail="{=movie.movieCode}" data-reserve="{=movie.movieCode}" onmouseover="jindo.$Element('downloadTooltip{=index+1}').show();" onmouseout="jindo.$Element('downloadTooltip{=index+1}').hide();">
    			<div class="obj_off tab4">
    				<a href="http://nstore.naver.com/tvstore/detail.nhn?mcode={=movie.movieCode}" target="_blank"  onfocus="jindo.$Element('downloadTooltip{=index+1}').show();oTimer.abort();" onblur="jindo.$Element('downloadTooltip{=index+1}').hide();movieChart.restartTimer();"><span class="rank"><em>{=index +1}�쐞</em></span>
    					{if movie.adult}
    						<span class="ico_rating_19">泥��냼�뀈 �쑀�빐臾�</span>
    					{elseif movie.lastKoreanGrade != null}
    						{js movieChart.getGradeIcon(=movie.lastKoreanGrade.code)}
    					{/if}
    					<span class="mask"></span> {if movie.salePossibleYn == true}<span class="purchase">援щℓ</span>{/if} {if movie.lendingPossibleYn == true}<span class="rental">����뿬</span>{/if}
    					<img src="https://movie-phinf.pstatic.net{=movie.posterImageUrl}?type=f125" alt="{js movieChart.replaceDoubleQuotationForHTML(=movie.movieTitle)}" width="125" height="179" onerror="this.src='https://ssl.pstatic.net/static/movie/2012/06/dft_img125x179.png'">
    					<span class="baseplate r">
    						<span class="spr stic_down l"><em>�뙋留ㅼ쑉</em></span>
    						<strong class="l">{js movieChart.numberFont(=movie.formattedSaleRate, 'rate')}<span class="char rate_pct"><em>%</em></span></strong>
    					</span>
    				</a><!-- N=a:run.da,r:{=index + 1},i:{=movie.movieCode} -->
    			</div>
    			<div id="downloadTooltip{=index+1}" class="obj_con" style="display:none">
    				<div class="obj_on{js movieChart.tooltipLengthOver(=movie.movieTitle)} {if (index+1)%5 == 0}rt{/if}">
    					<div class="tooltip">
    						<span class="top"></span>
    						<p class="mv_title">{=movie.movieTitle}</p>
    						<span class="bottom"></span><span class="bottom_r"></span>
    					</div>
    				</div>
    			</div>
    		</li>
    	{/for}
    {/if}
    </script>
    
    
    <script type="text/javascript">
    
    
    
    
    
    var flickContents = new Array(6);
    
    
    var htInfo = jindo.m.getDeviceInfo(); 
    var bUseCss3d = jindo.m._isUseCss3d() || (htInfo.galaxyS2 && (htInfo.version >= "4.0.3"));
    var oFlicking = new jindo.m.CircularFlicking(jindo.$('mflick'),{
    	nDuration : 100,
    	bHorizontal : true,
        sClassPrefix : 'flick-',
        nFlickThreshold : 40,
        nTotalContents : 6,
        bUseCss3d : bUseCss3d
    }).attach({
    
    	// ����씠癒� �젙吏� 諛� 硫붾돱 �븯�씠�씪�씠�똿
    	'beforeFlicking' : function(oCustomEvt) {
    		oTimer.abort();
    
    		var index = oCustomEvt.nContentIndex;
    		var nextIndex = movieChart.getNextIndex(index);
    		var previousIndex = movieChart.getPreviousIndex(index);
    
    		if (oCustomEvt.bLeft) {
    			movieChart.setMenuHighlighting(nextIndex);
    		} else {
    			movieChart.setMenuHighlighting(previousIndex);
    		}
    		
    		
    		this.getPanelElement().removeClass('blind');
    		this.getRightPanelElement().removeClass('blind');
    		this.getLeftPanelElement().removeClass('blind');
    	},
    	
    	// �뵆由ы궧泥섎━ 諛� ����씠癒� �옱�떆�옉
    	'afterFlicking' : function(oCustomEvt){
    		
    		if (oCustomEvt.bLeft) {
    			var type = movieChart.movieChartTab[oCustomEvt.nContentRightIndex];
    			
    			// �뵆由ы궧 ����옣蹂��닔�뿉 �씠誘� �뜲�씠�꽣媛� �엳�떎硫� ����옣蹂��닔 �씠�슜, �뾾�쑝硫� Ajax Call.
    			if (flickContents[oCustomEvt.nContentRightIndex]) {
    				movieChart.movieChartJsonCallBack(null, flickContents[oCustomEvt.nContentRightIndex], type, oCustomEvt.nContentRightIndex, oCustomEvt.nPanelRightIndex);
    			} else {
    				movieChart.ajaxCall(movieChart.movieChartJsonUrl, type, oCustomEvt.nContentRightIndex, oCustomEvt.nPanelRightIndex);
    			}
    			
    		} else {
    			var type = movieChart.movieChartTab[oCustomEvt.nContentLeftIndex];
    			
    			// �뵆由ы궧 ����옣蹂��닔�뿉 �씠誘� �뜲�씠�꽣媛� �엳�떎硫� ����옣蹂��닔 �씠�슜, �뾾�쑝硫� Ajax Call.
    			if (flickContents[oCustomEvt.nContentLeftIndex]) {
    				movieChart.movieChartJsonCallBack(null, flickContents[oCustomEvt.nContentLeftIndex], type, oCustomEvt.nContentLeftIndex, oCustomEvt.nPanelLeftIndex);
    			} else {
    				movieChart.ajaxCall(movieChart.movieChartJsonUrl, type, oCustomEvt.nContentLeftIndex, oCustomEvt.nPanelLeftIndex);
    			}
    		}
    
    		
    		this.getRightPanelElement().addClass('blind');
    		this.getLeftPanelElement().addClass('blind');
    		
    		movieChart.restartTimer();
    	}
    });
    
    //[MOVIEOP-5993] [紐⑤컮�씪�쎒] Android 怨듯넻�뙎湲� �씠�쟾/�떎�쓬 踰꾪듉 �겢由��떆 �룷而ㅼ떛 �쑀吏�(PC �솚寃쎌뿉�꽌�뒗 Flicking �릺吏� �븡�룄濡� �닔�젙.)
    var osInfo = jindo.$Agent().os();
    if(osInfo.win || osInfo.mac || osInfo.linux) {
    	oFlicking.attach({
    		'touchStart' : function(oCustomEvt){
    			oCustomEvt.stop();
    			}
    	});
    }
    
    
    var oTimer = new jindo.Timer();
    
    
    var movieChart = {
    		
    		movieChartDefaultJsonUrl : "/movieChartDefaultJson.nhn",
    		movieChartJsonUrl : "/movieChartJson.nhn",
    		
    		movieChartTab : new Array("RESERVE", "CURRENT", "COMMING", "POINT", "BOXOFFICE", "DOWNLOAD"),
    		movieChartAllViewUrl : new Array(
    				"/movie/running/current.nhn?order=reserve",
    				"/movie/running/current.nhn",
    				"/movie/running/premovie.nhn?order=reserve",
    				"/movie/running/current.nhn?order=point",
    				"/movie/sdb/rank/rboxoffice.nhn",
    				"http://nstore.naver.com/movie/top100List.nhn?rankingTypeCode=PC_D"
    		),
    
    		// 媛쒕큺�삁�젙�옉 紐⑸줉�쓽 留덉��留� �쁺�솕�쓽 �긽�쁺愿��씠 �뾾�떎硫�, �삁留ㅼ쑉�닚 媛쒕큺�삁�젙�옉�뿉�꽌 �뜲�씠�꽣媛� 遺�議깊빐�꽌 �긽�쁺愿��씠 �뾾�뒗 �뜲�씠�꽣�룄 梨꾩썙�꽔��� 寃쎌슦�씠湲� �븣臾몄뿉 �뜑蹂닿린 留곹겕 �젣怨듯븯吏� �븡�쓬
    		hasCommingMovieAllViewUrl : true,
    		
    		// domready�떆 �닔�뻾
    		init : function() {
    			movieChart.ajaxCall(movieChart.movieChartJsonUrl, movieChart.movieChartTab[0], 0, 0);
    			movieChart.setMenuHighlighting(0);
    			movieChart.startTimer();
    		},
    		
    		// load�떆 �닔�뻾
    		load : function() {
    			movieChart.ajaxCall(movieChart.movieChartJsonUrl, movieChart.movieChartTab[1], 1, 1);
    			movieChart.ajaxCall(movieChart.movieChartJsonUrl, movieChart.movieChartTab[movieChart.movieChartTab.length-1], movieChart.movieChartTab.length-1, 2);
    		},
    		
    		// ����씠癒� �옱�떆�옉
    		restartTimer : function() {
    			
    			if (oTimer.isRunning = true) {
    				oTimer.abort();
    			}
    			
    			oTimer = new jindo.Timer();
    			movieChart.startTimer();
    		},
    		
    		// ����씠癒� �떆�옉
    		startTimer : function() {
    			oTimer.start( function() {
    				oFlicking.moveNext();
    				return true;  
    			}, 7000);
    		},
    		
    		// JSON API �샇異�
    		ajaxCall : function(url, type, index, targetAreaIndex) {
    			var ajax = new jindo.$Ajax(url, { 
    				method : "GET",
    				onload : function(response){
    					if (url == movieChart.movieChartDefaultJsonUrl) {
    						// ����꽭�똿 
    						movieChart.movieChartDefaultJsonCallBack(response, null, index);
    					} else {
    						// 媛쒕퀎�꽭�똿
    						movieChart.movieChartJsonCallBack(response, null, type, index, targetAreaIndex);
    					}
    				}
    			});
    			ajax.header("ajax", "true");
    		    ajax.request({"type":type});
    		},
    		
    		// 臾대퉬李⑦듃 ����꽭�똿 CallBack �븿�닔
    		movieChartDefaultJsonCallBack : function(response, movieChartList, index) {
    			
    			if (movieChartList == null) {
    				var jsonData = response.json();
    				movieChartList = jsonData.movieChartList;
    			}
    			
    			var nextIndex = movieChart.getNextIndex(index);
    			var previousIndex = movieChart.getPreviousIndex(index);
    
    			oFlicking.setContentIndex(index);
    			oFlicking.getPanelElement().html(jindo.$Template(movieChart.movieChartTab[index] + "_template").process(movieChartList[0]));
    			oFlicking.getRightPanelElement().html(jindo.$Template(movieChart.movieChartTab[nextIndex] + "_template").process(movieChartList[1]));
    			oFlicking.getLeftPanelElement().html(jindo.$Template(movieChart.movieChartTab[previousIndex] + "_template").process(movieChartList[2]));
    
    			flickContents[index] = movieChartList[0];
    			flickContents[nextIndex] = movieChartList[1];
    			flickContents[previousIndex] = movieChartList[2];
    			
    			if (index == 2) {
    				this.setHasCommingMovieAllViewUrl(movieChartList[0]);
    				movieChart.setMenuHighlighting(index);
    			}
    			
    			
    			oFlicking.getPanelElement().removeClass('blind');
    			oFlicking.getRightPanelElement().addClass('blind');
    			oFlicking.getLeftPanelElement().addClass('blind');
    		},
    		
    		// �뵆由ы궧 諛� 醫뚯슦 �꽕鍮꾧쾶�씠�뀡 踰꾪듉 �겢由��뿉 �뵲瑜� CallBack �븿�닔
    		movieChartJsonCallBack : function(response, movieChartList, type, index, targetAreaIndex) {
    			
    			if (movieChartList == null) {
    				var jsonData = response.json();
    				movieChartList = jsonData.movieChartList;
    			}
    			
    			jindo.$Element("flick" + targetAreaIndex).html(jindo.$Template(type + "_template").process(movieChartList));
    			flickContents[index] = movieChartList;
    			
    			if (index == 2) {
    				this.setHasCommingMovieAllViewUrl(movieChartList);
    			}
    			
    			
    			oFlicking.getPanelElement().removeClass('blind');
    			oFlicking.getRightPanelElement().addClass('blind');
    			oFlicking.getLeftPanelElement().addClass('blind');
    		},
    		
    		// 臾대퉬李⑦듃 ����꽭�똿 �샇異�
    		fullSettingMovieChart : function(index) {
    			movieChart.setMenuHighlighting(index);
    			
    			var nextIndex = movieChart.getNextIndex(index);
    			var previousIndex = movieChart.getPreviousIndex(index);
    
    			// ����옣蹂��닔�뿉 �뜲�씠�꽣媛� �씠誘� �엳�떎硫� ����옣蹂��닔 �씠�슜, �븘�땲硫� Ajax Call.
    			if (flickContents[index] && flickContents[nextIndex] && flickContents[previousIndex]) {
    				var movieChartList = new Array(flickContents[index], flickContents[nextIndex], flickContents[previousIndex]);
    				movieChart.movieChartDefaultJsonCallBack(null, movieChartList, index);
    			} else {
    				movieChart.ajaxCall(movieChart.movieChartDefaultJsonUrl, movieChart.movieChartTab[index], index);
    			}
    		},
    		
    		// 硫붾돱 �븯�씠�씪�씠�똿 泥섎━
    		setMenuHighlighting : function(index) {
    			
    			// �꺆硫붾돱 �븯�씠�씪�씠�똿
    			for (i=0; i<movieChart.movieChartTab.length; i++) {
    				jindo.$Element(movieChart.movieChartTab[i] + "_tab").removeClass("on");
    			}
    			jindo.$Element(movieChart.movieChartTab[index] + "_tab").addClass("on");
    			
    			// �쟾泥대낫湲� URL �꽭�똿
    			jindo.$("movieChartAllView").href = movieChart.movieChartAllViewUrl[index];
    			
    			// [�떎�슫濡쒕뱶�닚]�씪 寃쎌슦, �쟾泥대낫湲� �븘�씠肄섏씠 �떎瑜대떎. (�깉李�)
    			if (movieChart.movieChartTab[index] == "DOWNLOAD") {
    				jindo.$Element(jindo.$$.getSingle(".all_view_go")).show();
    				jindo.$("movieChartAllView").target = "_blank";
    				jindo.$Element(jindo.$$.getSingle(".all_view_go")).addClass("dwn");
    			}
    			// [媛쒕큺�삁�젙�옉]�씪 寃쎌슦 �삁留ㅼ쑉�닚 媛쒕큺�삁�젙�옉�뿉�꽌 �뜲�씠�꽣媛� 遺�議깊빐�꽌 梨꾩썙�꽔��� 寃쎌슦�씠硫� �쟾泥� 蹂닿린 留곹겕瑜� 蹂댁뿬二쇱�� �븡�뒗�떎. 
    			else if (movieChart.movieChartTab[index] == "COMMING" && !this.hasCommingMovieAllViewUrl) {
    				jindo.$Element(jindo.$$.getSingle(".all_view_go")).hide();
    			}
    			else {
    				jindo.$Element(jindo.$$.getSingle(".all_view_go")).show();
    				jindo.$("movieChartAllView").target = "_self";
    				jindo.$Element(jindo.$$.getSingle(".all_view_go")).removeClass("dwn");
    			}
    			
    		},		
    		
    		// �몢媛쒖쓽 �룷�넗�씤�봽�씪�룄硫붿씤�쓣 遺꾩궛�빐�꽌 �젣怨� 
    		getPhotoInfraImageDomain : function() {
    			var photoInfraImageDomains = new Array("http://movie.phinf.naver.net", "http://movie2.phinf.naver.net");
    			return photoInfraImageDomains[Math.floor((Math.random()*(2)))];
    		},
    		
    		// �뵲�샂�몴 escape 泥섎━
    		replaceDoubleQuotationForHTML : function(title) {
    			if (title == null) {
    				return null;
    			}
    
    			var result = "";
    			for (i=0; i<title.length; i++) {
    				var tmpChar = title.charAt(i);
    				if (tmpChar == "\"") {
    					result += "&quot;";
    				} else if (tmpChar == "\n" || tmpChar == "\r") {
    					result += "";
    				} else {
    					result += tmpChar;
    				}
    			}
    			return result;
    		},
    		
    		// �씠誘몄���룿�듃 �젙�쓽
    		numberFont : function(value, charName) {
    			var result = "";
    
    			if (value == 'undefined') {
    				value = "0";
    			}
    			
    			for (i=0; i<value.length; i++) {
    				var tmpChar = value.charAt(i);
    
    				result += '<span class="char ' + charName + '_';
    				if (tmpChar == ".") {
    					result += "dot";
    				} else if (tmpChar == ",") {
    					result += "comma";
    				} else {
    					result += "num" + tmpChar;
    				}
    				result += '"><em>' + tmpChar + '</em></span>';
    			}
    
    			return result;
    		},
    		
    		// �룷�뒪�꽣 �댋�똻 湲몄씠�젣�븳 �솗�씤
    		tooltipLengthOver : function(value) {
    			if (value != null && value.length > 18) {
    				return " br";
    			}
    			return "";
    		},
    		
    		// �뵆由ы궧�쁺�뿭 �떎�쓬 index瑜� �뼸�뒗�떎.
    		getNextIndex : function(index) {
    			var nextIndex = index + 1;
    			if (nextIndex > movieChart.movieChartTab.length - 1) {
    				nextIndex = 0;
    			}
    			return nextIndex;
    		},
    		
    		// �뵆由ы궧�쁺�뿭 �씠�쟾 index瑜� �뼸�뒗�떎.
    		getPreviousIndex : function(index) {
    			var previousIndex = index - 1;
    			if (previousIndex < 0) {
    				previousIndex = movieChart.movieChartTab.length - 1;
    			}
    			return previousIndex;
    		}, 
    		
    		// 媛쒕큺�삁�젙�옉�쓽 �쟾泥대낫湲� 踰꾪듉 �끂異� �뿬遺�
    		setHasCommingMovieAllViewUrl : function(movieList) {
    			if (movieList.COMMING[movieList.COMMING.length - 1].theater == 0) {
    				this.hasCommingMovieAllViewUrl = false;	
    			} else {
    				this.hasCommingMovieAllViewUrl = true;	
    			}
    		},
    
    		// �벑湲� �븘�씠肄� html�쓣 �뼸�뒗�떎.
    		getGradeIcon : function(gradeCode) {
    			var result = '<span class="ico_rating_';
    			if (gradeCode == "1001001") {
    				result += 'all">�쟾泥� 愿��엺媛�'
    			} else if (gradeCode == "1001002") {
    				result += '12">12�꽭 愿��엺媛�'
    			} else if (gradeCode == "1001003") {
    				result += '15">15�꽭 愿��엺媛�'
    			} else if (gradeCode == "1001004") {
    				result += '18">泥��냼�뀈 愿��엺遺덇��'
    			} else if (gradeCode == "1001005") {
    				result += 'restricted">�젣�븳 �긽�쁺媛�'
    			} else {
    				return "";
    			}
    
    			result += '</span>'	;
    
    			return result;
    		}
    };
    
    
    var HomeMovieReviewAccordion = jindo.$Class({
    	$init : function(sClassName) {
    		_self = this;
    		this._wel = jindo.$Element("movieReview");
    		this._welList = this._wel.query ("ul.lst_con." + sClassName);
    		
    		this._wel.delegate(
    				"mouseover",
    				"._select_title",
    				jindo.$Fn(this._onMouseOverItem, this).bind()
    		);
    		
    		jindo.$A(jindo.$ElementList('._select_title_anchor').$value()).forEach(function(element, index, array) {
    			jindo.$Fn(_self._onMouseOverItem, _self).attach(element, "focus");
    		});
    	},
    	
    	_onMouseOverItem : function (we) {
    		we.stopDefault();
    		var nIndex = Number(jindo.$Element(we.element).data('index'));
    		
    		this.openReview(nIndex);
    	},
    	
    	openReview : function (nIndex) {
    		var aEls = this._welList.queryAll("li ! li");
    		
    		// �빐�떦�븯�뒗 �빆紐⑸쭔 <li class="on">
    		for (var i = 0; i < aEls.length; i++) {
    			aEls[i].cssClass("on", nIndex == i);
    		}
    	},
    	
    	showRandomMovie : function () {
    		var randNo = Math.floor(4 * Math.random());
    		this.openReview(randNo);
    	}
    });
    
    
    
    var oFirstHomeMovieReviewAccordion = new HomeMovieReviewAccordion("first");
    
    
    jindo.$Fn(function() {oFirstHomeMovieReviewAccordion.showRandomMovie();}).attach(document, "domready");
    
    jindo.$Fn(function() {movieChart.init();}).attach(document, "domready");
    jindo.$Fn(function() {movieChart.load();}).attach(window, "load");
    jindo.$Fn(function(evt){evt.stop(); oFlicking.movePrev();}, this).attach(jindo.$("flick_prev"),"click");
    jindo.$Fn(function(evt){evt.stop(); oFlicking.moveNext();} ,this).attach(jindo.$("flick_next"),"click");
    
    var nsc = "movie.home";
    </script>
    	</div>
    	<!-- //container -->
    	
    	<!-- footer -->
    	
    
    
    
    <div id="footer">
    	<div class="in_footer">
    		<div class="foot_con">
    				<ul>
    					<li class="first"><a href="http://www.naver.com/rules/service.html" target="rules">�씠�슜�빟愿�</a><!-- N=a:fot.agreement --></li>		
    					<li><a href="http://www.naver.com/rules/privacy.html" target="rules"><strong>媛쒖씤�젙蹂댁쿂由щ갑移�</strong></a><!-- N=a:fot.privacy --></li>
    					<li><a href="http://www.naver.com/rules/disclaimer.html" target="rules">梨낆엫�쓽 �븳怨꾩�� 踰뺤쟻怨좎��</a><!-- N=a:fot.disclaimer --></li>		
    					<li><a href="https://help.naver.com/support/service/main.nhn?serviceNo=800" target="customer">�쁺�솕 怨좉컼�꽱�꽣</a><!-- N=a:fot.help --></li>
    				</ul>
    				<p class="info">蹂� 肄섑뀗痢좎쓽 ����옉沅뚯�� ����옉沅뚯옄 �삉�뒗 �젣怨듭쿂�뿉 �엳�쑝硫�, �씠瑜� 臾대떒 �씠�슜�븯�뒗 寃쎌슦 ����옉沅뚮쾿 �벑�뿉 �뵲�씪 踰뺤쟻 梨낆엫�쓣 吏� �닔 �엳�뒿�땲�떎.</p>
    				<p class="info">
    					�궗�뾽�옄�벑濡앸쾲�샇 : 220-81-62517<span>�넻�떊�뙋留ㅼ뾽 �떊怨좊쾲�샇</span> : 寃쎄린�꽦�궓 �젣 2006 - 692�샇<span>����몴�씠�궗 : �븳�꽦�닕</span><span><a href="http://www.ftc.go.kr/info/bizinfo/communicationList.jsp">�궗�뾽�옄�벑濡앹젙蹂� �솗�씤</a><!-- N=a:fot.bizinfo --></span><br>
    					二쇱냼 : 寃쎄린�룄 �꽦�궓�떆 遺꾨떦援� 遺덉젙濡� 6 �꽕�씠踰� 洹몃┛�뙥�넗由� <span>����몴�쟾�솕 : 1588-3820</span>
    				</p> 
    				<address>
    					<a href="http://www.navercorp.com/" target="_blank" class="logo"><img src="https://ssl.pstatic.net/static/movie/2013/07/logo_naver.png" width="63" height="11" alt="NAVER"></a><!-- N=a:fot.nhn -->
    					<em>Copyright 짤</em>
    					<a href="http://www.navercorp.com/" target="_blank">NAVER Corp.</a><!-- N=a:fot.corp -->
    					<span>All Rights Reserved.</span>
    				</address>
    		</div>
    	</div>
    </div>
    
    
    
    
    
    
    
    
    <script type="text/javascript">
    
    if (false) {
    	var alertType = "NONE";
    	var koreanTitle = "";
    	var movieCode = "0";
    	var userReserveCount = "0";
    	var todayDatetime = "20181112145149";
    	var endDatetimeAfterTwoDays = "00000000000000";
    	
    	
    	if (movieCode > 0) {
    		openWriteActualPointAlert (alertType, koreanTitle, movieCode, userReserveCount, todayDatetime, endDatetimeAfterTwoDays);
    	}
    }
    
    function openWriteActualPointAlert (alertType, koreanTitle, movieCode, count, today, endDate) {
    	if (alertType == "ONE") {
    		setCookieLastUserReserveDate(today, endDate);
    		if (confirm("愿��엺�븯�떊 " + koreanTitle + "�뿉\n�룊�젏 �벑濡� �떆 �꽕�씠踰꾪럹�씠 �룷�씤�듃 500�썝 �쟻由�!\n吏�湲� �룊�젏�벐湲� 硫붾돱濡� �씠�룞�븯�떆寃좎뒿�땲源�?")) {
    			top.location.href = "https://movie.naver.com/movie/bi/mi/point.nhn?code=" + movieCode;
    		}
    	} else if (alertType == "MORE") {
    		setCookieLastUserReserveDate(today, endDate);
    		if (confirm("愿��엺�븯�떊 �옉�뭹�뿉 �룊�젏�쓣 �벑濡앺빐二쇱꽭�슂\n�옉�뭹�떦 �꽕�씠踰꾪럹�씠 �룷�씤�듃 500�썝�뵫 �쟻由�!\n�룊�젏 誘몃벑濡앹옉 由ъ뒪�듃瑜� �솗�씤�븯�떆寃좎뒿�땲源�?")) {
    			top.location.href = "http://ticket.movie.naver.com/Order/OverdueList.aspx";
    		}
    	}
    }
    
    function setCookieLastUserReserveDate(today, endDate) {
    	var cookieForNotOpenActualPointPopup = jindo.$Cookie();
    	
    	
    	cookieForNotOpenActualPointPopup.remove("lastUserReserveDatetime");
    	cookieForNotOpenActualPointPopup.remove("lastUserReserveCheckDatetime");
    	
    	cookieForNotOpenActualPointPopup.set("lastUserReserveDatetime", endDate, 9999, "movie.naver.com");
    	cookieForNotOpenActualPointPopup.set("lastUserReserveCheckDatetime", today, 9999, "movie.naver.com");
    }
    
    </script>
    
    
    
    
    
    
    
    
    <script type="text/javascript">
    	
    		
    		
    		
    		
    			var alertMessage = "吏��썝�릺吏� �븡�뒗 釉뚮씪�슦���濡� �꽌鍮꾩뒪 �씠�슜�뿉 �젣�븳�씠 �엳�뒿�땲�떎.";
    		
    	
    
    	function getBrowser() {
    		var ua = navigator.userAgent;
    		if (/NAVER/.test(ua)) {
    			return "NAVER_APP";
    		} else if (/IEMobile/.test(ua)) {
    			return "INTERNET_EXPLORER_MOBILE";
    		} else if (/MSIE/.test(ua) || /Trident/.test(ua)) {
    			return "INTERNET_EXPLORER";
    		} else if (/Firefox/.test(ua)) {
    			return "FIREFOX";
    		} else if (/Opera\//.test(ua) || /OPR\//.test(ua)) {
    			return "OPERA";
    		}  else if (/Swing\//.test(ua)) {
    			return "SWING";
    		} else if (/Chrome\//.test(ua) || /CriOS\//.test(ua)) {
    			return "CHROME";
    		} else if (/BAND\//.test(ua)) {
    			return "BAND_APP";
    		} else if (/FBAN\/FBIOS/.test(ua)) {
    			return "FACEBOOK_APP";
    		} else if (/Twitter/.test(ua)) {
    			return "TWITTER_APP";
    		} else if (/KAKAOTALK/.test(ua)) {
    			return "KAKAOTALK_APP";
    		} else if (/Android/.test(ua) && /Safari/.test(ua)) {
    			return "ANDROID_INTERNET_APP";
    		} else if (/Safari/.test(ua)) {
    			return "SAFARI";
    		}
    
    		return "";
    	}
    
    	if (getBrowser() === "UNKNOWN" && jindo.$Cookie().get("notSupportBrowserAlert") != 'true') {
    		alert(alertMessage);
    		jindo.$Cookie().set("notSupportBrowserAlert", "true", "9999", "movie.naver.com");
    	}
    
    
    </script>
    
    
    	<!-- //footer -->
    </div>
    <script type="text/javascript">
    
    jindo.$Fn(function (we) {
    
    	// �긽�떒 寃��깋�쁺�뿭
    	var oSearch = new nhn.movie.Search({
    		area : "jSearchArea",
    		autosearch : "https://auto-movie.naver.com/ac?q_enc=UTF-8&st=1&r_lt=1&n_ext=1&t_koreng=1&r_format=json&r_enc=UTF-8&r_unicode=0&r_escape=1&q=",
    		movelink : "/movie/bi/mi/basic.nhn?code=",
    		peoplelink : "/movie/bi/pi/basic.nhn?code="
    	});
    
        // 醫뚯륫 LNB
        var oLNB = new nhn.movie.LNB();
    	if( typeof oViewMode != "undefined") {
    		oViewMode.attach('change', jindo.$Fn(oLNB.update, oLNB).bind());
    	}
    
        //�쁺�솕寃��깋 寃곌낵�뿉�꽌 �룷而ㅼ뒪 �븘�썐�맆 寃쎌슦, 寃��깋 寃곌낵瑜� 吏��슦�룄濡� 蹂�寃�.
        jindo.$Element("lnb_gonaver").attach("focus",function(e){
        	
        	jindo.$Element('search_placeholder').attr({
        		"style" : "display: inline;"
        	})
        	jindo.$Element('ipt_tx_srch').$value().value="";
        	if(jindo.$Element("jAutoComplate") != null){
        		jindo.$Element("jAutoComplate").hide();
        	}
        });
    }).attach(document, 'domready');
    
    //LCS
    jindo.$Fn(function() {
        try{ lcs_do(); } catch(e){}
    }).attach(window, "pageshow");
    
    
    </script>
    <script type="text/javascript">
    	//nClick 珥덇린�솕 �쁺�뿭
    	//�겢由�濡쒓렇 吏묎퀎 肄붾뱶 異붽��
    	var ccsrv="cc.naver.com";
    	var nclk_evt = 1;
    	
    	nclk_do();
    	//nClick 珥덇린�솕 �쁺�뿭 �걹
    </script>
    </body>
    </html>
    

### <font color='blue'> UNIX / LINUX Basics

#### 표준 스트림
>  기본적으로 표준 입력은 키보드에서의 입력, 표준 출력은 콘솔 화면으로 출력
<br/>
<br/> - 표준 출력 리다이렉트 : 명령어 실행 결과(표준 출력)을 파일에 저장하기
<br/>  &nbsp;&nbsp; \$ 명령어 > 경로
<br/>
<br/> - 표준 입력 리다이렉트 : 파일의 내용을 명령어의 표준 입력으로 지정하기
<br/>  &nbsp;&nbsp; \$ 명령어 < 경로


```python
% ls | grep .ipynb
```

    'grep'은(는) 내부 또는 외부 명령, 실행할 수 있는 프로그램, 또는
    배치 파일이 아닙니다.
    


```python
! pip freeze > packages.txt
```


```python
# ! cat packages.txt
! type packages.txt
```

    absl-py==0.2.2
    alabaster==0.7.10
    alembic==1.0.0
    anaconda-client==1.6.5
    anaconda-navigator==1.6.9
    anaconda-project==0.8.0
    appdirs==1.4.3
    asn1crypto==0.22.0
    astor==0.7.1
    astroid==1.5.3
    astropy==2.0.2
    attrs==18.2.0
    Automat==0.7.0
    azure-cognitiveservices-nspkg==2.0.0
    azure-cognitiveservices-vision-customvision==0.3.0
    azure-cognitiveservices-vision-nspkg==2.0.0
    azure-common==1.1.14
    azure-nspkg==2.0.0
    babel==2.5.0
    backports.shutil-get-terminal-size==1.0.0
    banal==0.3.7
    beautifulsoup4==4.6.0
    bitarray==0.8.1
    bkcharts==0.2
    blaze==0.11.3
    bleach==1.5.0
    bokeh==0.12.10
    boto==2.48.0
    boto3==1.9.40
    botocore==1.12.40
    Bottleneck==1.2.1
    branca==0.2.0
    bz2file==0.98
    CacheControl==0.12.3
    certifi==2018.10.15
    cffi==1.10.0
    chardet==3.0.4
    click==6.7
    cloudpickle==0.4.0
    clyent==1.2.2
    cognitive-face==1.4.2
    colorama==0.3.9
    comtypes==1.1.2
    conda==4.5.11
    conda-build==3.0.27
    conda-verify==2.0.0
    constantly==15.1.0
    contextlib2==0.5.5
    cryptography==2.0.3
    cssselect==1.0.3
    cycler==0.10.0
    Cython==0.26.1
    cytoolz==0.8.2
    dask==0.15.3
    dataset==1.1.0
    datashape==0.5.4
    decorator==4.1.2
    distlib==0.2.5
    distributed==1.19.1
    docutils==0.14
    entrypoints==0.2.3
    et-xmlfile==1.0.1
    fastcache==1.0.2
    filelock==2.0.12
    Flask==0.12.2
    Flask-Cors==3.0.3
    folium==0.5.0
    gast==0.2.0
    gensim==3.6.0
    gevent==1.2.2
    glob2==0.5
    googlemaps==2.5.1
    greenlet==0.4.12
    grpcio==1.13.0
    h5py==2.7.0
    heapdict==1.0.0
    html5lib==0.9999999
    hyperlink==18.0.0
    idna==2.6
    imageio==2.2.0
    imagesize==0.7.1
    incremental==17.5.0
    ipykernel==4.6.1
    ipython==6.1.0
    ipython-genutils==0.2.0
    ipywidgets==7.0.0
    isodate==0.6.0
    isort==4.2.15
    itsdangerous==0.24
    jdcal==1.3
    jedi==0.10.2
    Jinja2==2.9.6
    jmespath==0.9.3
    JPype1==0.6.2
    jsonschema==2.6.0
    jupyter-client==5.1.0
    jupyter-console==5.2.0
    jupyter-core==4.3.0
    jupyterlab==0.27.0
    jupyterlab-launcher==0.4.0
    Keras==2.2.4
    Keras-Applications==1.0.6
    Keras-Preprocessing==1.0.5
    konlpy==0.4.4
    lazy-object-proxy==1.3.1
    llvmlite==0.20.0
    locket==0.2.0
    lockfile==0.12.2
    lxml==4.1.0
    Mako==1.0.7
    Markdown==2.6.11
    MarkupSafe==1.0
    matplotlib==2.1.0
    mccabe==0.6.1
    menuinst==1.4.10
    mistune==0.7.4
    mkl-fft==1.0.0
    mpmath==0.19
    msgpack-python==0.4.8
    msrest==0.5.4
    multipledispatch==0.4.9
    navigator-updater==0.1.0
    nbconvert==5.3.1
    nbformat==4.4.0
    networkx==2.0
    nltk==3.2.4
    normality==0.6.1
    nose==1.3.7
    notebook==5.0.0
    numba==0.35.0+10.g143f70e
    numexpr==2.6.2
    numpy==1.14.2
    numpydoc==0.7.0
    oauthlib==2.0.6
    odo==0.5.1
    olefile==0.44
    openpyxl==2.4.8
    packaging==16.8
    pandas==0.20.3
    pandas-datareader==0.5.0
    pandocfilters==1.4.2
    parsel==1.5.0
    partd==0.3.8
    path.py==10.3.1
    pathlib2==2.3.0
    patsy==0.4.1
    pep8==1.7.0
    pickleshare==0.7.4
    Pillow==4.2.1
    pkginfo==1.4.1
    ply==3.10
    progress==1.3
    prompt-toolkit==1.0.15
    protobuf==3.6.0
    psutil==5.4.0
    py==1.4.34
    py4j==0.10.7
    pyasn1==0.4.4
    pyasn1-modules==0.2.2
    pycodestyle==2.3.1
    pycosat==0.6.3
    pycparser==2.18
    pycrypto==2.6.1
    pycurl==7.43.0
    PyDispatcher==2.0.5
    pyflakes==1.6.0
    pygal==2.4.0
    pygal-maps-world==1.0.2
    pygame==1.9.3
    Pygments==2.2.0
    pylint==1.7.4
    PyMySQL==0.9.2
    pyodbc==4.0.17
    pyOpenSSL==17.2.0
    pyparsing==2.2.0
    PySocks==1.6.7
    pyspark==2.3.1
    pytagcloud==0.3.5
    pytest==3.2.1
    pytest-runner==4.2
    python-dateutil==2.6.1
    python-editor==1.0.3
    pytz==2017.2
    PyWavelets==0.5.2
    pywin32==221
    PyYAML==3.12
    pyzmq==16.0.2
    QtAwesome==0.4.4
    qtconsole==4.3.1
    QtPy==1.3.1
    queuelib==1.5.0
    requests==2.18.4
    requests-file==1.4.3
    requests-ftp==0.3.1
    requests-oauthlib==0.8.0
    rope==0.10.5
    ruamel-yaml==0.11.14
    s3transfer==0.1.13
    scikit-image==0.13.0
    scikit-learn==0.19.1
    scipy==0.19.1
    Scrapy==1.5.1
    seaborn==0.8
    selenium==3.8.1
    service-identity==17.0.0
    simplegeneric==0.8.1
    simplejson==3.13.2
    singledispatch==3.4.0.3
    six==1.11.0
    smart-open==1.7.1
    snowballstemmer==1.2.1
    sortedcollections==0.5.3
    sortedcontainers==1.5.7
    Sphinx==1.6.3
    sphinxcontrib-websupport==1.0.1
    spyder==3.2.4
    SQLAlchemy==1.1.13
    statsmodels==0.8.0
    sympy==1.1.1
    tables==3.4.2
    tblib==1.3.2
    tensorboard==1.8.0
    tensorflow==1.8.0
    termcolor==1.1.0
    testpath==0.3.1
    toolz==0.8.2
    torch==0.4.1
    torchfile==0.1.0
    torchvision==0.2.1
    tornado==4.5.2
    tqdm==4.23.4
    traitlets==4.3.2
    tweepy==3.5.0
    Twisted==18.7.0
    typing==3.6.2
    unicodecsv==0.14.1
    urllib3==1.22
    visdom==0.1.8.5
    w3lib==1.19.0
    watermark==1.6.1
    wcwidth==0.1.7
    webencodings==0.5.1
    websocket-client==0.53.0
    Werkzeug==0.12.2
    widgetsnbextension==3.0.2
    win-inet-pton==1.0.1
    win-unicode-console==0.5
    wincertstore==0.2
    wordcloud==1.3.1
    wrapt==1.10.11
    xlrd==1.1.0
    XlsxWriter==1.0.2
    xlwings==0.11.4
    xlwt==1.3.0
    zict==0.1.3
    zope.interface==4.5.0
    

<hr>
<marquee><font size=3 color='brown'>The BigpyCraft find the information to design valuable society with Technology & Craft.</font></marquee>
<div align='right'><font size=2 color='gray'> &lt; The End &gt; </font></div>
