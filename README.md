# Receptek - 3. beadandó - Alkalmazások fejlesztése

## I. Követelményanalízis
  - Funkcionális elvárások:
      Vendégként szeretnék recepteket feltölteni, amiket később visszanézhetek. (Receptek felvitele, listázása, szerkesztése)
  - Nem funkcionális követelmények:
      Felhasználóbarát kinézet, egyszerű és egyértelmű navigáció.
  - Szerepkörök:
      
      Vendég:A végpontok segítségével navigálhat a főoldal, receptlista, szerkesztés, és új recept oldalak között.

  - Használati eset diagram:
      ![haszn-eset](https://cloud.githubusercontent.com/assets/14230720/12414326/2809f37c-be95-11e5-9084-a608da346517.png)

  - Receptfelvételi folyamat pontos menete:
      
      ![folyamat](https://cloud.githubusercontent.com/assets/14230720/12414472/e52717fa-be95-11e5-87f4-f1c70010b5ee.png)


## II. Tervezés
  1. Architektúra terv:
    * Komponens diagram:
    
     ![komponens](https://cloud.githubusercontent.com/assets/14230720/12414646/21e2bd42-be97-11e5-881a-0d3202b8fe85.png)


    * Oldaltérkép:
        - Publikus: Receptlista, Recept megtekintése, Új receptek felvitele, Meglévő szerkesztése és törlése

    * Végpontok:
        - GET /: főoldal
        - GET /login: bejelentkezési oldal
        - GET /recipes/list: receptlista
        - GET /recipes/new: új recept felvitele
        - GET /recipes/:recipe_id : {recipe_id} azonosítójú recept megtekintése
        - GET /recipes/edit/:recipe_id : {recipe_id} azonosítójú recept szerkesztése
        
        - POST /recipes/new: új recept felvitele, adatok elküldése
        - POST /recipes/edit/:recipe_id : {recipe_id} azonosítójú recept szerkesztésének elmentése
        
  2. Felhasználóifelület-modell:
    * Oldalvázlatok:
        
      ![uj_recept](https://cloud.githubusercontent.com/assets/14230720/11021511/701e471a-8643-11e5-9e9b-2fb3175bfde9.jpg)
      
    * Designterv:
      
      ![designterv](https://cloud.githubusercontent.com/assets/14230720/11021527/f43e914e-8643-11e5-8009-264e80ebf2e0.png)

      ![designterv2](https://cloud.githubusercontent.com/assets/14230720/11021583/3a4a88a8-8646-11e5-84c6-4996a4db4fd9.png)

  3. Osztálymodell:
    * Adatmodell:
  
    ![nomnoml 3](https://cloud.githubusercontent.com/assets/14230720/12530829/88aa2ca2-c1eb-11e5-94e2-0732477b2759.png)

    * Adatbázisterv:
    
    ![nomnoml 4](https://cloud.githubusercontent.com/assets/14230720/12530833/a1b61ef4-c1eb-11e5-9528-58ca065e0177.png)
      
  4. Dinamikus működés:
    * Szekvencia diagram:
      
    ![szekvencia](https://cloud.githubusercontent.com/assets/14230720/12414823/4856682e-be98-11e5-8554-da94d5117a39.png)

## III. Implementáció
  - Fejlesztői környezet bemutatása:
      - Fejlesztői környezet gyanánt a Cloud9 webes IDE-t használjuk. Ez a c9.io weboldalról érhető el, rendelkeznünk kell           hozzá egy github felhasználói fiókkal. Belépés után egy demo projekt rendelkezésünkre is áll, amin keresztül                 megismerkedhetünk a felülettel.
        
  - Könyvtárstruktúrában lévő mappák funkiójának bemutatása:
      - app/pods/application: a host definiálása
      - app/pods/components: új recept kinézete és validálása, recept lista oldal kinézete
      - app/pods/index: a főoldal kinézete
      - app/pods/recipe: a receptek modellje
      - app/pods/recipes: szerkesztési oldal, új recept oldal, recept lista oldal kontrollerei, és kinézetük
      - app/templates: a főoldal sablonja
      - config: környezeti beállítások
      - node_modules: telepített modulok helye
      - tests/unit/pods/application: létezést vizsgáló teszt az appra
      - tests/unit/pods/recipe: modell unit teszt
      - tests/unit/pods/recipes: szerkesztés, listázás, új recept felvitelének tesztelése
  
## IV. Tesztelés
  - Tesztesetek felsorolása: unit teszt a recept adatmodellre
  
## V. Felhasználói dokumentáció
  - A program használata:
  
      Cloud9 keretrendszeren belül: Indítsuk el a 'Run' gombbal az applikációnkat, ekkor a konzol felületen megjelennek az         információk, többek között az, hogy milyen címen érhetjük el. Arra kattintva nyithatjuk meg az app főoldalát.
      
      A receptlista oldalon áttekinthetjük eddigi feltöltéseinket. Az Új recept felvitele gombra való kattintással egy űrlapon keresztül adhatjuk meg legújabb receptünk címét és leírását. Ha kitöltöttük a kötelező mezőket, a mentés vagy mégse gombbal elmenthetjük vagy elvethetjük azt, amit eddig beírtunk. Lehetőségünk van a meglévő receptek egyenkénti megtekintésére, vagy szerkesztésére, illetve törlésére.

