# Angular_prj
[Angular DOC](https://angular.cn/docs)  
[Youtube Angular Vedio](https://www.youtube.com/watch?v=csE6ue9w7YM&list=PLA0YHwTjkRztyUo4L6594L7ifAeWUoug7&ab_channel=%E8%B7%9F%E5%B1%B1%E5%9C%B0%E4%BA%BA%E5%AD%A6%E5%89%8D%E7%AB%AF)  

01. 安裝環境  
$ npm install -g @angular/cli  
$ ng (HELP)功能  
$ cd 目標資料夾  
$ ng new myapp  創建網站資料夾  
$ cd myapp  
$ code .  
$ ng serve --open  開啟服務主機  
02. 教程:英雄指南  
  myapp/src/style.css  CSS樣式文件  
$ ng generate component heroes  創建網頁組件  
  myapp/src/app/heroes/  網頁組件資料夾  
  myapp/src/app/heroes/heroes.component.ts  網頁資料組件  
  在myapp/src/app/app.component.html 加入 <app-heroes></app-heroes>  
  就會把 heroes 網頁畫面加入 主頁 當中  
  新增檔案 myapp/src/app/hero.ts  資料類別,定義資料名稱,型態  
  在 heroes.component.ts 寫入 import { Hero } from "../hero" , 導入資料類別  
03. ngModule 資料雙向綁定  
  在heroes.component.html 寫入 <input [(ngModel)]="hero.name" placeholder="name" />  
  在myapp/src/app/app.module.ts 寫入 import { FormsModule } from "@angular/forms";  
  @NgModule imports:新增一行 FormsModule  
  input<> 的資料修改會同步到 該hero資料  
04. 自定義資料  
  在app/新增檔案 mock-heros.ts  
  寫入 export const HEROES : Hero[] = [自定義資料]  (:)-> 繼承  
  在 heroes.component.ts 寫入 import { HEROES } from "../mock-heroes"; 導入資料類別  
05. Angular html 語法  
  *ngFor  
  *ngFor="let hero of heroes" (click)="onSelect(hero)"  Angular html 語法    
  在 heroes.component.ts 為註冊監聽(click)的 onSelect 方法寫CODE  
  selectedHero : Hero;  變數名稱與資料類型  
  onSelect(hero:Hero): void { this.selectedHero = hero; }  方法內容  
  *ngIf  
  *ngIf="selectedHero"  如果 selectedHero 是 空的，就不顯示這個 div    
  不知為何 selectedHero 一定要初始化, 使用 piple解決    
  在 heroes.component.ts 初始化 selectedHero 變數  
  selectedHero : Hero | null;  
  constructor() { this.selectedHero = null;}    
  [class.selected]="hero === selectedHero"  選擇到的物件變換html class裝飾  
07. 資料單向綁定  
$ ng generate component hero-detail  
    修飾 @Input() hero:Hero; 代表從外部傳入資料  
    在父組件的html <app-hero-detail [hero]="selectedHero"></app-hero-detail>  導入子組件  
    [子組件變數] = "父組件傳入的變數"  
08. 服務  數據同步服務  
$ ng generate service hero
    系統生成檔案 myapp/hero.service.ts  
    @Injectable()  注入 裝飾器  
    getHeroes():Hero[] { return HEROES;}  服務的方法 提供數據  
    在heroes.component.ts 註冊Service服務，import { HeroService } from '../hero.service';  
    heroes : Hero[]; 修改參數宣告  
    在 constructor 初始化參數  
    constructor(private heroService: HeroService) {  
    this.heroes = this.heroService.getHeroes();  
    }  构造函数
    getHeroes(): void { this.heroes = this.heroService.getHeroes(); }  
    ngOnInit() { this.getHeroes(); }  在 ngOnInit() 中调用
    让构造函数保持简单，只做初始化操作，比如把构造函数的参数赋值给属性。 构造函数不应该做任何事。
    但是似乎 heroService 只能在 constructor 參數宣告當中獲取物件, 所以在 constructor 初始參數
      
    數據同步服務  
    在hero.service.ts 註冊 import { Observable, from , of } from 'rxjs';  (rxjs -> reactive javascript)  
    getHeroes():Observable<Hero[]> { return of(HEROES);}  
    原返回資料型態 Hero[] 變為 Observable<Hero[]>  
    
    ### 這個部分實作失敗 
     Type 'Subscription' is missing the following properties from type 'Hero[]'  
     棄用 Observable  
09. 路由  
$ ng generate module app-routing --flat --module=app  
    在 src/app/app-routing.module.ts  添加 路由  
    const routes: Routes = [{ path: 'heroes', component: HeroesComponent }];  
    在 app.component.html 添加 路由連結  
    <nav><a routerLink="/heroes">Heroes</a></nav>  


