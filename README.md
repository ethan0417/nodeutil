NodeUtil
====================

This is just a tool collect for easy use of some tool library. I will pack some operation for more easy to use.

## Install

<pre>
npm install nodeutil
</pre>

## Usage

<pre>
var nu = require('nodeutil');
</pre>

## Using logger

<pre>
var log = nu.logger.getInstance();
log.info('Test logger...');
</pre>

## Using dateutil

<pre>
var dateutil = no.dateutil;
var pattern = 'yyyymmdd hh24:mi:ss';
dateutil.getNowString(pattern);
dateutil.getDateString(new Date(), pattern)
</pre>

## Using step

<pre>
var Step = nu.step;
Step(
  function step1(){
    //do something...
    return something1;
  },
  function step2(step1_returned){
    //do something
    return something2;
  },
  ...
)
</pre>

## Using cfgutil

<pre>
var cfgutil = nu.cfgutil;
//read from json file
var cfg = cfgutil.readJsonCfg('path to json config file');
</pre>

## Using mailutil

```javascript
var mailer = nu.mailutil;

mailer.init(
  {"smtpOptions":{"service":"Gmail", "auth": {"user": "your-account","pass": "your-password"}}, "sender": "NO-REPLY <no-reply@micloud.tw>"}
);

mailer.sendNodeMailAsync('receiver@gmail.com',
  'test mail send...',
  'send mail OK!',
  true,
  function(){
    console.log('Send mail done...');
  }
);
```

Using mailutil through localhost sendmail service

```javascript
var mailer = require('nodeutil').mailutil;

mailer.init(
      {"smtpOptions":{"host":"localhost"}, "sender": "NO-REPLY <no-reply@micloud.tw>"}
    );

mailer.sendNodeMailAsync('yourmail@gmail.com',
  'test mail send...',
  'send mail OK!',
  true,
  function(){
    console.log('Send mail done...');
  }
);
```

## Convert Json to Table
```javascript
var json2table = nu.json2table;
var json = [{aaa:123, bbb:223}, {aaa:223, bbb:323}];
console.log(json2table.ConvertJsonToTable(json));
```
The result:
```html
<table border="1" cellpadding="1" cellspacing="1"><thead><tr><th>aaa</th><th>bbb</th></tr></thead><tbody><tr><td>123</td><td>223</td></tr><tr><td>223</td><td>323</td></tr></tbody></table>
```
