# disabled-options
Handling disabled options using ng-options.

```
.directive('allowDisabledOptions',['$timeout', function($timeout) {
    return function(scope, element, attrs) {
        var ele = element;
        var scopeObj = attrs.allowDisabledOptions;
        $timeout(function(){
            var DS = ele.scope()[scopeObj];
            var options = ele.children();
            for(var i=0;i<DS.length;i++) {
                if(!DS[i].enabled) {
                    options.eq(i).attr('disabled', 'disabled');
                }
            }
        });
    }
}])
```
Use the directive in html like
```
<select ng-model="myModel" ng-options="o.id as o.name for o in Arr" allow-disabled-options="Arr"></select>
```

#### Note:
Arr is an array of object containing property enabled.
```
[
  {
    "id": 1,
    "name" "Test-1",
    "enabled": true
  },
  {
    "id": 2,
    "name" "Test-2",
    "enabled": false
  },
  {
    "id": 3,
    "name" "Test-3",
    "enabled": true
  }
]
```
