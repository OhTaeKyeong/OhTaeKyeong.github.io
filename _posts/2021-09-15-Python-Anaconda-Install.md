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
    <img src="/assets/post-image/Excel-5일-단기-1/슬라이드14.PNG">
</div>
<h2>Anaconda를 사용하는 이유</h2>
<p>아나콘다는 패키지와 개발 환경을 관리하는 프로그램이다. 아나콘다에서는 pip와 conda 명령어를 사용하여 라이브러리를 설치할 수 있고, conda명령어를 쓴다면 아나콘다가 라이브러리간의 버전을 어느 정도 자동으로 맞춰주기도 한다. 만약 패키지나 파이썬 버전이 프로젝트마다 다르게 사용될 경우라면 가상환경을 만들어 독립적으로 관리할 수 있고, 추후 가상환경을 제거하는 것만으로 모든 패키지를 제거할 수 있기 때문에 개발 환경을 관리하기에 수월하다.</p>

<br>
<h2>Anaconda 설치하기</h2>
<p>https://www.anaconda.com/products/individual-d#download-section 로 접속</p>
<div style="text-align: center;">
    <img src="/assets/post-image/Excel-5일-단기-1/슬라이드14.PNG">
</div>
<div style="text-align: center;">
    <img src="/assets/post-image/Excel-5일-단기-1/슬라이드15.PNG">
</div>



<br>
<h2>- 경사하강법</h2>
<div style="text-align: center;">
    <img src="/assets/post-image/Excel-5일-단기-1/슬라이드16.PNG">
</div>
<div style="text-align: center;">
    <img src="/assets/post-image/Excel-5일-단기-1/슬라이드17.PNG">
</div>

> 행렬을 통해 해를 구한다면 함수의 계수와 상수를 한번에 구할 수 있지만, 해가 존재하지 않거나 국소해가 무수히 많은 경우나 계산이 복잡한 경우를 고려한다면 빠르고 반복적인 컴퓨터의 계산을 통해 해에 근접하도록 수렴시키는 것이 합리적일 수 있다.

<br>
<h2>- 예제 1</h2>
<div style="text-align: center;">
    <img src="/assets/post-image/Excel-5일-단기-1/슬라이드18.PNG">
</div>
<div style="text-align: center;">
    <img src="/assets/post-image/Excel-5일-단기-1/슬라이드19.PNG">
</div>

> 사실 위와 같이 편미분 값 그대로를 사용하여 가중치를 업데이트 한다면(학습률=1) 최적해로 수렴하지 않을 수 있다. 실제로 학습자료의 계산대로라면 가중치는 발산하기 때문에, 위의 설명은 경사하강법의 계산 방법을 공부하는 데 참고만 하길 바란다.

<div style="text-align: center;">
    <img src="/assets/post-image/Excel-5일-단기-1/슬라이드20.PNG">
</div>
<div style="text-align: center;">
    <img src="/assets/post-image/Excel-5일-단기-1/슬라이드21.PNG">
</div>
{% highlight vb %}
Const L_rate = 0.01 '경사를 촘촘히 내려가기 위한 "학습률" 정의
Dim x As Double
Dim w As Double
Dim b As Double '가중치, 바이어스, 입력값 정의

Sub 경사하강법()

w = Cells(1, 5).Value
b = Cells(1, 6).Value '가중치, 바이어스를 가져올 셀 설정

For i = 1 To 5 '데이터의 개수만큼 계산 실행

    x = Cells(i, 1).Value '셀로부터 입력값 불러오기
    y = w * x + b 'f(x) = wX + b

    Cells(i, 3) = y 'f(x)값을 셀에 표시

    ans = Cells(i, 2).Value '실제값인 Y데이터 불러오기
    w = w - L_rate * (y - ans) * x
    b = b - L_rate * (y - ans)
    '학습률만큼 더 촘촘하게 경사하강법을 진행
Next i

Cells(1, 5) = w
Cells(1, 6) = b
'바뀐 가중치와 바이어스를 업데이트

End Sub
{% endhighlight %}

<br>
<h2>- 예제 2</h2>
<div style="text-align: center;">
    <img src="/assets/post-image/Excel-5일-단기-1/슬라이드22.PNG">
</div>
{% highlight vb %}
Const L_rate = 0.01
Dim x(1 To 3) As Double
Dim w(1 To 3) As Double
Dim b As Double

Sub 경사하강법()

w(1) = Cells(1, 7).Value
w(2) = Cells(1, 8).Value
w(3) = Cells(1, 9).Value
b = Cells(1, 10).Value

For i = 1 To 5

    y = 0
    For j = 1 To 3
        x(j) = Cells(i, j).Value
        y = y + w(j) * x(j)
    Next j
    y = y + b

    Cells(i, 5) = y

    ans = Cells(i, 4).Value

    For j = 1 To 3
        w(j) = w(j) - L_rate * (y - ans) * x(j)
    Next j
    b = b - L_rate * (y - ans)

Next i

Cells(1, 7) = w(1)
Cells(1, 8) = w(2)
Cells(1, 9) = w(3)
Cells(1, 10) = b

End Sub
{% endhighlight %}

> 예제2는 Input이 3개인 함수에 대해서도 경사하강법을 통해 원하는 함수가 만들어지도록 가중치가 수렴 가능하다는 것을 보여주는 예제이다. 추후 심층신경망에서는 수 백~수 천개의 가중치가 사용되기 때문에, w와 b는 배열로 선언하는 습관을 들이자.

<br>