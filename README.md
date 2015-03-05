Jasmine 2.0 - TeamCity Reporter
=======================


###How to use

1) In your spec runner add the following javascript code, after loading the [Jasmine 2.0](http://jasmine.github.io/2.0/introduction.html) scripts

```Javascript
var TeamcityReporter = jasmineRequire.TeamcityReporter();
window.teamcityReporter = new TeamcityReporter();
jasmine.getEnv().addReporter(window.teamcityReporter);
```

2) Execute your spec runner on an agent. An easy way to do this is to use the [PhantomJS](http://phantomjs.org) runner included with [TeamCity.Node](http://jasmine.github.io/2.0/introduction.html)

Select the PhantomJS build runner

![](https://raw.githubusercontent.com/scottiemc7/Jasmine2.0TeamCityReporter/master/images/BuildRunner.png)

Under `JavaScript to Execute` add the following, making sure to replace the path to your local .html spec runner

![](https://raw.githubusercontent.com/scottiemc7/Jasmine2.0TeamCityReporter/master/images/ScriptSource.png)

    var fs = require('fs');
    var url = 'file://localhost/' + fs.workingDirectory + PATH_TO_YOUR_LOCAL_SPEC_RUNNER_HTML_FILE;
    var page = require('webpage').create();
    var finishedReg = /##teamcity\[progressFinish/gi;
    
    //output any console messages and check to see if all of our testing is complete
    page.onConsoleMessage = function(msg, lineNum, sourceId) {
      console.log(msg);
      if(msg.match(finishedReg)) {
        phantom.exit();
      }
    };
    
    page.open(url, function (status) {});


<<<<<<< HEAD
=======
![](https://raw.githubusercontent.com/WilliamDoman/Jasmine2.0TeamCityReporter/master/images/Tests.PNG)


### Details of failed tests

![](https://raw.githubusercontent.com/WilliamDoman/Jasmine2.0TeamCityReporter/master/images/Details.PNG)
>>>>>>> dd64bde7a9e1981b237e5e84877c684723c9c2fb
