# Infinite Scroll

## Prérequis

##### Difficilement applicable sur une galerie de photo : la galerie avec Angular 2 charge toutes les photos dans un ngFor, alors que
l'infinite scroll charge au fur et à mesure les fichiers lorsque l'on "Scroll Down"

TUTO :
https://www.npmjs.com/package/angular2-infinite-scroll

https://github.com/orizens/ngx-infinite-scroll (ngx-infinite-scroll que j'utilise ici )

Il faut aussi savoir qu'il faut mettre autour d'une liste la div infinite-scroll et lui mettre un style overflow-y: scroll,
width et un height, pour créer une fenêtre.

### Gallery.component.ts
```
import { Component, Input } from '@angular/core';
import { InfiniteScrollModule } from 'ngx-infinite-scroll';

// http://4dev.tech/2016/11/creating-an-angular2-image-gallery/
// Tuto pour la galerie
@Component({
  selector: 'gallery',
  templateUrl: './gallery.component.html',
  styles: [`
  	
  	.modal-content {
	    width: 670px !important;
	}
	.btn-back, .btn-forward{
	position:absolute;
	opacity:0.9;
	background-color:black;
	padding:10px;
	top:190;
	color:white;
	text-weight:bold;
	cursor:pointer;
	}
 
	.btn-back{
		right:612px;
	}
	.btn-forward{
		left:612px;
	}

  `]
})
export class GalleryComponent { 
	images = [];
	array = [];
	sum = 4;
	scrollDistance = 2;	
  
   //@Input() datasource;
   selectedImage;

   constructor(){
      this.images = [
	{"url":"app/images/Motif/ecusson.png"},
	{"url":"app/images/Motif/original.png"},
	{"url":"app/images/Motif/jePeuxPas.png"},
	{"url":"app/images/Motif/mrGeek.png"},
	{"url":"app/images/Motif/mrsGeek.png"},
	{"url":"app/images/Motif/proudGeek.png"},
	{"url":"app/images/Motif/sexyGeek.png"},
	{"url":"app/images/Motif/starGeek.png"},
	{"url":"app/images/Motif/ecusson.png"},
	{"url":"app/images/Motif/original.png"},
	{"url":"app/images/Motif/jePeuxPas.png"},
	{"url":"app/images/Motif/mrGeek.png"},
	{"url":"app/images/Motif/mrsGeek.png"},
	{"url":"app/images/Motif/proudGeek.png"},
	{"url":"app/images/Motif/sexyGeek.png"},
	{"url":"app/images/Motif/starGeek.png"},
	{"url":"app/images/Motif/ecusson.png"},
	{"url":"app/images/Motif/original.png"},
	{"url":"app/images/Motif/jePeuxPas.png"},
	{"url":"app/images/Motif/mrGeek.png"},
	{"url":"app/images/Motif/mrsGeek.png"},
	{"url":"app/images/Motif/proudGeek.png"},
	{"url":"app/images/Motif/sexyGeek.png"},
	{"url":"app/images/Motif/starGeek.png"},
	{"url":"app/images/Motif/ecusson.png"},
	{"url":"app/images/Motif/original.png"},
	{"url":"app/images/Motif/jePeuxPas.png"},
	{"url":"app/images/Motif/mrGeek.png"},
	{"url":"app/images/Motif/mrsGeek.png"},
	{"url":"app/images/Motif/proudGeek.png"},
	{"url":"app/images/Motif/sexyGeek.png"},
	{"url":"app/images/Motif/starGeek.png"}
	
      ];

      for (let i = 0; i < this.sum; ++i) {
	      this.array.push(this.images[i]);
	    }
      
      
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
	addItems(startIndex, endIndex) {
	    for (let i = 0; i < this.sum; ++i) {
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

	
}
```
### Gallery.component.html
```
<div class="modal fade" id="selectedImageModal" >
	  <div class="modal-dialog" role="document">
	    <div class="modal-content">
	      <div class="modal-body">
	         <div class="selectedImage" *ngIf="selectedImage">
			   <img src="{{selectedImage.url}}" >
			   <div class="btn-back" (click)=navigate(false)>
			      &lt;
			   </div>
			   <div class="btn-forward" (click)=navigate(true)>
			      &gt;
			   </div>
			</div>

	      </div>
	    </div>
	  </div>
</div>
  	<ul id="thumbnailsList">

    <div 
            infinite-scroll
            [infiniteScrollDistance]="scrollDistance"
            [infiniteScrollUpDistance]="1.5"
            [infiniteScrollThrottle]="50"
            [scrollWindow]="false"
            (scrolled)="onScrollDown()"
            (scrolledUp)="onScrollUp()"
            style="overflow-y: scroll; width: 300px; height: 500px;">

  	   <li *ngFor="let image of array" >
  	      <img src="{{image.url}}" class="tn"
  		  width="191" height="146"  
  		  data-toggle="modal" data-target="#selectedImageModal"
                  (click)=setSelectedImage(image)>
  	   </li>

	</div>
  	</ul>

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
