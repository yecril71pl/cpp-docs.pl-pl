---
title: 'Wskazówki: mnożenie macierzy'
ms.date: 04/23/2019
ms.assetid: 61172e8b-da71-4200-a462-ff3a908ab0cf
ms.openlocfilehash: 6387e68304c7b1dbf0531729b7b73b519f40d159
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87215871"
---
# <a name="walkthrough-matrix-multiplication"></a>Wskazówki: mnożenie macierzy

W tym przewodniku krok po kroku pokazano, jak za pomocą C++ AMP przyspieszyć wykonywanie operacji mnożenia macierzy. Prezentowane są dwa algorytmy, jeden bez dzielenia i jeden z rozdzieleniem.

## <a name="prerequisites"></a>Wymagania wstępne

Przed rozpoczęciem:

- Przeczytaj [C++ amp przegląd](../../parallel/amp/cpp-amp-overview.md).

- Przeczytaj [przy użyciu kafelków](../../parallel/amp/using-tiles.md).

- Upewnij się, że korzystasz z systemu Windows 7 lub Windows Server 2008 R2.

### <a name="to-create-the-project"></a>Aby utworzyć projekt

Instrukcje dotyczące tworzenia nowego projektu różnią się w zależności od zainstalowanej wersji programu Visual Studio. Aby wyświetlić dokumentację preferowanej wersji programu Visual Studio, użyj kontrolki selektora **wersji** . Znajduje się w górnej części spisu treści na tej stronie.

::: moniker range="vs-2019"

### <a name="to-create-the-project-in-visual-studio-2019"></a>Aby utworzyć projekt w programie Visual Studio 2019

1. Na pasku menu wybierz pozycję **plik** > **Nowy** > **projekt** , aby otworzyć okno dialogowe **Tworzenie nowego projektu** .

1. W górnej części okna dialogowego Ustaw **Język** na **C++**, ustaw **platformę** na **Windows**i ustaw **Typ projektu** na **Console**.

1. Z listy filtrowane typy projektów wybierz pozycję **pusty projekt** , a następnie wybierz przycisk **dalej**. Na następnej stronie wprowadź *MatrixMultiply* w polu **Nazwa** , aby określić nazwę projektu, i w razie potrzeby określ lokalizację projektu.

   ![Nowa aplikacja konsolowa](../../build/media/mathclient-project-name-2019.png "Nowa aplikacja konsolowa")

1. Wybierz przycisk **Utwórz** , aby utworzyć projekt klienta.

1. W **Eksplorator rozwiązań**Otwórz menu skrótów dla **plików źródłowych**, a następnie wybierz polecenie **Dodaj** > **nowy element**.

1. W oknie dialogowym **Dodaj nowy element** wybierz pozycję **plik C++ (. cpp)**, wprowadź *MatrixMultiply. cpp* w polu **Nazwa** , a następnie wybierz przycisk **Dodaj** .

::: moniker-end

::: moniker range="<=vs-2017"

### <a name="to-create-a-project-in-visual-studio-2017-or-2015"></a>Aby utworzyć projekt w programie Visual Studio 2017 lub 2015

1. Na pasku menu w programie Visual Studio wybierz pozycję **plik** > **Nowy** > **projekt**.

1. W obszarze **zainstalowane** w okienku szablony wybierz pozycję **Visual C++**.

1. Wybierz pozycję **pusty projekt**, wprowadź *MatrixMultiply* w polu **Nazwa** , a następnie wybierz przycisk **OK** .

1. Wybierz przycisk **dalej** .

1. W **Eksplorator rozwiązań**Otwórz menu skrótów dla **plików źródłowych**, a następnie wybierz polecenie **Dodaj** > **nowy element**.

1. W oknie dialogowym **Dodaj nowy element** wybierz pozycję **plik C++ (. cpp)**, wprowadź *MatrixMultiply. cpp* w polu **Nazwa** , a następnie wybierz przycisk **Dodaj** .

::: moniker-end

## <a name="multiplication-without-tiling"></a>Mnożenie bez dzielenia

W tej sekcji Rozważmy mnożenie dwóch macierzy, a i B, które są zdefiniowane w następujący sposób:

![3&#45;przez&#45;2 macierz A](../../parallel/amp/media/campmatrixanontiled.png "3&#45;przez&#45;2 macierz A")

![2&#45;przez&#45;3 macierze B](../../parallel/amp/media/campmatrixbnontiled.png "2&#45;przez&#45;3 macierze B")

A to macierz 3-na-2, a B to macierz 2-na-3. Iloczyn mnożenia A przez B to następująca macierz 3-by-3. Produkt jest obliczany przez pomnożenie wierszy A przez kolumny elementów B według elementu.

![3&#45;według&#45;3 macierzy produktu](../../parallel/amp/media/campmatrixproductnontiled.png "3&#45;według&#45;3 macierzy produktu")

### <a name="to-multiply-without-using-c-amp"></a>Aby pomnożyć bez używania C++ AMP

1. Otwórz MatrixMultiply. cpp i użyj poniższego kodu, aby zamienić istniejący kod.

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

   Algorytm jest prostą implementacją definicji mnożenia macierzy. Nie używa żadnych algorytmów równoległych lub wielowątkowych, aby skrócić czas obliczeń.

1. Na pasku menu wybierz kolejno opcje **plik**  >  **Zapisz wszystko**.

1. Wybierz skrót klawiaturowy **F5** , aby rozpocząć debugowanie i sprawdzić, czy dane wyjściowe są poprawne.

1. Wybierz **klawisz ENTER** , aby zakończyć działanie aplikacji.

### <a name="to-multiply-by-using-c-amp"></a>Aby pomnożyć przy użyciu C++ AMP

1. W MatrixMultiply. cpp Dodaj następujący kod przed `main` metodą.

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

   Kod AMP przypomina kod inny niż AMP. Wywołanie `parallel_for_each` uruchamia jeden wątek dla każdego elementu w `product.extent` , i zastępuje **`for`** pętle dla wiersza i kolumny. Wartość komórki w wierszu i kolumnie jest dostępna w `idx` . Dostęp do elementów obiektu można uzyskać za `array_view` pomocą `[]` operatora i zmiennej indeksu albo `()` operatora i zmiennych wierszy i kolumn. Przykład ilustruje obydwie metody. `array_view::synchronize`Metoda kopiuje wartości `product` zmiennej z powrotem do `productMatrix` zmiennej.

1. Dodaj poniższe `include` instrukcje i **`using`** w górnej części MatrixMultiply. cpp.

   ```cpp
   #include <amp.h>
   using namespace concurrency;
   ```

1. Zmodyfikuj `main` metodę, aby wywołać `MultiplyWithAMP` metodę.

   ```cpp
   int main() {
       MultiplyWithOutAMP();
       MultiplyWithAMP();
       getchar();
   }
   ```

1. Naciśnij **Ctrl** + skrót klawiaturowy CTRL**F5** , aby rozpocząć debugowanie i sprawdzić, czy dane wyjściowe są poprawne.

1. Naciśnij klawisz **spacji** , aby zakończyć działanie aplikacji.

## <a name="multiplication-with-tiling"></a>Mnożenie z rozdzieleniem

Dzielenie jest techniką, w której można podzielić dane na podzbiory o równym rozmiarze, które są znane jako kafelki. Trzy rzeczy zmieniają się w przypadku korzystania z dzielenia.

- Można tworzyć `tile_static` zmienne. Dostęp do danych w `tile_static` miejscu może być dużo szybszy niż dostęp do danych w obszarze globalnym. Wystąpienie `tile_static` zmiennej jest tworzone dla każdego kafelka, a wszystkie wątki na kafelku mają dostęp do zmiennej. Główną zaletą dzielenia jest wzrost wydajności spowodowany `tile_static` dostępem.

- Można wywołać metodę [tile_barrier:: wait](reference/tile-barrier-class.md#wait) , aby zatrzymać wszystkie wątki w jednym kafelku w określonym wierszu kodu. Nie można zagwarantować kolejności, w której wątki będą działać, tylko wtedy, gdy wszystkie wątki w jednym kafelku zostaną zatrzymane w wywołaniu `tile_barrier::wait` przed kontynuowaniem wykonywania.

- Masz dostęp do indeksu wątku względem całego `array_view` obiektu i indeksu względem kafelka. Za pomocą lokalnego indeksu można ułatwić odczytywanie i debugowanie kodu.

Aby skorzystać z dzielenia na fragmenty macierzy, algorytm musi podzielić macierz na kafelki, a następnie skopiować dane kafelków do zmiennych, `tile_static` Aby uzyskać szybszy dostęp. W tym przykładzie macierz jest partycjonowana do podmacierzy o równym rozmiarze. Produkt jest znaleziony przez pomnożenie podmacierzy. W tym przykładzie dwie macierze i ich produkty są następujące:

![4&#45;według&#45;4 macierzy A](../../parallel/amp/media/campmatrixatiled.png "4&#45;według&#45;4 macierzy A")

![4&#45;według&#45;4 macierzy B](../../parallel/amp/media/campmatrixbtiled.png "4&#45;według&#45;4 macierzy B")

![4&#45;według&#45;4 macierzy produktu](../../parallel/amp/media/campmatrixproducttiled.png "4&#45;według&#45;4 macierzy produktu")

Macierze są podzielone na cztery macierze 2x2, które są zdefiniowane w następujący sposób:

![4&#45;w przypadku macierzy&#45;4 podzielonej na 2&#45;przez&#45;2 macierzy&#45;](../../parallel/amp/media/campmatrixapartitioned.png "4&#45;w przypadku macierzy&#45;4 podzielonej na 2&#45;przez&#45;2 macierzy&#45;")

![4&#45;przez&#45;4 macierz B podzielone na 2&#45;przez&#45;2 macierzy&#45;](../../parallel/amp/media/campmatrixbpartitioned.png "4&#45;przez&#45;4 macierz B podzielone na 2&#45;przez&#45;2 macierzy&#45;")

Produkt a i B można teraz napisać i obliczyć w następujący sposób:

![4&#45;przez&#45;4 macierz B z podziałem na 2&#45;przez&#45;2 macierzy&#45;](../../parallel/amp/media/campmatrixproductpartitioned.png "4&#45;przez&#45;4 macierz B z podziałem na 2&#45;przez&#45;2 macierzy&#45;")

Ponieważ macierze `a` za pomocą `h` są macierzami 2x2, wszystkie produkty i ich sumy są również macierzami 2x2. Następuje również, że produkt a i B jest macierzą 4x4 zgodnie z oczekiwaniami. Aby szybko sprawdzić algorytm, Oblicz wartość elementu w pierwszym wierszu, w pierwszej kolumnie w produkcie. W przykładzie, który będzie wartością elementu w pierwszym wierszu i pierwszą kolumną `ae + bg` . Musisz tylko obliczyć pierwszą kolumnę, pierwszy wiersz `ae` i `bg` dla każdego okresu. Ta wartość dla `ae` jest równa `(1 * 1) + (2 * 5) = 11` . Wartość parametru `bg` is `(3 * 1) + (4 * 5) = 23` . Końcowa wartość to `11 + 23 = 34` , która jest poprawna.

Aby zaimplementować ten algorytm, kod:

- Używa `tiled_extent` obiektu zamiast `extent` obiektu w `parallel_for_each` wywołaniu.

- Używa `tiled_index` obiektu zamiast `index` obiektu w `parallel_for_each` wywołaniu.

- Tworzy `tile_static` zmienne do przechowywania podmacierzy.

- Używa `tile_barrier::wait` metody do zatrzymania wątków do obliczania produktów podmacierzy.

### <a name="to-multiply-by-using-amp-and-tiling"></a>Aby pomnożyć przy użyciu AMP i rozdzielenie

1. W MatrixMultiply. cpp Dodaj następujący kod przed `main` metodą.

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

   Ten przykład jest znacznie różny niż w przypadku przykładu bez dzielenia. Kod używa następujących kroków koncepcyjnych:
   1. Skopiuj elementy kafelka [0, 0] z `a` do `locA` . Skopiuj elementy kafelka [0, 0] z `b` do `locB` . Zwróć uwagę `product` , że jest to fragmenty, nie `a` i `b` . W związku z tym, można użyć indeksów globalnych, aby uzyskać dostęp do `a, b` , i `product` . Wywołanie `tile_barrier::wait` jest niezbędne. Powoduje zatrzymanie wszystkich wątków na kafelku do momentu `locA` wypełnienia obu `locB` .

   1. Pomnóż `locA` i `locB` Umieść wyniki w `product` .

   1. Skopiuj elementy kafelka [0, 1] z `a` do `locA` . Skopiuj elementy kafelka [1, 0] z `b` do `locB` .

   1. Pomnóż `locA` i `locB` Dodaj je do wyników, które już znajdują się w `product` .

   1. Mnożenie kafelka [0, 0] zostało zakończone.

   1. Powtórz dla innych czterech kafelków. Dla kafelków nie istnieje indeksowanie, a wątki można wykonać w dowolnej kolejności. W miarę wykonywania każdego wątku `tile_static` zmienne są tworzone dla każdego kafelka odpowiednio i wywołania do `tile_barrier::wait` sterowania przepływem programu.

   1. Analizując algorytm blisko, Zauważ, że każda podmacierz jest ładowana do `tile_static` pamięci dwa razy. Ten transfer danych trwa. Jednak gdy dane są w `tile_static` pamięci, dostęp do danych jest znacznie szybszy. Ponieważ Obliczanie produktów wymaga powtarzanego dostępu do wartości w podmacierzy, istnieje ogólny wzrost wydajności. Dla każdego algorytmu eksperymentowanie jest wymagane, aby znaleźć optymalny algorytm i rozmiar kafelka.

   W przykładach innych niż AMP i nienależących do kafelków każdy element A i B jest dostępny cztery razy z pamięci globalnej w celu obliczenia produktu. W przykładzie kafelka każdy element jest dostępny dwa razy z pamięci globalnej i cztery razy z `tile_static` pamięci. To nie jest znaczący wzrost wydajności. Jeśli jednak a i B były macierzami 1024x1024, a rozmiar kafelka wynosi 16, nastąpi znaczący wzrost wydajności. W takim przypadku każdy element zostałby skopiowany do `tile_static` pamięci tylko 16 razy i dostęp do `tile_static` pamięci 1024 razy.

1. Zmodyfikuj metodę Main, aby wywołać `MultiplyWithTiling` metodę, jak pokazano.

   ```cpp
   int main() {
       MultiplyWithOutAMP();
       MultiplyWithAMP();
       MultiplyWithTiling();
       getchar();
   }
   ```

1. Naciśnij **Ctrl** + skrót klawiaturowy CTRL**F5** , aby rozpocząć debugowanie i sprawdzić, czy dane wyjściowe są poprawne.

1. Naciśnij klawisz **spacji** , aby zakończyć działanie aplikacji.

## <a name="see-also"></a>Zobacz także

[C++ AMP (C++ Accelerated Massive Parallelism)](../../parallel/amp/cpp-amp-cpp-accelerated-massive-parallelism.md)<br/>
[Przewodnik: debugowanie aplikacji C++ AMP](../../parallel/amp/walkthrough-debugging-a-cpp-amp-application.md)
