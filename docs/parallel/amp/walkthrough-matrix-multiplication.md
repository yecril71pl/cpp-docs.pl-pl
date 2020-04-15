---
title: 'Wskazówki: mnożenie macierzy'
ms.date: 04/23/2019
ms.assetid: 61172e8b-da71-4200-a462-ff3a908ab0cf
ms.openlocfilehash: f30f8dc235bf0e76c342bea26a35bcbb36cfa237
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81366810"
---
# <a name="walkthrough-matrix-multiplication"></a>Wskazówki: mnożenie macierzy

W tym przewodniku krok po kroku pokazano, jak używać C++ AMP, aby przyspieszyć wykonywanie mnożenia macierzy. Prezentowane są dwa algorytmy, jeden bez kafelków i jeden z kafelkami.

## <a name="prerequisites"></a>Wymagania wstępne

Przed rozpoczęciem:

- Przeczytaj [przegląd C++ AMP](../../parallel/amp/cpp-amp-overview.md).

- Przeczytaj [za pomocą kafelków](../../parallel/amp/using-tiles.md).

- Upewnij się, że korzystasz z co najmniej systemu Windows 7 lub Windows Server 2008 R2.

### <a name="to-create-the-project"></a>Aby utworzyć projekt

Instrukcje dotyczące tworzenia nowego projektu różnią się w zależności od wersji programu Visual Studio, które zostały zainstalowane. Aby wyświetlić dokumentację preferowanej wersji programu Visual Studio, użyj formantu selektor **wersji.** Znajduje się w górnej części spisu treści na tej stronie.

::: moniker range="vs-2019"

### <a name="to-create-the-project-in-visual-studio-2019"></a>Aby utworzyć projekt w programie Visual Studio 2019

1. Na pasku menu wybierz pozycję **Plik** > **nowego** > **projektu,** aby otworzyć okno dialogowe Tworzenie nowego **projektu.**

1. W górnej części okna dialogowego ustaw **język** na **C++,** ustaw **platformę** na **Windows**i ustaw **typ projektu** na **Konsola**.

1. Z filtru listy typów projektów wybierz pozycję **Pusty projekt,** a następnie wybierz pozycję **Dalej**. Na następnej stronie wprowadź *MatrixMultiply* w polu **Nazwa,** aby określić nazwę projektu, i w razie potrzeby określ lokalizację projektu.

   ![Nowa aplikacja konsoli](../../build/media/mathclient-project-name-2019.png "Nowa aplikacja konsoli")

1. Wybierz przycisk **Utwórz,** aby utworzyć projekt klienta.

1. W **Eksploratorze rozwiązań**otwórz menu skrótów dla **plików źródłowych**, a następnie wybierz pozycję **Dodaj** > **nowy element**.

1. W oknie dialogowym **Dodawanie nowego elementu** wybierz pozycję Plik **C++ (cpp)**, wprowadź *plik MatrixMultiply.cpp* w polu **Nazwa,** a następnie wybierz przycisk **Dodaj.**

::: moniker-end

::: moniker range="<=vs-2017"

### <a name="to-create-a-project-in-visual-studio-2017-or-2015"></a>Aby utworzyć projekt w programie Visual Studio 2017 lub 2015

1. Na pasku menu w programie Visual Studio wybierz pozycję **Plik** > **nowego** > **projektu**.

1. W obszarze **Zainstalowane** w okienku szablonów wybierz pozycję **Visual C++**.

1. Wybierz **pozycję Pusty projekt**, wprowadź *matrixmultiply* w polu **Nazwa,** a następnie wybierz przycisk **OK.**

1. Wybierz przycisk **Dalej.**

1. W **Eksploratorze rozwiązań**otwórz menu skrótów dla **plików źródłowych**, a następnie wybierz pozycję **Dodaj** > **nowy element**.

1. W oknie dialogowym **Dodawanie nowego elementu** wybierz pozycję Plik **C++ (cpp)**, wprowadź *plik MatrixMultiply.cpp* w polu **Nazwa,** a następnie wybierz przycisk **Dodaj.**

::: moniker-end

## <a name="multiplication-without-tiling"></a>Mnożenie bez kafelków

W tej sekcji należy wziąć pod uwagę mnożenie dwóch macierzy, A i B, które są zdefiniowane w następujący sposób:

![3&#45;przez&#45;2 matrycę A](../../parallel/amp/media/campmatrixanontiled.png "3&#45;przez&#45;2 matrycę A")

![2&#45;&#45;3 matrycy B](../../parallel/amp/media/campmatrixbnontiled.png "2&#45;&#45;3 matrycy B")

A jest matrycą 3 na 2, a B matrycą 2 na 3. Produktem mnożenia A przez B jest następująca macierz 3 na 3. Produkt jest obliczany przez pomnożenie wierszy A przez kolumny elementu B przez element.

![3&#45;&#45;3 matrycy produktu](../../parallel/amp/media/campmatrixproductnontiled.png "3&#45;&#45;3 matrycy produktu")

### <a name="to-multiply-without-using-c-amp"></a>Mnożenie bez użycia C++ AMP

1. Otwórz MatrixMultiply.cpp i użyj następującego kodu, aby zastąpić istniejący kod.

   ```cpp
   #include <iostream>

   void MultiplyWithOutAMP() {
       int aMatrix[3][2] = {{1, 4}, {2, 5}, {3, 6}};
       int bMatrix[2][3] = {{7, 8, 9}, {10, 11, 12}};
       int product[3][3] = {{0, 0, 0}, {0, 0, 0}, {0, 0, 0}};

       for (int row = 0; row < 3; row++) {
           for (int col = 0; col < 3; col++) {
               // Multiply the row of A by the column of B to get the row, column of product.
               for (int inner = 0; inner < 2; inner++) {
                   product[row][col] += aMatrix[row][inner] * bMatrix[inner][col];
               }
               std::cout << product[row][col] << "  ";
           }
           std::cout << "\n";
       }
   }

   int main() {
       MultiplyWithOutAMP();
       getchar();
   }
   ```

   Algorytm jest prostą implementacją definicji mnożenia macierzy. Nie używa żadnych algorytmów równoległych lub wątkowych, aby skrócić czas obliczeń.

1. Na pasku menu wybierz pozycję Zapisz**wszystko** **.** > 

1. Wybierz skrót klawiaturowy **F5,** aby rozpocząć debugowanie i sprawdź, czy dane wyjściowe są poprawne.

1. Wybierz **pozycję Enter,** aby zakończyć działanie aplikacji.

### <a name="to-multiply-by-using-c-amp"></a>Aby pomnożyć za pomocą C++ AMP

1. W MatrixMultiply.cpp dodaj następujący kod `main` przed metodą.

   ```cpp
   void MultiplyWithAMP() {
   int aMatrix[] = { 1, 4, 2, 5, 3, 6 };
   int bMatrix[] = { 7, 8, 9, 10, 11, 12 };
   int productMatrix[] = { 0, 0, 0, 0, 0, 0, 0, 0, 0 };

   array_view<int, 2> a(3, 2, aMatrix);

   array_view<int, 2> b(2, 3, bMatrix);

   array_view<int, 2> product(3, 3, productMatrix);

   parallel_for_each(product.extent,
      [=] (index<2> idx) restrict(amp) {
          int row = idx[0];
          int col = idx[1];
          for (int inner = 0; inner <2; inner++) {
              product[idx] += a(row, inner)* b(inner, col);
          }
      });

   product.synchronize();

   for (int row = 0; row <3; row++) {
      for (int col = 0; col <3; col++) {
          //std::cout << productMatrix[row*3 + col] << "  ";
          std::cout << product(row, col) << "  ";
      }
      std::cout << "\n";
     }
   }
   ```

   Kod AMP przypomina kod niż AMP. Wywołanie `parallel_for_each` rozpoczyna jeden wątek `product.extent`dla każdego elementu `for` w , i zastępuje pętle dla wiersza i kolumny. Wartość komórki w wierszu i kolumnie `idx`jest dostępna w pliku . Dostęp do elementów `array_view` obiektu można uzyskać `[]` za pomocą operatora i `()` zmiennej indeksu lub do operatora oraz zmiennych wierszy i kolumn. W przykładzie przedstawiono obie metody. Metoda `array_view::synchronize` kopiuje wartości `product` zmiennej z `productMatrix` powrotem do zmiennej.

1. Dodaj następujące `include` `using` instrukcje i instrukcje w górnej części MatrixMultiply.cpp.

   ```cpp
   #include <amp.h>
   using namespace concurrency;
   ```

1. `main` Zmodyfikuj `MultiplyWithAMP` metodę, aby wywołać metodę.

   ```cpp
   int main() {
       MultiplyWithOutAMP();
       MultiplyWithAMP();
       getchar();
   }
   ```

1. Naciśnij skrót klawiaturowy **Ctrl**+**F5,** aby rozpocząć debugowanie i sprawdzić, czy dane wyjściowe są poprawne.

1. Naciśnij **spację,** aby wyjść z aplikacji.

## <a name="multiplication-with-tiling"></a>Mnożenie z kafelkami

Kafli jest techniką, w której dane partycjonowania do równych rozmiarów podzbiorów, które są znane jako kafelki. Trzy rzeczy zmieniają się podczas korzystania z kafelków.

- Można tworzyć `tile_static` zmienne. Dostęp do `tile_static` danych w przestrzeni może być wiele razy szybszy niż dostęp do danych w przestrzeni globalnej. Wystąpienie zmiennej `tile_static` jest tworzony dla każdego kafelka, a wszystkie wątki na kafelku mają dostęp do zmiennej. Podstawową zaletą kafelków jest `tile_static` przyrost wydajności dzięki dostępowi.

- Można wywołać [tile_barrier::wait](reference/tile-barrier-class.md#wait) metody, aby zatrzymać wszystkie wątki w jednym kafelku w określonym wierszu kodu. Nie można zagwarantować kolejność, w której wątki będą uruchamiane, tylko, że wszystkie wątki w jednym kafelku zatrzyma się `tile_barrier::wait` na wywołanie przed ich kontynuowaniem wykonywania.

- Masz dostęp do indeksu wątku względem `array_view` całego obiektu i indeksu względem kafelka. Za pomocą indeksu lokalnego, można ułatwić odczytanie i debugowanie kodu.

Aby skorzystać z kafelków w mnożeniu macierzy, algorytm musi podzielić macierz na kafelki, a następnie skopiować dane kafelków do zmiennych w `tile_static` celu szybszego dostępu. W tym przykładzie macierz jest podzielony na podmateitryki o równym rozmiarze. Produkt znajduje się przez pomnożenie podmateiów. Dwa macierze i ich produkt w tym przykładzie to:

![4&#45;&#45;4 matrycą A](../../parallel/amp/media/campmatrixatiled.png "4&#45;&#45;4 matrycą A")

![4&#45;przez&#45;4 matrycę B](../../parallel/amp/media/campmatrixbtiled.png "4&#45;przez&#45;4 matrycę B")

![4&#45;&#45;4 matrycy produktu](../../parallel/amp/media/campmatrixproducttiled.png "4&#45;&#45;4 matrycy produktu")

Macierze są podzielone na cztery macierze 2x2, które są zdefiniowane w następujący sposób:

![4&#45;przez&#45;4 matrycy A podzielony na 2&#45;przez&#45;2 sub&#45;matryce](../../parallel/amp/media/campmatrixapartitioned.png "4&#45;przez&#45;4 matrycy A podzielony na 2&#45;przez&#45;2 sub&#45;matryce")

![4&#45;przez&#45;4 macierzy B podzielonych na 2&#45;przez&#45;2 matryce pod&#45;](../../parallel/amp/media/campmatrixbpartitioned.png "4&#45;przez&#45;4 macierzy B podzielonych na 2&#45;przez&#45;2 matryce pod&#45;")

Produkt A i B można teraz zapisać i obliczyć w następujący sposób:

![4&#45;&#45;4 matrycą A B podzieloną na 2&#45;przez&#45;2 matryce podrzędne&#45;](../../parallel/amp/media/campmatrixproductpartitioned.png "4&#45;&#45;4 matrycą A B podzieloną na 2&#45;przez&#45;2 matryce podrzędne&#45;")

Ponieważ `a` macierze `h` są matrycami 2x2, wszystkie produkty i ich sumy są również matrycami 2x2. Wynika z tego również, że produkt A i B jest matrycą 4x4, zgodnie z oczekiwaniami. Aby szybko sprawdzić algorytm, oblicz wartość elementu w pierwszym wierszu, pierwszej kolumnie w produkcie. W tym przykładzie będzie to wartość elementu w pierwszym wierszu i pierwszej kolumnie . `ae + bg` Wystarczy obliczyć pierwszą kolumnę, `ae` `bg` pierwszy wiersz i dla każdego terminu. Ta wartość `ae` `(1 * 1) + (2 * 5) = 11`jest . Wartość dla `bg` `(3 * 1) + (4 * 5) = 23`jest . Ostateczna wartość `11 + 23 = 34`jest , co jest poprawne.

Aby zaimplementować ten algorytm, kod:

- Używa `tiled_extent` obiektu zamiast obiektu `extent` w wywołaniu. `parallel_for_each`

- Używa `tiled_index` obiektu zamiast obiektu `index` w wywołaniu. `parallel_for_each`

- Tworzy `tile_static` zmienne do przechowywania podmateiów.

- Używa metody, `tile_barrier::wait` aby zatrzymać wątki do obliczania produktów podmateich.

### <a name="to-multiply-by-using-amp-and-tiling"></a>Aby pomnożyć za pomocą AMP i kafelków

1. W MatrixMultiply.cpp dodaj następujący kod `main` przed metodą.

   ```cpp
   void MultiplyWithTiling() {
       // The tile size is 2.
       static const int TS = 2;

       // The raw data.
       int aMatrix[] = { 1, 2, 3, 4, 5, 6, 7, 8, 1, 2, 3, 4, 5, 6, 7, 8 };
       int bMatrix[] = { 1, 2, 3, 4, 5, 6, 7, 8, 1, 2, 3, 4, 5, 6, 7, 8 };
       int productMatrix[] = { 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0 };

       // Create the array_view objects.
       array_view<int, 2> a(4, 4, aMatrix);
       array_view<int, 2> b(4, 4, bMatrix);
       array_view<int, 2> product(4, 4, productMatrix);

       // Call parallel_for_each by using 2x2 tiles.
       parallel_for_each(product.extent.tile<TS, TS>(),
           [=] (tiled_index<TS, TS> t_idx) restrict(amp)
           {
               // Get the location of the thread relative to the tile (row, col)
               // and the entire array_view (rowGlobal, colGlobal).
               int row = t_idx.local[0];
               int col = t_idx.local[1];
               int rowGlobal = t_idx.global[0];
               int colGlobal = t_idx.global[1];
               int sum = 0;

               // Given a 4x4 matrix and a 2x2 tile size, this loop executes twice for each thread.
               // For the first tile and the first loop, it copies a into locA and e into locB.
               // For the first tile and the second loop, it copies b into locA and g into locB.
               for (int i = 0; i < 4; i += TS) {
                   tile_static int locA[TS][TS];
                   tile_static int locB[TS][TS];
                   locA[row][col] = a(rowGlobal, col + i);
                   locB[row][col] = b(row + i, colGlobal);
                   // The threads in the tile all wait here until locA and locB are filled.
                   t_idx.barrier.wait();

                   // Return the product for the thread. The sum is retained across
                   // both iterations of the loop, in effect adding the two products
                   // together, for example, a*e.
                   for (int k = 0; k < TS; k++) {
                       sum += locA[row][k] * locB[k][col];
                   }

                   // All threads must wait until the sums are calculated. If any threads
                   // moved ahead, the values in locA and locB would change.
                   t_idx.barrier.wait();
                   // Now go on to the next iteration of the loop.
               }

               // After both iterations of the loop, copy the sum to the product variable by using the global location.
               product[t_idx.global] = sum;
           });

       // Copy the contents of product back to the productMatrix variable.
       product.synchronize();

       for (int row = 0; row <4; row++) {
           for (int col = 0; col <4; col++) {
               // The results are available from both the product and productMatrix variables.
               //std::cout << productMatrix[row*3 + col] << "  ";
               std::cout << product(row, col) << "  ";
           }
           std::cout << "\n";
       }
   }
   ```

   Ten przykład znacznie różni się od przykładu bez kafli. Kod używa tych kroków koncepcyjnych:
   1. Skopiuj elementy płytki[0,0] do `a` `locA`. Skopiuj elementy płytki[0,0] do `b` `locB`. Należy `product` zauważyć, że `a` jest `b`sąsiadująco, nie i . W związku z tym można użyć `a, b`globalnych indeksów, aby uzyskać dostęp , i `product`. Wezwanie do `tile_barrier::wait` jest niezbędne. Zatrzymuje wszystkie wątki w kafelku, `locA` `locB` aż oba i są wypełnione.

   1. Pomnóż `locA` `locB` i `product`umieść wyniki w .

   1. Skopiuj elementy płytki[0,1] do `a` `locA`. Skopiuj elementy płytki [1,0] `b` do pliku `locB`.

   1. Pomnożyć `locA` i `locB` dodać je `product`do wyników, które są już w .

   1. Mnożenie płytek[0,0] jest kompletne.

   1. Powtórz tę czynność dla pozostałych czterech płytek. Nie ma indeksowania specjalnie dla kafelków i wątki można wykonać w dowolnej kolejności. Jak każdy wątek `tile_static` wykonuje, zmienne są tworzone dla każdego `tile_barrier::wait` kafelka odpowiednio i wywołanie do sterowania przepływem programu.

   1. Podczas dokładnego zbadania algorytmu należy zauważyć, że `tile_static` każdy podmatebator jest dwukrotnie ładowany do pamięci. Ten transfer danych wymaga czasu. Jednak gdy dane są `tile_static` w pamięci, dostęp do danych jest znacznie szybszy. Ponieważ obliczanie produktów wymaga wielokrotnego dostępu do wartości w podmatryczach, istnieje ogólny przyrost wydajności. Dla każdego algorytmu eksperymentowanie jest wymagane, aby znaleźć optymalny algorytm i rozmiar kafelka.

   W przykładach innych niż AMP i innych niż kafelki każdy element A i B jest dostępny cztery razy z pamięci globalnej, aby obliczyć produkt. W przykładzie kafelka każdy element jest dostępny dwa razy `tile_static` z pamięci globalnej i cztery razy z pamięci. Nie jest to znaczący wzrost wydajności. Jednakże, jeśli A i B były matrycami 1024x1024, a rozmiar płytek 16, nastąpiłby znaczny wzrost wydajności. W takim przypadku każdy element zostanie `tile_static` skopiowany do pamięci tylko `tile_static` 16 razy i dostęp z pamięci 1024 razy.

1. Zmodyfikuj `MultiplyWithTiling` metodę główną, aby wywołać metodę, jak pokazano.

   ```cpp
   int main() {
       MultiplyWithOutAMP();
       MultiplyWithAMP();
       MultiplyWithTiling();
       getchar();
   }
   ```

1. Naciśnij skrót klawiaturowy **Ctrl**+**F5,** aby rozpocząć debugowanie i sprawdzić, czy dane wyjściowe są poprawne.

1. Naciśnij **spację,** aby wyjść z aplikacji.

## <a name="see-also"></a>Zobacz też

[C++ AMP (C++ Accelerated Massive Parallelism)](../../parallel/amp/cpp-amp-cpp-accelerated-massive-parallelism.md)<br/>
[Przewodnik: debugowanie aplikacji C++ AMP](../../parallel/amp/walkthrough-debugging-a-cpp-amp-application.md)
