# I] Current location (html) localise le portable par wi-fi ou internet

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
# II] $cordovaGeolocation : Permet de se localiser en direct avec la puce du téléphone

Dans le app.js :
```
angular.module('starter', ['ionic', 'starter.controllers', 'starter.mapcontroller', 'starter.services', 'ngMap', 'ngCordova'])

.run(function($ionicPlatform, $cordovaGeolocation) {
  $ionicPlatform.ready(function() {
    // Hide the accessory bar by default (remove this to show the accessory bar above the keyboard
    // for form inputs)

    $cordovaGeolocation.getCurrentPosition()
    .then(function(){

    })

    if (window.cordova && window.cordova.plugins.Keyboard) {
      cordova.plugins.Keyboard.hideKeyboardAccessoryBar(true);
      cordova.plugins.Keyboard.disableScroll(true);

    }
    if (window.StatusBar) {
      // org.apache.cordova.statusbar required
      StatusBar.styleDefault();
    }
  });
})
```
Dans le controller : 

```
.controller('GeoCtrl', function($scope, NgMap, $cordovaGeolocation) {

	NgMap.getMap().then(function(map) {
    // console.log(map.getCenter());
    // console.log('markers', map.markers);
    // console.log('shapes', map.shapes);

  });

  var posOptions = {timeout: 10000, enableHighAccuracy: false};
  $cordovaGeolocation
    .getCurrentPosition(posOptions)
    .then(function (position) {
      var lat  = position.coords.latitude
      var long = position.coords.longitude

      $scope.currentPosition = [lat, long];

    }, function(err) {
      // error
    });

});
```

Dans la vue : 

```
<ion-view view-title="Maps">
    <ion-content scroll="false">
        <div map-lazy-load="https://maps.google.com/maps/api/js">
  <ng-map center="currentPosition" zoom="18">
  	 <marker position="current-location" title="Je suis là" animation="Animation.DROP"></marker>
  </ng-map>
</div>
    </ion-content>
</ion-view>

```
