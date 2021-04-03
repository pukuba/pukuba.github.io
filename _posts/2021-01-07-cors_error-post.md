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

원인은 WS와 WAS의 두 곳에서 cors 설정을 하여서 multiValue가 된 것이었습니다.


(WAS) server.ts 의 cors 설정.
``` ts
const app = express()
app.use(cors())
```

(WS) nginx 의 cors 설정.
``` nginx
add_header 'Access-Control-Allow-Origin' '*';
```

다음과 같이 설정을 하였었는데.

WAS에서 cors 설정을 제거하여서 해결하였습니다.

WS, WAS 두곳에서 cors 설정을 한 것으로 뜬 에러니 둘중 아무곳에서 설정을 제거해주면 됩니다.