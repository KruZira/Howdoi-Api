# Howdoi-Api under Maintenance

<p align="center"><strong>⚡ Never open your browser to look for help again ⚡</strong></p>

## <p align="center"><strong> Introduction to howdoi and it's Api </strong></p>

Are you a hack programmer? Do you find yourself constantly Googling for how to do basic programming tasks?

Suppose you want to know how to format a date in bash. Why open your browser and read through blogs (risking major distraction) when you can simply stay in the console and ask howdoi 👌

```
$ howdoi format date bash
> DATE=`date +%Y-%m-%d`
```

But Instead of this 👆, now you can use the Api

```
$ python3 howdoiapi.py "format date bash"

# put current date as yyyy-mm-dd in $date
# -1 -> explicit current date, bash >=4.3 defaults to current time if not provided
# -2 -> start time for shell
printf -v date '%(%Y-%m-%d)T\n' -1

# put current date as yyyy-mm-dd HH:MM:SS in $date
printf -v date '%(%Y-%m-%d %H:%M:%S)T\n' -1

# to print directly remove -v flag, as such:
printf '%(%Y-%m-%d)T\n' -1
# -> current date printed to terminal

```

# why did you make an api for howdoi

 You can't `pip install howdoi` in some os because 
 of some libraries that comes with howdoi, so why 
 not make a call to the Api and get a response

### From python

```markdown
import sys,requests,json

headers = {
    'Content-Type': 'application/x-www-form-urlencoded'}
data = f'txt={sys.argv[1]}'

sent_data = requests.post('http://howdoi.remote.moe', headers=headers, data=data)
print(sent_data.status_code)
data = json.loads(sent_data.json())
for i in data:
    print(i["answer"])
    print(i["link"])
```

### From curl

```markdown
curl -X POST -d "txt=format date bash" http://howdoi.remote.moe
```

### From JavaScript
**fetch**
```markdown
fetch('http://howdoi.remote.moe', {
    method: 'POST',
    headers: {
        'Content-Type': 'application/x-www-form-urlencoded'
    },
    body: 'txt=format date bash'
});
```
**JavaScript (Ajax)**

```
var url = "http://howdoi.remote.moe";

var xhr = new XMLHttpRequest();
xhr.open("POST", url);

xhr.setRequestHeader("Content-Type", "application/x-www-form-urlencoded");

xhr.onreadystatechange = function () {
   if (xhr.readyState === 4) {
      console.log(xhr.status);
      console.log(xhr.responseText);
   }};

var data = "txt=format date bash";

xhr.send(data);

```

### From Java

```
URL url = new URL("http://howdoi.remote.moe");
HttpURLConnection http = (HttpURLConnection)url.openConnection();
http.setRequestMethod("POST");
http.setDoOutput(true);
http.setRequestProperty("Content-Type", "application/x-www-form-urlencoded");

String data = "txt=format date bash";

byte[] out = data.getBytes(StandardCharsets.UTF_8);

OutputStream stream = http.getOutputStream();
stream.write(out);

System.out.println(http.getResponseCode() + " " + http.getResponseMessage());
http.disconnect();
```

### From PHP
```
<?php

$url = "http://howdoi.remote.moe";

$curl = curl_init($url);
curl_setopt($curl, CURLOPT_URL, $url);
curl_setopt($curl, CURLOPT_POST, true);
curl_setopt($curl, CURLOPT_RETURNTRANSFER, true);

$headers = array(
   "Content-Type: application/x-www-form-urlencoded",
);
curl_setopt($curl, CURLOPT_HTTPHEADER, $headers);

$data = "txt=format date bash";

curl_setopt($curl, CURLOPT_POSTFIELDS, $data);

//for debug only!
curl_setopt($curl, CURLOPT_SSL_VERIFYHOST, false);
curl_setopt($curl, CURLOPT_SSL_VERIFYPEER, false);

$resp = curl_exec($curl);
curl_close($curl);
var_dump($resp);

?>

```

### Check out the cli howdoi

 see [here](https://github.com/gleitz/howdoi)


### Built with 💕 by Kruz

**Python Cli Package 📦**

Contact [Telegram](https://t.me/Wishfox)

Find My Article on [Medium /Howdoi Api](https://medium.com/@odilikruz/how-the-howdoi-api-can-help-you-find-answers-to-questions-in-real-time-a54b4bf144eb)
