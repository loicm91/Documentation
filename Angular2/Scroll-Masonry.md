# Infinite Scroll

## Prérequis

##### Difficilement applicable sur une galerie de photo : la galerie avec Angular 2 charge toutes les photos dans un ngFor, alors que
l'infinite scroll charge au fur et à mesure les fichiers lorsque l'on "Scroll Down"

TUTO :
https://www.npmjs.com/package/angular2-infinite-scroll

https://github.com/orizens/ngx-infinite-scroll (ngx-infinite-scroll que j'utilise ici )

Il faut aussi savoir qu'il faut mettre autour d'une liste la div infinite-scroll et lui mettre un style overflow-y: scroll,
width et un height, pour créer une fenêtre.

### home.component.ts
```
import { Component, OnInit } from '@angular/core';


@Component({
  selector: 'app-home',
  templateUrl: './home.component.html',
  styleUrls: ['./home.component.css']
})
export class HomeComponent implements OnInit {

  images = [];
	array = [];
	sum = 12;
  scrollDistance = 2;	
  selectedImage;
  
     constructor(){
        this.images = [
        '../../assets/image/JMF-Valentine/IMG_7946.jpg',
        '../../assets/image/AB-Loane/_Y5A9270.jpg',
        '../../assets/image/CB-Chinatown/2-web.jpg',
        '../../assets/image/AB-Anna/13.jpg',
        '../../assets/image/JP-Voodoo/EDITO VOODOO8465348.jpg',
        '../../assets/image/Apprecial/4.jpg',
        '../../assets/image/EC-MaximeD/CLOTIS_8287.JPG',
        '../../assets/image/MS-Cite/1E7A2018.jpg',
        '../../assets/image/YJ-Jouvanceau/1.jpg',
        '../../assets/image/Mobiendo/1.jpg',
        '../../assets/image/AB-Dasha/_Y5A7970_retouch_Mads Bjerre Henriksen.jpg',
        '../../assets/image/JMF-Valentine/IMG_7946.jpg',
        '../../assets/image/AB-Loane/_Y5A9270.jpg',
        '../../assets/image/CB-Chinatown/2-web.jpg',
        '../../assets/image/AB-Anna/13.jpg',
        '../../assets/image/JP-Voodoo/EDITO VOODOO8465348.jpg',
        '../../assets/image/Apprecial/4.jpg',
        '../../assets/image/EC-MaximeD/CLOTIS_8287.JPG',
        '../../assets/image/MS-Cite/1E7A2018.jpg',
        '../../assets/image/YJ-Jouvanceau/1.jpg',
        '../../assets/image/Mobiendo/1.jpg',
        '../../assets/image/AB-Dasha/_Y5A7970_retouch_Mads Bjerre Henriksen.jpg'
      ] 
    
      for (let i = 0; i < this.sum; ++i) {
        this.array.push(this.images[i]);
      }
      

    }

  ngOnInit() {
   
  }

setSelectedImage(image){
  this.selectedImage= image;	
}


navigate(direction){
  var index = this.images.indexOf(this.selectedImage)+(direction ? 1: -1);
  if(index >= 0 && index < this.images.length){
    this.selectedImage = this.images[index];	
  }
}
//Pour que ça boucle à l'infini :
// addItems(startIndex, endIndex) {
//   for (let i = 0; i < this.sum; ++i) {
//     this.array.push(this.images[i]);
//   }
// }
//Sinon juste lister ce qu'il y a :
addItems(startIndex, endIndex) {
  for (let i = startIndex; i < endIndex; ++i) {
    this.array.push(this.images[i]);
  }
}
onScrollDown () {
  console.log('scrolled down!!')
  const start = this.sum;
  this.sum += 2;
  this.addItems(start, this.sum);
}

onScrollUp () {
  console.log('scrolled up!!')
}

  // pictures = [
  //   {url: '../../assets/image/JMF-Valentine/IMG_7946.jpg'},
  //   {url: '../../assets/image/AB-Loane/_Y5A9270.jpg'},
  //   {url: '../../assets/image/CB-Chinatown/2-web.jpg'},
  //   {url: '../../assets/image/AB-Anna/13.jpg'},
  //   {url: '../../assets/image/JP-Voodoo/EDITO VOODOO8465348.jpg'},
  //   {url: '../../assets/image/Apprecial/4.jpg'},
  //   {url: '../../assets/image/EC-MaximeD/CLOTIS_8287.JPG'},
  //   {url: '../../assets/image/MS-Cite/1E7A2018.jpg'},
  //   {url: '../../assets/image/YJ-Jouvanceau/1.jpg'},
  //   {url: '../../assets/image/Mobiendo/1.jpg'},
  //   {url: '../../assets/image/AB-Dasha/_Y5A7970_retouch_Mads Bjerre Henriksen.jpg'}
  // ]
}

```
### home.component.html
```
<masonry>

  <div 
          infinite-scroll
          [infiniteScrollDistance]="scrollDistance"
          [infiniteScrollUpDistance]="1.5"
          [infiniteScrollThrottle]="50"
          [scrollWindow]="true"
          (scrolled)="onScrollDown()"
          (scrolledUp)="onScrollUp()">

          <masonry-brick *ngFor="let image of array" >
          <img class="rangement" src="{{image}}">
            </masonry-brick>

  </div>
</masonry
```
### App.module.ts

```
...
import { InfiniteScrollModule } from 'ngx-infinite-scroll';


@NgModule({
  declarations: [
    AppComponent,
    AboutComponent,
    RepoBrowserComponent,
    RepoListComponent,
    RepoDetailComponent,
    HomeComponent,
    HommeComponent,
    FemmeComponent,
    ContactComponent,
    ImagesComponent,
    GalleryComponent
  
  ],
  imports: [
    BrowserModule,
    FormsModule,
    ReactiveFormsModule,
    HttpModule,
    // VirtualScrollModule,
    Ng2UploaderModule,
    InfiniteScrollModule,
    RouterModule.forRoot(rootRouterConfig, { useHash: true })
  ],
  providers: [
    GithubService
  ],
  bootstrap: [ AppComponent ]
})
export class AppModule {

}

```
