#Current location (html) localise le portable par wi-fi ou internet ou GPS

```
<ion-view view-title="Maps">
    <ion-content>
        <div map-lazy-load="https://maps.google.com/maps/api/js">
  <ng-map center="current-location" zoom="18">
  	 <marker position="current-location" title="are" animation="Animation.DROP"></marker>
  </ng-map>
</div>
    </ion-content>
</ion-view>

```


#Controller NgMap
```
angular.module('starter.mapcontroller', [])

.controller('MapsCtrl', function($scope, NgMap){
  NgMap.getMap().then(function(map) {
    // console.log(map.getCenter());
    // console.log('markers', map.markers);
    // console.log('shapes', map.shapes);

  });
})
```
