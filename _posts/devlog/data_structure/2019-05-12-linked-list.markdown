---
layout: post
title:  "링크드리스트 (Linked List)의 종류와 특징"
subtitle:   "링크드리스트 (Linked List)의 종류와 특징"
categories: devlog
tags: datastructure
comments: true
---

## Linked List란

---

Linked List(연결 리스트)는 각 노드들이 **일자로** 링크(**연결**) 되어 있는 구조를 말합니다.
각각의 노드는 자신 다음의 노드나 이전 노드를 가르키고 있습니다.

## Linked List의 종류

---

- 단일 연결 리스트
- 이중 연결 리스트
- 원형(선형) 연결 리스트

## 구현 API ( 간단하게 )

---

- int InsertNode(T newData, bool addTail = true)
  - 노드를 맨 앞이나 맨 뒤에 추가한다.
- int InsertNode(T newData, int index)
  - 노드를 원하는 index에 삽입한다.
- int RemoveNode(T removeData, bool matchRemoveAll = false)
  - 데이터와 일치하는 노드를 삭제한다.
- int RemoveAt(int index)
  - 원하는 인덱스의 노드를 삭제한다.
- void PrintNode()
  - 모든 노드를 출력한다.

## 단일 연결 리스트

---

![600px-Single_linked_list](https://user-images.githubusercontent.com/10609257/57582432-b691c600-74ff-11e9-9848-05225163cbc9.png)

### 특징

---

- 각 노드는 자신의 다음 노드만 가르킵니다.

### 구현 코드

---

[코드 보기](https://gist.github.com/Youngchangoon/3a7616b67cd38c2d5024abb18f6b6088)

## 이중 연결 리스트

---

![600px-Single_linked_list](https://user-images.githubusercontent.com/10609257/57582432-b691c600-74ff-11e9-9848-05225163cbc9.png)

### 특징

---

- 각 노드는 자신의 이전과 다음의 노드를 가르킵니다.

### 구현 코드

---

[코드 보기](https://gist.github.com/Youngchangoon/213435e5feb49acba0e5616b8bcb09d5)

## 원형 연결 리스트

---

![600px-Circurlar_linked_list](https://user-images.githubusercontent.com/10609257/57582434-b691c600-74ff-11e9-84c9-e411c670a53e.png)

### 특징

---

- 시작 노드와 끝노드가 이어져 있습니다.

### 구현 코드

---

[코드 보기](https://gist.github.com/Youngchangoon/b60c96b72e6d60e45baaf3610eb8c5ed)

### 출처

---

- [위키백과](https://ko.wikipedia.org/wiki/%EC%97%B0%EA%B2%B0_%EB%A6%AC%EC%8A%A4%ED%8A%B8)