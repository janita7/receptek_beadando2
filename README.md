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
      
     


## II. Tervezés
  1. Architektúra terv:
    * Komponens diagram:
    
      ![komp_diagram](https://cloud.githubusercontent.com/assets/14230720/11126372/e60effb8-896e-11e5-8a19-b9cd043be2be.png)


    * Oldaltérkép:
        - Publikus: Receptlista, Új receptek felvitele, Meglévő szerkesztése és törlése

    * Végpontok:
        - GET /: főoldal
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
  
      ![adatmodell](https://cloud.githubusercontent.com/assets/14230720/11125257/3d39dfca-8969-11e5-8a5f-49c42f442915.png)

    * Adatbázisterv:
    
      ![adatbterv](https://cloud.githubusercontent.com/assets/14230720/11125318/96f60f0c-8969-11e5-9c28-edd280099359.png)
      
    * Recept állapotdiagramja:
    
      ![alldiag](https://cloud.githubusercontent.com/assets/14230720/11133015/97e5f808-8993-11e5-8fed-3eb3167d4113.png)
      
  4. Dinamikus működés:
    * Szekvencia diagram:
      
    ![nomnoml](https://cloud.githubusercontent.com/assets/14230720/11134219/6514ebc0-899b-11e5-84f8-3d9dd77da568.png)
    ![nomnoml 1](https://cloud.githubusercontent.com/assets/14230720/11134221/690adc6c-899b-11e5-8a4a-e874d9619642.png)
    ![nomnoml 2](https://cloud.githubusercontent.com/assets/14230720/11134224/6d7649c6-899b-11e5-91d6-f90f3195e3e1.png)

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

