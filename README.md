# Development-of-Autonomous-Driving-System

<h1 align="center">
  <img src='./img/' alt="" width="">

  <div>팀 퓨리오사</div>
  <h2 align="center">  싸피레이스 :trophy: 우승</h2>
</h1>


# :one: 프로젝트 개요

## 1. 개발 기간 

| 개발기간 | 24.05.24 ~ 24.07.04 |
| --- | --- |

## 2. 구성 팀

| 팀원 | 역할 | 세부 내용 | 
| --- | --- | --- |
| 박준영 | Team Leader, Process Developer | PID 알고리즘 개발, 복구 시스템 개발 |
| 임용구 | Process Developer | 알고리즘 오차 검증 |
| 최봉준 | Process Developer | PID 알고리즘 개발, 장애물 회피 시스템 개발 |

## 3. 팀 프로젝트 목표

SSAFY에서 개최하는 SSAFY RACE(싸피레이스) 자율주행 알고리즘 경진 대회의 가장 어려운 맵인 싸피맵에 대해서 1등을 하기 위함이다. 

가장 빠른 방법으로 결승선에 통과하되, 다른 차들과 경쟁하여 그 누구보다 먼저 들어감이 가장 중요하며, 예선전에서는 자동차가 혼자 달려서 가장 빠른 순서대로 들어가는 자동차가 결승전에 참가할 수 있음으로 해당 사항을 유의하며 알고리즘을 작성해야 한다.

이 Repo는 싸피레이스에서 가장 어려운 맵인 싸피맵에서 최우승상을 받은 회고록을 작성하기 위함이다. (++ 알고리즘 회고록)


</br>  
</br>  

# :two: 회고록

거의 반년이 지난 지금이지만 싸피레이스 싸피 맵에서 우승했던 그 과정들을 회고하면서 작성해보려고 한다.   

또한, 싸피맵에서 작성했던 코드들을 리뷰하면서 내가 어떤 코드를 작성했었고, 또한 이 코드가 어떤 식으로 구동되었으며, 개선사항들은 뭐가 필요한지에 대해서, 혹은 지금의 나라면 어떤 방법으로 다시 코드를 구현했을지에 대해서 다시 한번 회고를 하려고 한다.   

## 1. 왜 싸피레이스에 참여했는지?

싸피레이스를 알게된 계기는 싸피가 시작되는 1월이었다. 싸피에 입과하면서 한 기수 위 선배들이 참여한 싸피레이스 대회를 보게 되었는데, 영상을 보는 내내 싸피레이스가 매력적으로 느껴졌었다.

여러 자동차들이 주행하는 모습을 보면, 어떤 자동차는 정주행으로 움직이는 차량, 곡선으로 움직이는 차량, 다른 자동차를 견제하면서 움직이는 차량, 커브길이 있을 때에는 밖에서 안으로 들어오는 차량 등등 다양한 방법으로 주행하는 차량들이 있음을 알 수 있었다. 그 때 당시에는 '어떻게 코드에 개발자의 생각이 담겨서 저렇게 특성이 보이는 차량으로 변할 수 있을까' 라는 생각을 많이 했었던 것 같다. 또한, 각자의 팀들이 치밀하게 준비한 전략들을 보면서 '나도 저렇게 해보고 싶다' 라는 생각을 많이 했었던 것 같다.

## 2. 팀 구성 과정

싸피레이스는 총 3인이 1개의 팀으로 구성되는데, 반에 상관없이 각자 인원을 구인해서 결성한다. 나는 반에서 싸피레이스에 관심을 가지는 친구들을 설득해서 팀을 구성했었다. 팀 구성 초기 과정에서는 다들 그냥 호기심만 가지고 우승을 해야겠다라는 목표는 따로 가지고 있지 않았지만, 어찌저찌 잘 구했던 것 같다.....   

전체 팀은 약 300 팀이 구성되었지만, 대회가 끝난 지금에서야 생각해보건데 진심으로 하는 팀은 해봐야 100 팀도 안되는 것 같다는 생각이 든다. 코드 테스트를 해볼 때 배틀을 해볼 수 있는데, 제대로 된 팀은 몇 안되었던 걸로 기억한다.

## 3. 대회 기간 중 개발 과정

프로젝트 개발 기간은 위에 약 40일 정도 적은 것 같은데, 실제 개발했던 기간은 2주도 안되었던 것 같다. 싸피레이스의 시작은 방학 기간과도 같기 때문에 좀 놀다가 막바지에 새벽까지 개발했었다.

자율주행 코드 개발에 대해서 간단히 요약하자면, 가장 빠른 자동차가 우승하는 코드를 짜면 된다. 어떤 방법으로든 결승선에 가장 먼저 도착하는 차량이 우승하는 것이다. 하지만, 주어지는 환경 변수들은 그렇게 쉽지 않다.   

싸피레이스에서는 맵에 대한 정보와 자동차에 대한 정보가 0.1초 마다 API로 전달되는데, 그 API를 받아서 0.1초 안에 계산하여 return 하는 것이 중요하다. 따라서 알고리즘을 작성하려면 0.1초 안에 구현해야 하는데, 파이썬 기준으로는 통상적으로 200만번 안에 계산을 해야하는 것이다. 다만, 서버와 통신을 한다는 점과 일부 데이터가 오류로 반환된다거나 혹은 데이터가 정확하게 리턴되지 않는 경우도 생각해야 한다. 따라서, 실시간으로 데이터를 주고 받는 상황에서는 오류에 대해서도 많이 고민해봐야 한다.

정확한 정보는 말할 수 없지만, 대략적으로는 차량에 대한 다양한 변수들(속도, 위치, 각도 etc...), 도로에 대한 정보(방향, 각도, 거리 etc...)와 장애물과 상대방 차량에 대한 정보가 주어진다. return 값을 받는 시점에서 주어지는 정보들을 가지고 최선의 알고리즘을 작성해야하는 것이다. 여기서 팁을 주자면, 우리 팀은 차량의 State를 많이 고려했던 것 같다. 현재 차량이 어떤 상태인지에 대해서 먼저 규정하고 그 상태에 대해서 문제가 될만한 요소가 접근하거나 혹은 아주 짧은 미래에 방해를 할 수도 있을 것이라고 여겨지는 상황 변수들에 대해서는 어떻게든 방향을 틀던지 속도를 줄이던지 이런 방법을 통해서 제어를 했었다.

우리는 자율주행 코드에 있어서 PID 알고리즘을 적용하려고 많이 노력했었다. PID 알고리즘은 자율주행에 대해서 학습하면서 알게 되었는데, 해당 알고리즘은 자동차의 컨트롤러 역할을 수행한다. 0.1초 라는 짧은 시간 안에 차량의 오차값을 return 하고 오류를 수정하기에 적합한 알고리즘이라고 생각했다. 이 외에도 자율주행 모드와 복구 모드를 따로 두어 차량이 정상적인 주행 상태가 아니라면 복구 모드를 활성화 시키도록 작성했다. 이 모드들을 따로 적용하기 위해 따로 PIDController라는 클래스를 정의했었고, 각자의 코드가 영향 받지 않게 결합성이 낮도록 함수로 모듈화를 하도록 노력했었다.

개발한 알고리즘을 최적화하는 과정은 맘먹은대로 쉽지 않았다. 코드를 작성한 부분이 어째선지 제대로 작동하지 않을때도 많았고, 단지 수치값을 1만 수정했었을 뿐인데, 엄청난 오차를 보여주며 제대로 구동하지 않을 때도 많았다. 우리는 알고리즘을 개발하는 과정 속에서 임의로 만든 변수들을 각 파라미터로 두고 많은 테스트 보드를 작성해서 테스트를 해봤다. 근데, 테스트 보드를 작성해도 뭐가 좋고 나쁜지 몰라서 그냥 가장 빠른걸로 채택했다... 주행 과정 중에서 원치 않은 과정이 나오는 테스트보드가 가장 빠를 때도 있었지만 그런 결과가 베스트로 생길 때는 주관적으로 제거했었다. 주관적으로 처리했을 때는 수치로 정확하게 검증하지 않았던 점이 매우 아쉬운 부분이었지만, 해당 코드를 직접 작성했던 작성자의 직관으로 처리했던 테스트 보드들은 의외로 제거하는 것이 정답이었을 때가 많았다. (직관을 무시하고 제일 빠른걸로 들고갔는데, 다른 변수 테스트하다가 다 터짐.... 나중에서야 중요한 사실을 알게 되어서 테스트 보드 하나 통쨰로 날림...)

싸피배틀 맵 같은 경우에는 싸피 측에서 만든 싸피봇과 배틀할 수 있는 기회도 있는데, 싸피봇 자동차는 총 LV 1부터 4까지 주어진다. 1부터 4까지 전부 이기면 소정의 선물을 받을 수도 있다. 우리 팀은 우승팀답게 다 이겼다. 의외로 이 싸피봇들은 꽤나 강적인데, LV2에서 거의 모든 팀들이 다 꺽인다... 알고보니 LV3 인가 LV4는 전년도 대회 우승자 코드였다고 했었던 것 같다. 다음 번 싸피 봇은 우리 팀의 코드가 올라갈 수도 있을 것 같다.

마지막 주차가 정말 개발 과정에 있어서 하이라이트 였는데, 여태까지 작성했던 코드를 계속 테스트하면서 결과를 확인하고 문제있던 부분을 수정하는 행위를 반복했다. 테스트 한번 당 총 4~6분 정도 걸리기도 하고, 코드를 올릴 수 있는 제한도 있기 때문에 신중하게 검토하고 테스트를 등록했었던 것 같다. 이 마지막 주차에 싸피봇 LV4도 이기고 가장 빠른 시간도 도출해낼 수 있었는데, 역시 알고리즘 구현에서 가장 중요한 건 디버깅과 노가다였다... 시간을 투자한 만큼 결과가 나올 수 있었던 것 같다.

## 4. 결승 당일

결승 당일은 특별한게 없었다. 당일까지도 결과를 모른 채로 기다리고 있었는데, 어느 순간 조용히 부른다. 그래서 갔더니 갑자기 방송을 탔다... 아무것도 모른채로 어버버버 하다가 바보처럼 웃기만하고 끝났던 것 같다. 사실 방송 과정 중에 라이브로 경기를 계속 보고 있었는데, 정신이 너무 없어서 누가 우승인지 어디까지 갔는지 잘 보지도 못했다.

--- 작성중...


# :three: 코드 회고록

---- 작성중...