---
title: Użycie fragmentów | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 06/28/2018
ms.technology:
- cpp-amp
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: acb86a86-2b7f-43f1-8fcf-bcc79b21d9a8
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 3c02b5d558ccf2c1353e96dd1990b6d4178457aa
ms.sourcegitcommit: 208d445fd7ea202de1d372d3f468e784e77bd666
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/29/2018
ms.locfileid: "37121952"
---
# <a name="using-tiles"></a>Użycie fragmentów

Aby zmaksymalizować przyspieszenie aplikacji, można użyć kafelków. Kafelków dzieli wątków równy podzestawy prostokątne lub *Kafelki*. Użycie kafelka odpowiedni rozmiar i algorytm sąsiadującym przyspieszenie jeszcze więcej można uzyskać w kodzie C++ AMP. Podstawowe składniki kafelków są:

- `tile_static` zmienne. Główną zaletą kafelków jest bardziej wydajne z `tile_static` dostępu. Dostęp do danych w `tile_static` pamięci może być znacznie szybsze niż dostęp do danych w przestrzeni globalnej (`array` lub `array_view` obiektów). Wystąpienie `tile_static` zmiennej jest tworzony dla każdego kafelka, a wszystkie wątki na kafelku mają dostęp do zmiennej. W typowych algorytmu sąsiadującym, dane są kopiowane do `tile_static` raz z pamięci globalnej pamięci i uzyskać dostęp wiele razy z `tile_static` pamięci.

- [tile_barrier::wait — metoda](reference/tile-barrier-class.md#wait). Wywołanie `tile_barrier::wait` wstrzymuje wykonywanie bieżącego wątku, aż zostanie wszystkie wątki na kafelku tego samego wywołanie `tile_barrier::wait`. Nie gwarantuje kolejność wątki będą uruchamiane w, tylko wykonujące nie wątków na kafelku poza wywołanie `tile_barrier::wait` dopóki wszystkie wątki osiągnięto wywołania. Oznacza to, że za pomocą `tile_barrier::wait` metody, można wykonać zadania na podstawie kafelka przez Kafelek, a nie na poziomie wątku przez wątek. Algorytm kafelków typowe ma kod do zainicjowania `tile_static` pamięci dla całego kafelka następuje wywołanie `tile_barrer::wait`. Kod, który następuje `tile_barrier::wait` zawiera obliczenia, które wymagają dostępu do wszystkich `tile_static` wartości.

- Lokalne i globalne indeksowania. Masz dostęp do indeksu wątku względem całą `array_view` lub `array` obiektu i pod indeksem względem kafelka. Przy użyciu lokalnego indeksu może ułatwić kodu do odczytu i debugowania. Należy zwykle użyć lokalnego indeksowania dostępu `tile_static` zmiennych i indeksowania globalnego dostępu `array` i `array_view` zmiennych.

- [tiled_extent — klasa](../../parallel/amp/reference/tiled-extent-class.md) i [tiled_index — klasa](../../parallel/amp/reference/tiled-index-class.md). Możesz użyć `tiled_extent` obiekt zamiast `extent` obiektu w `parallel_for_each` wywołania. Możesz użyć `tiled_index` obiekt zamiast `index` obiektu w `parallel_for_each` wywołania.

Aby skorzystać z kafelków, z algorytmu musi partycji domeny obliczeń na kafelkach a następnie skopiuj danych kafelków w `tile_static` zmienne szybszy dostęp.

## <a name="example-of-global-tile-and-local-indices"></a>Przykład globalnych kafelka, a lokalny indeksów

Poniższy diagram przedstawia macierz 8 x 9 danych, które są rozmieszczone na kafelkach 2 x 3.

![8&#45;przez&#45;9 macierzy podzielone na 2&#45;przez&#45;3 Kafelki](../../parallel/amp/media/usingtilesmatrix.png "usingtilesmatrix")

W poniższym przykładzie przedstawiono globalnych kafelka i lokalnego indeksy tego rozmieszczany macierzy. `array_view` Obiekt jest tworzony przy użyciu elementów typu `Description`. `Description` Zawiera globalny, Kafelek i lokalne Indeksy elementu w macierzy. Kod w wywołaniu `parallel_for_each` ustawia wartości globalnej, Kafelek i lokalne indeksów każdego elementu. Dane wyjściowe są wyświetlane wartości w `Description` struktury.

```cpp
#include <iostream>
#include <iomanip>
#include <Windows.h>
#include <amp.h>
using namespace concurrency;

const int ROWS = 8;
const int COLS = 9;

// tileRow and tileColumn specify the tile that each thread is in.
// globalRow and globalColumn specify the location of the thread in the array_view.
// localRow and localColumn specify the location of the thread relative to the tile.
struct Description {
    int value;
    int tileRow;
    int tileColumn;
    int globalRow;
    int globalColumn;
    int localRow;
    int localColumn;
};

// A helper function for formatting the output.
void SetConsoleColor(int color) {
    int colorValue = (color == 0)  4 : 2;
    SetConsoleTextAttribute(GetStdHandle(STD_OUTPUT_HANDLE), colorValue);
}

// A helper function for formatting the output.
void SetConsoleSize(int height, int width) {
    COORD coord;
    
    coord.X = width;
    coord.Y = height;
    SetConsoleScreenBufferSize(GetStdHandle(STD_OUTPUT_HANDLE), coord);
    
    SMALL_RECT* rect = new SMALL_RECT();
    rect->Left = 0;
    rect->Top = 0;
    rect->Right = width;
    rect->Bottom = height;
    SetConsoleWindowInfo(GetStdHandle(STD_OUTPUT_HANDLE), true, rect);
}

// This method creates an 8x9 matrix of Description structures.
// In the call to parallel_for_each, the structure is updated
// with tile, global, and local indices.
void TilingDescription() {
    // Create 72 (8x9) Description structures.
    std::vector<Description> descs;
    for (int i = 0; i < ROWS * COLS; i++) {
        Description d = {i, 0, 0, 0, 0, 0, 0};
        descs.push_back(d);
    }

    // Create an array_view from the Description structures.
    extent<2> matrix(ROWS, COLS);
    array_view<Description, 2> descriptions(matrix, descs);

    // Update each Description with the tile, global, and local indices.
    parallel_for_each(descriptions.extent.tile< 2, 3>(),
        [=] (tiled_index< 2, 3> t_idx) restrict(amp)
    {
        descriptions[t_idx].globalRow = t_idx.global[0];
        descriptions[t_idx].globalColumn = t_idx.global[1];
        descriptions[t_idx].tileRow = t_idx.tile[0];
        descriptions[t_idx].tileColumn = t_idx.tile[1];
        descriptions[t_idx].localRow = t_idx.local[0];
        descriptions[t_idx].localColumn= t_idx.local[1];
    });

    // Print out the Description structure for each element in the matrix.
    // Tiles are displayed in red and green to distinguish them from each other.
    SetConsoleSize(100, 150);
    for (int row = 0; row < ROWS; row++) {
        for (int column = 0; column < COLS; column++) {
            SetConsoleColor((descriptions(row, column).tileRow + descriptions(row, column).tileColumn) % 2);
            std::cout << "Value: " << std::setw(2) << descriptions(row, column).value << "      ";
        }
        std::cout << "\n";

        for (int column = 0; column < COLS; column++) {
            SetConsoleColor((descriptions(row, column).tileRow + descriptions(row, column).tileColumn) % 2);
            std::cout << "Tile:   " << "(" << descriptions(row, column).tileRow << "," << descriptions(row, column).tileColumn << ")  ";
        }
        std::cout << "\n";

        for (int column = 0; column < COLS; column++) {
            SetConsoleColor((descriptions(row, column).tileRow + descriptions(row, column).tileColumn) % 2);
            std::cout << "Global: " << "(" << descriptions(row, column).globalRow << "," << descriptions(row, column).globalColumn << ")  ";
        }
        std::cout << "\n";

        for (int column = 0; column < COLS; column++) {
            SetConsoleColor((descriptions(row, column).tileRow + descriptions(row, column).tileColumn) % 2);
            std::cout << "Local:  " << "(" << descriptions(row, column).localRow << "," << descriptions(row, column).localColumn << ")  ";
        }
        std::cout << "\n";
        std::cout << "\n";
    }
}

void main() {
    TilingDescription();
    char wait;
    std::cin >> wait;
}
```

Główne pracy przykładu znajduje się w definicji `array_view` obiektu i wywołania w celu `parallel_for_each`.

1. Wektor `Description` struktury jest kopiowana do 8 x 9 `array_view` obiektu.

2. `parallel_for_each` Metoda jest wywoływana z `tiled_extent` obiektu jako domenie obliczeniowej. `tiled_extent` Obiekt jest tworzony przez wywołanie metody `extent::tile()` metody `descriptions` zmiennej. Parametrów typu w wywołaniu `extent::tile()`, `<2,3>`, określić, że są tworzone Kafelki 2 x 3. W związku z tym macierzy 8 x 9 wypełniania do 12 Kafelki, cztery wiersze i trzy kolumny.

3. `parallel_for_each` Metoda jest wywoływana przy użyciu `tiled_index<2,3>` obiektu (`t_idx`) jako indeks. Parametry typu indeksu (`t_idx`) musi być zgodna z parametrów typu w domenie obliczeniowej (`descriptions.extent.tile< 2, 3>()`).

4. Po wykonaniu każdego wątku indeksu `t_idx` zwraca informacje o którym kafelka wątek znajduje się w (`tiled_index::tile` właściwości) oraz lokalizację wątku w kafelku (`tiled_index::local` właściwości).

## <a name="tile-synchronizationtilestatic-and-tilebarrierwait"></a>Kafelek synchronizacji — tile_static i tile_barrier::wait

Poprzedni przykład ilustruje układu kafelków i indeksów, ale nie jest bardzo przydatny.  Kafelków staje się przydatne, gdy są integralną częścią algorytmu i wykorzystać Kafelki `tile_static` zmiennych. Ponieważ wszystkie wątki na kafelku dostęp do `tile_static` zmiennych, wywołania `tile_barrier::wait` są używane do dostępu do synchronizowania `tile_static` zmiennych. Chociaż wszystkie wątki na kafelku mają dostęp do `tile_static` zmiennych, brak nie gwarantuje kolejności wykonywania wątków na kafelku. Poniższy przykład przedstawia użycie `tile_static` zmienne i `tile_barrier::wait` metodę obliczania średniej wartości każdego kafelka. Poniżej przedstawiono klucze do zrozumienia w przykładzie:

1. RawData jest przechowywany w macierzy 8 x 8.

2. Rozmiar kafelka jest 2 x 2. Spowoduje to utworzenie Siatka 4 x 4 kafelków i średnie mogą być przechowywane w macierzy 4 x 4 przy użyciu `array` obiektu. Istnieje ograniczona liczba typów, które można przechwytywać przez odwołanie w funkcji ograniczonej przez AMP. `array` Klasy jest jednym z nich.

3. Rozmiar macierzy i rozmiar próbki są definiowane za pomocą `#define` instrukcji, ponieważ parametry typu `array`, `array_view`, `extent`, i `tiled_index` musi być wartości stałych. Można również użyć `const int static` deklaracji. Dodatkowa korzyść jest prosta, aby zmienić rozmiar próbki do obliczenia średniej Kafelki ponad 4 x 4.

4. A `tile_static` 2 x 2 tablicy wartości zmiennoprzecinkowych jest zadeklarowany dla każdego kafelka. Mimo że deklaracji w ścieżce kodu dla każdego wątku, tylko jedna tablica jest tworzony dla każdego kafelka w macierzy.

5. Brak wiersza kodu, aby skopiować wartości w każdym Kafelek, aby `tile_static` tablicy. Dla każdego wątku po skopiowaniu wartość do tablicy, w wątku zatrzyma wykonywanie z powodu wywołania `tile_barrier::wait`.

6. Gdy wszystkie wątki na kafelku osiągnęły bariery, może zostać obliczona średnia. Kod wykonywany dla każdego wątku, nie istnieje `if` oświadczenie tylko obliczania średniej w jednym wątku. Średnia jest przechowywana w zmiennej średnie. Bariera jest zasadniczo konstrukcja kontrolujące obliczenia przez Kafelek, tak jak można użyć `for` pętli.

7. Dane w `averages` zmiennej, ponieważ jest on `array` obiektów, należy skopiować do hosta. W tym przykładzie używane operatora konwersji wektora.

8. W pełny przykład można zmienić SAMPLESIZE 4 i kod wykonywany poprawnie bez żadnych innych zmian.

```cpp
#include <iostream>
#include <amp.h>
using namespace concurrency;

#define SAMPLESIZE 2
#define MATRIXSIZE 8
void SamplingExample() {

    // Create data and array_view for the matrix.
    std::vector<float> rawData;
    for (int i = 0; i < MATRIXSIZE * MATRIXSIZE; i++) {
        rawData.push_back((float)i);
    }
    extent<2> dataExtent(MATRIXSIZE, MATRIXSIZE);
    array_view<float, 2> matrix(dataExtent, rawData);

    // Create the array for the averages.
    // There is one element in the output for each tile in the data.
    std::vector<float> outputData;
    int outputSize = MATRIXSIZE / SAMPLESIZE;
    for (int j = 0; j < outputSize * outputSize; j++) {
        outputData.push_back((float)0);
    }
    extent<2> outputExtent(MATRIXSIZE / SAMPLESIZE, MATRIXSIZE / SAMPLESIZE);
    array<float, 2> averages(outputExtent, outputData.begin(), outputData.end());

    // Use tiles that are SAMPLESIZE x SAMPLESIZE.
    // Find the average of the values in each tile.
    // The only reference-type variable you can pass into the parallel_for_each call
    // is a concurrency::array.
    parallel_for_each(matrix.extent.tile<SAMPLESIZE, SAMPLESIZE>(),
        [=, &averages] (tiled_index<SAMPLESIZE, SAMPLESIZE> t_idx) restrict(amp)
    {
        // Copy the values of the tile into a tile-sized array.
        tile_static float tileValues[SAMPLESIZE][SAMPLESIZE];
        tileValues[t_idx.local[0]][t_idx.local[1]] = matrix[t_idx];

        // Wait for the tile-sized array to load before you calculate the average.
        t_idx.barrier.wait();

        // If you remove the if statement, then the calculation executes for every
        // thread in the tile, and makes the same assignment to averages each time.
        if (t_idx.local[0] == 0 && t_idx.local[1] == 0) {
            for (int trow = 0; trow < SAMPLESIZE; trow++) {
                for (int tcol = 0; tcol < SAMPLESIZE; tcol++) {
                    averages(t_idx.tile[0],t_idx.tile[1]) += tileValues[trow][tcol];
                }
            }
            averages(t_idx.tile[0],t_idx.tile[1]) /= (float) (SAMPLESIZE * SAMPLESIZE);
        }
    });

    // Print out the results.
    // You cannot access the values in averages directly. You must copy them
    // back to a CPU variable.
    outputData = averages;
    for (int row = 0; row < outputSize; row++) {
        for (int col = 0; col < outputSize; col++) {
            std::cout << outputData[row*outputSize + col] << " ";
        }
        std::cout << "\n";
    }
    // Output for SAMPLESSIZE = 2 is:
    //  4.5  6.5  8.5 10.5
    // 20.5 22.5 24.5 26.5
    // 36.5 38.5 40.5 42.5
    // 52.5 54.5 56.5 58.5

    // Output for SAMPLESIZE = 4 is:
    // 13.5 17.5
    // 45.5 49.5
}

int main() {
    SamplingExample();
}
```

## <a name="race-conditions"></a>Warunki wyścigu

Może być kuszące utworzyć `tile_static` zmiennej o nazwie `total` i zwiększyć wartości zmiennej dla każdego wątku, w następujący sposób:

```cpp
// Do not do this.
tile_static float total;
total += matrix[t_idx];
t_idx.barrier.wait();

averages(t_idx.tile[0],t_idx.tile[1]) /= (float) (SAMPLESIZE* SAMPLESIZE);
```

Pierwszy tego podejścia przy rozwiązywaniu problemu jest to, że `tile_static` zmienne nie mogą mieć inicjatory. Drugi problemu jest brak wyścigu na przypisanie do `total`, ponieważ wszystkie wątki na kafelku mają dostęp do zmiennej w losowej kolejności. Można programu algorytmu, aby zezwolić tylko jeden wątek razem w każdej bariery dostępu do, jak pokazano w następnym. To rozwiązanie nie jest jednak rozszerzonego.

```cpp
// Do not do this.
tile_static float total;
if (t_idx.local[0] == 0&& t_idx.local[1] == 0) {
    total = matrix[t_idx];
}
t_idx.barrier.wait();

if (t_idx.local[0] == 0&& t_idx.local[1] == 1) {
    total += matrix[t_idx];
}
t_idx.barrier.wait();

// etc.
```

## <a name="memory-fences"></a>Ogrodzenia pamięci

Istnieją dwa rodzaje uzyskuje dostęp do pamięci, które należy zsynchronizować — dostęp do pamięci globalnej i `tile_static` dostęp do pamięci. A `concurrency::array` obiektu przydziela tylko pamięci globalnej. A `concurrency::array_view` może odwoływać się pamięci globalnej `tile_static` pamięci i/lub, w zależności od tego, jak został skonstruowany.  Istnieją dwa rodzaje pamięci, która musi być synchronizowany:

- pamięć globalna

- `tile_static`

A *ogranicznika pamięci* zapewnia pamięci, są dostępne dla innych wątków na kafelku wątku i pamięci, uzyskuje dostęp do są wykonywane zgodnie z kolejnością program. Aby to zapewnić, kompilatory i procesorów nie zmieniać kolejność odczyty i zapisy między ogrodzenia. W C++ AMP ogranicznika pamięci jest tworzony przez wywołanie do jednej z następujących metod:

- [tile_barrier::wait — metoda](reference/tile-barrier-class.md#wait): tworzy ogranicznika wokół zarówno globalnych i `tile_static` pamięci.

- [tile_barrier::wait_with_all_memory_fence — metoda](reference/tile-barrier-class.md#wait_with_all_memory_fence): tworzy ogranicznika wokół zarówno globalnych i `tile_static` pamięci.

- [tile_barrier::wait_with_global_memory_fence — metoda](reference/tile-barrier-class.md#wait_with_global_memory_fence): tworzy ogranicznika wokół tylko pamięci globalnej.

- [tile_barrier::wait_with_tile_static_memory_fence — metoda](reference/tile-barrier-class.md#wait_with_tile_static_memory_fence): tworzy ogranicznika wokół tylko `tile_static` pamięci.

Wywoływanie określonego ogranicznika, wymagany może poprawić wydajność aplikacji. Typ bariery ma wpływ na sposób kompilator i sprzętem zmienić kolejność instrukcje. Na przykład, jeśli używasz ogranicznika pamięci globalnej, ma to zastosowanie tylko do globalnej pamięci uzyskuje dostęp do i z tego powodu, kompilatora i sprzętu może zmienić kolejność odczytuje i zapisuje `tile_static` zmienne na dwóch stronach ogrodzenia.

W następnym przykładzie bariera synchronizuje zapisywania `tileValues`, `tile_static` zmiennej. W tym przykładzie `tile_barrier::wait_with_tile_static_memory_fence` jest wywoływana zamiast `tile_barrier::wait`.

```cpp
// Using a tile_static memory fence.
parallel_for_each(matrix.extent.tile<SAMPLESIZE, SAMPLESIZE>(),
    [=, &averages] (tiled_index<SAMPLESIZE, SAMPLESIZE> t_idx) restrict(amp)
{
    // Copy the values of the tile into a tile-sized array.
    tile_static float tileValues[SAMPLESIZE][SAMPLESIZE];
    tileValues[t_idx.local[0]][t_idx.local[1]] = matrix[t_idx];

    // Wait for the tile-sized array to load before calculating the average.
    t_idx.barrier.wait_with_tile_static_memory_fence();

    // If you remove the if statement, then the calculation executes
    // for every thread in the tile, and makes the same assignment to
    // averages each time.
    if (t_idx.local[0] == 0&& t_idx.local[1] == 0) {
        for (int trow = 0; trow <SAMPLESIZE; trow++) {
            for (int tcol = 0; tcol <SAMPLESIZE; tcol++) {
                averages(t_idx.tile[0],t_idx.tile[1]) += tileValues[trow][tcol];
            }
        }
    averages(t_idx.tile[0],t_idx.tile[1]) /= (float) (SAMPLESIZE* SAMPLESIZE);
    }
});
```

## <a name="see-also"></a>Zobacz także

[C++ AMP (C++ Accelerated Massive Parallelism)](../../parallel/amp/cpp-amp-cpp-accelerated-massive-parallelism.md)  
[tile_static, słowo kluczowe](../../cpp/tile-static-keyword.md)  
