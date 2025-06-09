<html>
    <head><title>新增使用者</title></head>
    <body>
<?php
    // 顯示所有錯誤
    error_reporting(0);
    // 啟動 session，用於驗證使用者是否登入
    session_start();
    // 檢查是否有登入，沒有則導向登入頁面
    if (!$_SESSION["id"]) {
        echo "請登入帳號";
        echo "<meta http-equiv=REFRESH content='3, url=2.login.html'>";
    }
    else{    
        echo "
            <form action=15.user_add.php method=post>
                帳號：<input type=text name=id><br>
                密碼：<input type=text name=pwd><p></p>
                <input type=submit value=新增> <input type=reset value=清除>
            </form>
        ";
    }
?>
    </body>
</html>

<?php

error_reporting(0);
session_start();
if (!$_SESSION["id"]) {
    echo "請登入帳號";
    echo "<meta http-equiv=REFRESH content='3, url=2.login.html'>";
}
else{    

   #mysqli_connect() 建立資料庫連結
   $conn=mysqli_connect("db4free.net", "immust", "immustimmust", "immust");
   #mysqli_query() 從資料庫查詢資料
   #新增資料SQL命令：insert into 表格名稱(欄位1,欄位2) values(欄位1的值,欄位2的值)
   $sql="insert into user(id,pwd) values('{$_POST['id']}', '{$_POST['pwd']}')";
   #echo $sql;
   if (!mysqli_query($conn, $sql)) {
     echo "新增命令錯誤";
   }
   else{
     echo "新增使用者成功，三秒鐘後回到網頁";
     echo "<meta http-equiv=REFRESH content='3, url=18.user.php'>";
   }
}
?>

<?php
    error_reporting(0);
    session_start();
    if (!$_SESSION["id"]) {
        echo "請登入帳號";
        echo "<meta http-equiv=REFRESH content='3, url=2.login.html'>";
    }
    else{   
        $conn=mysqli_connect("db4free.net", "immust", "immustimmust", "immust");
        $sql="delete from user where id='{$_GET["id"]}'";
        #echo $sql;
        if (!mysqli_query($conn,$sql)){
            echo "使用者刪除錯誤";
        }else{
            echo "使用者刪除成功";
        }
        echo "<meta http-equiv=REFRESH content='3, url=18.user.php'>";
    }
?>

<html>
    <head><title>使用者管理</title></head>
    <body>
    <?php
        error_reporting(0);
        session_start();
        if (!$_SESSION["id"]) {
            echo "請登入帳號";
            echo "<meta http-equiv=REFRESH content='3, url=2.login.html'>";
        }
        else{   
            echo "<h1>使用者管理</h1>
                [<a href=14.user_add_form.php>新增使用者</a>] [<a href=11.bulletin.php>回佈告欄列表</a>]<br>
                <table border=1>
                    <tr><td></td><td>帳號</td><td>密碼</td></tr>";
            
            $conn=mysqli_connect("db4free.net", "immust", "immustimmust", "immust");
            $result=mysqli_query($conn, "select * from user");
            while ($row=mysqli_fetch_array($result)){
                echo "<tr><td><a href=19.user_edit_form.php?id={$row['id']}>修改</a>||<a href=17.user_delete.php?id={$row['id']}>刪除</a></td><td>{$row['id']}</td><td>{$row['pwd']}</td></tr>";
            }
            echo "</table>";
        }
    ?> 
    </body>
</html>

<html>
    <head><title>修改使用者</title></head>
    <body>
    <?php
    error_reporting(0);
    session_start();
    if (!$_SESSION["id"]) {
        echo "請登入帳號";
        echo "<meta http-equiv=REFRESH content='3, url=2.login.html'>";
    }
    else{   
        $conn=mysqli_connect("db4free.net", "immust", "immustimmust", "immust");
        $result=mysqli_query($conn, "select * from user where id='{$_GET['id']}'");
        $row=mysqli_fetch_array($result);
        echo "
        <form method=post action=20.user_edit.php>
            <input type=hidden name=id value={$row['id']}>
            帳號：{$row['id']}<br> 
            密碼：<input type=text name=pwd value={$row['pwd']}><p></p>
            <input type=submit value=修改>
        </form>
        ";
    }
    ?>
    </body>
</html>

<?php

    error_reporting(0);
    session_start();
    if (!$_SESSION["id"]) {
        echo "請登入帳號";
        echo "<meta http-equiv=REFRESH content='3, url=2.login.html'>";
    }
    else{   
        $conn=mysqli_connect("db4free.net", "immust", "immustimmust", "immust");
        if (!mysqli_query($conn, "update user set pwd='{$_POST['pwd']}' where id='{$_POST['id']}'")){
            echo "修改錯誤";
            echo "<meta http-equiv=REFRESH content='3, url=18.user.php'>";
        }else{
            echo "修改成功，三秒鐘後回到網頁";
            echo "<meta http-equiv=REFRESH content='3, url=18.user.php'>";
        }
    }

?>

<?php
    // 關閉錯誤訊息顯示
    error_reporting(0);
    // 啟用 session，讓伺服器可以追蹤使用者登入狀態
    session_start();
    // 判斷使用者是否已登入（檢查 session 中是否存在 id）
    if (!$_SESSION["id"]) {
        // 若未登入，顯示訊息提醒使用者先登入
        echo "please login first";
        // 3 秒後自動跳轉回登入頁面（2.login.html）
        echo "<meta http-equiv=REFRESH content='3, url=2.login.html'>";
    }
    else{
        // 若已登入，顯示新增佈告的 HTML 表單
        echo "
        <html>
            <head><title>新增佈告</title></head>
            <body>
                <form method=post action=23.bulletin_add.php>
                    標    題：<input type=text name=title><br>
                    內    容：<br><textarea name=content rows=20 cols=20></textarea><br>
                    佈告類型：<input type=radio name=type value=1>系上公告 
                            <input type=radio name=type value=2>獲獎資訊
                            <input type=radio name=type value=3>徵才資訊<br>
                    發布時間：<input type=date name=time><p></p>
                    <input type=submit value=新增佈告> <input type=reset value=清除>
                </form>
            </body>
        </html>
        ";
    }
?>

<?php
    // 關閉錯誤訊息顯示
    error_reporting(0);
    // 啟用 session 功能，用於判斷使用者登入狀態
    session_start();
    // 檢查 session 中是否有使用者 id，判斷是否登入
    if (!$_SESSION["id"]) {
        // 若未登入，提示使用者先登入
        echo "please login first";
        // 3 秒後自動跳轉回登入頁面
        echo "<meta http-equiv=REFRESH content='3, url=2.login.html'>";
    }
    else{
        $conn=mysqli_connect("db4free.net", "immust", "immustimmust", "immust");
        $sql="insert into bulletin(title, content, type, time) 
        values('{$_POST['title']}','{$_POST['content']}', {$_POST['type']},'{$_POST['time']}')";
        if (!mysqli_query($conn, $sql)){
            echo "新增命令錯誤";
        }
        else{
            echo "新增佈告成功，三秒鐘後回到網頁";
            echo "<meta http-equiv=REFRESH content='3, url=11.bulletin.php'>";
        }
    }
?>

<?php
    error_reporting(0);
    session_start();
    if (!$_SESSION["id"]) {
        echo "please login first";
        echo "<meta http-equiv=REFRESH content='3, url=2.login.html'>";
    }
    else{
        
        $conn=mysqli_connect("db4free.net", "immust", "immustimmust", "immust");
        $result=mysqli_query($conn, "select * from bulletin where bid={$_GET["bid"]}");
        $row=mysqli_fetch_array($result);
        $checked1="";
        $checked2="";
        $checked3="";
        if ($row['type']==1)
            $checked1="checked";
        if ($row['type']==2)
            $checked2="checked";
        if ($row['type']==3)
            $checked3="checked";
        echo "
        <html>
            <head><title>新增佈告</title></head>
            <body>
                <form method=post action=27.bulletin_edit.php>
                    佈告編號：{$row['bid']}<input type=hidden name=bid value={$row['bid']}><br>
                    標    題：<input type=text name=title value={$row['title']}><br>
                    內    容：<br><textarea name=content rows=20 cols=20>{$row['content']}</textarea><br>
                    佈告類型：<input type=radio name=type value=1 {$checked1}>系上公告 
                            <input type=radio name=type value=2 {$checked2}>獲獎資訊
                            <input type=radio name=type value=3 {$checked3}>徵才資訊<br>
                    發布時間：<input type=date name=time value={$row['time']}><p></p>
                    <input type=submit value=修改佈告> <input type=reset value=清除>
                </form>
            </body>
        </html>
        ";
    }
?>

<?php

    error_reporting(0);
    session_start();
    if (!$_SESSION["id"]) {
        echo "請登入帳號";
        echo "<meta http-equiv=REFRESH content='3, url=2.login.html'>";
    }
    else{   
        $conn=mysqli_connect("db4free.net", "immust", "immustimmust", "immust");
        if (!mysqli_query($conn, "update bulletin set title='{$_POST['title']}',content='{$_POST['content']}',time='{$_POST['time']}',type={$_POST['type']} where bid='{$_POST['bid']}'")){
            echo "修改錯誤";
            echo "<meta http-equiv=REFRESH content='3, url=11.bulletin.php'>";
        }else{
            echo "修改成功，三秒鐘後回到佈告欄列表";
            echo "<meta http-equiv=REFRESH content='3, url=11.bulletin.php'>";
        }
    }

?>

<?php
    error_reporting(0);
    session_start();
    if (!$_SESSION["id"]) {
        echo "請登入帳號";
        echo "<meta http-equiv=REFRESH content='3, url=2.login.html'>";
    }
    else{   
        $conn=mysqli_connect("db4free.net", "immust", "immustimmust", "immust");
        $sql="delete from bulletin where bid='{$_GET["bid"]}'";
        #echo $sql;
        if (!mysqli_query($conn,$sql)){
            echo "佈告刪除錯誤";
        }else{
            echo "佈告刪除成功";
        }
        echo "<meta http-equiv=REFRESH content='3, url=11.bulletin.php'>";
    }
?>

<html>
    <head><title>明新科技大學資訊管理系</title>
    <meta charset="utf-8">
    <link href="https://cdn.bootcss.com/flexslider/2.6.3/flexslider.min.css" rel="stylesheet">
    <script src="https://cdn.bootcss.com/jquery/2.2.2/jquery.min.js"></script>
    <script src="https://cdn.bootcss.com/flexslider/2.6.3/jquery.flexslider-min.js"></script>        
    <script>
        $(window).load(function() {
            $('.flexslider').flexslider({
                animation: "slide",
                rtl: true
            });
        });
    </script>
    <style>
        *{
            margin:0;
            color:gray;
            text-align:center;
        }
        /* top */
        .top{
             background-color: white;
        }
        .top .container{
            display: flex;
            align-items: center;
            justify-content: space-between;
            padding:10px;
        }
        .top .logo{
            /*border:1px solid red;*/
            font-size: 35px;
            font-weight: bold;
        }
        .top .logo img{
            width: 100px;
            vertical-align: middle;
        }
        .top .top-nav{
            /*border:1px solid red;*/
            font-size: 25px;
            font-weight: bold;       
        }
        .top .top-nav a{
            text-decoration: none;
        }
        /* nav */
        .nav {
            background-color:#333;
            display: flex;
            justify-content: center;
        }
        .nav ul {
            list-style-type: none;  
            margin: 0; 
            padding: 0; 
            overflow: hidden; 
            background-color: #333; 
        }
        .nav li {
            float: left; 
        }
        .nav li a {    
            display: block;  
            color: white;  
            text-align: center;  
            padding: 14px 16px;  
            text-decoration: none;  
        }
        .nav li a:hover {
            background-color: #111; 
        }
        /*下拉式選單*/
        .dropdown:hover .dropdown-content {
            display: block;   /*使用block呈現上下排列*/
        }
        li.dropdown:hover{
            background-color: #333;  /*設定背景顏色*/
        }
        .dropdown-content {  /*設定下拉選單內容格式*/
            display: none;
            position: absolute;
            background-color: #333;
            min-width: 160px;
            z-index: 1;
        }
        .dropdown-content a {/*設定下拉選單連結內容格式*/
            color: black;
            padding: 12px 16px;
            text-decoration: none;
            display: block;
            text-align: left;
        }

        /* slider */
        .slider{
            background-color: black;
        }
        /* banner*/
        .banner{
            background-image: linear-gradient(#ABDCFF,#0396FF);
            padding:30px;
        }
        .banner h1{
            padding: 20px;
        }        
        /*faculty*/
        .faculty {
            display: block;
            justify-content: center;
            background-color:white;
            padding:40px;
        }
        .faculty h2 {
            font-size: 25px;
            color: rgb(50,51,52);
            padding-bottom:40px;
        }
        .faculty .container {
            /*border:1px solid red;*/
            display: flex;
            justify-content: space-around;
            align-items: center;
        }
        .faculty .teacher{
            /*border:1px solid blue;*/
            display:block;
            text-decoration: none;
        }
        .faculty .teacher img{
            height: 200px;
            width: 200px;
        }
        .faculty .teacher h3{
            color: White;
            background-color: rgba(39,40,34,.500);
            text-align: center;           
        }
        /*contact*/
        .contact {
            display: block;
            justify-content: center;
            margin-top: 30px;
            margin-bottom: 30px;                
        }
        .contact h2{
            color: rgb(54, 82, 110);
            font-size: 25px;
        }
        .contact .infos{
            display:flex;
            margin-top: 30px; 
            justify-content: center;
        }
        .contact .infos .left{
            display:block;
            text-align: left;
            margin-right: 30px;
        }
        .contact .infos .left b{
            display:block;
            text-align: left;
            margin-top: 10px;
            text-decoration: bold;
            color: Gray;
            font-size: 18px;
            line-height: 18px;
        }
        .contact .infos .left span{
            display:block;
            text-align: left;
            margin-top: 10px;
            color: rgba(39,40,34,0.5);
            font-size: 16px;
            padding-left: 27px;
        }
        .contact .infos .right{
            height: 200px;               
        }
        .contact .infos .right iframe{
            width: 100%;
            height: 100%;
            border: 1px solid rgba(39,40,34,0.50);
        }
        /*footer*/
        .footer{
            display: flex;
            justify-content: center;
            background-color: rgb(25,26,30);
            padding: 30px 0;
        }
        /*登入畫面css*/
        .modal {
            display: none; /* Hidden by default */
            position: fixed; /* Stay in place */
            z-index: 1; /* Sit on top */
            right: 50;
            top: 50;
            width: 20%; /* Full width */
            height: 20%; /* Full height */
            overflow: auto; /* Enable scroll if needed */
            background-color: rgba(255,255,255,0.9); /* Black w/ opacity */
            padding-top: 50px;
        }  /*登入畫面css*/
        /*佈告欄*/
        .bulletin{
            display: block;
            justify-content: center;
            background-color: rgb(255,204,153);
            padding: 30px 0;

        }
        .bulletin h1{
            padding:10px;
        }
        .bulletin table{
            border-collapse:collapse;
            font-family: 微軟正黑體;
            font-size:16px; 
            border:1px solid #000;
        }
        .bulletin table th{
            background-color: #abdcff;
            color: #ffffff;
        }
        .bulletin table td{
            background-color: #ffffff;
            color: #0396ff;
        }
    </style>
    </head>
    <body>
        <div class="top">
            <div class="container">
                <div class="logo">
                  <img src="https://github.com/shhuangmust/html/raw/111-1/IMMUST_LOGO.JPG">
                  明新科技大學資訊管理系
                </div>
                <div class="top-nav">
                  <a href=>明新科大</a>
                  <a href=>明新管理學院</a>
                  <!---跳出登入畫面-->
                  <label onclick="document.getElementById('login').style.display='block'">登入</label>
                  <div id="login" class="modal">
                    <span onclick="document.getElementById('login').style.display='none'">&times; 管理系統登入</span>
                    <form method=post action="10.login.php">
                        帳號：<input type=text name="id"><br />
                        密碼：<input type=password name="pwd"><p></p>
                        <input type=submit value="登入"> <input type=reset value="清除">
                    </form>
                  </div>  
                  <!---登入畫面-->
                </div>
              </div>
        </div>
        <div class="nav">   
            <ul>
                <li><a href="#home">首頁</a></li>
                <li><a href="#introduction">系所簡介</a></li>
                <li  class="dropdown"><a href="#faculty">成員簡介</a>
                    <div class="dropdown-content">
                        <a href="#faculty">黃老師</a>
                        <a href="#faculty">李老師</a>
                        <a href="#faculty">應老師</a>
                    </div>                       
                </li>
                <li><a href="#about">相關資訊</a></li>
            </ul>
        </div>
        <div class="slider">
            <div class="flexslider">
                <ul class="slides">
                    <li><img src="https://github.com/shhuangmust/html/raw/111-1/slider1.JPG" /></li>
                    <li><img src="https://github.com/shhuangmust/html/raw/111-1/slider2.JPG" /></li>
                    <li><img src="https://github.com/shhuangmust/html/raw/111-1/slider3.JPG" /></li>
                </ul>
            </div>
        </div>
        <!---佈告欄--->
        <div class="bulletin">
           <h1>最新公告</h1>
            <?php
                $conn=mysqli_connect("db4free.net", "immust", "immustimmust", "immust");
                $result=mysqli_query($conn, "select * from bulletin");
                echo "<table border=2><tr><th>佈告編號</th><th>佈告類別</th><th>標題</th><th>佈告內容</th><th>發佈時間</th></tr>";
                while ($row=mysqli_fetch_array($result)){
                    echo "<tr><td>";
                    echo $row["bid"];
                    echo "</td><td>";
                    if ($row["type"]==1) echo "系上公告";  
                    if ($row["type"]==2) echo "獲獎資訊"; 
                    if ($row["type"]==3) echo "徵才資訊"; 
                    echo "</td><td>"; 
                    echo $row["title"];
                    echo "</td><td>";
                    echo $row["content"]; 
                    echo "</td><td>";
                    echo $row["time"];
                    echo "</td></tr>";
                }
                echo "</table>";
            ?>
        </div>
        <!---佈告欄--->
        <div class="banner" id="introduction">
            <h1>系所簡介</h1>
            <h1>歷年教育部評鑑皆榮獲一等</h1>
            <h1>明新科技大學資訊管理系</h1>
            <h1>全國私立科大第一資管系</h1>
        </div>
        <div class="faculty" id="faculty">
            <h2>師資介紹</h2>
            <div class="container">
                <a class="teacher" href="">
                    <img src="https://github.com/shhuangmust/html/raw/111-1/faculty1.jpg" />
                    <h3>黃老師</h3>
                </a>
                <a class="teacher" href="">
                    <img src="https://github.com/shhuangmust/html/raw/111-1/faculty2.jpg" />
                    <h3>李老師</h3>
                </a>
                <a class="teacher" href="">
                    <img src="https://github.com/shhuangmust/html/raw/111-1/faculty3.jpg" />
                    <h3>應老師</h3>
                </a>        
            </div>
        </div>
        <div class="contact" id="about">
                <h2>相關資訊</h2>
                <div class="infos">
                    <div class="left">
                        <b>明新科技大學管理學院大樓二樓</b>
                        <span>304新竹縣新豐鄉新興路1號</span>
                        <b> 電話:03-5593142</b>
                        <span>分機:3431、3432、3433</span>
                        <b> 傳真:03-5593142</b>
                        <span>分機:3440</span>
                    </div>
                    <div class="right">
                        <iframe src="https://www.google.com/maps/embed?pb=!1m18!1m12!1m3!1d3044.185885150929!2d120.98912333466727!3d24.86332844316392!2m3!1f0!2f0!3f0!3m2!1i1024!2i768!4f13.1!3m3!1m2!1s0x34683154faa8283b%3A0x92cb1c5564a574ef!2z5piO5paw56eR5oqA5aSn5a24!5e0!3m2!1szh-TW!2stw!4v1536665837954" frameborder="0" style="border:0" allowfullscreen></iframe>
                    </div>
                </div>
        </div>
        <div class="footer">
            &copy;Copyright 2022 Department of Information Management, MUST. All rights reserved. 維護者 Tony SHHuang
        </div>
     </body>
</html>