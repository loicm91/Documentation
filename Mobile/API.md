#API : Du fichier JSON à la Vue (Sans le Service)

##App.Js : 
####Créer la route dans les .state :

```

.state('app.contacts', {
    url: '/contacts',
    views: {
      'menuContent': {
        templateUrl: 'templates/contacts.html',
         controller: 'ContactsCtrl'
      }
    }
  })
  .state('app.contact', {
    url: '/contacts/:idUser',
    views: {
      'menuContent': {
        templateUrl: 'templates/contact.html',
        controller: 'ContactCtrl'
      }
    }
  })
 
```
##Controller.js :
####Créer les controllers :

```
.controller('ContactsCtrl', function($scope, $http) {
  $http({
  method: 'GET',
  url: 'http://carbillet.net/api-digitalGrenoble/users/' //mettre le '/' à la fin pour aller chercher le dossier .php
}).then(function successCallback(response) {
    // this callback will be called asynchronously
    // when the response is available
    //console.log(response.data)
    $scope.contacts = response.data.users;

  }, function errorCallback(response) {
    // called asynchronously if an error occurs
    // or server returns response with an error status.
  });
 
})

.controller('ContactCtrl', function($scope, $stateParams, $http){
  console.log($stateParams.idUser)
  var user = $stateParams.idUser;
  $http({
  method: 'GET',
  url: 'http://carbillet.net/api-digitalGrenoble/users/' //mettre le '/' à la fin pour aller chercher le dossier .php
}).then(function successCallback(response) {
    // this callback will be called asynchronously
    // when the response is available
    //console.log(response.data)
    $scope.contacts = response.data.users;
    $scope.user = user;
    console.log($scope.contacts)
    
  }, function errorCallback(response) {
    // called asynchronously if an error occurs
    // or server returns response with an error status.
  });
})
```

##Dans la Vue : 
###Contacts.html : 

```
<ion-view view-title="Contacts">
  <ion-content>
    <ion-list>
      <ion-item ng-repeat="contact in contacts" ui-sref="app.contact({idUser: contact.idUser})">
        {{contact.name}} {{contact.lastname}}
      </ion-item>
    </ion-list>
  </ion-content>
</ion-view>
```
####On veut cliquer sur le contact et afficher les détails dans une autre page : contact.html

```
<ion-view view-title="Contact">
  <ion-content>
  	<ion-list ng-repeat="contact in contacts" >
  		<ion-item ng-if="user == contact.idUser"> <!--'ng-if' pour mettre en condition le fait qu'on veut les détails de l'id que l'on récupère en cliquant sur le contact depuis la liste-->
    		<h1>{{contact.name}}</h1>
    		<h2>{{contact.lastname}}</h2>
    	</ion-item>
    </ion-list>
  </ion-content>
</ion-view>
```
