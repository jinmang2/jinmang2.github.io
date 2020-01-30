---
title: "[비전공자를 위한 자료구조 및 알고리즘] 우주 최강 러닛에서 듣는 온라인강의"
date: 2020-01-26 22:38:00 -0400
categories: DataStructure
---
## 비전공자의 설움, `러닛`에서 풀고자한 금융수학 전공자

안녕하세요,<br>
2020년 1월 24일부터 동년 4월 24일까지 러닛의 가디언즈로 활동하게된 진명훈입니다.

저는 금융수학을 전공한 비전공자로 현재는 챗봇회사에서 딥러닝 개발자로 근무하고 있습니다. 회사에서 협업을 진행하면서 비전공자기 때문에 소통이 안되는 부분이 존재했고, C언어, 도커, 자료구조 및 기획까지... 공부해야할 것들이 산처럼 많았습니다.<br>

이 모든 것들을 독학하기엔 시간이 효율적이지 못하고 불가능했기 때문에 여러 교육 플랫폼들을 찾아봤는데 정말 괜찮은 플랫폼이 있어 소개해드리고자 합니다.

## 러닛? 뭐하는 곳이지?
<img src="https://github.com/jinmang2/jinmang2.github.io/blob/master/assets/images/learnit_1.PNG?raw=true" width="800px" height="450px" alt="그림 설명" />

```
혼자 또 같이 하는 진짜 공부,
우주 최초 플립러닝 스터디 플랫폼
```

러닛은 위와 같은 이념을 가지고 운영하는 플립러닝 스터디 플랫폼으로, `programming`, `data science`, `marketing`, `business` 카테고리들에 대한 class를 운영하고 있습니다.

Online강의를 플립러닝 방식으로 진행하고 있고 수준급의 다양한 강의를 접할 수 있는 스터디 플랫폼이라고 하네요.

## 음... 알겠어. 러닛에 대해 소개좀 해줘.

### 1. **깔끔한 UI/UX 제공, 쉬운 접근성**

[https://www.learnit.co.kr/](https://www.learnit.co.kr/)로 이동하면 러닛 홈페이지로 가실 수 있습니다.

접속하시면 아래와 같은 깔끔한 화면이 제공되고

![image](https://github.com/jinmang2/jinmang2.github.io/blob/master/assets/images/learnit_main_page.PNG?raw=true)

`class`탭에서 원하는 강의를 선택하셔서

![image](https://github.com/jinmang2/jinmang2.github.io/blob/master/assets/images/learnit_classes.PNG?raw=true)

`마이페이지`에 들어가서 `지금 수강하기` 버튼을 클릭하면 간단하게 강의를 들을 수 있습니다! (모바일에서도 간편하게 진행 가능해요~)

![image](https://github.com/jinmang2/jinmang2.github.io/blob/master/assets/images/learnit_mypage.PNG?raw=true)

### 2. **플립 러닝**

![image](https://github.com/jinmang2/jinmang2.github.io/blob/master/assets/images/learnit_fliplearnit.PNG?raw=true)

러닛은 `플립러닝 플랫폼`인데요, 플립러닝이란 혼자할 수 있는 것은 혼자서 하고, 같이할 수 있는 것은 같이 하는 수업 방식으로

1. 다같이 모일 시간을 절약 가능하고
2. 혼자서 공부하는 것보다 훨씬 능률이 좋게 학습할 수 있습니다.

### 3. **학습 피드 기능**

강의를 들으며 혼자 공부하다보면 막힐 때가 있잖아요? 이럴 때 러닛의 효과적인 기능이 `학습 피드`입니다.

![image](https://github.com/jinmang2/jinmang2.github.io/blob/master/assets/images/learnit_feed.PNG?raw=true)

하단 강의자료 옆 `학습피드` 버튼을 누르고 궁금한 부분을 작성하면 멘토분이 깔끔하게 이에 대한 답변을 해주십니다ㅎㅎ.


## 간단 강의 후기

포스팅을 작성하기 전, `비전공 개발자를 위한 자료구조+알고리즘` 강의의 커리귤럼 중 `1. 자료구조와 알고리즘`, `2. 배열과 연결리스트` 강의를 들었는데요, 

1. 설명을 명확하고 쉽게 말씀을 해주시고
2. 개념에 대한 설명만 있는 것이 아니라 실제 배열과 연결리스트를 `python`으로 구현하는 방법까지,
3. 그리고 실제로 자신이 학습할 수 있도록 `DoublyLinkedList`구현 및 에러 처리 과제까지!!

너무나도 좋은 강의였습니다 :)

![image](https://github.com/jinmang2/jinmang2.github.io/blob/master/assets/images/learnit_4.PNG?raw=true)

위는 제가 실제로 들은 강의 영상 중 일부를 캡처한 부분인데요, 강사님이 직접 코딩하는 내용을 보며 수강자가 직접 학습할 수 있게 도움을 주신답니다!

저도 에러 처리를 추가하고 과제를 수행 중인데 아직 완성하지 못했어요 ㅠㅠ 주말에 과제를 완성하고 뒤의 강의를 들을 예정입니다~
```python
# 노드 정의
# 노드를 표현할 representation 정의
class Node(object):
    def __init__(self, data):
        self.data = data
        self.next = None
        self.prev = None
    
    def __repr__(self):
        return 'Node({}, link)'.format(self.data)
        
# 강사님이 작성한 LinkedList
# 몇 가지 에러처리 작성
class LinkedList(object):
    def __init__(self):
        dummy = Node('<HEAD>')
        self.head = dummy
        self.tail = dummy
        self.n = 0
        
    def append(self, new_node):
        self.tail.next = new_node
        self.tail = new_node
        self.n += 1
        
    def get(self, idx):
        if idx > self.n:
            raise ValueError(
                "'idx' is larger than the total number of nodes")
        elif idx == 0:
            return self.head
        elif idx == self.n:
            return self.tail
        else:
            cur_node = self.head
            i = 0
            while i != idx:
                cur_node = cur_node.next
                i += 1
            return cur_node
    
    def insert(self, target_node, new_node):
        new_node.next = target_node.next
        target_node.next = new_node
        self.n += 1
        
    def delete(self, prev_node):
        target_node = prev_node.next
        prev_node.next = prev_node.next.next
        del target_node
        self.n -= 1
        
    @classmethod
    def _isNode(cls, data):
        if isinstance(data, Node):
            return data
        else:
            return Node(data)
        
    def __str__(self):
        cur = self.head
        result = []
        while cur:
            result.append(cur.data)
            cur = cur.next
        return " - ".join(result)

# 강사님이 작성한 LinkedList 객체를 상속받아 작성한 내 LinkedList
# get, insert를 Node를 input으로 받아도 되도록 수정
# delete가 idx만 받아도 작동되도록 
class SinglyLinkedList(LinkedList):
    def __init__(self):
        super().__init__()
        
    def append(self, node):
        node = self._isNode(node)
        super().append(node)
        
    def get(self, node, use_idx=False):
        if not isinstance(node, Node):
            if isinstance(node, int) and use_idx:
                return super().get(node)
            else:
                node = Node(node)
        cur_node = self.head
        while cur_node.data != node.data:
            if cur_node is None:
                raise ValueError('None of them matched')
            cur_node = cur_node.next
        return cur_node
    
    def insert(self, idx, node):
        if self.n == 0:
            raise EmptyError("No node exists in LinkedList.")
        target_node = self.get(idx, use_idx=True)
        node = self._isNode(node)
        super().insert(target_node, node)
        
    def _insert(self, target_node, new_node):
        super().insert(target_node, new_node)
            
    def delete(self, idx):
        if self.n == 0:
            raise EmptyError('No node exists in LinkedList.')
        prev_node = self.get(idx, use_idx=True)
        super().delete(prev_node)
        
    def _delete(self, prev_node):
        super().delete(prev_node)
        
    def clear(self):
        self.head.next = None
        self.tail = self.head
        self.n = 0
        
    def __str__(self):
        cur_node = self.head.next
        string = self.head.data + '-> '
        if cur_node is None:
            string += '"EMPTY"'
        while cur_node:
            string += str(cur_node.data)
            if cur_node.next:
                string += ' -> '
            cur_node = cur_node.next
        return string + ' <-<TAIL>'
           
# 현재 작성중인 이중연결리스트 과제!
# 주말에 완료할 예정 ㅠㅠ
class DoublyLinkedList(LinkedList):
    def __init__(self):
        super().__init__()
        
    def append(self, node):
        node = self._isNode(node)
        node.prev = self.tail # prev도 연결해줌
        super().append(node)
        
    def get(self, node, idx=False):
        if not isinstance(node, Node):
            if isinstance(node, int) and idx:
                if node < (self.n // 2):
                    super().get(node)
                else:
                    cur_node = self.tail
                    i = self.n
                    while i != node:
                        cur_node = cur_node.prev
                        i -= 1
                    return cur_node
            else:
                node = Node(node)
        cur_node = self.head
        while cur_node.data != node.data:
            if cur_node is None:
                print('None of them matched')
                return -1
            cur_node = cur_node.next
        return cur_node
    
    def insert(self, idx, node):
        if self.n == 0:
            raise EmptyError("No node exists in LinkedList.")
        target_node = self.get(idx, use_idx=True)
        node = self._isNode(node)
        super().insert(target_node, node)
    
class EmptyError(Exception):  # 에러 처리
    pass
```
[소스 코드 바로보기!](https://nbviewer.jupyter.org/github/jinmang2/DataStructure_and_Algorithm/blob/master/HW1.LinkedList.ipynb)

저는 향후 주차별로 1강의를 듣고 과제를 수행, 이를 제 [github.com/jinmang2/DataStructure_and_Algorithm](https://github.com/jinmang2/DataStructure_and_Algorithm)에 업로드할 예정이고,

이 강의를 수강함으로써 성장할 제 모습이 기대가 되네요 ㅎㅎ

나머진 추가로 강의를 듣고 다음 포스팅에서 뵙겠습니다~

> 본 포스팅은 러닛 가디언즈 활동의 일부로 강의 콘텐츠를 제공받아 직접 체험하고 작성한 솔직한 후기입니다.
