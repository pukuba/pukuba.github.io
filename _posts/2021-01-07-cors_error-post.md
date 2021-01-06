---
title: cors 에러 header contains multiple values
layout: post
tags: Study
categories: Note
date: 2021-01-07 01:38:00 

--- 

cors error 해결하기.

최근 API 개발을 하다가 브라우저에서 API를 호출하니 

`The 'Access-Control-Allow-Origin' header contains multiple values` 라는 에러를 접하게 되었습니다.

원인은 nginx 와 server.ts 두 곳에서 cors 설정을 하여서 multiValue가 된 것이었습니다.


server.ts 의 cors 설정.
``` ts
const app = express()
app.use(cors())
```

nginx 의 cors 설정.
``` nginx
add_header 'Access-Control-Allow-Origin' '*';
```

다음과 같이 설정을 하였었는데.

nginx 에서 위의 설정을 제거해주니 해결되었습니다.

서버 소프트웨어나 서버 파일에 되어있는 cors 설정을 한곳에만 해주면 다음과 같은 에러를 해결할 수 있습니다.