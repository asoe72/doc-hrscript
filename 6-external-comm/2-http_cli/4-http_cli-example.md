# 6.2.4 Examples of HTTP Client Communication

```python
import http_cli
var cli=http_cli.HttpCli()

var domain="http://192.168.1.200:8888"

# get
cli.get domain+"/device/direction"
print cli.body.ry
     
# put
cli.body.ry=90
cli.put domain+"/device/direction"
     
# post
cli.body=={ name: "WORK #32", color: "green", state: "OK" }
cli.post domain+"/display/update"

# delete
cli.delete domain+"/items/3"

end
```

