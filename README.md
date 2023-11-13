PDF(with screenshots) - https://rb.gy/v215ld

Q. Implement an Application in AngularJs, 
with minimum two components. Investigate how to perform Unit 
Testing for any two components in the Application, write appropriate 
test cases of the elements in the components for the Unit Testing. 
Or 
Design and implement a Single Page Application using AngularJs. 
Investigate how to perform routing and navigation, use of service and 
dependency injection, use 
of pipes and structural directives. Do it in a group (minimum 3 
students and maximum 5 
students). Same Groups of DA-1can be Continued. 


Title of the Project: “Rotten Potatoes” – Online Movie reviews web 
application 

Aim: Create a Single Page Application (SPA) using Angular that allows 
users to explore and rate movies.

Introduction 

The project is a Single Page Application (SPA) built with Angular, 
designed to provide users with an interactive platform for exploring 
and rating movies. It incorporates various Angular features and offers 
a seamless user experience through dynamic navigation and realtime movie data. 

Angular Features 

- Routing and Navigation 
- Components and Templates 
- Services and Dependency Injection 
- HTTP Client for API interaction 
- Two-way Data Binding 
- Forms and Validation 
- ngFor and ngIf for dynamic content 
- Angular Modules for code organization
  
Components and Functions

1. Login Component:

 - Handles user authentication. 
 - Validates user credentials. 
There are many functions used in this login component like login(), 
Login Component, beforeEach(). 
-Login(): 
 It handles with the input given by the user in login page. 
 It display an error message if any of the requirements are not 
met.

Code: 

login() { 
 if(this.username.trim().length == 0) { 
 this.errorMsg = "Username is required"; 
 } 
 else if (this.username.trim().length == 0) { 
 this.errorMsg = "Password is required"; 
 } 
 else { 
 this.errorMsg = ""; 
 let res= this.auth.login(this.username, this.password); 
 if(res === 200) { 
 this.router.navigate(['home']); 
 }if(res == 403) { 
 this.errorMsg = "Invalid Credentials" 
 } 
 } 
 } 
 
-LoginComponent(): 

 We have included login function in this function which 
implements OnInit() function. 
 It comes under typescript. 

Code: 

export class LoginComponent implements OnInit { 
 username=""; 
 password=""; 
 errorMsg=""; 
 constructor(private auth: AuthService, private router: Router) { } 
 ngOnInit(): void { 
 } 
 login() { 
 if(this.username.trim().length == 0) { 
 this.errorMsg = "Username is required"; 
 } 
 else if (this.username.trim().length == 0) { 
 this.errorMsg = "Password is required"; 
 } 
 else { 
 this.errorMsg = ""; 
 let res= this.auth.login(this.username, this.password); 
 if(res === 200) { 
 this.router.navigate(['home']); 
 }if(res == 403) { 
 this.errorMsg = "Invalid Credentials" 
 } 
 } 
 } 
 
} 
-beforeEach(): 
 It is used to fetch the dependencies with the help of injection 
function. 
 It is also a part of typescript. 
Code: 
beforeEach(() => { 
 TestBed.configureTestingModule({ 
 declarations: [LoginComponent] 
 }); 
 fixture = TestBed.createComponent(LoginComponent); 
 component = fixture.componentInstance; 
 fixture.detectChanges(); 
 }); 
 it('should create', () => { 
 expect(component).toBeTruthy(); 
 }); 
}); 

2. Header Component
   
There are many functions used like beforeEach(), it(). 
-beforeEach() 
 It is used to fetch the dependencies with the help of injection 
function. 
 It is also a part of typescript. 
Code
beforeEach(() => { 
 TestBed.configureTestingModule({ 
 declarations: [HeaderComponent] 
 }); 
 fixture = TestBed.createComponent(HeaderComponent); 
 component = fixture.componentInstance; 
 fixture.detectChanges(); 
 }); 
-goToHome(): 
 For navigating to home. 
Code: 
goToHome() { 
 this.router.navigate(['home']); 
 } 
-Logout(): 
 For logging out. 
Code: 
logout() { 
 this.router.navigate(['login']); 
 } 
 
3. Movie Details Component
   
 - Displays detailed information about a selected movie. 
 - Allows users to rate and review movies. 
Functions used like getTheMovie(), beforeEach(). ngOnIt(). 
-getTheMovie() 
 To get into the movie. 
Code 
getMovie() { 
 this.http.get(this.url).subscribe((movies) => { 
 this.movies = movies; 
 let index = this.movies.findIndex( 
 (movie: { id: string }) => movie.id == this.id 
 ); 
 if (index > -1) { 
 this.movie = this.movies[index]; 
 } 
 }); 
 } 
-beforeEach() 
 It is used to fetch the dependencies with the help of injection 
function. 
 It is also a part of typescript. 
Code
beforeEach(() => { 
 TestBed.configureTestingModule({ 
 declarations: [HeaderComponent] 
 }); 
 fixture = TestBed.createComponent(HeaderComponent); 
 component = fixture.componentInstance; 
 fixture.detectChanges(); 
 }); 
-ngOnIt() 
 It is used to do additional initialization if needed. 
Code
ngOnInit(): void { 
 this.type = this.route.snapshot.params['type']; 
 this.id = this.route.snapshot.params['id']; 
 if (this.type === 'trending') { 
 this.url = 'http://localhost:4200/assets/data/trendingmovies.json'; 
 } 
 if (this.type === 'theatre') { 
 this.url = 'http://localhost:4200/assets/data/theatre-movies.json'; 
 } 
 if (this.type === 'popular') { 
 this.url = 'http://localhost:4200/assets/data/popularmovies.json'; 
 } 
 this.getMovie();
 }
 
4. Home Component

 - Handles home functionality. 
There are functions used like beforeEach(), it(), ngOnInit(), 
getTrendingMovies, getTheatreMovies, getPopularMovies. 
-beforeEach() 
 It is used to fetch the dependencies with the help of injection 
function. 
 It is also a part of typescript. 
Code 
beforeEach(() => { 
 TestBed.configureTestingModule({ 
 declarations: [HeaderComponent] 
 }); 
 fixture = TestBed.createComponent(HeaderComponent); 
 component = fixture.componentInstance; 
 fixture.detectChanges(); 
 }); 
-ngOnIt(): 
 It is used to do additional initialization if needed. 
Code
ngOnInit(): void { 
 this.type = this.route.snapshot.params['type']; 
 this.id = this.route.snapshot.params['id']; 
 if (this.type === 'trending') { 
 this.url = 'http://localhost:4200/assets/data/trendingmovies.json'; 
 } 
 if (this.type === 'theatre') { 
 this.url = 'http://localhost:4200/assets/data/theatre-movies.json'; 
 } 
 if (this.type === 'popular') { 
 this.url = 'http://localhost:4200/assets/data/popularmovies.json'; 
 } 
 this.getMovie(); 
 } 
-getTrendingMovies 
 For getting trendingmovies in the home page. 
Code 
 getTrendingMovies() { 
 this.http 
 .get('http://localhost:4200/assets/data/trending-movies.json') 
 .subscribe((movies) => { 
 this.trendingMovies = movies; 
 }); 
 } 
-getTheatreMovies(): 
 It is used to get all the specific theatre movies. 
Code
getTheatreMovies() { 
 this.http 
 .get('http://localhost:4200/assets/data/theatre-movies.json') 
 .subscribe((movies) => { 
 this.theatreMovies = movies; 
 }); 
 } 
-getPopularMovies(): 
 It is used for getting all the specific popular movies. 
Code 
getPopularMovies() { 
 this.http 
 .get('http://localhost:4200/assets/data/popular-movies.json') 
 .subscribe((movies) => { 
 this.popularMovies = movies; 
 }); 

5. Service Component:

There are functions like logout(), login(), AuthService(). 
-Logout(): 
 This function is used to navigate to the login page from the 
home page. 
Code
logout() { 
 this.router.navigate(['login']); 
 } 
-Login(): 
 It validates the user input given for the username and 
password. 
Code: 
login(uname: string,pword: string) { 
 if(uname === "suren" && pword === 'rot@tomato1234') { 
 return 200; 
 } 
 else { 
 return 403; 
 } 
 } 
 
Routing and Navigation: 

- The application uses Angular's routing to navigate between different 
components/pages, such as the login page, landing page, and movie 
details page. 
- Routing is configured in the `app-routing.module.ts` file.

Service and Dependencies: 

1. Authentication Service: 
 - Manages user authentication. 
2. Movie Service: 
 - Handles movie data retrieval from an external API. 
3. Rating Service: 
- Manages user ratings for movies.
  
Test Cases: 

Modified code in login component: 

1) login.component.spec.ts : 
 Here, the extra code added was marked in bold. 
 Here, import FormsModule, ReactiveFormsModule from angular/forms. 
 In beforeEach() function, import the above two modules using “imports” 
keyword. 
 Add a test case called testing title for checking whether the title of the 
component is matching or not. 
import { ComponentFixture, TestBed } from '@angular/core/testing'; 
import { LoginComponent } from './login.component'; 
import { FormsModule, ReactiveFormsModule } from '@angular/forms'; 
describe('LoginComponent', () => { 
 let component: LoginComponent; 
 let fixture: ComponentFixture<LoginComponent>; 
 beforeEach(() => { 
 TestBed.configureTestingModule({ 
 declarations: [LoginComponent], 
 imports: [FormsModule, ReactiveFormsModule], 
 }).compileComponents(); 
 fixture = TestBed.createComponent(LoginComponent); 
 component = fixture.componentInstance; 
 fixture.detectChanges(); 
 }); 
 it('should create', () => { 
 expect(component).toBeTruthy(); 
 }); 
 it('testing title',() => { 
 expect(component.componentName).toBe("login") 
 }) 

1) login.component.ts:

 Add the component name here for linking it with the 
login.component.spec.ts file using componentNmae keyword as shown 
below. 
 Here, the extra code added was marked in bold. 
import { Component, OnInit } from '@angular/core'; 
import { AuthService } from '../services/auth.service'; 
import { Router } from '@angular/router'; 
@Component({ 
 selector: 'app-login', 
 templateUrl: './login.component.html', 
 styleUrls: ['./login.component.scss'] 
}) 
export class LoginComponent implements OnInit { 
 componentName="login"
 username=""; 
 password=""; 
 errorMsg=""; 
 constructor(private auth: AuthService, private router: Router) { } 
 ngOnInit(): void { 
 } 
 login() { 
 if(this.username.trim().length == 0) { 
 this.errorMsg = "Username is required"; 
 } 
 else if (this.username.trim().length == 0) { 
 this.errorMsg = "Password is required"; 
 } 
 else { 
 this.errorMsg = ""; 
 let res= this.auth.login(this.username, this.password); 
 if(res === 200) { 
 this.router.navigate(['home']); 
 }if(res == 403) { 
 this.errorMsg = "Invalid Credentials"
 } 
 } 
 } 
 
} 

Modified code added in home component:

1) home.component.spec.ts: 
 Likewise login component, do the changes in the home component. 
 Here, import FormsModule, ReactiveFormsModule from angular/forms. 
 In beforeEach() function, import the above two modules using “imports” 
keyword. 
 Add a test case called testing title for checking whether the title of the 
component is matching or not. 
 Here, the extra code added was marked in bold. 
import { ComponentFixture, TestBed } from '@angular/core/testing'; 
import { HomeComponent } from './home.component'; 
import { HeaderComponent } from '../header/header.component'; 
import { StarRatingComponent } from '../feature/star-rating/starrating.component'
import { HttpClientTestingModule } from
'@angular/common/http/testing'; 
import { MovieComponent } from '../movie/movie.component'; 
import { LoginComponent } from '../login/login.component'; 
import { FormsModule, ReactiveFormsModule } from '@angular/forms'; 
TestBed.configureTestingModule({ 
 declarations: [HomeComponent, HeaderComponent, 
StarRatingComponent, MovieComponent, LoginComponent], 
 
}) 
describe('HomeComponent', () => { 
 let component: HomeComponent; 
 let fixture: ComponentFixture<HomeComponent>; 
 beforeEach(() => { 
 TestBed.configureTestingModule({ 
 declarations: 
[HomeComponent,StarRatingComponent,HeaderComponent,LoginComponent,Mo
vieComponent], 
 imports: [HttpClientTestingModule, FormsModule, 
ReactiveFormsModule], 
 }).compileComponents(); 
 fixture = TestBed.createComponent(HomeComponent); 
 component = fixture.componentInstance; 
 }); 
 it('should create', () => { 
 expect(component).toBeTruthy(); 
 }); 
 it('testing title',() => { 
 expect(component.componentName).toBe("home") 
 }) 
}); 

2) home.component.ts:
   
 Add the component name here for linking it with the 
login.component.spec.ts file using componentNmae keyword as shown 
below. 
 Here, the extra code added was marked in bold. 
import { Component, OnInit } from '@angular/core'; 
import { HttpClient } from '@angular/common/http'; 
import { Router } from '@angular/router'; 
@Component({ 
 selector: 'app-home', 
 templateUrl: './home.component.html', 
 styleUrls: ['./home.component.scss'], 
}) 
export class HomeComponent implements OnInit { 
 componentName="home"
 trendingMovies: any; 
 theatreMovies: any; 
 popularMovies: any; 
 constructor(private http: HttpClient, private router: Router) { } 
 ngOnInit(): void { 
 this.getTrendingMovies(); 
 this.getTheatreMovies(); 
 this.getPopularMovies(); 
 
 } 
 getTrendingMovies() { 
 this.http 
 .get('http://localhost:4200/assets/data/trending-movies.json') 
 .subscribe((movies) => { 
 this.trendingMovies = movies; 
 }); 
 } 
 getTheatreMovies() { 
 this.http 
 .get('http://localhost:4200/assets/data/theatre-movies.json') 
 .subscribe((movies) => { 
 this.theatreMovies = movies; 
 }); 
 } 
 getPopularMovies() { 
 this.http 
 .get('http://localhost:4200/assets/data/popular-movies.json') 
 .subscribe((movies) => { 
 this.popularMovies = movies; 
 }); 
 } 
 goToMovie(type: string, id: string) { 
 this.router.navigate(['movie', type, id]); 
 } 
} 

Modified code added in movie component: 

1) movie.component.spec.ts: 
 Likewise home component, do the changes in the home component. 
 Here, import FormsModule, ReactiveFormsModule from angular/forms. 
 In beforeEach() function, import the above two modules using “imports” 
keyword. 
 Add a test case called testing title for checking whether the title of the 
component is matching or not. 
 Here, the extra code added was marked in bold. 
import { ComponentFixture, TestBed } from '@angular/core/testing'; 
import { HomeComponent } from '../home/home.component'; 
import { HeaderComponent } from '../header/header.component'; 
import { StarRatingComponent } from '../feature/star-rating/starrating.component'; 
import { HttpClientTestingModule } from
'@angular/common/http/testing'; 
import { MovieComponent } from '../movie/movie.component'; 
import { LoginComponent } from '../login/login.component'; 
import { ActivatedRoute, convertToParamMap } from '@angular/router'; 
import { NgbRatingModule } from '@ng-bootstrap/ng-bootstrap'; 
import { FormsModule, ReactiveFormsModule } from '@angular/forms'; 
describe('MovieComponent', () => { 
 let component: MovieComponent; 
 let fixture: ComponentFixture<MovieComponent>; 
 let activatedRoute: ActivatedRoute; 
 beforeEach(() => { 
 activatedRoute = { 
 snapshot: { 
 paramMap: convertToParamMap({ type: 'any', id: 'any' }), 
 }, 
 } as ActivatedRoute; 
 TestBed.configureTestingModule({ 
 imports: [HttpClientTestingModule,NgbRatingModule, 
FormsModule, ReactiveFormsModule], 
 declarations: [MovieComponent, StarRatingComponent, 
HeaderComponent, LoginComponent, HomeComponent], 
 providers: [{ provide: ActivatedRoute, useValue: 
activatedRoute }], 
 }).compileComponents(); 
 fixture = TestBed.createComponent(MovieComponent); 
 component = fixture.componentInstance; 
 }); 
 it('should create the component', () => { 
 expect(component).toBeTruthy(); 
 }); 
 it('testing title',() => { 
 expect(component.componentName).toBe("movie") 
 }) 

1) movie.component.ts:
   
 Add the component name here for linking it with the 
login.component.spec.ts file using componentNmae keyword as shown 
below. 
 Here, the extra code added was marked in bold. 
import { HttpClient } from '@angular/common/http'; 
import { Component, OnInit } from '@angular/core'; 
import { ActivatedRoute } from '@angular/router'; 
@Component({ 
 selector: 'app-movie', 
 templateUrl: './movie.component.html', 
 styleUrls: ['./movie.component.scss'], 
}) 
export class MovieComponent implements OnInit { 
 componentName="movie"
 type = ''; 
 id = ''; 
 url = ''; 
 movies: any; 
 movie: any; 
 constructor(private route: ActivatedRoute, private http: 
HttpClient) {} 
 ngOnInit(): void { 
 this.type = this.route.snapshot.params['type']; 
 this.id = this.route.snapshot.params['id']; 
 if (this.type === 'trending') { 
 this.url = 'http://localhost:4200/assets/data/trendingmovies.json'; 
 } 
 if (this.type === 'theatre') { 
 this.url = 'http://localhost:4200/assets/data/theatremovies.json'; 
 } 
 if (this.type === 'popular') { 
 this.url = 'http://localhost:4200/assets/data/popularmovies.json'; 
 } 
 this.getMovie(); 
 } 
 getMovie() { 
 this.http.get(this.url).subscribe((movies) => { 
 this.movies = movies; 
 let index = this.movies.findIndex( 
 (movie: { id: string }) => movie.id == this.id 
 ); 
 if (index > -1) { 
 this.movie = this.movies[index]; 
 } 
 }); 
 } 
} 

Modified code added in header component: 

1) header.component.spec.ts:
   
 Likewise home component, do the changes in the home component. 
 Here, import FormsModule, ReactiveFormsModule from angular/forms. 
 In beforeEach() function, import the above two modules using “imports” 
keyword. 
 Add a test case called testing title for checking whether the title of the 
component is matching or not. 
 Here, the extra code added was marked in bold. 
import { ComponentFixture, TestBed } from '@angular/core/testing'; 
import { HeaderComponent } from './header.component'; 
import { FormsModule, ReactiveFormsModule } from '@angular/forms'; 
describe('HeaderComponent', () => { 
 let component: HeaderComponent; 
 let fixture: ComponentFixture<HeaderComponent>; 
 beforeEach(() => { 
 TestBed.configureTestingModule({ 
 declarations: [HeaderComponent], 
 imports: [FormsModule, ReactiveFormsModule], 
 }).compileComponents(); 
 fixture = TestBed.createComponent(HeaderComponent); 
 component = fixture.componentInstance; 
 fixture.detectChanges(); 
 }); 
 it('should create', () => { 
 expect(component).toBeTruthy(); 
 }); 
 it('testing title',() => { 
 expect(component.componentName).toBe("header") 
 })
}); 

3) header.component.ts:
   
 Add the component name here for linking it with the 
login.component.spec.ts file using componentNmae keyword as shown 
below. 
 Here, the extra code added was marked in bold. 
import { Router } from '@angular/router'; 
import { Component, OnInit } from '@angular/core'; 
import { AuthService } from '../services/auth.service'; 
@Component({ 
 selector: 'app-header', 
 templateUrl: './header.component.html', 
 styleUrls: ['./header.component.scss'] 
}) 
export class HeaderComponent { 
 componentName="header"
 constructor(private router: Router, private auth: AuthService) { } 
 ngOnInit(): void { 
 } 
 goToHome() { 
 this.router.navigate(['home']); 
 } 
 logout() { 
 this.router.navigate(['login']); 
 } 
 
 
} 

Modified code added in star-rating component: 

1) star-rating.component.spec.ts:
   
 Likewise home component, do the changes in the home component. 
 Here, import FormsModule, ReactiveFormsModule from angular/forms. 
 In beforeEach() function, import the above two modules using “imports” 
keyword. 
 Add a test case called testing title for checking whether the title of the 
component is matching or not. 
 Here, the extra code added was marked in bold. 
import { ComponentFixture, TestBed } from '@angular/core/testing'; 
import { StarRatingComponent } from './star-rating.component'; 
import { NgbRatingModule } from '@ng-bootstrap/ng-bootstrap'; 
import { FormsModule, ReactiveFormsModule } from '@angular/forms'; 
 
describe('StarRatingComponent', () => { 
 let component: StarRatingComponent; 
 let fixture: ComponentFixture<StarRatingComponent>; 
 beforeEach(() => { 
 TestBed.configureTestingModule({ 
 declarations: [StarRatingComponent], 
 imports: [NgbRatingModule, FormsModule, ReactiveFormsModule], 
 }).compileComponents(); 
 fixture = TestBed.createComponent(StarRatingComponent); 
 component = fixture.componentInstance; 
 fixture.detectChanges(); 
 }); 
 it('should create', () => { 
 expect(component).toBeTruthy(); 
 }); 
 it('testing title',() => { 
 expect(component.componentName).toBe("star-rating") 
 }) 
}); 

2) star-rating.component.ts:
   
 Add the component name here for linking it with the 
login.component.spec.ts file using componentNmae keyword as shown 
below. 
 Here, the extra code added was marked in bold. 
import { Component, Input, OnInit } from '@angular/core'; 
@Component({ 
 selector: 'app-star-rating', 
 templateUrl: './star-rating.component.html', 
 styleUrls: ['./star-rating.component.scss'] 
}) 
export class StarRatingComponent implements OnInit { 
 componentName="star-rating"
 @Input() rating: any; 
 @Input() isReadOnly: boolean = false; 
 constructor() { } 
 ngOnInit(): void { 
 // Initialization code here
 } 
} 

 Default test case in all components: 

1) Login component:
   
import { ComponentFixture, TestBed } from '@angular/core/testing'; 
import { LoginComponent } from './login.component'; 
import { FormsModule, ReactiveFormsModule } from '@angular/forms'; 
describe('LoginComponent', () => { 
 let component: LoginComponent; 
 let fixture: ComponentFixture<LoginComponent>; 
 beforeEach(() => { 
 TestBed.configureTestingModule({ 
 declarations: [LoginComponent], 
 imports: [FormsModule, ReactiveFormsModule], // Include 
FormsModule
 }).compileComponents(); 
 fixture = TestBed.createComponent(LoginComponent); 
 component = fixture.componentInstance; 
 fixture.detectChanges(); 
 }); 
 it('should create', () => { 
 expect(component).toBeTruthy(); 
 }); 
 it('testing title',() => { 
 expect(component.componentName).toBe("login") 
 }) 
}); 

 It checks whether the component is really created or not. 

3) Home Component:
   
import { ComponentFixture, TestBed } from '@angular/core/testing'; 
import { HomeComponent } from './home.component'; 
import { HeaderComponent } from '../header/header.component'; 
import { StarRatingComponent } from '../feature/star-rating/starrating.component'
import { HttpClientTestingModule } from
'@angular/common/http/testing'; 
import { MovieComponent } from '../movie/movie.component'; 
import { LoginComponent } from '../login/login.component'; 
import { FormsModule, ReactiveFormsModule } from '@angular/forms'; 
TestBed.configureTestingModule({ 
 declarations: [HomeComponent, HeaderComponent, 
StarRatingComponent, MovieComponent, LoginComponent], 
 
}) 
describe('HomeComponent', () => { 
 let component: HomeComponent; 
 let fixture: ComponentFixture<HomeComponent>; 
 beforeEach(() => { 
 TestBed.configureTestingModule({ 
 declarations: 
[HomeComponent,StarRatingComponent,HeaderComponent,LoginComponent,Mo
vieComponent], 
 imports: [HttpClientTestingModule, FormsModule, 
ReactiveFormsModule], 
 }).compileComponents(); 
 fixture = TestBed.createComponent(HomeComponent); 
 component = fixture.componentInstance; 
 }); 
 it('should create', () => { 
 expect(component).toBeTruthy(); 
 }); 
 it('testing title',() => { 
 expect(component.componentName).toBe("home") 
 }) 
}); 
 The highlighted code above is the default code checking whether the 
component is really created or not. 
 It is actually a test case. 

3) Header Component:
   
import { ComponentFixture, TestBed } from '@angular/core/testing'; 
import { HeaderComponent } from './header.component'; 
import { FormsModule, ReactiveFormsModule } from '@angular/forms'; 
describe('HeaderComponent', () => { 
 let component: HeaderComponent; 
 let fixture: ComponentFixture<HeaderComponent>; 
 beforeEach(() => { 
 TestBed.configureTestingModule({ 
 declarations: [HeaderComponent], 
 imports: [FormsModule, ReactiveFormsModule], // Include 
FormsModule
 }).compileComponents(); 
 fixture = TestBed.createComponent(HeaderComponent); 
 component = fixture.componentInstance; 
 fixture.detectChanges(); 
 }); 
 it('should create', () => { 
 expect(component).toBeTruthy(); 
 }); 
 it('testing title',() => { 
 expect(component.componentName).toBe("header") 
 }) 
}); 

 It checks whether the component is really existing or not. 

5) Movie Component:
   
import { ComponentFixture, TestBed } from '@angular/core/testing'; 
import { HomeComponent } from '../home/home.component'; 
import { HeaderComponent } from '../header/header.component'; 
import { StarRatingComponent } from '../feature/star-rating/starrating.component'; // Import StarRatingComponent
import { HttpClientTestingModule } from
'@angular/common/http/testing'; 
import { MovieComponent } from '../movie/movie.component'; 
import { LoginComponent } from '../login/login.component'; 
import { ActivatedRoute, convertToParamMap } from '@angular/router'; 
import { NgbRatingModule } from '@ng-bootstrap/ng-bootstrap'; 
import { FormsModule, ReactiveFormsModule } from '@angular/forms'; 
describe('MovieComponent', () => { 
 let component: MovieComponent; 
 let fixture: ComponentFixture<MovieComponent>; 
 let activatedRoute: ActivatedRoute; 
 beforeEach(() => { 
 activatedRoute = { 
 snapshot: { 
 paramMap: convertToParamMap({ type: 'any', id: 'any' }), 
 }, 
 } as ActivatedRoute; 
 TestBed.configureTestingModule({ 
 imports: [HttpClientTestingModule,NgbRatingModule, 
FormsModule, ReactiveFormsModule], 
 declarations: [MovieComponent, StarRatingComponent, 
HeaderComponent, LoginComponent, HomeComponent], // Include 
StarRatingComponent
 providers: [{ provide: ActivatedRoute, useValue: 
activatedRoute }], 
 }).compileComponents(); 
 fixture = TestBed.createComponent(MovieComponent); 
 component = fixture.componentInstance; 
 }); 
 it('should create the component', () => { 
 expect(component).toBeTruthy(); 
 });
 it('testing title',() => { 
 expect(component.componentName).toBe("movie") 
 }) 
}); 
 The highlighted code above denotes the default test case as mentioned 
above. 

7) Star rating component:
   
import { ComponentFixture, TestBed } from '@angular/core/testing'; 
import { StarRatingComponent } from './star-rating.component'; 
import { NgbRatingModule } from '@ng-bootstrap/ng-bootstrap'; 
import { FormsModule, ReactiveFormsModule } from '@angular/forms'; 
describe('StarRatingComponent', () => { 
 let component: StarRatingComponent; 
 let fixture: ComponentFixture<StarRatingComponent>; 
 beforeEach(() => { 
 TestBed.configureTestingModule({ 
 declarations: [StarRatingComponent], 
 imports: [NgbRatingModule, FormsModule, ReactiveFormsModule], 
 }).compileComponents(); 
 fixture = TestBed.createComponent(StarRatingComponent); 
 component = fixture.componentInstance; 
 fixture.detectChanges(); 
 }); 
 it('should create', () => { 
 expect(component).toBeTruthy(); 
 }); 
 it('testing title',() => { 
 expect(component.componentName).toBe("star-rating") 
 }) 
}); 
 The highlighted code above denotes the default test case checking the real 
existence of the component. 
Testing the components(Screenshots): 
 Here, as we can see all the 14 specs(i.e, all the test cases along with the 
default test cases), are executed and there were no failures in the 
execution.
 Hence, this is the jasmine and karma window representing the execution 
of all the test cases and displaying whether there are any failures.
Future Work 
To modify the project into a full Single Page Application (SPA): 
- Implement lazy loading for modules to improve application load 
times. 
- Enhance user profile management and movie recommendations. 
- Incorporate user authentication via social media. 
- Implement a backend to store and manage user data, reviews, and 
ratings.

Conclusion 

The Angular-based Single Page Application (SPA) project successfully 
demonstrates the use of various Angular features for creating an 
interactive movie exploration and rating platform. It offers dynamic 
navigation, user authentication, and real-time data interaction. 
Future work can extend the project's capabilities and make it more 
feature-rich. 
******************************************************** 
