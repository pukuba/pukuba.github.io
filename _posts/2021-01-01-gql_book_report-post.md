---
title: GraphQL 을 처음 공부하는 데 있어 좋은 책.
layout: post
tags: Study 
categories: Book-Report
date: 2021-01-01 16:38:00 

--- 

웹 앱 API 개발을 위한 GraphQL을 읽다.

<div style="display: inline-block">
    <img src="/images/GQL_Book1.png">
    <img src="/images/GQL_Book2.png">
</div>

> GraphQL을 처음 공부하는 데 있어 매우 좋은 책.

예전에 GraphQL을 처음 공부하기 위해서 구입한 책입니다.

GraphQL을 공부하고싶다면 이 책으로 시작하는것을 추천드립니다.

GraphQL의 개념과 장점, Graphql Apollo, 그래프이론, 실제 GraphQL을 어디서 사용하는지 뿐만아니라 실제 제품을 위한 GraphQL 사용에 관해서도 소계합니다.

## 좋았던점

Type, Query, Mutation, Subscription을 알려주고 Photo Upload 프로젝트를 진행하는 부분이 책에 있는데

위 프로젝트를 책을 보면서 같이 공부하면 대부분의 프로젝트에서도 이제 GraphQL을 사용할 수 있을 정도가 됩니다.

Node.js + MongoDB + React Apollo + Github Auth 등을 사용하여서 프로젝트를 진행하는데 Query, Mutation, Type, Subscripton, GraphQL의 장점 단점등을 위 프로젝트를 통해서 알게되는데 매우 좋게 진행한거같습니다.

실제 제품에서도 사용할수 있도록 GQL 에서의 파일 업로드, 보안에 대해서 알려주고

이제 이 책을 읽고난뒤 어떻게 공부해야 하는지 또한 알려주는것이 매우 좋았던것 같습니다.

## 아쉬운점

Node.js 14 이상부터는 파일 업로드에 이슈가 있습니다.

``` json
"resolutions": {
    "**/apollo-server-core/graphql-upload": "^11.0.0"
  }
```

`package.json 파일에 위와 같은 문구를 추가해주고 yarn install 을 하면 이슈를 해결할 수 있습니다.`


GraphQL N + 1 Problem, PersistGraphQL 조금더 전문적인부분.

상황에 따른 GraphQL, REST 어떤게 더 효율적인지 를 알려주었으면 조금더 좋았을거 같았습니다.

## 결론

사실 아쉬운 점은 책을 읽고 나서 다 스스로 공부할 수 있다. 이 책을 읽고 제대로 조금 공부해보면 알 수 있는 내용이기 때문이다.

처음 GraphQL을 접한다면 GraphQL을 어떻게 사용해야 되는지 현재 프로젝트에 어떻게 적용하는지 어떻게 시작해야 지는지를 다 알려주는 책.

저는 너무 재밌게 흥미롭게 읽었습니다.

GraphQL을 공부하는 데 있어서 책을 구매하고 싶다면 위 책을 매우 추천해 드립니다.