---
title: tile_static — słowo kluczowe
ms.date: 11/04/2016
f1_keywords:
- tile_static_CPP
helpviewer_keywords:
- tile_static keyword
ms.assetid: d78384d4-65d9-45cf-b3df-7e904f489d06
ms.openlocfilehash: 1e0e967edd1808b27d3d4e92f29f7472608f8e65
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50588165"
---
# <a name="tilestatic-keyword"></a>tile_static — słowo kluczowe

**Tile_static** — słowo kluczowe jest używane do deklarowania zmiennej, która może zostać oceniony przez wszystkie wątki we fragmencie wątków. Okres istnienia zmiennej rozpoczyna się, gdy wykonywanie osiągnie punkt deklaracji i kończy się, gdy funkcja jądra. Aby uzyskać więcej informacji na temat korzystania z kafelków, zobacz [kafelków za pomocą](../parallel/amp/using-tiles.md).

**Tile_static** — słowo kluczowe ma następujące ograniczenia:

- Może służyć tylko w zmiennych, które znajdują się w funkcję, która ma `restrict(amp)` modyfikator.

- Nie można używać zmiennych, które są typami wskaźnika lub odwołania.

- A **tile_static** zmiennej nie może mieć inicjatora. Domyślne konstruktory i destruktory nie są wywoływane automatycznie.

- Wartość niezainicjowanej **tile_static** zmienna jest niezdefiniowana.

- Jeśli **tile_static** zmienna jest zadeklarowana w wykres wywołań, który jest ścieżką przez wywołanie niefragmentującą `parallel_for_each`, generowane jest ostrzeżenie i zachowanie zmienna jest niezdefiniowana.

## <a name="example"></a>Przykład

W poniższym przykładzie przedstawiono sposób **tile_static** zmienna może służyć do gromadzenie danych między kilka wątków we fragmencie.

```cpp
// Sample data:
int sampledata[] = {
    2, 2, 9, 7, 1, 4,
    4, 4, 8, 8, 3, 4,
    1, 5, 1, 2, 5, 2,
    6, 8, 3, 2, 7, 2};

// The tiles:
// 2 2    9 7    1 4
// 4 4    8 8    3 4
//
// 1 5    1 2    5 2
// 6 8    3 2    7 2

// Averages:
int averagedata[] = {
    0, 0, 0, 0, 0, 0,
    0, 0, 0, 0, 0, 0,
    0, 0, 0, 0, 0, 0,
    0, 0, 0, 0, 0, 0,
};

array_view<int, 2> sample(4, 6, sampledata);
array_view<int, 2> average(4, 6, averagedata);

parallel_for_each(
    // Create threads for sample.extent and divide the extent into 2 x 2 tiles.
    sample.extent.tile<2,2>(),
    [=](tiled_index<2,2> idx) restrict(amp)
    {
        // Create a 2 x 2 array to hold the values in this tile.
        tile_static int nums[2][2];
        // Copy the values for the tile into the 2 x 2 array.
        nums[idx.local[1]][idx.local[0]] = sample[idx.global];
        // When all the threads have executed and the 2 x 2 array is complete, find the average.
        idx.barrier.wait();
        int sum = nums[0][0] + nums[0][1] + nums[1][0] + nums[1][1];
        // Copy the average into the array_view.
        average[idx.global] = sum / 4;
      }
);

for (int i = 0; i < 4; i++) {
    for (int j = 0; j < 6; j++) {
        std::cout << average(i,j) << " ";
    }
    std::cout << "\n";
}

// Output:
// 3 3 8 8 3 3
// 3 3 8 8 3 3
// 5 5 2 2 4 4
// 5 5 2 2 4 4
// Sample data.
int sampledata[] = {
    2, 2, 9, 7, 1, 4,
    4, 4, 8, 8, 3, 4,
    1, 5, 1, 2, 5, 2,
    6, 8, 3, 2, 7, 2};

// The tiles are:
// 2 2    9 7    1 4
// 4 4    8 8    3 4
//
// 1 5    1 2    5 2
// 6 8    3 2    7 2

// Averages.
int averagedata[] = {
    0, 0, 0, 0, 0, 0,
    0, 0, 0, 0, 0, 0,
    0, 0, 0, 0, 0, 0,
    0, 0, 0, 0, 0, 0,
};

array_view<int, 2> sample(4, 6, sampledata);
array_view<int, 2> average(4, 6, averagedata);

parallel_for_each(
    // Create threads for sample.grid and divide the grid into 2 x 2 tiles.
    sample.extent.tile<2,2>(),
    [=](tiled_index<2,2> idx) restrict(amp)
    {
        // Create a 2 x 2 array to hold the values in this tile.
        tile_static int nums[2][2];
        // Copy the values for the tile into the 2 x 2 array.
        nums[idx.local[1]][idx.local[0]] = sample[idx.global];
        // When all the threads have executed and the 2 x 2 array is complete, find the average.
        idx.barrier.wait();
        int sum = nums[0][0] + nums[0][1] + nums[1][0] + nums[1][1];
        // Copy the average into the array_view.
        average[idx.global] = sum / 4;
      }
);

for (int i = 0; i < 4; i++) {
    for (int j = 0; j < 6; j++) {
        std::cout << average(i,j) << " ";
    }
    std::cout << "\n";
}

// Output.
// 3 3 8 8 3 3
// 3 3 8 8 3 3
// 5 5 2 2 4 4
// 5 5 2 2 4 4
```

## <a name="see-also"></a>Zobacz także

[Modyfikatory specyficzne dla firmy Microsoft](../cpp/microsoft-specific-modifiers.md)<br/>
[Przegląd C++ AMP](../parallel/amp/cpp-amp-overview.md)<br/>
[parallel_for_each — funkcja (C++ AMP)](../parallel/amp/reference/concurrency-namespace-functions-amp.md#parallel_for_each)<br/>
[Przewodnik: mnożenie macierzy](../parallel/amp/walkthrough-matrix-multiplication.md)