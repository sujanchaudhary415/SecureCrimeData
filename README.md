# SecureCrimeData
code of js 


<%@page import="com.util.Utility"%>
<%@page import="java.sql.ResultSet"%>
<%@page import="com.DAO.AdminDAO"%><html>
<head>
	<link href="<%=request.getContextPath() %>/Resources/CSS/style.css" rel="stylesheet" type="text/css" />
	<link href="<%=request.getContextPath() %>/Resources/CSS/message.css" rel="stylesheet" type="text/css" />
	<link href="<%=request.getContextPath() %>/Resources/CSS/button.css" rel="stylesheet" type="text/css" />
	<link href="<%=request.getContextPath() %>/Resources/CSS/login.css" rel="stylesheet" type="text/css" />
	<script type="text/javascript" src="<%=request.getContextPath() %>/Resources/JS/style.js"></script>

</head>
<body onload="startTimer()">

<%
    int no=Utility.parse(request.getParameter("no"));
    ResultSet rs=(ResultSet)request.getAttribute("rs");
    int id=0,deptId=0,designId=0;
	String username="",name="",add="",email="",phone="";
	
	AdminDAO adminDAO = AdminDAO.getInstance();
	
	while(rs.next())
	{
		id=rs.getInt(1);
		username=rs.getString(2);
		name=rs.getString(4);
		deptId=rs.getInt(5);
		designId=rs.getInt(6);
		add = rs.getString(7);
		phone = rs.getString(10);
		email = rs.getString(11);
	}

	if(no==1)
	{
%>
			<div class="error" id="message" style="position:absolute;top:225px;left:300px">		
				<p>Opp's,Seems something went wrong ..!</p>
			</div>
<%
	}
	else if(no==0)
	{
%>
			<br>
			<div align="right" style="position:absolute;top:15px;left:375px">
				<a class="gradientbuttons" href="<%=request.getContextPath() %>/EditUserProfile?username=<%=username %>&no=1">Edit Profile</a>&nbsp;&nbsp;&nbsp;&nbsp;
				<a class="gradientbuttons" href="<%=request.getContextPath() %>/ChangeUserPassword?username=<%=username %>&no=1&id=<%=id %>" target="myIframe">Change Password</a>
			</div>
			<br>
			<div id="a2" align="right" style="position:absolute;top:45px;left:11px">
			
				<p>
				
					<table>
							<tr>
									<td colspan="3" align="center">
									<font color="#000000" style="font-style: bold" size="5">User Profile Details</font>
									</td>
									 
