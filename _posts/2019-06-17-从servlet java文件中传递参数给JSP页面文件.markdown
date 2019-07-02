---
layout:  post
title:   从servlet java文件中传递参数给JSP页面文件
date:   2019-06-17 18:52:33
author:  "唐传林"
header-img: "img/post-bg-2015.jpg"
catalog:   true

---
发送端（servlet java文件）：

    
    
    String  a="test123";
    HttpSession session=request.getSession(); 
    session.setAttribute("a",a); 
    

接收端（JSP页面文件）：

    
    
    <%
    	String a = (String)session.getAttribute("a");
    	out.println(a);
    %>
    

