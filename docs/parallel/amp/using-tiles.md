---
title: Użycie fragmentów
ms.date: 11/19/2018
ms.assetid: acb86a86-2b7f-43f1-8fcf-bcc79b21d9a8
ms.openlocfilehash: 6c935134e033d12fc140c8d377ef59d0b47265fc
ms.sourcegitcommit: a930a9b47bd95599265d6ba83bb87e46ae748949
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/22/2020
ms.locfileid: "76518260"
---
# <a name="using-tiles"></a>Użycie fragmentów

Możesz użyć dzielenia, aby zmaksymalizować przyspieszenie aplikacji. Dzielenie dzieli wątki na równe prostokątne podzestawy lub *kafelki*. Jeśli używasz odpowiedniego rozmiaru kafelka i algorytmu wieloskładnikowego, możesz uzyskać jeszcze więcej przyspieszenia z kodu C++ amp. Podstawowe składniki rozdzielenie to:

- zmienne `tile_static`. Główną zaletą dzielenia jest wzrost wydajności `tile_static` dostępu. Dostęp do danych w pamięci `tile_static` może być znacznie szybszy niż dostęp do danych w obszarze globalnym (`array` lub `array_view` obiektów). Wystąpienie zmiennej `tile_static` jest tworzone dla każdego kafelka, a wszystkie wątki na kafelku mają dostęp do zmiennej. W typowym algorytmie rozdzielonym dane są kopiowane do `tile_static` pamięci z pamięci globalnej, a następnie dostępne wiele razy z pamięci `tile_static`.

- [tile_barrier:: wait — Metoda](reference/tile-barrier-class.md#wait). Wywołanie `tile_barrier::wait` zawiesza wykonywanie bieżącego wątku do momentu, aż wszystkie wątki w tym samym kafelku osiągną wywołanie do `tile_barrier::wait`. Nie można zagwarantowania kolejności, w której wątki będą działać, tylko wtedy, gdy żadne wątki na kafelku nie zostaną wykonane przed wywołaniem `tile_barrier::wait`, dopóki wszystkie wątki nie osiągną wywołania. Oznacza to, że za pomocą metody `tile_barrier::wait` można wykonać zadania na podstawie kafelka na kafelku, a nie na podstawie wątku. Typowy algorytm rozmieszczania ma kod służący do inicjowania `tile_static` pamięci dla całego kafelka, po którym następuje wywołanie `tile_barrer::wait`. Kod, który następuje `tile_barrier::wait` zawiera obliczenia, które wymagają dostępu do wszystkich wartości `tile_static`.

- Indeksowanie lokalne i globalne. Masz dostęp do indeksu wątku względem całego `array_view` lub obiektu `array` i indeksu względem kafelka. Użycie lokalnego indeksu może ułatwić odczytywanie i debugowanie kodu. Zwykle do uzyskiwania dostępu do zmiennych `tile_static` i globalnego indeksowania w celu uzyskania dostępu do zmiennych `array` i `array_view` służy funkcja indeksowania lokalnego.

- Klasa [tiled_extent](../../parallel/amp/reference/tiled-extent-class.md) i [Klasa tiled_index](../../parallel/amp/reference/tiled-index-class.md). Używasz obiektu `tiled_extent` zamiast obiektu `extent` w wywołaniu `parallel_for_each`. Używasz obiektu `tiled_index` zamiast obiektu `index` w wywołaniu `parallel_for_each`.

Aby skorzystać z dzielenia, algorytm musi podzielić domenę obliczeniową na kafelki, a następnie skopiować dane kafelków do `tile_static` zmiennych, aby uzyskać szybszy dostęp.

## <a name="example-of-global-tile-and-local-indices"></a>Przykład indeksów globalnych, kafelków i lokalnych

Poniższy diagram przedstawia 8x9 macierz danych, które są rozmieszczone w kafelkach 2x3.

![8&#45;przez&#45;9 macierzy podzielony na 2&#45;przez&#45;3 kafelki](../../parallel/amp/media/usingtilesmatrix.png "8&#45;przez&#45;9 macierzy podzielony na 2&#45;przez&#45;3 kafelki")

Poniższy przykład wyświetla globalne, kafelki i lokalne indeksy tej macierzy z rozmnożoną. Obiekt `array_view` jest tworzony przy użyciu elementów typu `Description`. `Description` przechowuje indeksy globalne, kafelki i lokalne elementu w macierzy. Kod w wywołaniu `parallel_for_each` ustawia wartości globalnych, kafelków i indeksów lokalnych każdego elementu. Dane wyjściowe są wyświetlane w strukturach `Description`.

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

int main() {
    TilingDescription();
    char wait;
    std::cin >> wait;
}
```

Główna część tego przykładu znajduje się w definicji obiektu `array_view` i wywołaniu `parallel_for_each`.

1. Wektor struktur `Description` jest kopiowany do obiektu 8x9 `array_view`.

2. Metoda `parallel_for_each` jest wywoływana z obiektem `tiled_extent` jako domena obliczeniowa. Obiekt `tiled_extent` jest tworzony przez wywołanie metody `extent::tile()` zmiennej `descriptions`. Parametry typu wywołania do `extent::tile()`, `<2,3>`, określa, że są tworzone kafelki 2x3. W ten sposób macierz 8x9 jest podzielona na 12 kafelków, cztery wiersze i trzy kolumny.

3. Metoda `parallel_for_each` jest wywoływana przy użyciu obiektu `tiled_index<2,3>` (`t_idx`) jako indeksu. Parametry typu indeksu (`t_idx`) muszą być zgodne z parametrami typu w domenie obliczeniowej (`descriptions.extent.tile< 2, 3>()`).

4. Po wykonaniu każdego wątku indeks `t_idx` zwraca informacje o tym kafelku, w którym znajduje się wątek (`tiled_index::tile` Property) i lokalizacji wątku w obrębie kafelka (`tiled_index::local` Właściwość).

## <a name="tile-synchronizationtile_static-and-tile_barrierwait"></a>Synchronizacja kafelków — tile_static i tile_barrier:: wait

W poprzednim przykładzie pokazano układ kafelków i indeksy, ale nie jest to bardzo przydatne.  Dzielenie jest przydatne, gdy kafelki są integralne względem algorytmu i wykorzystania `tile_static` zmiennych. Ponieważ wszystkie wątki na kafelku mają dostęp do zmiennych `tile_static`, wywołania do `tile_barrier::wait` są używane do synchronizowania dostępu do zmiennych `tile_static`. Chociaż wszystkie wątki we fragmencie mają dostęp do zmiennych `tile_static`, nie ma gwarantowanej kolejności wykonywania wątków w kafelku. Poniższy przykład pokazuje, jak używać zmiennych `tile_static` i metody `tile_barrier::wait`, aby obliczyć średnią wartość każdego kafelka. Oto klucze służące do poznania przykładu:

1. RawData jest przechowywany w macierzy 8x8.

2. Rozmiar kafelka to 2x2. Spowoduje to utworzenie siatki z siatką, a orednie mogą być przechowywane w macierzy 4x4 przy użyciu obiektu `array`. Istnieje tylko ograniczona liczba typów, które można przechwycić przez odwołanie w funkcji ograniczonej przez AMP. Klasa `array` jest jedną z nich.

3. Rozmiar macierzy i rozmiar próbki są definiowane przy użyciu instrukcji `#define`, ponieważ parametry typu `array`, `array_view`, `extent`i `tiled_index` muszą być wartościami stałymi. Można również użyć deklaracji `const int static`. Dodatkową korzyścią jest to, że można zmienić rozmiar próbki, aby obliczyć średnią na kafelkach 4x4.

4. `tile_static` 2x2 tablica wartości zmiennoprzecinkowych jest zadeklarowana dla każdego kafelka. Chociaż deklaracja znajduje się w ścieżce kodu dla każdego wątku, tylko jedna tablica jest tworzona dla każdego kafelka w macierzy.

5. Istnieje wiersz kodu służący do kopiowania wartości z każdego kafelka do tablicy `tile_static`. Dla każdego wątku po skopiowaniu wartości do tablicy wykonywanie wątku jest przerywane z powodu wywołania do `tile_barrier::wait`.

6. Gdy wszystkie wątki we fragmencie osiągnęły barierę, można obliczyć średnią. Ponieważ kod jest wykonywany dla każdego wątku, istnieje instrukcja `if`, aby obliczyć jedynie średnią w jednym wątku. Średnia jest przechowywana w zmiennej averages. Bariera to zasadniczo konstrukcja, która kontroluje obliczenia według kafelka, podobnie jak w przypadku użycia pętli `for`.

7. Dane w zmiennej `averages`, ponieważ jest obiektem `array`, należy skopiować z powrotem do hosta. W tym przykładzie używa operatora konwersji wektora.

8. W kompletnym przykładzie można zmienić SAMPLESIZE na 4, a kod jest wykonywany prawidłowo bez żadnych innych zmian.

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

Może być skłonny do utworzenia zmiennej `tile_static` o nazwie `total` i zwiększenia tej zmiennej dla każdego wątku, tak jak to:

```cpp
// Do not do this.
tile_static float total;
total += matrix[t_idx];
t_idx.barrier.wait();

averages(t_idx.tile[0],t_idx.tile[1]) /= (float) (SAMPLESIZE* SAMPLESIZE);
```

Pierwszy problem z tym podejściem polega na tym, że zmienne `tile_static` nie mogą mieć inicjatorów. Drugi problem polega na tym, że istnieje sytuacja wyścigu na przypisaniu do `total`, ponieważ wszystkie wątki na kafelku mają dostęp do zmiennej w określonej kolejności. Można programować algorytm, aby zezwalać tylko jednemu wątkowi na dostęp do sumy w każdej barierie, jak pokazano Dalej. Jednak to rozwiązanie nie jest rozszerzalne.

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

## <a name="memory-fences"></a>Horyzonty pamięci

Istnieją dwa rodzaje dostępu do pamięci, które muszą zostać zsynchronizowane — dostęp do pamięci globalnej i `tile_static` dostęp do pamięci. Obiekt `concurrency::array` przydziela tylko pamięć globalną. `concurrency::array_view` może odwoływać się do pamięci globalnej, `tile_static` pamięci lub obu, w zależności od tego, jak został skonstruowany.  Istnieją dwa rodzaje pamięci, które muszą być synchronizowane:

- pamięć globalna

- `tile_static`

*Ogranicznik pamięci* zapewnia dostępność dostępu do pamięci dla innych wątków w kafelku wątku, a dostęp do pamięci są wykonywane zgodnie z kolejnością programu. Aby zapewnić, że kompilatory i procesory nie porządkują operacji odczytu i zapisu w obrębie ogrodzenia. W C++ amp, ogranicznik pamięci jest tworzony przez wywołanie jednej z następujących metod:

- [tile_barrier:: wait — Metoda](reference/tile-barrier-class.md#wait): tworzy ogranicznik wokół globalnej i `tile_static` pamięci.

- [tile_barrier:: Wait_with_all_memory_fence Metoda](reference/tile-barrier-class.md#wait_with_all_memory_fence): tworzy ogranicznik wokół globalnej i `tile_static` pamięci.

- [tile_barrier:: wait_with_global_memory_fence, Metoda](reference/tile-barrier-class.md#wait_with_global_memory_fence): tworzy horyzont dookoła tylko pamięci globalnej.

- [tile_barrier:: Wait_with_tile_static_memory_fence Metoda](reference/tile-barrier-class.md#wait_with_tile_static_memory_fence): tworzy horyzont wokół tylko `tile_static` pamięci.

Wywołanie określonego ogranicznika może poprawić wydajność aplikacji. Typ bariery ma wpływ na sposób kompilatora i instrukcji zmiany kolejności sprzętowej. Na przykład w przypadku korzystania z globalnego ogranicznika pamięci ma zastosowanie tylko do dostępu do pamięci globalnej, w związku z czym kompilator i sprzęt mogą zmienić kolejność operacji odczytu i zapisu w `tile_static` zmiennych po obu stronach ogranicznika.

W następnym przykładzie bariera synchronizuje zapisy do `tileValues`, `tile_static` zmienną. W tym przykładzie `tile_barrier::wait_with_tile_static_memory_fence` jest wywoływana zamiast `tile_barrier::wait`.

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

[C++ AMP (C++ Accelerated Massive Parallelism)](../../parallel/amp/cpp-amp-cpp-accelerated-massive-parallelism.md)<br/>
[tile_static, słowo kluczowe](../../cpp/tile-static-keyword.md)
