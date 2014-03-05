easysse-client
==============

Listen to Server-Sent Events, sincerely, most definitely


Demo
----

Please see [node-easysse][server] for a demo


Usage
-----

Using [node-easysse][server] with express

```js
var require("easysse");
app.get("/chat-stream", easysse);

app.post("/chat", function(req, res) {
  easysse.emit("chat", req.body.username, req.body.message);
});
```

Using easysse-client

```html
<script src="easysse-client.js"></script>
<script>
  var client = easysseClient.connect("/chat-stream");

  client.on("chat", function(username, message){
    console.log(username, "says", message);
  });

  $.post("/chat", {username: "mjackson", message: "hehe"});
  // "mjackson says hehe"
</script>
```


API
---

* **on**(eventType, cb) &mdash; add an event listener of
  `eventType`.

  (*alias* `addEventListener`)

* **off**(eventType, cb) &mdash; remove an event listener of
  `eventType`.

  (*alias* `addEventListener`)


Compatibility
-------------

Tested on Chrome 33
Please submit any other compatibility reports


License
-------

&copy; 2014 nkitsune, mosdef.biz
easysse-client may be freely distributed under the BSD license.
For all details and documentation:
https://github.com/mosdefbiz/easysse-client

[server]: https://github.com/mosdefbiz/node-easysse
