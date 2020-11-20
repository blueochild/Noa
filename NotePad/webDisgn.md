## 웹 디자인 자바 스크립트 코드

### 슬라이드 좌 -> 우
     
     setInterval(function(){
    $('.slider').animate({
        marginLeft : -1200
    }, 1000, function(){
        $('.slider>li').eq(0).appendTo('.slider')
        $('.slider').animate({
            marginLeft : 0
        }, 0)
      })
    }, 3000)
     
     
슬라이드 위 -> 아래는 marginLeft를 marginTop으로 고쳐쓰고 css에서 세로로 이미지가 정렬되게 한다.

### 슬라이드 fadein, fadeout
     
     # html
     
     <div class="main">
          <div id="slide">
               <div><img src="https://placeimg.com/750/750/any/grayscale" alt=""></div>
               <div><img src="https://placeimg.com/1000/750/any" alt=""></div>
               <div><img src="https://placeimg.com/750/800/any/grayscale" alt=""></div>
               <div><img src="https://placeimg.com/1000/800/any" alt=""></div>
          </div>
     </div>

     # js

     $('#slide > div:gt(0)').hide();

     setInterval(function(){
          $('#slide > div:first')
               .fadeOut(1000)
               .next()
               .fadeIn(1000)
               .end()
               .appendTo('#slide');
     },3000);

***

### 헤더의 메뉴바

     window.onload = function(){
      $('.mainmenu li').mouseover(function(){
        $('.submenu').stop().slideDown()
      }).mouseout(function(){
        $('.submenu').stop().slideUp()
      })
    }
    
    
### 탭 메뉴 

    var tabBtn = $('.tab_btn > ul > li')
    var tabCont = $('.tab_cont > ul')

    tabCont.hide().eq(0).show()

    tabBtn.click(function(e){
        e.preventDefault()
        var target = $(this)
        var index = target.index()
        tabBtn.removeClass("active")
        target.addClass("active")
        tabCont.css("display","none");
        tabCont.eq(index).css("display","block");

    })
    
해당 코드를 window.onload에 menu와 함께 넣는다.  

***

### 팝업창

    $(".layerPopup").click(function(e){
      e.preventDefault();
      $(".layer").show();
    });
    $(".layer .layer_close").click(function(e){
      e.preventDefault();
      $(".layer").hide();
    });
    
    
.layerPopup(열기 버튼 클래스)이나 .layer .layer_close (닫기 버튼 클래스) 대신에 자신이 명시한 클래스를 넣어도 된다. 
그리고 팝업 레이어에는 display : none;을 적용한다.
