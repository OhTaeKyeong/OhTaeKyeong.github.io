---
layout: post
title: "[Object Detection] YOLOv3 (2)"
excerpt: "Custom Dataset 학습하기"
categories:
- CV
tags:
- Computer Vision
- Object Detection
- YOLO
last_modified_at: 2021-09-15T19:48:00+09:00
comments : true
---
<hr>
<div>
    <h2>개발환경 및 요구사항</h2>
    <ol type="i">
        <li>
            <h4>Anaconda3</h4>
            <p>: YOLOv3가 정상적으로 작동하기 위해서는 낮은 버전의 Python과 기타 라이브러리들이 설치되어야 하기 때문에 가상환경을 만들어서 관리해 주어야 한다.</p>
        </li>
        <li>
            <h4>Python 3.6 + Tensorflow 1.15.0 + Keras 2.2.4</h4>
            <p>: Github에서 Clone을 할 코드가 돌아갈 버전을 하나하나 삽질하며 테스트 해본 결과 위의 조합이 가장 적절하다. 코드 상에서 에러가 난다면 반드시 버전을 확인 할 것!</p>
        </li>
        <li>
            <h4>Windows10 + CUDA 10.0 + cuDNN 7.6.2</h4>
            <p>: CPU를 사용한다면 설치하지 않아도 되지만, GPU를 사용하는 것이 학습속도가 체감상 10배는 빠른 것 같다. Tensorflow 1.15.0을 지원하는 최신버전의 CUDA는 10.0이고, cuDNN은 CUDA 버전에 호환되는 것을 설치하면 된다.</p>
            <p><small>+ GPU에 따라서 지원하는 CUDA가 다른 것 같다. 여기서는 Geforce gtx-1060을 사용하였다. 만약 CUDA 10.0을 지원하지 않는 GPU를 사용하고 있다면 본 게시글에서 사용하는 코드로는 YOLOv3를 절대 학습시킬 수 없다. (CPU를 사용해도 되지만 정말 느리다.)</small></p>
        </li>
    </ol>
    <br>
</div>
<br>


<div>
    <h2>Anaconda 설치하기</h2>
    <div style="text-align: center;">
        <img src="/assets/post-image/CV-Object-Detection-YOLOv3/logo-anaconda.png">
    </div>
    <p><a href = "https://ohtaekyeong.github.io/others/2021/09/15/Others-Anaconda-Install.html" target = "blank" >[Anaconda] 설치하기</a>게시글을 참고하여 아나콘다 설치를 진행한다.</p>
    <br>
</div>
<br>


<div>
    <h2>GPU 환경 세팅</h2>
    <h4>- CUDA 10.0 설치</h4>
    <div style="text-align: center;">
        <img src="/assets/post-image/CV-Object-Detection-YOLOv3/CUDA10.0.png">
    </div>
    <p><a href = "https://developer.nvidia.com/cuda-10.0-download-archive?target_os=Windows&target_arch=x86_64&target_version=10&target_type=exelocal" target = "blank" >https://developer.nvidia.com/cuda-10.0-download-archive?target_os=Windows&target_arch=x86_64&target_version=10&target_type=exelocal</a>로 접속하여 윈도우 환경으로 다운로드 후 설치한다.</p>
    <br>
    <h4>- cuDNN 7.6.2 설치</h4>
    <div style="text-align: center;">
        <img src="/assets/post-image/CV-Object-Detection-YOLOv3/cuDNN7.6.2.png">
    </div>
    <div style="text-align: center;">
        <img src="/assets/post-image/CV-Object-Detection-YOLOv3/cuDNN_Releases.png">
    </div>
    <p><a href = "https://developer.nvidia.com/cudnn" target = "blank" >https://developer.nvidia.com/cudnn</a>로 접속하여 Download cuDNN을 누른다. 회원가입 후 설문조사를 하는 복잡한 과정이 요구된다.. Archived cuDNN Releases를 누른 다음 설치된 CUDA에 맞는 버전을 아무거나 골라 설치해도 되지만, 7.6.2버전을 추천한다.</p>
    <br>
    <div style="text-align: center;">
        <img src="/assets/post-image/CV-Object-Detection-YOLOv3/cuDNN_file.png">
    </div>
    <p>다운로드 된 압축파일을 풀고 해당 파일을 CUDA가 설치된 경로(C:\Program Files\NVIDIA GPU Computing Toolkit\CUDA\v10.0)에 복사 붙여넣기를 해주면 cuDNN의 설치가 완료된다.</p>
    <br>
</div>
<br>