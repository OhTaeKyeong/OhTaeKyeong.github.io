---
layout: post
title: "[Anaconda] 설치하기"
excerpt: "설치 후 주피터 실행하기"
categories:
- Others
tags:
- Others
- Anaconda
last_modified_at: 2021-09-15T20:21:00+09:00
comments : true
---
<hr>

<div style="text-align: center;">
    <img src="/assets/post-image/Python-Anaconda-Install/logo-anaconda.png">
</div>
<h2>Anaconda를 사용하는 이유</h2>
<p>아나콘다는 패키지와 개발 환경을 관리하는 프로그램이다. 아나콘다에서는 pip와 conda 명령어를 사용하여 라이브러리를 설치할 수 있고, conda명령어를 쓴다면 아나콘다가 라이브러리간의 버전을 어느 정도 자동으로 맞춰주기도 한다. 만약 패키지나 파이썬 버전이 프로젝트마다 다르게 사용될 경우라면 가상환경을 만들어 독립적으로 관리할 수 있고, 추후 가상환경을 제거하는 것만으로 모든 패키지를 제거할 수 있기 때문에 개발 환경을 관리하기에 수월하다.</p>

<br>
<br>
<h2>Anaconda 설치하기</h2>
<h4>- 사이트 접속 후 설치</h4>
<div style="text-align: center;">
    <img src="/assets/post-image/Python-Anaconda-Install/Anaconda사이트.png">
</div>
<p><a href = "https://www.anaconda.com/products/individual-d#download-section" target = "blank" >https://www.anaconda.com/products/individual-d#download-section</a> 로 접속</p>

<br>
<h4>- 다운로드 후 Install 진행</h4>
<div style="text-align: center;">
    <img src="/assets/post-image/Python-Anaconda-Install/Setup1.PNG">
</div>
<div style="text-align: center;">
    <img src="/assets/post-image/Python-Anaconda-Install/Setup2.PNG">
</div>
<div style="text-align: center;">
    <img src="/assets/post-image/Python-Anaconda-Install/Setup3.PNG">
</div>
<div style="text-align: center;">
    <img src="/assets/post-image/Python-Anaconda-Install/Setup4.PNG">
</div>
<div style="text-align: center;">
    <img src="/assets/post-image/Python-Anaconda-Install/Setup5.PNG">
</div>
<div style="text-align: center;">
    <img src="/assets/post-image/Python-Anaconda-Install/Setup6.PNG">
</div>
<div style="text-align: center;">
    <img src="/assets/post-image/Python-Anaconda-Install/Setup7.PNG">
</div>
<div style="text-align: center;">
    <img src="/assets/post-image/Python-Anaconda-Install/Setup8.PNG">
</div>
<div style="text-align: center;">
    <img src="/assets/post-image/Python-Anaconda-Install/Setup9.PNG">
</div>
<p>별도의 과정없이 설치를 쭉 진행하면 된다.</p>

<br>
<br>
<h2>아나콘다 실행하기</h2>
<h4>- 시작 메뉴에서 새로 설치된 항목 확인</h4>
<div style="text-align: center;">
    <img src="/assets/post-image/Python-Anaconda-Install/Folder_list.png">
</div>
<p>Anaconda Prompt를 클릭하여 실행</p>

<br>
<h4>- 아나콘다 프롬프트 실행</h4>
<div style="text-align: center;">
    <img src="/assets/post-image/Python-Anaconda-Install/cmd.PNG">
</div>
<p>Anaconda Prompt를 클릭하면 cmd 창이 뜨고 (base) 환경으로 실행이 될 것이다. 아나콘다는 주피터 노트북이 기본으로 설치되어있기 때문에, jupyter notebook 이라는 명령어를 입력하여 노트북이 정상적으로 실행되는 것 까지 확인된다면 성공적으로 Anaconda설치가 된 것이다.</p>

<br>