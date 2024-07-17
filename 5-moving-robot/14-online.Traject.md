# 5.14 online.Traject


### Description  
* As position are input to Ethernet through UDP or TCP communication, robot move toward the command. 

### Syntax 
```python
     global onl_trj
     var desired_pose 

     onl_trj=online.Traject()
     onl_trj.time_from_start=-1.0
     onl_trj.look_ahead_time=1.0
     onl_trj.interval=0.1
     onl_trj.init
     onl_trj.buf_in desired_pose
 
```

### Parameter 
* time_from_start : elapsed time from start position (-1: disable)  
* look_head_time : time delay for robot moving (unit : [s])  
* interval : time interval between commands (unit : [s])  
* init : online trajectory operation init  
* buf_in  : user should set the pose data or string data (ex. [0.000,90.000,0.000,0.000,-90.000,0.000]) in joint space coordinate



### Example
> joint angle data is obtained from "msg" command through "enet" command. 

```python
     import enet
     global enet0
     enet0=enet.ENet("tcp")
     enet0.ip_addr="192.168.1.213"
     enet0.lport=7000
     enet0.rport=7000
     var ret=enet0.open()
     ret=enet0.listen()
     ret=enet0.accept()

     global onl_trj
     onl_trj=online.Traject()
     onl_trj.time_from_start=-1.0
     onl_trj.look_ahead_time=1.0
     onl_trj.interval=0.1
     onl_trj.init

     var str_pose
10   enet0.recv
     str_pose=result()
     onl_trj.buf_in str_pose
     goto 10
     end 
```


--- 
{% hint style="info" %}

* The role of robot language "online.Traject()" is that robot move toward desired joint angle command from "enet" through communication.   

{% endhint %}
