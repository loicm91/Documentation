#API : Du fichier JSON à la Vue

##App.Js : 
####Créer la route dans les .states :

'''

  .state('app.contacts', {
    url: '/contacts',
    views: {
      'menuContent': {
        templateUrl: 'templates/contacts.html',
         controller: 'ContactsCtrl'
      }
    }
  })
 
  '''
