---
title: 'Przewodnik: Mnożenie macierzy'
ms.date: 11/19/2018
ms.assetid: 61172e8b-da71-4200-a462-ff3a908ab0cf
ms.openlocfilehash: 597ba0f47c7b081f62c82bf8e1ca01c286d35140
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62237293"
---
# <a name="walkthrough-matrix-multiplication"></a>Przewodnik: Mnożenie macierzy

Ten przewodnik krok po kroku pokazano, jak używać biblioteki C++ AMP, aby przyspieszyć wykonywanie mnożenie macierzy. Dwa algorytmy są prezentowane jeden bez fragmentacji i jeden z fragmentacji.

## <a name="prerequisites"></a>Wymagania wstępne

Przed rozpoczęciem:

- Odczyt [Przegląd C++ AMP](../../parallel/amp/cpp-amp-overview.md).

- Odczyt [użycie fragmentów](../../parallel/amp/using-tiles.md).

- Upewnij się, że ten Windows 7, Windows 8, Windows Server 2008 R2 lub Windows Server 2012 jest zainstalowana na komputerze.

### <a name="to-create-the-project"></a>Aby utworzyć projekt

1. Na pasku menu w programie Visual Studio, wybierz **pliku** > **New** > **projektu**.

1. W obszarze **zainstalowane** w okienku szablonów zaznacz **Visual C++**.

1. Wybierz **pusty projekt**, wprowadź *MatrixMultiply* w **nazwa** , a następnie wybierz **OK** przycisku.

1. Wybierz **dalej** przycisku.

1. W **Eksploratora rozwiązań**, otwórz menu skrótów dla **pliki źródłowe**, a następnie wybierz **Dodaj** > **nowy element**.

1. W **Dodaj nowy element** okno dialogowe, wybierz opcję **plik C++ (.cpp)**, wprowadź *MatrixMultiply.cpp* w **nazwa** , a następnie wybierz  **Dodaj** przycisku.

## <a name="multiplication-without-tiling"></a>Mnożenie bez fragmentacji

W tej sekcji należy wziąć pod uwagę mnożenie dwóch macierzy, A i B, które są zdefiniowane w następujący sposób:

![3&#45;przez&#45;macierzy 2 A](../../parallel/amp/media/campmatrixanontiled.png "3&#45;przez&#45;macierzy 2 A")

![2&#45;przez&#45;macierzy 3 B](../../parallel/amp/media/campmatrixbnontiled.png "2&#45;przez&#45;macierzy 3 B")

Jest tabela 3, 2 i B jest tabela 2, 3. Produkt multiplikujący a, B jest następujący macierzy 3 x 3. Produkt jest obliczane przez pomnożenie wierszy A według kolumn B elementów.

![3&#45;przez&#45;macierzy 3 produktu](../../parallel/amp/media/campmatrixproductnontiled.png "3&#45;przez&#45;macierzy 3 produktu")

### <a name="to-multiply-without-using-c-amp"></a>Aby pomnożyć bez korzystania z C++ AMP

1. Otwórz MatrixMultiply.cpp i użyj poniższego kodu, aby zastąpić istniejący kod.

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

   Algorytm jest prosta implementacja definicji mnożenie macierzy. Nie używa żadnych algorytmy równoległe lub niezhierarchizowanych skracają czas obliczeń.

1. Na pasku menu wybierz **pliku** > **Zapisz wszystko**.

1. Wybierz **F5** skrót klawiaturowy, aby rozpocząć debugowanie i sprawdź poprawność danych wyjściowych.

1. Wybierz **Enter** aby zakończyć działanie aplikacji.

### <a name="to-multiply-by-using-c-amp"></a>Aby pomnożyć przez korzystanie z C++ AMP

1. W MatrixMultiply.cpp, Dodaj następujący kod przed `main` metody.

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

   W kodzie AMP podobny kod non-AMP. Wywołanie `parallel_for_each` uruchamia jeden wątek dla każdego elementu w `product.extent`i zastępuje `for` pętli dla wierszy i kolumn. Wartość komórki na wierszy i kolumn jest dostępna w `idx`. Możesz uzyskać dostęp do elementów `array_view` obiektu przy użyciu `[]` operatora i zmienna index lub `()` operatora i zmienne wierszy i kolumn. W przykładzie pokazano obu tych metod. `array_view::synchronize` Metoda kopiuje wartości `product` zmiennej do `productMatrix` zmiennej.

1. Dodaj następujący kod `include` i `using` instrukcji w górnej części MatrixMultiply.cpp.

```cpp
#include <amp.h>
using namespace concurrency;
```

1. Modyfikowanie `main` metodę do wywołania `MultiplyWithAMP` metody.

```cpp
void main() {
    MultiplyWithOutAMP();
    MultiplyWithAMP();
    getchar();
}
```

1. Wybierz **Ctrl**+**F5** skrót klawiaturowy, aby rozpocząć debugowanie i sprawdź poprawność danych wyjściowych.

1. Wybierz **spacja** aby zakończyć działanie aplikacji.

## <a name="multiplication-with-tiling"></a>Mnożenie przy użyciu fragmentacji

Fragmentacji to technika partycjonowanie danych na równe wielkości podzestawy, które są znane jako kafelki. Trzy rzeczy zmianie, gdy używasz fragmentacji.

- Możesz utworzyć `tile_static` zmiennych. Dostęp do danych w `tile_static` miejsce może być wiele razy szybciej niż dostęp do danych w globalnej przestrzeni. Wystąpienie `tile_static` zmiennej jest tworzone dla każdego fragmentu i wszystkie wątki we fragmencie mają dostęp do zmiennej. Podstawową zaletą fragmentacji jest przyrost wydajności ze względu na `tile_static` dostępu.

- Możesz wywołać [tile_barrier::wait](reference/tile-barrier-class.md#wait) metodę, aby zatrzymać wszystkie wątki w jednym kafelkiem w określonym wierszu kodu. Nie gwarantuje kolejności, w jakim wątki będą uruchamiane, tylko że wszystkie wątki w jednym kafelkiem zakończy się w wywołaniu do `tile_barrier::wait` kontynuowania wykonywania.

- Masz dostęp do indeksu wątku dla całego `array_view` obiektu i indeksu dla fragmentu. Za pomocą lokalnego indeksu, użytkownik może uczynić kod łatwiejszym do odczytywania i debugowania.

Aby skorzystać z fragmentacji w mnożenie macierzy, algorytm musi podzielić macierzy na kafelkach i następnie skopiuj dane kafelka do `tile_static` zmienne szybszy dostęp. W tym przykładzie macierzy zostanie poddana partycjonowaniu na submatrices taki sam rozmiar. Produktu znajduje się przez pomnożenie submatrices. Są dwa macierzy, a ich produktów, w tym przykładzie:

![4&#45;przez&#45;macierzy 4 A](../../parallel/amp/media/campmatrixatiled.png "4&#45;przez&#45;macierzy 4 A")

![4&#45;przez&#45;macierzy 4 B](../../parallel/amp/media/campmatrixbtiled.png "4&#45;przez&#45;macierzy 4 B")

![4&#45;przez&#45;macierzy 4 produktu](../../parallel/amp/media/campmatrixproducttiled.png "4&#45;przez&#45;macierzy 4 produktu")

Macierze są partycjonowane na macierzy cztery 2 x 2, które są zdefiniowane w następujący sposób:

![4&#45;przez&#45;macierzy 4 A poddana partycjonowaniu na 2&#45;przez&#45;2 sub&#45;macierzy](../../parallel/amp/media/campmatrixapartitioned.png "4&#45;przez&#45;macierzy 4 A poddana partycjonowaniu na 2&#45;przez&#45;2 sub&#45;macierzy")

![4&#45;przez&#45;macierzy 4 B poddana partycjonowaniu na 2&#45;przez&#45;2 sub&#45;macierzy](../../parallel/amp/media/campmatrixbpartitioned.png "4&#45;przez&#45;macierzy 4 B poddana partycjonowaniu na 2&#45;przez&#45;2 sub&#45;macierzy")

Produkt A i B mogą teraz zapisywane i obliczana w następujący sposób:

![4&#45;przez&#45;macierzy 4 B poddana partycjonowaniu na 2&#45;przez&#45;2 sub&#45;macierzy](../../parallel/amp/media/campmatrixproductpartitioned.png "4&#45;przez&#45;macierzy 4 B poddana partycjonowaniu na 2&#45;przez&#45;2 sub&#45;macierzy")

Ponieważ macierzy `a` za pośrednictwem `h` macierzy 2 x 2, wszystkie produkty i sum z nich są również macierzy 2 x 2. Również wynika, że produkt A i B jest macierzy 4 x 4, zgodnie z oczekiwaniami. Można szybko sprawdzić algorytm, należy obliczyć wartość elementu w pierwszym wierszu, w pierwszej kolumnie w produkcie. W przykładzie, który byłby wartość elementu w pierwszym wierszu i pierwszą kolumnę `ae + bg`. Masz do obliczania, pierwszą kolumnę pierwszego wiersza `ae` i `bg` każdego terminu. Tę wartość dla `ae` jest `(1 * 1) + (2 * 5) = 11`. Wartość `bg` jest `(3 * 1) + (4 * 5) = 23`. Końcowa wartość jest `11 + 23 = 34`, który jest poprawny.

Aby zaimplementować ten algorytm kod:

- Używa `tiled_extent` zamiast obiektu `extent` obiektu `parallel_for_each` wywołania.

- Używa `tiled_index` zamiast obiektu `index` obiektu `parallel_for_each` wywołania.

- Tworzy `tile_static` zmienne do przechowywania submatrices.

- Używa `tile_barrier::wait` metodę, aby zatrzymać wątki w obliczeniach produktów submatrices.

### <a name="to-multiply-by-using-amp-and-tiling"></a>Aby pomnożyć przy użyciu AMP i fragmentacji

1. W MatrixMultiply.cpp, Dodaj następujący kod przed `main` metody.

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

    1. Skopiuj elementy fragmentu [0,0] `a` do `locA`. Skopiuj elementy fragmentu [0,0] `b` do `locB`. Należy zauważyć, że `product` jest rozmieszczany nie `a` i `b`. W związku z tym, umożliwiają indeksów globalnych dostęp `a, b`, i `product`. Wywołanie `tile_barrier::wait` ma zasadnicze znaczenie. Zatrzymuje wszystkie wątki we fragmencie do momentu zarówno `locA` i `locB` są wypełnione.

    2. Pomnóż `locA` i `locB` i umieszcza wyniki `product`.

    3. Skopiuj elementy fragmentu [0,1] `a` do `locA`. Skopiuj elementy fragmentu [1,0] `b` do `locB`.

    4. Pomnóż `locA` i `locB` i dodać je do wyników, które już znajdują się w `product`.

    5. Mnożenie kafelka [0,0] zostało ukończone.

    6. Powtórz dla cztery Kafelki. Nie ma żadnych indeksowania specjalnie dla kafelków i wątki można wykonać w dowolnej kolejności. Gdy jest wykonywana każdego wątku, `tile_static` zmienne są tworzone dla każdego kafelka odpowiednio i wywołania `tile_barrier::wait` przepływem programu.

    7. Ponieważ algorytm jest ściśle zbadać, zwróć uwagę, że każdy submatrix zostanie załadowana do `tile_static` pamięci dwa razy. Czy potrwać transferu danych. Jednakże gdy dane znajdują się w `tile_static` pamięć, jest znacznie szybszy dostęp do danych. Obliczanie produkty wymagają powtarzalny dostęp do wartości w submatrices, dlatego jest ogólny są bardziej wydajne. Dla każdego algorytmu eksperymentowania jest wymagany do znalezienia optymalnej algorytmu i Rozmiar kafelka.

         W przykładach non-AMP i innych kafelka, każdy element obiektu A i B jest dostępne cztery razy w globalnej pamięci, aby obliczyć produktu. W tym przykładzie kafelka każdy element jest dostępny, dwa razy z globalnej pamięci i czterokrotnie `tile_static` pamięci. To nie jest istotne są bardziej wydajne. Jeśli A i B zostały 1024 x 1024 macierzy i rozmiar fragmentu były 16, byłoby znaczące są bardziej wydajne. W takim przypadku każdy element jest kopiowany do `tile_static` pamięci tylko 16 razy i uzyskać dostęp z `tile_static` pamięci razy 1024.

2. Modyfikowanie głównej metody do wywołania `MultiplyWithTiling` metodzie, jak pokazano.

```cpp
void main() {
    MultiplyWithOutAMP();
    MultiplyWithAMP();
    MultiplyWithTiling();
    getchar();
}
```

3. Wybierz **Ctrl**+**F5** skrót klawiaturowy, aby rozpocząć debugowanie i sprawdź poprawność danych wyjściowych.

4. Wybierz **miejsca** pasek, aby zakończyć działanie aplikacji.

## <a name="see-also"></a>Zobacz także

[C++ AMP (C++ Accelerated Massive Parallelism)](../../parallel/amp/cpp-amp-cpp-accelerated-massive-parallelism.md)<br/>
[Przewodnik: Debugowanie aplikacji C++ AMP](../../parallel/amp/walkthrough-debugging-a-cpp-amp-application.md)
