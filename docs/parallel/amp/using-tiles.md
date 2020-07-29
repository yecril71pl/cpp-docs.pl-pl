---
title: Użycie fragmentów
ms.date: 11/19/2018
ms.assetid: acb86a86-2b7f-43f1-8fcf-bcc79b21d9a8
ms.openlocfilehash: edef9154b0c4da6f53c8ac40ee84e55e9b38a9b7
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87228469"
---
# <a name="using-tiles"></a>Użycie fragmentów

Możesz użyć dzielenia, aby zmaksymalizować przyspieszenie aplikacji. Dzielenie dzieli wątki na równe prostokątne podzestawy lub *kafelki*. Jeśli używasz odpowiedniego rozmiaru kafelka i algorytmu wieloskładnikowego, możesz uzyskać jeszcze większą przyspieszenie w kodzie C++ AMP. Podstawowe składniki rozdzielenie to:

- `tile_static`modyfikacj. Główną zaletą dzielenia jest wzrost wydajności `tile_static` dostępu. Dostęp do danych w `tile_static` pamięci może być znacznie szybszy niż dostęp do danych w obszarze globalnym ( `array` lub w `array_view` obiektach). Wystąpienie `tile_static` zmiennej jest tworzone dla każdego kafelka, a wszystkie wątki na kafelku mają dostęp do zmiennej. W typowym algorytmie rozdzielonym dane są kopiowane do `tile_static` pamięci raz z pamięci globalnej, a następnie dostępne wiele razy z `tile_static` pamięci.

- [tile_barrier:: wait — Metoda](reference/tile-barrier-class.md#wait). Wywołanie `tile_barrier::wait` wstrzymuje wykonywanie bieżącego wątku do momentu, aż wszystkie wątki w tym samym kafelku osiągną wywołanie `tile_barrier::wait` . Nie można zagwarantowania kolejności, w której wątki będą działać, tylko wtedy, gdy żadne wątki na kafelku nie zostaną wykonane w ciągu wywołania do `tile_barrier::wait` momentu, aż wszystkie wątki osiągną wywołanie. Oznacza to, że za pomocą `tile_barrier::wait` metody, można wykonywać zadania na kafelku na kafelku, a nie na podstawie wątku. Typowy algorytm rozmieszczania ma kod `tile_static` służący do inicjowania pamięci dla całego kafelka, po którym następuje wywołanie `tile_barrier::wait` . Poniższy kod `tile_barrier::wait` zawiera obliczenia, które wymagają dostępu do wszystkich `tile_static` wartości.

- Indeksowanie lokalne i globalne. Masz dostęp do indeksu wątku względem całego `array_view` lub `array` obiektu i indeksu względem kafelka. Użycie lokalnego indeksu może ułatwić odczytywanie i debugowanie kodu. Zazwyczaj do uzyskiwania dostępu do `tile_static` zmiennych i globalnego indeksowania dostępu i zmiennych służy funkcja indeksowania `array` lokalnego `array_view` .

- Klasa [tiled_extent](../../parallel/amp/reference/tiled-extent-class.md) i [Klasa tiled_index](../../parallel/amp/reference/tiled-index-class.md). Używasz `tiled_extent` obiektu zamiast `extent` obiektu w `parallel_for_each` wywołaniu. Używasz `tiled_index` obiektu zamiast `index` obiektu w `parallel_for_each` wywołaniu.

Aby skorzystać z dzielenia, algorytm musi podzielić domenę obliczeniową na kafelki, a następnie skopiować dane kafelków do `tile_static` zmiennych, aby uzyskać szybszy dostęp.

## <a name="example-of-global-tile-and-local-indices"></a>Przykład indeksów globalnych, kafelków i lokalnych

Poniższy diagram przedstawia 8x9 macierz danych, które są rozmieszczone w kafelkach 2x3.

![8&#45;przez&#45;9 macierz podzielony na 2&#45;przez&#45;3 kafelków](../../parallel/amp/media/usingtilesmatrix.png "8&#45;przez&#45;9 macierz podzielony na 2&#45;przez&#45;3 kafelków")

Poniższy przykład wyświetla globalne, kafelki i lokalne indeksy tej macierzy z rozmnożoną. `array_view`Obiekt jest tworzony za pomocą elementów typu `Description` . `Description`Przechowuje globalne, kafelki i lokalne indeksy elementu w macierzy. Kod w wywołaniu `parallel_for_each` Ustawia wartości globalnych, kafelków i indeksów lokalnych każdego elementu. Dane wyjściowe są wyświetlane w `Description` strukturach.

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

Główna część tego przykładu znajduje się w definicji `array_view` obiektu i wywołaniu metody `parallel_for_each` .

1. Wektor `Description` struktur jest kopiowany do `array_view` obiektu 8x9.

2. `parallel_for_each`Metoda jest wywoływana z `tiled_extent` obiektem jako domeny obliczeniowej. `tiled_extent`Obiekt jest tworzony przez wywołanie `extent::tile()` metody `descriptions` zmiennej. Parametry typu wywołania do `extent::tile()` , `<2,3>` określają, że są tworzone kafelki 2x3. W ten sposób macierz 8x9 jest podzielona na 12 kafelków, cztery wiersze i trzy kolumny.

3. `parallel_for_each`Metoda jest wywoływana przy użyciu `tiled_index<2,3>` obiektu ( `t_idx` ) jako indeksu. Parametry typu index ( `t_idx` ) muszą być zgodne z parametrami typu w domenie obliczeniowej ( `descriptions.extent.tile< 2, 3>()` ).

4. Po wykonaniu każdego wątku indeks `t_idx` zwraca informacje o tym kafelku, w którym znajduje się wątek, `tiled_index::tile` i lokalizacji wątku w kafelku ( `tiled_index::local` Właściwości).

## <a name="tile-synchronizationtile_static-and-tile_barrierwait"></a>Synchronizacja kafelków — tile_static i tile_barrier:: wait

W poprzednim przykładzie pokazano układ kafelków i indeksy, ale nie jest to bardzo przydatne.  Dzielenie jest przydatne, gdy kafelki są integralne względem algorytmu i `tile_static` zmienne wykorzystania. Ponieważ wszystkie wątki na kafelku mają dostęp do `tile_static` zmiennych, wywołania `tile_barrier::wait` są używane do synchronizowania dostępu do `tile_static` zmiennych. Chociaż wszystkie wątki we fragmencie mają dostęp do `tile_static` zmiennych, nie ma żadnej gwarantowanej kolejności wykonywania wątków w kafelku. Poniższy przykład pokazuje, jak używać `tile_static` zmiennych i metody, `tile_barrier::wait` Aby obliczyć średnią wartość każdego kafelka. Oto klucze służące do poznania przykładu:

1. RawData jest przechowywany w macierzy 8x8.

2. Rozmiar kafelka to 2x2. Spowoduje to utworzenie siatki z płytkią 4x4, a średnia może być przechowywana w macierzy 4x4 przy użyciu `array` obiektu. Istnieje tylko ograniczona liczba typów, które można przechwycić przez odwołanie w funkcji ograniczonej przez AMP. `array`Klasa jest jedną z nich.

3. Rozmiar macierzy i rozmiar próbki są definiowane przy użyciu `#define` instrukcji, ponieważ parametry typu `array` ,, `array_view` `extent` i `tiled_index` muszą być wartościami stałymi. Można również używać `const int static` deklaracji. Dodatkową korzyścią jest to, że można zmienić rozmiar próbki, aby obliczyć średnią na kafelkach 4x4.

4. `tile_static`Dla każdego kafelka jest zadeklarowana tablica 2x2 wartości zmiennoprzecinkowych. Chociaż deklaracja znajduje się w ścieżce kodu dla każdego wątku, tylko jedna tablica jest tworzona dla każdego kafelka w macierzy.

5. Istnieje wiersz kodu służący do kopiowania wartości z każdego kafelka do `tile_static` tablicy. Dla każdego wątku po skopiowaniu wartości do tablicy wykonywanie wątku jest przerywane z powodu wywołania do `tile_barrier::wait` .

6. Gdy wszystkie wątki we fragmencie osiągnęły barierę, można obliczyć średnią. Ponieważ kod jest wykonywany dla każdego wątku, istnieje instrukcja służąca `if` do obliczania średniej tylko dla jednego wątku. Średnia jest przechowywana w zmiennej averages. Bariera to zasadniczo konstrukcja, która kontroluje obliczenia według kafelka, podobnie jak w przypadku użycia **`for`** pętli.

7. Dane w `averages` zmiennej, ponieważ jest to `array` obiekt, należy skopiować z powrotem do hosta. W tym przykładzie używa operatora konwersji wektora.

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
    // Output for SAMPLESIZE = 2 is:
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

Może być skłonny do tworzenia `tile_static` zmiennej o nazwie `total` i zwiększania tej zmiennej dla każdego wątku, tak jak to:

```cpp
// Do not do this.
tile_static float total;
total += matrix[t_idx];
t_idx.barrier.wait();

averages(t_idx.tile[0],t_idx.tile[1]) /= (float) (SAMPLESIZE* SAMPLESIZE);
```

Pierwszym problemem w tym podejściu jest to, że `tile_static` zmienne nie mogą mieć inicjatorów. Drugi problem polega na tym, że na przypisaniu występuje sytuacja wyścigu `total` , ponieważ wszystkie wątki na kafelku mają dostęp do zmiennej w określonej kolejności. Można programować algorytm, aby zezwalać tylko jednemu wątkowi na dostęp do sumy w każdej barierie, jak pokazano Dalej. Jednak to rozwiązanie nie jest rozszerzalne.

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

Istnieją dwa rodzaje dostępu do pamięci, które muszą być zsynchronizowane — dostęp do pamięci globalnej i `tile_static` dostęp do pamięci. `concurrency::array`Obiekt przydziela tylko pamięć globalną. `concurrency::array_view`Może odwoływać się do pamięci globalnej, `tile_static` pamięci lub obu — w zależności od tego, jak został skonstruowany.  Istnieją dwa rodzaje pamięci, które muszą być synchronizowane:

- pamięć globalna

- `tile_static`

*Ogranicznik pamięci* zapewnia dostępność dostępu do pamięci dla innych wątków w kafelku wątku, a dostęp do pamięci są wykonywane zgodnie z kolejnością programu. Aby zapewnić, że kompilatory i procesory nie porządkują operacji odczytu i zapisu w obrębie ogrodzenia. W C++ AMP ogranicznik pamięci jest tworzony przez wywołanie jednej z następujących metod:

- [tile_barrier:: wait — Metoda](reference/tile-barrier-class.md#wait): tworzy ogranicznik między globalnym i `tile_static` pamięcią.

- [tile_barrier:: wait_with_all_memory_fence — Metoda](reference/tile-barrier-class.md#wait_with_all_memory_fence): tworzy ogranicznik między globalnym i `tile_static` pamięcią.

- [tile_barrier:: wait_with_global_memory_fence, Metoda](reference/tile-barrier-class.md#wait_with_global_memory_fence): tworzy horyzont dookoła tylko pamięci globalnej.

- [tile_barrier:: Wait_with_tile_static_memory_fence Metoda](reference/tile-barrier-class.md#wait_with_tile_static_memory_fence): tworzy horyzont tylko wokół `tile_static` pamięci.

Wywołanie określonego ogranicznika może poprawić wydajność aplikacji. Typ bariery ma wpływ na sposób kompilatora i instrukcji zmiany kolejności sprzętowej. Na przykład w przypadku korzystania z globalnego ogranicznika pamięci ma zastosowanie tylko do dostępu do pamięci globalnej, w związku z czym kompilator i sprzęt mogą zmienić kolejność odczytów i zapisów w `tile_static` zmiennych po obu stronach ogrodzenia.

W następnym przykładzie bariera synchronizuje zapisy do `tileValues` , `tile_static` zmienna. W tym przykładzie `tile_barrier::wait_with_tile_static_memory_fence` jest wywoływana zamiast `tile_barrier::wait` .

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
[tile_static — słowo kluczowe](../../cpp/tile-static-keyword.md)
