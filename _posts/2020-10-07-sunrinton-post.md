---
title: 선린톤 (선린인터넷 고등학교 해커톤) 후기
layout: post
tags: Sunrin Hackathon 
categories: Review
date: 2020-10-07 13:38:00 

--- 

## *서론*
교내에서 해커톤 대회를 하면 티셔츠와 치킨을 준다는 소리에 팀원을 구해서 바로 대회를 나가게 되었습니다.

프론트 - 2
백엔드 - 1
디자인 - 1

으로 대회를 참가하였습니다.

## *사용한 기술*
- Node.js 12.19.0 (LTS)
    - express
    - Apollo Server

- DB
    - MongoDB

- API
    - GraphQL
    
- Naver Cloud Platform
    - CLOVA Premium Voice (CPV)

## *후기*
<img src="https://github.com/LovePrincipal/Sunrin2020-Hackathon-App/raw/master/screenshot/banner.png"> 

주제는 "문자"였습니다. 아이디어가 생각나지 않아서 2시간정도 생각하다 같은팀이신 선배님이 점자를 번역하는 서비스를 생각하셔서 바로 개발하게 되었습니다.

> 실제, 2017년 보건복지부 장애인 실태 조사에 따르면 시각장애인의 점자 해독 여부는 가능하다 (12.4%),
불가능하다 (86.0%), 배우는 중이다 (1.6%)로 점자를 아는 시각장애인 분들보다 모르는 분들이 더 많다는 통계가 분석되었습니다.

선배님께서 다양한 자료들을 보여주시며 아이디어를 구체적으로 알려주시고 어떻게 로직을 구성할껀지 구체적으로 소통을 하여 쉽고 빠르게 개발할수 있었습니다.

<img src="https://github.com/LovePrincipal/Sunrin2020-Hackathon-App/raw/master/screenshot/mockup.png">

제가 한것은 프론트에서 점자번호를 서버에 보내주면 점자를 풉니다.

"ㅇ ㅏ ㄴ ㄴ ㅕ ㅇ ㅎ ㅏ ㅅ ㅔ ㅇ ㅛ" 이런식으로 풀어지는데. 그럼 이 풀어진 문자들을 이어주고. 이 이어진 문자열을 NCP에 CPV 기능을 활용하여 음성과 점자가 어떻게 한글로 나오는지를 다시 반환해주는 쿼리를 짜는게 저의 역할이였고 아이디어가 너무좋아서 놀고먹었던 해커톤입니다.


## *결과*

동상.

좋은팀원을 만나서 편하게 개발할 수 있어서 좋았습니다. :)