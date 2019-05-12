---
layout: post
title:  "링크드리스트 (Linked List) 종류와 특징"
subtitle:   "링크드리스트 (Linked List) 종류와 특징"
categories: devlog
tags: datastructure
---

# Linked List란?
---

Linked List(연결 리스트)는 각 노드들이 **일자로** 링크(**연결**) 되어 있는 구조를 말합니다. 

각각의 노드는 자신 다음의 노드나 이전 노드를 가르키고 있습니다. 

# Linked List의 종류
---

- 단일 연결 리스트
- 이중 연결 리스트
- 원형(선형) 연결 리스트

## 구현할 API ( 간단하게 )
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

[코드 보기](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/bcb5ea06-d242-4d2a-9653-3568e51d7670/Program.cs?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Credential=ASIAT73L2G45F3Z5NWFI%2F20190512%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20190512T124238Z&X-Amz-Expires=86400&X-Amz-Security-Token=AgoJb3JpZ2luX2VjEKv%2F%2F%2F%2F%2F%2F%2F%2F%2F%2FwEaCXVzLXdlc3QtMiJHMEUCICi3nf98domqkB5HCUuiTN6U8oRcoL4BfULRqxArN%2B8NAiEAvSJRwwnsy0XpOMs39XBmSeKoeGYhvwaB70k%2F%2Ffmm1P4q4wMIpP%2F%2F%2F%2F%2F%2F%2F%2F%2F%2FARAAGgwyNzQ1NjcxNDkzNzAiDJQr4QWE1x0Hp1YyQyq3A8FQo38tplQ8Uzl0RES938oYYq7Ia6J1A6TybaFDpbz7Wonr5IGbTwAyOd%2BPDOKbKrQ2KRLaLzT7nHsTjVUgtdPO8P25fc6SCzPtL03cUAJG2eEaNOoVXjndAbFpKCcCNx3squ%2FIY8y4TQE%2FiFTY%2BwDRPV0QKV%2FTr1LYSZOrqq%2FmY2nzrLY6kWw7Xz7dq92Kfo6MP4NMw%2BULkDAW3%2FkP5T0pBIB3soXjC5R6BwiOd%2F%2FIf2vPdw1EsJrrgYdZChAT33QOe9RNGmal8HtSHfxUfbayKa%2Frp%2BWME7mXR9AhDKBuS6YjnQj%2BXoZ0z3bRnR%2B9OtFEfXQF%2BhTFUDizhZIWKFT33luCPSKfEXmzNFJ15B%2FIz%2F5jQlaCvBcu3wqE9wtASLwU%2FknfiAk8xqSRa14Q6RSitUWMmKfP6jS68%2B8FErRsQPIR%2FLxL8z5zpdPlnyj9tic9lWoUk6nFDlBb1%2FguloSsO6nUqJXbCO3Fk46mtbypWxDAkPmNN5VP2yeYg2z6o0xPNuMbCf8FsNIVpbtP0iFle7iol5HU055%2F9op1D9r9o41oNlzw2Vj7vS8hQFjiSKcCZ2klCZcwrvHf5gU6tAHddRvgyGi8h%2FkGjoBkHvlkpUXKq1PNUvbnqEimxSVZX3%2FLrUKJaGbpVsNc%2F%2FWRp6Wgt23pTFVNEuzm5y8CYGkFj0FIPulYLkxDUiGOcdNSpVzPPlYX7OnPsdVfSKIsQeUtDvzVHYaNwZPZ9dBEryZ7U4%2FCBb%2FY71SHs3lmtfJgtc8FDMsstG757vnoJSmWwjIcp0GzJ88S4rOVBYCvLHmBTbtZuO%2BEthkSxKFzJzd5FENGLsI%3D&X-Amz-Signature=4f411b98e05545b31951ba547c4bc21000e9272e39fcf932a4b4bbede25a420e&X-Amz-SignedHeaders=host&response-content-disposition=filename%20%3D%22Program.cs%22)


## 이중 연결 리스트
---

![600px-Single_linked_list](https://user-images.githubusercontent.com/10609257/57582432-b691c600-74ff-11e9-9848-05225163cbc9.png)

### 특징
---

- 각 노드는 자신의 이전과 다음의 노드를 가르킵니다.

### 구현 코드
---

[코드 보기](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/b855bca7-8fb6-4458-a333-a56ed07ce28b/Program.cs?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Credential=ASIAT73L2G45AEU5QORE%2F20190512%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20190512T124548Z&X-Amz-Expires=86400&X-Amz-Security-Token=AgoJb3JpZ2luX2VjEKv%2F%2F%2F%2F%2F%2F%2F%2F%2F%2FwEaCXVzLXdlc3QtMiJFMEMCICUsHIuCOIPLShDJVffdMHe7QNTa1EJswBQVasQBzSWLAh9Y1zh64J533NMyzVeEzjyoWHsSkte2MRnclOWNPahhKuMDCKT%2F%2F%2F%2F%2F%2F%2F%2F%2F%2FwEQABoMMjc0NTY3MTQ5MzcwIgyA%2FyBbH32M02uAXMkqtwOcQ1yLLrWCMAsTgZiYlittCm%2BSK%2FJWHzs6l9ID%2BW93n735ppWT4CChNHJUgdhiqn9ZNqcavJoWYARsB1hZEhMbwydTB0ENqT54o9MfTZOUxN5Iu2ILXoMKnT2pnhZEuP8Hl2ul8ttL1A4AWwnJA%2Bq1Qhoo8yh%2BwsL6Kgs%2FmFYsp%2FAq%2Fraqb33cGXr4BTm0cIYBPGW1YkwxZYTOIgh1NAgwHETb1N5wZD6Bfd6Lp2s9hQOPYbQ9QRaWwh5JXETtT2upWm%2BfhXjG4kvSOK5fA4HIK1Vr7fDC0m9IkhJNT5o%2F%2Fa7JSJnpx%2BAl7gnhy9eIilFlQ4%2Fkiv2dSMh811hsBru%2FyUThthaADMdTpYwgZMtNmlqTBu%2BFoonqabc%2BXHrhTO75Y4ikma9ZHeL80rjdz2o%2BdLVkr9j1S9DTwq15yUFWV85qt5dvBUTViTH7Be%2Bayfm2UCdXOBJqO0LY95boiL86rC4WgAOMeioNrMv5RXo4w7qVeTlS4pNBa4iMxYW2QwHcLXViBsk7JCUDxcmQpw3ImS9%2B3GJ%2BiTN1BYBjnXyMhOjjf1Osl3ryaW0FguGci95wjTyFBa37MJCA4OYFOrYB3rmGjRxiUahGxpKPNhEIzHZxpEWXTJPdD6wdhdLJI%2Bq7SejweFErmJvQHMRLVoA2I0rwlCYK9s0EZiTSGTviXFeBmdWHMJUQdMMhzzWcOaZy3D8KVPYD7TOgqy8nX07dk3%2Bx7efH29%2BbYFza7BQ5SAZ7hPLqbMsMt3zIM5fwu%2BVztn57MFr7Hx6oaEq2XTh9fge4nnME%2Fbwqcq%2BjVOiukIRjbcmzslu9QziSFz2WLOEAqpZUdTA%3D&X-Amz-Signature=f1f68905652a8b158cee99bfc7b782b9a0609d40ea82d16f59d6313c3027b795&X-Amz-SignedHeaders=host&response-content-disposition=filename%20%3D%22Program.cs%22)

## 원형 연결 리스트
---

![600px-Circurlar_linked_list](https://user-images.githubusercontent.com/10609257/57582434-b691c600-74ff-11e9-84c9-e411c670a53e.png)

### 특징
---

- 시작 노드와 끝노드가 이어져 있습니다.

### 구현 코드
---

[코드 보기](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/6fd0ec5f-b976-4e2b-89b1-d8864cc7f292/Program.cs?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Credential=ASIAT73L2G45LJZVT2FA%2F20190512%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20190512T124559Z&X-Amz-Expires=86400&X-Amz-Security-Token=AgoJb3JpZ2luX2VjEKv%2F%2F%2F%2F%2F%2F%2F%2F%2F%2FwEaCXVzLXdlc3QtMiJGMEQCIC05kiPwT8pcRjCGxRd4unlA76DWDh5uGWRGjU8YtSW3AiB2axwz5uCy5rFlz8cAn9ROZhuEaqYVXeXwa3T8HpHGiyrjAwik%2F%2F%2F%2F%2F%2F%2F%2F%2F%2F8BEAAaDDI3NDU2NzE0OTM3MCIMkroIeaqinuKzPAuaKrcDOorHRUX3HAkUoWiJSIcTZL0goNhRrumvqRBKFAjOxAO1o6mRCPKcVcWFA3ZREJcMup%2FiXFG%2Biuqqp2TYqAbBKdIpJBzJuYaA5XXY8Wdae%2Fn3b67hR1ozCBr9p36Z36%2B8dapgx3ByXQuOrNzoDYEDPbBvNjYqwWTF2rB%2BOjYW6OBePkD%2F3kxzROTGAIqPUkKaQm7fazttrbYBxaANiPbsZlT6E%2Fhqaop%2BfKZD4M9i9b23%2F%2FhvlbeX4DcyaB5ywkhJvmb6Onf0jv22rFUpKk2cee0qGXQy5XkIVOEjABYw%2FBKhf2%2BNbcovvwTaQilQ4nM7NNfRUMFn4QPJvKzl2E%2BW9L%2FnMqsWNqURr8OfVn0BoGil5HtYndrt4lG9hzMTs4U5JVuwQTJMmYFnbpcjYfH%2BE4BNRUSd9bVRs1aV9sZPS7APL28mwPX6dZVYDDwEBixsJZDIqNznsi9fsVcnnjxFEJHNM%2FULi%2F7Yd6Y1sX%2F8tHGkuQ8r%2B2i0FAeKiiqKbhM5lqmD%2BFAHO7u6R6iG5eFCEuPGdRI5sl3favERgr%2B4m%2B6oC%2FczQ2G1Iik8et6BeRkQBtGE9nYurzCogODmBTq1AansoSAB5Fo7dGEH%2FoywTegPxORzh%2FUO1fyqoMYlk7eQ24c3PkXxGOhYns5k%2FB8EEj1yy1yC%2B9FeG9gbs%2Bs9oeAADNImgAqaBXEjKAKfCwK1OCQdLz%2F2vkoV%2FAP9JZUZsCHgRd8IN5VgPpTZayzgCs0zFSIczmcsfhSPw9K2KZhm9D%2Bs2eikq16D45J4Y%2BqeMjXn9azdtix77eXbojp8ai0XKL%2FAIf9OoIfvjymHS2GZ2BLkS3Q%3D&X-Amz-Signature=6c493f404c661bc403fa7f5e8226d48fda93b07b968b5aaf3a80acb714d814c5&X-Amz-SignedHeaders=host&response-content-disposition=filename%20%3D%22Program.cs%22)

### 출처
---

- [위키백과](https://ko.wikipedia.org/wiki/%EC%97%B0%EA%B2%B0_%EB%A6%AC%EC%8A%A4%ED%8A%B8)