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
ms.openlocfilehash: df2f449cce01dc2d0903ff802ffb94914b68bceb
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2018
ms.locfileid: "46386271"
---
# <a name="using-tiles"></a>Użycie fragmentów

Można użyć fragmentacji, aby zmaksymalizować przyspieszenie aplikacji. Fragmentacja dzieli wątki na równe podzestawy prostokątne lub *Kafelki*. Jeśli używasz odpowiedniego rozmiaru fragmentu oraz algorytmu fragmentacji możesz uzyskać jeszcze większe od kodu C++ AMP. Podstawowe składniki fragmentacji to:

- `tile_static` zmienne. Podstawową zaletą fragmentacji jest przyrost wydajności z `tile_static` dostępu. Dostęp do danych w `tile_static` pamięci może być znacznie szybszy niż dostęp do danych w przestrzeni globalnej (`array` lub `array_view` obiektów). Wystąpienie `tile_static` zmiennej jest tworzone dla każdego fragmentu i wszystkie wątki we fragmencie mają dostęp do zmiennej. W typowym algorytmie fragmentacji, dane są kopiowane do `tile_static` pamięci z globalnej pamięci i uzyskiwać dostęp wiele razy z `tile_static` pamięci.

- [tile_barrier::wait — metoda](reference/tile-barrier-class.md#wait). Wywołanie `tile_barrier::wait` zawiesza wykonywanie bieżącego wątku, dopóki wszystkie wątki w tym samym fragmencie nie osiągną wywołania `tile_barrier::wait`. Nie można zagwarantować kolejność, w jakim wątki będą uruchamiane, tylko że żadne wątki we fragmencie nie zostaną wykonane po wywołaniu `tile_barrier::wait` dopóki wszystkie wątki nie osiągną wywołania. Oznacza to, że za pomocą `tile_barrier::wait` metody, można wykonać zadania na zasadzie kafelka, Kafelek, a nie na poziomie wątek po wątku. Typowy algorytm fragmentacji posiada kod do inicjowania `tile_static` pamięci dla całego fragmentu, poprzedzony wywołaniem do `tile_barrer::wait`. Kod, który następuje po `tile_barrier::wait` zawiera obliczenia, które wymagają dostępu do wszystkich `tile_static` wartości.

- Lokalne i globalne indeksowanie. Masz dostęp do indeksu wątku dla całego `array_view` lub `array` obiektu i indeksu dla fragmentu. Używanie lokalnego indeksu może ułatwić kodu do odczytywania i debugowania. Zazwyczaj używane jest indeksowanie lokalne dostęp do `tile_static` zmiennych oraz indeksowanie globalne, aby uzyskać dostęp do `array` i `array_view` zmiennych.

- [tiled_extent, klasa](../../parallel/amp/reference/tiled-extent-class.md) i [tiled_index, klasa](../../parallel/amp/reference/tiled-index-class.md). Możesz użyć `tiled_extent` zamiast obiektu `extent` obiektu `parallel_for_each` wywołania. Możesz użyć `tiled_index` zamiast obiektu `index` obiektu `parallel_for_each` wywołania.

Aby skorzystać z fragmentacji, algorytm musi podzielić domenę obliczeniową na fragmenty i następnie skopiuj dane kafelka do `tile_static` zmienne szybszy dostęp.

## <a name="example-of-global-tile-and-local-indices"></a>Przykładem globalnego, Kafelek fragmentarycznego oraz lokalnego

Poniższy diagram przedstawia macierz 8 x 9, danych, które są ułożone WE fragmenty 2 x 3.

![8&#45;przez&#45;9 tabela jest podzielona na 2&#45;przez&#45;3 Kafelki](../../parallel/amp/media/usingtilesmatrix.png "usingtilesmatrix")

Poniższy przykład wyświetla globalne, a lokalnych wskaźników to sąsiadująco w macierzy. `array_view` Obiekt jest tworzony przy użyciu elementów typu `Description`. `Description` Przechowuje globalną, Kafelek, fragmentaryczne oraz lokalne elementów macierzy. Kod w wywołaniu `parallel_for_each` ustawia wartości globalnych, Kafelek fragmentarycznych oraz lokalnych każdego elementu. Dane wyjściowe wyświetlają wartości w `Description` struktury.

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

Główna Praca przykładu jest wykonywana w definicji elementu `array_view` obiektu i wywołanie `parallel_for_each`.

1. Wektor `Description` struktury są kopiowane do 8 x 9 `array_view` obiektu.

2. `parallel_for_each` Metoda jest wywoływana z `tiled_extent` obiektu jako domena obliczająca. `tiled_extent` Obiekt jest tworzony przez wywołanie `extent::tile()` metody `descriptions` zmiennej. Parametry typu wywołania metody `extent::tile()`, `<2,3>`, określ, czy 2 x 3 Kafelki są tworzone. W efekcie macierz 8 x 9 jest rozmieszczany na 12 fragmentów, cztery wiersze i trzy kolumny.

3. `parallel_for_each` Metoda jest wywoływana przy użyciu `tiled_index<2,3>` obiektu (`t_idx`) jako indeks. Parametry typu indeksu (`t_idx`) muszą odpowiadać parametrom typu domeny obliczającej (`descriptions.extent.tile< 2, 3>()`).

4. Po wykonaniu każdego wątku, indeks `t_idx` zwraca informacje o który Kafelek wątek znajduje się w (`tiled_index::tile` właściwości) i lokalizację wątku we fragmencie (`tiled_index::local` właściwości).

## <a name="tile-synchronizationtilestatic-and-tilebarrierwait"></a>Synchronizacja — tile_static i tile_barrier::wait

Poprzedni przykład ilustruje układ fragmentów i wskaźniki, ale nie jest bardzo przydatne.  Fragmentacja jest użyteczna gdy fragmenty są integralną częścią algorytmów i wykorzystują `tile_static` zmiennych. Ponieważ wszystkie wątki we fragmencie mają dostęp do `tile_static` zmiennych, wywołania `tile_barrier::wait` są używane do synchronizowania dostępu do `tile_static` zmiennych. Mimo że wszystkie wątki we fragmencie mają dostęp do `tile_static` zmiennych, nie jest zagwarantowana kolejność wykonywania wątków we fragmencie. Poniższy przykład pokazuje, jak używać `tile_static` zmienne i `tile_barrier::wait` metodę obliczania średniej wartości każdego fragmentu. W tym miejscu są kluczem do zrozumienia przykładu:

1. Obiekt rawData jest przechowywany w macierzy 8 x 8.

2. Rozmiar fragmentu to 2 x 2. Spowoduje to utworzenie siatkę 4 x 4 fragmentów, a średnie mogą być przechowywane w macierzy 4 x 4 za pomocą `array` obiektu. Istnieje ograniczona liczba typów, które można przechwycić poprzez odwołanie w funkcji ograniczonej przez AMP. `array` Klasy jest jednym z nich.

3. Rozmiar macierzy i rozmiar próbki są definiowane za pomocą `#define` instrukcji, ponieważ parametry typu `array`, `array_view`, `extent`, i `tiled_index` muszą być wartościami stałymi. Można również użyć `const int static` deklaracji. Jako dodatkowa korzyść jest prosta, aby zmienić rozmiar próbki do obliczania średniej ponad 4 x 4 fragmentów.

4. A `tile_static` zadeklarowano tablicę 2 x 2 wartości zmiennoprzecinkowych dla każdego kafelka. Mimo że deklaracja znajduje się w ścieżce kodu dla każdego wątku, tylko jedna tablica jest tworzona dla każdego fragmentu w macierzy.

5. Istnieje linia kodu pozwalająca kopiować wartości każdego fragmentu do `tile_static` tablicy. Dla każdego wątku, po skopiowaniu wartości do tablicy, wykonanie wątku zatrzymuje ze względu na wywołanie `tile_barrier::wait`.

6. Gdy wszystkie wątki we fragmencie osiągnęły barierę, może zostać obliczona średnia. Ponieważ kod jest wykonywany dla każdego wątku, występuje `if` instrukcję w celu obliczenia średniej w jednym wątku. Średnia jest przechowywana w zmiennej averages. Bariera to zasadniczo konstrukcja obliczeń przez kafelka, ile może używać `for` pętli.

7. Dane w `averages` zmiennej, ponieważ jest on `array` obiektów, muszą zostać skopiowane z powrotem do hosta. W tym przykładzie użyto operator konwersji wektorowej.

8. W kompletnym przykładzie można zmienić SAMPLESIZE na 4 i kod zostanie wykonywany prawidłowo bez żadnych innych zmian.

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

Może być kuszące utworzenie `tile_static` zmiennej o nazwie `total` i zwiększanie wartość zmiennej dla każdego wątku w następujący sposób:

```cpp
// Do not do this.
tile_static float total;
total += matrix[t_idx];
t_idx.barrier.wait();

averages(t_idx.tile[0],t_idx.tile[1]) /= (float) (SAMPLESIZE* SAMPLESIZE);
```

Pierwszym problemem w tym podejściu jest to, że `tile_static` zmiennych nie mogą mieć inicjatorów. Drugi problem to sytuacja wyścigu przy przypisaniu do `total`, ponieważ wszystkie wątki we fragmencie mają dostęp do zmiennej w losowej kolejności. Można programować algorytm zezwalający tylko jednemu wątkowi na dostęp do zmiennej total przy każdej barierze, jak pokazano dalej. To rozwiązanie nie jest jednak rozszerzalne.

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

Istnieją dwa rodzaje dostępów do pamięci, które muszą być synchronizowane — dostęp do pamięci globalnej oraz `tile_static` dostęp do pamięci. A `concurrency::array` obiekt przydziela tylko pamięć globalną. A `concurrency::array_view` może odwoływać się do globalnej pamięci, `tile_static` pamięci i / lub, w zależności od tego, jak został zbudowany.  Istnieją dwa rodzaje pamięci, które muszą być synchronizowane:

- pamięć globalna

- `tile_static`

A *horyzont pamięci* gwarantuje, że dostęp do pamięci jest dostępny dla innych wątków we fragmencie wątków i uzyskuje dostęp do są wykonywane w założonej kolejności pamięci. Aby to zapewnić kompilatory oraz procesory nie zmieniają kolejności odczytów i zapisów ramach horyzontu. W bibliotece C++ AMP horyzont pamięci jest tworzony przez wywołanie jednej z następujących metod:

- [tile_barrier::wait — metoda](reference/tile-barrier-class.md#wait): tworzy horyzont wokół zarówno globalnych i `tile_static` pamięci.

- [tile_barrier::wait_with_all_memory_fence — metoda](reference/tile-barrier-class.md#wait_with_all_memory_fence): tworzy horyzont wokół zarówno globalnych i `tile_static` pamięci.

- [tile_barrier::wait_with_global_memory_fence — metoda](reference/tile-barrier-class.md#wait_with_global_memory_fence): tworzy horyzont tylko wokół pamięci globalnej.

- [tile_barrier::wait_with_tile_static_memory_fence — metoda](reference/tile-barrier-class.md#wait_with_tile_static_memory_fence): tworzy horyzont tylko wokół `tile_static` pamięci.

Podczas wywoływania określonych wymaganego horyzontu może zwiększyć wydajność aplikacji. Typ bariery wpływa na tym, jak kompilator i sprzęt zmiana kolejności instrukcji. Na przykład, jeśli używasz horyzontu pamięci globalnej, dotyczy tylko dostępu do pamięci globalnej i dlatego kompilator i sprzęt mogą zmieniać kolejność odczytuje i zapisuje `tile_static` zmiennych po obu stronach horyzontu.

W następnym przykładzie bariera synchronizuje zapisy do `tileValues`, `tile_static` zmiennej. W tym przykładzie `tile_barrier::wait_with_tile_static_memory_fence` nosi nazwę zamiast `tile_barrier::wait`.

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
