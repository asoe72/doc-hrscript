# 5.14 online.Traject


## 설명 
* UDP나 TCP 통신에 의해 이더넷으로 로봇의 위치데이터가 입력될 때, 이를 반영하여 로봇을 제어 


## 문법 
```python
     global onl_trj
     var desired_pose 

     onl_trj=online.Traject()
     onl_trj.time_from_start=-1.0
     onl_trj.look_ahead_time=1.0
     onl_trj.interval=0.1
     onl_trj.init
     onl_trj.exe desired_pose
 
```

## 파라미터 
* time_from_start : 시작 지령으로 부터 경과된 시간 (-1= 미사용)
* look_ahead_time : 지령 출력을 위한 지연시간 (단위 [s])
* interval : 지령 사이의 시간 (단위 [s])
* init : 온라인 지령상태 초기화 
* exe <포즈데이터> : <포즈> 데이터는 로봇의 축 각도로 설정  



## 사용 예 
> enet 명령어를 통해 외부에서 로봇 각축 데이터 msg 명령을 전달 받는다. 

```python
     import enet
     global enet0
     enet0=enet.ENet("tcp")
     enet0.ip_addr="192.168.1.213"
     enet0.lport=7000
     enet0.rport=7000
     enet0.open()
     var ret=enet0.open()
     ret=enet0.listen()
     ret=enet0.accept()

     global onl_trj
     onl_trj=online.Traject()
     onl_trj.time_from_start=-1.0
     onl_trj.look_ahead_time=1.0
     onl_trj.interval=0.1
     onl_trj.init

     var desired_pose
     var msg
10   enet0.recv
     msg=result()
     desired_pose=Pose(msg)
     onl_trj.exe desired_pose
     goto 10
     end 
```


--- 
{% hint style="info" %}

* online.Traject 명령어는 enet 명령어를 통해 외부로 부터  통신을 이용하여 전달 받은 외부 지령으로, 로봇을 움직이게 합니다.    

{% endhint %}
