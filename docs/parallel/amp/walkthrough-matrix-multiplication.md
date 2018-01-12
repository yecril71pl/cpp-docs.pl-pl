---
title: "Wskazówki: Mnożenie macierzy | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
ms.assetid: 61172e8b-da71-4200-a462-ff3a908ab0cf
caps.latest.revision: "16"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: f91bed0b33ae29d7928ec7df3420eb4878b51eef
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="walkthrough-matrix-multiplication"></a>Wskazówki: mnożenie macierzy
Ten przewodnik krok po kroku przedstawiono sposób użycia C++ AMP w celu przyspieszenia wykonywania mnożenie macierzy. Dwa algorytmy są prezentowane, jeden bez kafelków i jeden z kafelków.  
  
## <a name="prerequisites"></a>Wymagania wstępne  
 Przed rozpoczęciem:  
  
-   Odczyt [Przegląd C++ AMP](../../parallel/amp/cpp-amp-overview.md).  
  
-   Odczyt [przy użyciu Kafelki](../../parallel/amp/using-tiles.md).  
  
-   Upewnij się, że [!INCLUDE[win7](../../build/includes/win7_md.md)], [!INCLUDE[win8](../../build/reference/includes/win8_md.md)], [!INCLUDE[winsvr08_r2](../../parallel/amp/includes/winsvr08_r2_md.md)], lub [!INCLUDE[winserver8](../../build/reference/includes/winserver8_md.md)] jest zainstalowany na tym komputerze.  
  
### <a name="to-create-the-project"></a>Aby utworzyć projekt  
  
1.  Na pasku menu programu Visual Studio wybierz **pliku**, **nowy**, **projektu**.  
  
2.  W obszarze **zainstalowana** w okienku szablonów wybierz **Visual C++**.  
  
3.  Wybierz **pusty projekt**, wprowadź `MatrixMultiply` w **nazwa** polu, a następnie wybierz pozycję **OK** przycisku.  
  
4.  Wybierz **dalej** przycisku.  
  
5.  W **Eksploratora rozwiązań**, otwórz menu skrótów **pliki źródłowe**, a następnie wybierz pozycję **Dodaj**, **nowy element**.  
  
6.  W **Dodaj nowy element** okno dialogowe, wybierz opcję **plik C++ (.cpp)**, wprowadź `MatrixMultiply.cpp` w **nazwa** polu, a następnie wybierz pozycję **Dodaj** przycisk.  
  
## <a name="multiplication-without-tiling"></a>Mnożenia bez kafelków  
 W tej sekcji należy wziąć pod uwagę mnożenia macierzy dwa, A i B, które są zdefiniowane w następujący sposób:  
  
 ![3 &#45; przez &#45; 2 macierzy](../../parallel/amp/media/campmatrixanontiled.png "campmatrixanontiled")  
  
 ![2 &#45; przez &#45; 3 macierzy](../../parallel/amp/media/campmatrixbnontiled.png "campmatrixbnontiled")  
  
 Macierzy 3 na 2 jest A i B jest macierzy 2 przez 3. Produkt multiplikujący a b jest następujące macierzy 3 x 3. Produkt jest obliczany przez pomnożenie wiersze A według kolumn B elementów.  
  
 ![3 &#45; przez &#45; 3 macierzy](../../parallel/amp/media/campmatrixproductnontiled.png "campmatrixproductnontiled")  
  
### <a name="to-multiply-without-using-c-amp"></a>Aby pomnożyć bez korzystania z C++ AMP  
  
1.  Otwórz MatrixMultiply.cpp i użyć poniższego kodu, aby zastąpić istniejący kod.  
  
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
  
void main() {  
    MultiplyWithOutAMP();  
    getchar();  
}  
```  
  
    The algorithm is a straightforward implementation of the definition of matrix multiplication. It does not use any parallel or threaded algorithms to reduce the computation time.  
  
2.  Na pasku menu wybierz **pliku**, **Zapisz wszystko**.  
  
3.  Wybierz skrót klawiaturowy F5 Rozpocznij debugowanie i sprawdź, czy dane wyjściowe jest poprawna.  
  
4.  Wybierz Enter, aby zakończyć działanie aplikacji.  
  
### <a name="to-multiply-by-using-c-amp"></a>Aby pomnożyć przy użyciu C++ AMP  
  
1.  W MatrixMultiply.cpp, Dodaj następujący kod przed `main` metody.  
  
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
  
    The AMP code resembles the non-AMP code. The call to `parallel_for_each` starts one thread for each element in `product.extent`, and replaces the `for` loops for row and column. The value of the cell at the row and column is available in `idx`. You can access the elements of an `array_view` object by using either the `[]` operator and an index variable, or the `()` operator and the row and column variables. The example demonstrates both methods. The `array_view::synchronize` method copies the values of the `product` variable back to the `productMatrix` variable.  
  
2.  Dodaj następujące `include` i `using` instrukcje w górnej części MatrixMultiply.cpp.  
  
```cpp  
#include <amp.h>  
using namespace concurrency;  
```  
  
3.  Modyfikowanie `main` metodę do wywołania `MultiplyWithAMP` metody.  
  
```cpp  
void main() {  
    MultiplyWithOutAMP();  
    MultiplyWithAMP();  
    getchar();  
}  
```  
  
4.  Wybierz skrótu klawiaturowego Ctrl + F5 można rozpocząć debugowania, a następnie sprawdź poprawność danych wyjściowych.  
  
5.  Wybierz klawisz spacji, aby zakończyć działanie aplikacji.  
  
## <a name="multiplication-with-tiling"></a>Mnożenie z kafelków  
 Kafelków to technika partycjonowania danych na o wielkości równej podzbiory, które są znane jako kafelki. Trzy czynności zmienić, gdy używasz kafelków.  
  
-   Można utworzyć `tile_static` zmiennych. Dostęp do danych w `tile_static` miejsca można wielokrotnie szybszy dostęp do danych w globalnej przestrzeni. Wystąpienie `tile_static` zmiennej jest tworzony dla każdego kafelka, a wszystkie wątki na kafelku mają dostęp do zmiennej. Główną zaletą kafelków jest bardziej wydajne, ze względu na `tile_static` dostępu.  
  
-   Możesz wywołać [tile_barrier::wait](reference/tile-barrier-class.md#wait) metodę, aby zatrzymać wszystkie wątki w jednej kafelków na określony wiersz kodu. Nie może zagwarantować kolejności wątki będą uruchamiane tylko w, wszystkie wątki w jednej kafelków zostanie zatrzymane w wywołaniu `tile_barrier::wait` kontynuowania wykonywania.  

  
-   Masz dostęp do indeksu wątku względem całą `array_view` obiektu i pod indeksem względem kafelka. Przy użyciu indeksu lokalnej, możesz wprowadzić kod łatwiej odczytywać i debugowania.  
  
 Aby skorzystać z kafelków w mnożenie macierzy, algorytm musi podziału macierzy na kafelkach i następnie skopiować dane kafelka w `tile_static` zmienne szybszy dostęp. W tym przykładzie macierzy jest podzielona na partycje w submatrices taki sam rozmiar. Znaleziono przez pomnożenie submatrices produktu. Macierzy dwa i ich produktów, w tym przykładzie są:  
  
 ![4 &#45; przez &#45; 4 macierzy](../../parallel/amp/media/campmatrixatiled.png "campmatrixatiled")  
  
 ![4 &#45; przez &#45; 4 macierzy](../../parallel/amp/media/campmatrixbtiled.png "campmatrixbtiled")  
  
 ![4 &#45; przez &#45; 4 macierzy](../../parallel/amp/media/campmatrixproducttiled.png "campmatrixproducttiled")  
  
 Macierze są podzielone na partycje w macierzy cztery 2 x 2, które są zdefiniowane w następujący sposób:  
  
 ![4 &#45; przez &#45;4 macierzy podzielona na partycje do 2 &#45; w &#45; 2 sub &#45; macierze](../../parallel/amp/media/campmatrixapartitioned.png "campmatrixapartitioned")  
  
 ![4 &#45; przez &#45;4 macierzy podzielona na partycje do 2 &#45; w &#45; 2 sub &#45; macierze](../../parallel/amp/media/campmatrixbpartitioned.png "campmatrixbpartitioned")  
  
 Produkt A i B mogą teraz zapisywane i oblicza w następujący sposób:  
  
 ![4 &#45; przez &#45;4 macierzy podzielona na partycje do 2 &#45; w &#45; 2 sub &#45; macierze](../../parallel/amp/media/campmatrixproductpartitioned.png "campmatrixproductpartitioned")  
  
 Ponieważ macierze `a` za pośrednictwem `h` są macierzy 2 x 2, wszystkie produkty i sumy z nich są również macierzy 2 x 2. Również wynika, że A * B jest macierz 4 x 4 zgodnie z oczekiwaniami. Można szybko sprawdzić algorytmu, obliczenia wartości elementu w pierwszym wierszu, pierwsza kolumna w ramach produktu. W przykładzie, który byłby wartość elementu w pierwszym wierszu i pierwszą kolumnę `ae + bg`. Należy obliczyć pierwszej kolumny, pierwszy wiersz `ae` i `bg` dla każdego warunku. Tę wartość dla `ae` jest `1*1 + 2*5 = 11`. Wartość `bg` jest `3*1 + 4*5 = 23`. Końcowa wartość jest `11 + 23 = 34`, która jest poprawna.  
  
 Aby zaimplementować ten algorytm kodu:  
  
-   Używa `tiled_extent` obiekt zamiast `extent` obiektu w `parallel_for_each` wywołania.  
  
-   Używa `tiled_index` obiekt zamiast `index` obiektu w `parallel_for_each` wywołania.  
  
-   Tworzy `tile_static` zmienne do przechowywania submatrices.  
  
-   Używa `tile_barrier::wait` metodę, aby zatrzymać wątków obliczania produktów submatrices.  
  
### <a name="to-multiply-by-using-amp-and-tiling"></a>Aby pomnożyć przy użyciu AMP i kafelków  
  
1.  W MatrixMultiply.cpp, Dodaj następujący kod przed `main` metody.  
  
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
  
    This example is significantly different than the example without tiling. The code uses these conceptual steps:  
  
    1.  Skopiować elementy fragmentu [0,0] `a` do `locA`. Skopiować elementy fragmentu [0,0] `b` do `locB`. Zwróć uwagę, że `product` jest rozmieszczany nie `a` i `b`. W związku z tym użyj wskaźników globalnego dostępu do `a, b`, i `product`. Wywołanie `tile_barrier::wait` jest niezbędne. Zatrzymuje wszystkie wątki na kafelku przed zakończeniem `locA` i `locB` są wypełnione.  
  
    2.  Należy pomnożyć `locA` i `locB` i umieszcza wyniki `product`.  
  
    3.  Skopiować elementy fragmentu [0,1] `a` do `locA`. Skopiować elementy fragmentu [1,0] `b` do `locB`.  
  
    4.  Należy pomnożyć `locA` i `locB` i dodaj je do wyników, które już znajdują się w `product`.  
  
    5.  Mnożenia fragmentu [0,0] została ukończona.  
  
    6.  Powtórz dla cztery Kafelki. Nie istnieje żadne indeksowania specjalnie z myślą o Kafelki i wątki można wykonać w dowolnej kolejności. Gdy każdy wątek jest wykonywana, `tile_static` zmienne są tworzone dla każdego kafelka odpowiednio i wywołania w celu `tile_barrier::wait` sterując przepływem programu.  
  
    7.  Jak należy dokładnie zbadać algorytmu, zwróć uwagę, że każdy submatrix zostanie załadowana do `tile_static` pamięci dwa razy. Transfer danych w tym potrwać. Jednak gdy dane są `tile_static` pamięci, dostęp do danych jest znacznie szybsze. Obliczanie produktów wymaga ciągłego dostępu do wartości w submatrices, dlatego jest bardziej ogólną wydajność. Dla każdego algorytmu eksperymenty musi znaleźć optymalne algorytmu i Rozmiar kafelka.  
  
         W przykładach non-AMP i z systemem innym niż kafelka, każdy element A i B dostępne cztery razy z globalnej pamięci do obliczenia produktu. W przykładzie kafelka uzyskać dostępu do każdego elementu dwa razy z globalnej pamięci i cztery razy `tile_static` pamięci. To nie jest bardziej wydajne znaczące. Jeśli A i B zostały 1024 x 1024 macierzy, a rozmiar kafelka zostały 16, będą bardziej znaczące wydajne. W takim przypadku każdy element może być kopiowane do `tile_static` pamięci tylko 16 razy i dostępne w `tile_static` pamięci razy 1024.  
  
2.  Modyfikowanie głównej metody do wywołania `MultiplyWithTiling` metody, jak pokazano.  
  
```cpp  
void main() {  
    MultiplyWithOutAMP();  
    MultiplyWithAMP();  
    MultiplyWithTiling();  
    getchar();  
}  
```  
  
3.  Wybierz skrótu klawiaturowego Ctrl + F5 można rozpocząć debugowania, a następnie sprawdź poprawność danych wyjściowych.  
  
4.  Wybierz spacji, aby zakończyć działanie aplikacji.  
  
## <a name="see-also"></a>Zobacz też  
 [C++ AMP (C++ Accelerated Massive Parallelism)](../../parallel/amp/cpp-amp-cpp-accelerated-massive-parallelism.md)   
 [Przewodnik: debugowanie aplikacji C++ AMP](../../parallel/amp/walkthrough-debugging-a-cpp-amp-application.md)

