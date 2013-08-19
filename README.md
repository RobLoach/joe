# Joe

[![Build Status](https://secure.travis-ci.org/bevry/joe.png?branch=master)](http://travis-ci.org/bevry/joe "Check this project's build status on TravisCI")
[![NPM version](https://badge.fury.io/js/joe.png)](https://npmjs.org/package/joe "View this project on NPM")
[![Gittip donate button](http://badgr.co/gittip/bevry.png)](https://www.gittip.com/bevry/ "Donate weekly to this project using Gittip")
[![Flattr donate button](https://raw.github.com/balupton/flattr-buttons/master/badge-89x18.gif)](http://flattr.com/thing/344188/balupton-on-Flattr "Donate monthly to this project using Flattr")
[![PayPayl donate button](https://www.paypalobjects.com/en_AU/i/btn/btn_donate_SM.gif)](https://www.paypal.com/au/cgi-bin/webscr?cmd=_flow&SESSION=IHj3DG3oy_N9A9ZDIUnPksOi59v0i-EWDTunfmDrmU38Tuohg_xQTx0xcjq&dispatch=5885d80a13c0db1f8e263663d3faee8d14f86393d55a810282b64afed84968ec "Donate once-off to this project using Paypal")

Joe is a JavaScript testing framework that actually works. Unlike Mocha, we won't die on you abruptly when executing dynamically created tests and are always able to associate the correct test to the correct corresponding test suite. Switching from Mocha is trivial and only takes a few minutes. 


## Install

### Backend

1. [Install Node.js](http://bevry.me/node/install)
2. `npm install --save-dev joe joe-reporter-console`

### Frontend

1. [See Browserify](http://browserify.org/)


## Usage

### Example

``` javascript
// define your test suite
require('joe').describe('suite name', function(describe,it){
	// group together items into sub suites if you desire
	describe('sub suite name', function(describe,it){
		// create both synchronous and asynchronous tests
		it('synchronous test', function(){
			// do your stuff
		});
		it('asynchronous test name', function(complete){
			setTimeout(function(){
				// do your stuff
				complete();
			},500);
		});
	});
	// you can also define tests dynamically when using the completion callback on the group
	describe('lets create dynamic tests', function(describe,it,done){
		setTimeout(function(){
			it('a synchronous dynamic test',function(){
				// do your stuff
			});
			done();
		},500)
	});
});
```

```
$ node example.js 
suite name
suite name ➞  sub suite name
suite name ➞  sub suite name ➞  synchronous test
suite name ➞  sub suite name ➞  synchronous test ✔   
suite name ➞  sub suite name ➞  asynchronous test name
suite name ➞  sub suite name ➞  asynchronous test name ✔   
suite name ➞  sub suite name ✔  
suite name ➞  lets create dynamic tests
suite name ➞  lets create dynamic tests ➞  a synchronous dynamic test
suite name ➞  lets create dynamic tests ➞  a synchronous dynamic test ✔   
suite name ➞  lets create dynamic tests ✔  
suite name ✔  

3/3 tests ran successfully, everything passed
```


### Complete API

[Complete API guide here.](https://github.com/bevry/joe/wiki/Using)


### Custom Reporters

[Instructions and listing here.](https://github.com/bevry/joe/wiki/Using-Custom-Reporters)


## History
You can discover the history inside the [History.md](https://github.com/bevry/joe/blob/master/History.md#files) file


## License
Licensed under the incredibly [permissive](http://en.wikipedia.org/wiki/Permissive_free_software_licence) [MIT License](http://creativecommons.org/licenses/MIT/)
<br/>Copyright &copy; 2012+ [Bevry Pty Ltd](http://bevry.me)