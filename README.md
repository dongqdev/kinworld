# KinWorld-Knowledge In The World

Spring Boot(백엔드)와 Vue + Vuetify(프론트엔드)를 결합한 웹 프로젝트 템플릿입니다.
현재 코드 기준으로는 "지식 서비스"의 도메인 기능(게시글/검색/분류/추천)보다,
프론트엔드 레이아웃 구성과 Spring Boot 정적 리소스 통합 배포 구조를 확인하는 데 초점이 맞춰져 있습니다.

### 현재 구현된 기능(코드 기준)

+ 상단 App Bar, 좌측 Navigation Drawer, Footer 레이아웃
+ 다크모드 토글 스위치
+ 기본 콘텐츠 영역(test 텍스트)
+ Vue 빌드 결과물을 Spring Boot static 리소스로 출력하도록 연동

### 아직 보강이 필요한 영역

+ 지식 데이터 모델 및 API
+ 사용자 기능(로그인/권한)
+ 지식 검색/조회/작성 화면

요약하면, "세상의 모든 지식"은 현재 완성 기능이라기보다 프로젝트의 목표 비전이며,
실제 구현은 초기 UI 골격과 배포 연동 단계입니다.



## INDEX

+ [I. 개발환경 - Development Envirenment](#I-개발환경-Development-Environment)
+ [II. 설정 - Setup](#II-설정-Setup)
+ [III. 레이아웃-Layout](#III-레이아웃-Layout)



## I. 개발환경-Development Environment

![SpringBoot_Vue](md_pic/springBoot_vue.png)

+ IDE : Eclipse
+ SpringBoot 2
+ Vue cli 3
+ Java
+ Gradle
+ MariaDB
+ Windows



## II. 설정-Setup

##### 1. Go to [SpringBoot Initializr](https://start.spring.io/)

![SpringBoot Initializr](md_pic/SpringBootInitializr.png)

##### 2. Add Dependencies

+ Spring Web
+ Thymeleaf

##### 3. Generate and Unzip

##### 4. Import Gradle Project 

![importGradle](md_pic/importGradle.png)

![basicGradlePj](md_pic/basicGradlePj.png)

##### 5.  Go to [node.js Download](https://nodejs.org/en/download/)

![downloadNodejs](md_pic/downloadNodejs.png)

##### 6.  명령프롬포트 실행 1

+ Windows 

```
  npm i -g @vue/cli // vue-cli 3.x
  npm i -g vue-cli // vue-cli 2.x
```


##### 7. 환경변수 설정

+ 시스템 PATH에 ```C:\Users\유저명\AppData\Roaming\npm``` 경로 추가

##### 8.  명령프롬포트 실행

+ Move Gradle Project Directory

```
  cd kinworld
```

+ Create Project

```
	vue create '프로젝트 명' // vue-cli 3.X
    vue init webpack '프로젝트 명' // vue-cli 2.X
```

 + Build

```
    cd frontend
    npm install
    npm run build
```

##### 10. Run in local Server

```
    npm run serve // vue-cli 3.x
    npm run dev // vue-cli 2.x
```

##### 11. Create vue.config.js

![vueConfigJs](/md_pic/vueConfigJs.png)

```
    module.exports = {  
      outputDir: "../src/main/resources/static",  
      indexPath: "../static/index.html",  
      devServer: {  
        proxy: "http://localhost:8080"  
      },  
      chainWebpack: config => {  
        const svgRule = config.module.rule("svg");    
        svgRule.uses.clear();    
        svgRule.use("vue-svg-loader").loader("vue-svg-loader");  
      }  
    };
```

+ outputDir은 npm run build로 빌드 시 파일이 생성되는 위치
+ indexPath는 index.html 파일이 생성될 위치를 지정
+ devServer는 Back-End( Spring Boot의 내장 was의 주소)

##### 12. Maria DB Setting

```
    #datasource
    spring.datasource.driverClassName=org.mariadb.jdbc.Driver
    spring.datasource.url=jdbc:mariadb://localhost:3306/kinworld
    spring.datasource.username=root
    spring.datasource.password=password
```

##### 13. Go to http://localhost:8080/

![startVue](md_pic/startVue.png)

# III. 레이아웃-Layout

##### 1. Add Vuetify

```
	npm add vuetify
```

![vuetify](md_pic/vuetify.png)

##### 2.  Use vue-tree-nav

###### npm install --save vue-tree-nav

#####  ![](C:\workSpace\kinworld\md_pic\navmenu.gif)

