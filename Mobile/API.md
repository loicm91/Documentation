#API : Du fichier JSON à la Vue

##App.Js : 
####Créer la route dans les .states :

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
