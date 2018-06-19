---
title: tile_static — słowo kluczowe | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- tile_static_CPP
dev_langs:
- C++
helpviewer_keywords:
- tile_static keyword
ms.assetid: d78384d4-65d9-45cf-b3df-7e904f489d06
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 092ba4a438378f12ae1ab332bce906df38b267e7
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
ms.locfileid: "32422166"
---
# <a name="tilestatic-keyword"></a>tile_static — słowo kluczowe
`tile_static` Słowo kluczowe jest używane w celu zadeklarowania zmiennej dostępnej przez wszystkie wątki na kafelku wątków. Okres istnienia zmiennej uruchamiana, gdy wykonanie osiągnie punkt deklaracji i kończy się po powrocie z funkcji jądra. Aby uzyskać więcej informacji na temat używania Kafelki, zobacz [przy użyciu Kafelki](../parallel/amp/using-tiles.md).  
  
 `tile_static` — Słowo kluczowe ma następujące ograniczenia:  
  
-   Może służyć tylko dla zmiennych, które znajdują się w funkcji, która ma `restrict(amp)` modyfikator.  
  
-   Nie można używać na zmiennych typu wskaźnik lub odwołanie.  
  
-   A `tile_static` zmiennej nie może mieć inicjatora. Domyślne konstruktory i destruktory nie są automatycznie wywoływane.  
  
-   Wartość niezainicjowanej `tile_static` zmienna jest niezdefiniowana.  
  
-   Jeśli `tile_static` zmienna jest zadeklarowana w wykresu wywołań, znajdującym się przez wywołanie rozmieszczany `parallel_for_each`, generowania ostrzeżeń i zachowanie zmienna jest niezdefiniowana.  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie przedstawiono sposób `tile_static` zmienna może służyć do kumulują się danych między kilka wątków na kafelku.  
  
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
  
## <a name="see-also"></a>Zobacz też  
 [Modyfikatory specyficzne dla firmy Microsoft](../cpp/microsoft-specific-modifiers.md)   
 [Przegląd C++ AMP](../parallel/amp/cpp-amp-overview.md)   
 [parallel_for_each — funkcja (C++ AMP)](../parallel/amp/reference/concurrency-namespace-functions-amp.md#parallel_for_each)   
 [Przewodnik: mnożenie macierzy](../parallel/amp/walkthrough-matrix-multiplication.md)