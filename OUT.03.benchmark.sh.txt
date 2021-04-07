================================================================================
START:    Mon, Apr  5, 2021  7:39:49 PM
PWD:      /c/Users/demouser/Desktop/nd00333_AZMLND_C2-master/starter_files
CMD:      bash benchmark.sh
================================================================================

This is ApacheBench, Version 2.3 <$Revision: 1879490 $>
Copyright 1996 Adam Twiss, Zeus Technology Ltd, http://www.zeustech.net/
Licensed to The Apache Software Foundation, http://www.apache.org/

Benchmarking a85baf51-a2f1-472f-834e-25a5c9a10c70.southcentralus.azurecontainer.io (be patient)...INFO: POST header == 
---
POST /score HTTP/1.0
Content-length: 812
Content-type: application/json
Authorization: Bearer eeinpPN0cRjaQog4Hu9mo0yebStKO4yZ
Host: a85baf51-a2f1-472f-834e-25a5c9a10c70.southcentralus.azurecontainer.io
User-Agent: ApacheBench/2.3
Accept: */*


---
LOG: header received:
HTTP/1.0 200 OK
Content-Length: 32
Content-Type: application/json
Date: Mon, 05 Apr 2021 19:39:49 GMT
Server: nginx/1.10.3 (Ubuntu)
X-Ms-Request-Id: 617ccd5b-404e-4b4a-abb5-16c0119e4ddd
X-Ms-Run-Function-Failed: False

"{\"result\": [\"no\", \"no\"]}"
LOG: Response code = 200
LOG: header received:
HTTP/1.0 200 OK
Content-Length: 32
Content-Type: application/json
Date: Mon, 05 Apr 2021 19:39:49 GMT
Server: nginx/1.10.3 (Ubuntu)
X-Ms-Request-Id: a7b4d7e9-ccb6-46fd-9a61-c6cf3ed65c7b
X-Ms-Run-Function-Failed: False

"{\"result\": [\"no\", \"no\"]}"
LOG: Response code = 200
LOG: header received:
HTTP/1.0 200 OK
Content-Length: 32
Content-Type: application/json
Date: Mon, 05 Apr 2021 19:39:49 GMT
Server: nginx/1.10.3 (Ubuntu)
X-Ms-Request-Id: 6b526d97-a645-4c53-9ef5-cbb0eccebc32
X-Ms-Run-Function-Failed: False

"{\"result\": [\"no\", \"no\"]}"
LOG: Response code = 200
LOG: header received:
HTTP/1.0 200 OK
Content-Length: 32
Content-Type: application/json
Date: Mon, 05 Apr 2021 19:39:49 GMT
Server: nginx/1.10.3 (Ubuntu)
X-Ms-Request-Id: 32e87608-fa5e-4866-bc33-a9859142eead
X-Ms-Run-Function-Failed: False

"{\"result\": [\"no\", \"no\"]}"
LOG: Response code = 200
LOG: header received:
HTTP/1.0 200 OK
Content-Length: 32
Content-Type: application/json
Date: Mon, 05 Apr 2021 19:39:49 GMT
Server: nginx/1.10.3 (Ubuntu)
X-Ms-Request-Id: 1e0bd428-ba46-4436-b12f-47ad7d5c9263
X-Ms-Run-Function-Failed: False

"{\"result\": [\"no\", \"no\"]}"
LOG: Response code = 200
LOG: header received:
HTTP/1.0 200 OK
Content-Length: 32
Content-Type: application/json
Date: Mon, 05 Apr 2021 19:39:49 GMT
Server: nginx/1.10.3 (Ubuntu)
X-Ms-Request-Id: 8112fb1f-9672-4a51-a100-183decfbf2a7
X-Ms-Run-Function-Failed: False

"{\"result\": [\"no\", \"no\"]}"
LOG: Response code = 200
LOG: header received:
HTTP/1.0 200 OK
Content-Length: 32
Content-Type: application/json
Date: Mon, 05 Apr 2021 19:39:50 GMT
Server: nginx/1.10.3 (Ubuntu)
X-Ms-Request-Id: 6b6c520b-030c-4452-8ecb-b82a9535cd14
X-Ms-Run-Function-Failed: False

"{\"result\": [\"no\", \"no\"]}"
LOG: Response code = 200
LOG: header received:
HTTP/1.0 200 OK
Content-Length: 32
Content-Type: application/json
Date: Mon, 05 Apr 2021 19:39:50 GMT
Server: nginx/1.10.3 (Ubuntu)
X-Ms-Request-Id: b9c5899a-38f2-420c-b9dc-efbaff034bc7
X-Ms-Run-Function-Failed: False

"{\"result\": [\"no\", \"no\"]}"
LOG: Response code = 200
LOG: header received:
HTTP/1.0 200 OK
Content-Length: 32
Content-Type: application/json
Date: Mon, 05 Apr 2021 19:39:50 GMT
Server: nginx/1.10.3 (Ubuntu)
X-Ms-Request-Id: 0a0425b3-3b90-459f-8283-c1e8eaf49329
X-Ms-Run-Function-Failed: False

"{\"result\": [\"no\", \"no\"]}"
LOG: Response code = 200
LOG: header received:
HTTP/1.0 200 OK
Content-Length: 32
Content-Type: application/json
Date: Mon, 05 Apr 2021 19:39:50 GMT
Server: nginx/1.10.3 (Ubuntu)
X-Ms-Request-Id: f6a5d087-5173-49c4-a473-e9b045b3a526
X-Ms-Run-Function-Failed: False

"{\"result\": [\"no\", \"no\"]}"
LOG: Response code = 200
..done


Server Software:        nginx/1.10.3
Server Hostname:        a85baf51-a2f1-472f-834e-25a5c9a10c70.southcentralus.azurecontainer.io
Server Port:            80

Document Path:          /score
Document Length:        32 bytes

Concurrency Level:      1
Time taken for tests:   0.884 seconds
Complete requests:      10
Failed requests:        0
Total transferred:      2590 bytes
Total body sent:        10640
HTML transferred:       320 bytes
Requests per second:    11.31 [#/sec] (mean)
Time per request:       88.431 [ms] (mean)
Time per request:       88.431 [ms] (mean, across all concurrent requests)
Transfer rate:          2.86 [Kbytes/sec] received
                        11.75 kb/s sent
                        14.61 kb/s total

Connection Times (ms)
              min  mean[+/-sd] median   max
Connect:        1    3   1.7      2       7
Processing:    69   86  12.4     87     105
Waiting:       69   86  12.4     86     105
Total:         71   88  12.6     93     107

Percentage of the requests served within a certain time (ms)
  50%     93
  66%     93
  75%     96
  80%    104
  90%    107
  95%    107
  98%    107
  99%    107
 100%    107 (longest request)

================================================================================
END:      Mon, Apr  5, 2021  7:39:50 PM
================================================================================

