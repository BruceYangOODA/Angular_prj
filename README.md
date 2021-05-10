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
  <input/>的資料修改會同步到 該hero資料  
