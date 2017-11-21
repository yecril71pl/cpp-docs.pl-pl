---
title: "Porady: wykonywanie mapowania i zmniejszanie operacji wykonywane równolegle | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- parallel_transform function, example
- parallel map and reduce, example
- parallel_reduce function, example
ms.assetid: 9d19fac0-4ab6-4380-a375-3b18eeb87720
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 6648933aa972ec1391afe2d9cecd37b15ad53f9c
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="how-to-perform-map-and-reduce-operations-in-parallel"></a>Porady: wykonywanie mapowania i zmniejszanie operacji wykonywane równolegle

Ten przykład przedstawia sposób użycia [concurrency::parallel_transform](reference/concurrency-namespace-functions.md#parallel_transform) i [concurrency::parallel_reduce](reference/concurrency-namespace-functions.md#parallel_reduce) algorytmów i [concurrency::concurrent_unordered_map](../../parallel/concrt/reference/concurrent-unordered-map-class.md)klasy Liczenie wystąpień słowa w plikach.  
  
 A *mapy* operacja dotyczy funkcji każdej wartości w sekwencji. A *zmniejszyć* operacji łączy elementy sekwencji w jedną wartość. Standardowa biblioteka C++ można użyć [std::transform](../../standard-library/algorithm-functions.md#transform) i [std::accumulate](../../standard-library/numeric-functions.md#accumulate) funkcji wykonywanie mapowania i zmniejszanie operacji. Jednak aby zwiększyć wydajność wiele problemów, można użyć `parallel_transform` algorytmu do wykonania tej operacji mapy równolegle i `parallel_reduce` algorytmu do wykonania tej operacji Zmniejsz równolegle. W niektórych przypadkach można użyć `concurrent_unordered_map` umożliwia wykonywanie mapowania i zmniejszanie w jednej operacji.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład liczby wystąpień słowa w plikach. Używa [std::vector](../../standard-library/vector-class.md) do reprezentowania zawartości dwóch plików. Operacja mapy oblicza wystąpienia każdego wyrazu w przypadku każdego wektora. Operacja Zmniejsz akumuluje liczba znaków w obu kierunków.  
  
 [!code-cpp[concrt-parallel-map-reduce#1](../../parallel/concrt/codesnippet/cpp/how-to-perform-map-and-reduce-operations-in-parallel_1.cpp)]  
  
## <a name="compiling-the-code"></a>Kompilowanie kodu  
 Aby skompilować kod, skopiuj go i następnie wklej go w projekcie programu Visual Studio lub wklej go w pliku o nazwie `parallel-map-reduce.cpp` , a następnie uruchom następujące polecenie w oknie Wiersz polecenia programu Visual Studio.  
  
 **Cl.exe/ehsc równoległe map — reduce.cpp**  
  
## <a name="robust-programming"></a>Niezawodne programowanie  
 W tym przykładzie, można użyć `concurrent_unordered_map` klasy, która jest zdefiniowana w concurrent_unordered_map.h—to wykonywanie mapowania i zmniejszyć w jednej operacji.  
  
 [!code-cpp[concrt-parallel-map-reduce#2](../../parallel/concrt/codesnippet/cpp/how-to-perform-map-and-reduce-operations-in-parallel_2.cpp)]  
  
 Zazwyczaj parallelize tylko zewnętrznym lub wewnętrznym pętli. Parallelize wewnętrzny pętli, jeśli masz względnie mało plików i każdy plik zawiera wiele słów. Parallelize zewnętrzne pętli, jeśli jest stosunkowo wiele plików, a każdy plik zawiera kilka słów.  
  
## <a name="see-also"></a>Zobacz też  
 [Algorytmy równoległe](../../parallel/concrt/parallel-algorithms.md)   
 [parallel_transform — funkcja](reference/concurrency-namespace-functions.md#parallel_transform)   
 [parallel_reduce — funkcja](reference/concurrency-namespace-functions.md#parallel_reduce)   
 [concurrent_unordered_map — klasa](../../parallel/concrt/reference/concurrent-unordered-map-class.md)
