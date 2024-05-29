PROJEKT NUMER 1 "TRANSFORMACJE WSPÓŁRZĘDNYCH"

PRZEPROWADZONE TRANSFORMACJE:
```sh
    XYZ (geocentryczne) -> BLH (elipsoidalne fi, lambda, h)
    BLH -> XYZ
    XYZ -> NEUp
    BL(GRS80, WGS84, elipsoida Krasowskiego) -> 2000
    BL(GRS80, WGS84, elipsoida Krasowskiego) -> 1992
```
 WYBRANE ELIPOSIDY:
 ```sh
     GRS80
     WGS84
     Elipsoida Krasowskiego
 ```
 WYKORZYSTYWANE NARZĘDZIA PRACY:
 ```sh
    Systemy operacyjne: Windows 11 oraz macOS 12.5.1
    Python oraz importowane biblioteki: numpy oraz argparse
```

OPIS PROGRAMU:
```sh
 Plik przyjmuje argumenty podane za pomocą następujących flag:
 ```

 ```sh
   -plik przyjmuje plik (koniecznie z rozszerzeniem), w którym znajdują się dane potrzebne do wykonania transformacji
   -elip przyjmuje nazwę modelu elipsoidy, na której chcemy dokonać transformacji
   -funkcja przyjmuje nazwę transformacji, którą chcemy wykonać
  ```
  
  WYBÓR ELIPSOIDY:
  ```sh
  Możliwe, jest wtedy, gdy wpiszemy nazwę wybranej przez nas elipsoidy:
  ```
  ```sh
   'WGS84'
   'GRS80'
   'Elipsoida Krasowskiego'
  ```
  
  WYBÓR TRANSFORMACJI:
  ```sh
  Transformację wybieramy, wpisując jedną z poniższych nazw.
  ```
  ```sh
   'XYZ_BLH'
   'BLH_XYZ'
   'XYZ_NEU'
   'BL_PL1992'
   'BL_PL2000'
  ```
  KOMUNIKAT
  ```sh
  Po wybraniu wszystkich parametrów i załadowaniu pliku z przykładowymi danymi, utworzy się plik z wynikami obliczeń w formacie txt.
```
  ```sh
   Zapisano
  ```
 NAZWA ZAPISANEGO PLIKU:
  ```sh
  "WYNIK_{funkcja}.txt"
  (gdzie {funkcja} oznacza nazwę transformacji, którą chcemy wykonać)
  ```
  
  PRZYKŁADOWE WYWOŁANIA PROGRAMU:
  ```sh
    -> python skrypt.py -plik dane.txt -elip GRS80 -funkcja XYZ_BLH
    -> python skrypt.py -plik dane.txt -elip WGS84 -funkcja BL_PL1992
    -> python skrypt.py -plik dane.txt -elip Elipsoida Krasowskiego -funkcja BL_XYZ
    -> python skrypt.py -plik dane.txt -elip WGS84 -funkcja XYZ_NEU
  ```
  
  
  PRZYKŁADOWE TRANSFORMACJE:
  
  XYZ ---> BLH
  ```sh
  Dla danych z pliku (kolejno X[m], Y[m], Z[m]) otrzymujemy wyniki (w kolejnych linijkach fi1, l1, h1, fi2, l2, h2, ...)
  ```
  ```sh
    5.209727221932659802e+01
    2.103153333279777115e+01
    1.413986623901873827e+02
    5.209727216202450961e+01
    2.103153314423015274e+01
    1.413998245187103748e+02
    5.209727212128520080e+01
    2.103153295566253433e+01
    1.414033538121730089e+02
    5.209727208606682325e+01
    2.103153276709491948e+01
    1.414076721612364054e+02
    5.209727208694960154e+01
    2.103153322806154435e+01
    1.414101303610950708e+02
    5.209727211984851181e+01
    2.103153317776271081e+01
    1.414022109359502792e+02
    5.209727206994543280e+01
    2.103153299757823191e+01
    1.414065340962260962e+02
    5.209727206155152146e+01
    2.103153280586428764e+01
    1.414110632874071598e+02
    5.209727212004385422e+01
    2.103153325424560194e+01
    1.414072633692994714e+02
    5.209727213641129140e+01
    2.103153317776271081e+01
    1.414045780999585986e+02
    5.209727210179833179e+01
    2.103153332234535000e+01
    1.414075766596943140e+02
    5.209727215407200163e+01
    2.103153318299952090e+01
    1.414055828107520938e+02
  ```



  
  BLH ---> XYZ
 ```sh
  Dla danych z przykładowego pliku, otrzymujemy wyniki (kolejno X[m], Y[m], Z[m])
  ```
  ```sh
    3.519148476177780423e+06;-8.058846240752805956e+06;7.221782633644362912e+06
    3.518246811368130147e+06;-8.060617148406046443e+06;7.220251167392918840e+06
    3.517344529170780908e+06;-8.062387742863076739e+06;7.218719484124908224e+06
    3.516441628994218074e+06;-8.064158022301887162e+06;7.217187582870155573e+06
    3.520158619975043926e+06;-8.061159468966477551e+06;7.218719486032334156e+06
    3.519011511451998260e+06;-8.060834155242622830e+06;7.219638519677306525e+06
    3.518300408910815138e+06;-8.062658984539208002e+06;7.217953559884781018e+06
    3.517155899965156335e+06;-8.064259403564777225e+06;7.216727970327695832e+06
    3.519906124335436150e+06;-8.060581254222247750e+06;7.219485354949392378e+06
    3.519011512378350366e+06;-8.060834157364573330e+06;7.219638521584975533e+06
    3.520609529018185567e+06;-8.060274053074301220e+06;7.219485354313515127e+06
    3.518961021663734689e+06;-8.060718500659395941e+06;7.219791687940459698e+06
  ```
  
  XYZ, X0Y0Z0 ---> NEU  (kolejno fi, lambda, h)
  ```sh
Po przeprowadzeniu transformacji, otrzymujemy następujące wartości ( kolejno : N, E, U)
```
Ważne jest, aby współrzędne punktów podane zostały w odpowiedniej kolejności - jako pierwsze podać należy współrzędne początku układu NEU (x0, y0), a dopiero potem współrzędne, do których policzyć chcemy wektor. Stąd, żeby otrzymać jeden punkt wyjściowy należy wprowadzić dane aż dwóch punktów wejściowych.
  ```sh
-6.376098582823808494e-03;-1.292264747426501506e-02;1.162128304618341088e-03
  ```
BL ---> XY PL1992 dla danych z pliku 'BL_PL1992.txt' (kolejno fi, lambda)
```sh
Kolejną transfomacją, która będzie wykonana jest przeliczenie współrzędnych geodezyjnech do układu współrzędnych 1992. Otrzymujemy wyniki (kolejno X92[m],Y92[m])
 ``` 
  ```sh
-7.588505031305843012e+30;8.995907769979433183e+26
-7.601933921345102224e+30;8.991733227929724057e+26
-7.615366088553399143e+30;8.987551910347780673e+26
-7.628801521376370621e+30;8.983363817970532831e+26
-7.615366737067724896e+30;8.987552548154295784e+26
-7.607306654979123807e+30;8.990061769041092960e+26
-7.622083721748648864e+30;8.985459029878421452e+26
-7.632833014007675425e+30;8.982106292312742579e+26
-7.608650082541807507e+30;8.989643894326340210e+26
-7.607306654979123807e+30;8.990061769041092960e+26
-7.608650244527395998e+30;8.989644053815074412e+26
-7.605963454533838509e+30;8.990479767387636561e+26
  ```
BL ---> XY PL2000 (kolejno fi, lambda)
```sh
Dla danych z pliku, otrzymujemy wyniki (kolejno x2000, y2000)
 ```
  ```sh
-7.593850300552112147e+30;9.002123020348507139e+26
-7.607288649775469569e+30;8.997945594122355164e+26
-7.620730278476284891e+30;8.993761387682765189e+26
-7.634175175092058088e+30;8.989570401767178289e+26
-7.620730927438665889e+30;8.993762025921336143e+26
-7.612665167909139471e+30;8.996272980425200495e+26
-7.627452643504934053e+30;8.991667061245331678e+26
-7.638209507465871892e+30;8.988312007286308629e+26
-7.614009541766529683e+30;8.995854816999262031e+26
-7.612665167909139471e+30;8.996272980425200495e+26
-7.614009703864036002e+30;8.995854976596036995e+26
-7.611321021326504558e+30;8.996691267565764269e+26
  ```  

 
