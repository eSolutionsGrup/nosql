http://jsonplaceholder.typicode.com/

**all photos**
http://jsonplaceholder.typicode.com/photos

**get a photo**
http://jsonplaceholder.typicode.com/photos/1


**Timing Details With cURL**
https://blog.josephscott.org/2011/10/14/timing-details-with-curl/


curl-format.txt
```
time_namelookup: %{time_namelookup} \n
time_connect: %{time_connect} \n
time_appconnect: %{time_appconnect} \n
time_pretransfer: %{time_pretransfer} \n
time_redirect: %{time_redirect} \n
time_starttransfer: %{time_starttransfer} \n
——— \n 
time_total: %{time_total} \n
```

run
```
curl -w "@curl-format.txt" -o /dev/null -s http://jsonplaceholder.typicode.com/photos
```