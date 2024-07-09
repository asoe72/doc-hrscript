﻿# 6.2.4 HTTP client 통신 예제

```python
     import http_cli
     var cli=http_cli.HttpCli()
     var url, body, query, status_code
     var domain="http://192.168.1.200:8888"

     # get
     cli.get domain+"/device/direction"
     body = cli.body

     #check the communication status
     if cli.status>=400 or cli.status<0
        goto 99 		#http communication error
     endif

     # put
     url = domain+"/device/direction"
     body.ry=90
     cli.body=body
     cli.put(url, 3000, *Timeout)

     # post
     cli.body={ name: "WORK #32", color: "green", state: "OK" }
     cli.post domain+"/display/update", 5000, *Timeout

     # delete
     cli.delete(domain+"/items")

     end
     
  99 print "error status"
     
     *Timeout
     print "timeout"
```

