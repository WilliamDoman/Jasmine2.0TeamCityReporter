Jasmine 2.0 - TeamCity Reporter
=======================


To use: in your spec runner javascript code add the following

```Javascript
var TeamcityReporter = jasmineRequire.TeamcityReporter();
window.teamcityReporter = new TeamcityReporter();
jasmine.getEnv().addReporter(window.teamcityReporter);
```



