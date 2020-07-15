---
title: openfalcon相应页面取消登陆校验（不正规)
date: 2020-07-15 17:59:19
tags:
  - openfalcon问题
categories:
  - openfalcon
---

项目需要将openfalcon的chat图表无需登录展示出来

1. 使用官方推荐的Grafana视图自行扩展https://book.open-falcon.org/zh_0_2/dev/support_grafana.html
2. 通过API获取数据，自己实现展示

3. 通过修改dashboard的权限校验实现
<!-- more -->
主要介绍修改dashboard修改权限
修改rrd/view/__init__.py中的权限校验
如下图：

![修改代码](img/1.png)

取消权限后隐藏页面上的导航栏
导航栏页面在  rrd/templates/navbar.html
里面是导航栏信息，可以根据需求更改

```html
<nav class="navbar navbar-default" role="navigation" style="background-color: #fff;">
<div class="container-fluid">
    <div class="navbar-header">
        <button type="button" class="navbar-toggle" data-toggle="collapse" data-target=".navbar-ex1-collapse">
        </button>
        <a class="navbar-brand" href="/">Falcon+</a>
    </div>
    <div class="collapse navbar-collapse navbar-ex1-collapse">
        <ul class="nav navbar-nav navbar-right">
         <li {%if g.nav_menu == "nav_dashboard"%}class="active"{%endif%}><a href="/">Dashboard</a></li>
         <li class="dropdown" {%if g.nav_menu == "nav_screen"%}class="active"{%endif%}>
           <a href="#" class="dropdown-toggle" data-toggle="dropdown" role="button" aria-expanded="false">Screen<span class="caret"></span></a>
           <ul class="dropdown-menu" role="menu" style="font-size:12px;">
               <li><a href="/screen">screens</a></li>
               <li><a href="/screen/add">+screen</a></li>
           </ul>
          </li>
          <li {%if g.nav_menu == "p_hostgroup"%}class="active"{%endif%}><a href="/portal/hostgroup">HostGroups</a></li>
          <li {%if g.nav_menu == "p_template"%}class="active"{%endif%}><a href="/portal/template">Templates</a></li>
          <li {%if g.nav_menu == "p_expression"%}class="active"{%endif%}><a href="/portal/expression">Expressions</a></li>
          <li {%if g.nav_menu == "p_nodata"%}class="active"{%endif%}><a href="/portal/nodata">Nodata</a></li>
          <li {%if g.nav_menu == "p_alarm-dash"%}class="active"{%endif%}><a href="/portal/alarm-dash/case">Alarm-Dashboard</a></li>
          <li class="dropdown">
              <a href="#" class="dropdown-toggle" data-toggle="dropdown" role="button" aria-expanded="false">
                  {%if g.user%} Welcome {{g.user.name}}{%else%}Sign in{%endif%}<span class="caret"></span></a>
              <ul class="dropdown-menu" role="menu" style="font-size:12px;">
                  {%if g.user%}
                      <li><a href="/user/profile">Profile</a></li>
                      <li><a href="/user/list">Users</a></li>
                      <li><a href="/team/list">Teams</a></li>
                      <li><a href="/auth/logout">Logout</a></li>
                  {%else%}
                      <li><a href="/auth/login">Login</a></li>
                      <li><a href="/auth/register">Sign Up</a></li>
                  {%endif%}
                  <li><a href="https://github.com/open-falcon/dashboard">fork me on Github</a></li>
              </ul>
          </li>
        </ul>
    </div>
</div>
</nav>

```
