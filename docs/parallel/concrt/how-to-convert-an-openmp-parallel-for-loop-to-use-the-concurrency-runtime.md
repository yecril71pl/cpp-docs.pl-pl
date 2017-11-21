---
title: "Porady: konwertowanie paraleli OpenMP dla pętli do korzystania ze współbieżności środowiska wykonawczego | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- converting from OpenMP to the Concurrency Runtime, parallel for loops
- converting from OpenMP to the Concurrency Runtime, parallel loops
- parallel for loops, converting from OpenMP to the Concurrency Runtime
- parallel loops, converting from OpenMP to the Concurrency Runtime
ms.assetid: d8a7b656-f86c-456e-9c5d-a7d52f94646e
caps.latest.revision: "13"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 7304b45f59219c529be5c1d430ea3183febd958a
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="how-to-convert-an-openmp-parallel-for-loop-to-use-the-concurrency-runtime"></a>Porady: konwertowanie paraleli OpenMP dla pętli do korzystania ze współbieżności środowiska wykonawczego

W tym przykładzie pokazano, jak przekonwertować podstawowego pętli, które używa OpenMP [równoległych](../../parallel/concrt/how-to-use-parallel-invoke-to-write-a-parallel-sort-routine.md#parallel) i [dla](../../parallel/openmp/reference/for-openmp.md) dyrektywy do korzystania ze współbieżności środowiska wykonawczego [concurrency::parallel_for](reference/concurrency-namespace-functions.md#parallel_for) algorytm.  
  
## <a name="example"></a>Przykład  
 W tym przykładzie używane zarówno OpenMP, jak i współbieżności środowiska wykonawczego do obliczenia liczba liczb pierwszych w tablicy wartości losowych.  
  
 [!code-cpp[concrt-openmp#1](../../parallel/concrt/codesnippet/cpp/how-to-convert-an-openmp-parallel-for-loop-to-use-the-concurrency-runtime_1.cpp)]  
  
 W tym przykładzie tworzy następujące dane wyjściowe.  
  
```Output  
Using OpenMP...  
found 107254 prime numbers.  
Using the Concurrency Runtime...  
found 107254 prime numbers.  
```  
  
 `parallel_for` Algorytmu i OpenMP 3.0 Zezwalaj dla typu indeksu podpisany typ całkowity lub typem całkowitym bez znaku. `parallel_for` Algorytm również sprawdza, czy określony zakres nie przepełnienie poziomu typu ze znakiem. OpenMP w wersji 2.0 i 2.5 umożliwiają tylko dla typów podpisanych integralną indeksu. OpenMP także nie można zweryfikować zakresu indeksu.  
  
 Wersja w tym przykładzie, który korzysta ze współbieżności środowiska wykonawczego używa również [concurrency::combinable](../../parallel/concrt/reference/combinable-class.md) obiekt zamiast [atomic](../../parallel/openmp/reference/atomic.md) dyrektywy, aby zwiększyć wartość licznika bez konieczności Synchronizacja.  
  
 Aby uzyskać więcej informacji na temat `parallel_for` i inne algorytmy równoległe, zobacz [algorytmy równoległe](../../parallel/concrt/parallel-algorithms.md). Aby uzyskać więcej informacji na temat `combinable` , zobacz [równoległe kontenery oraz obiekty](../../parallel/concrt/parallel-containers-and-objects.md).  
  
## <a name="example"></a>Przykład  

 W tym przykładzie modyfikuje poprzedniego do działania na [std::array](../../standard-library/array-class-stl.md) obiektu zamiast w macierzystym tablicy. Ponieważ OpenMP w wersji 2.0 i 2.5 pozwalają na podpisane typów całkowitych indeksu tylko w `parallel_for` konstrukcji, Iteratory nie można użyć do uzyskania dostępu do elementów kontenera standardowa biblioteka C++ równolegle. Biblioteka równoległych wzorców (PLL) zapewnia [concurrency::parallel_for_each](reference/concurrency-namespace-functions.md#parallel_for_each) algorytmu, który wykonuje zadania, równoległe iteracyjne kontenera, np. udostępnianych przez standardowa biblioteka C++. Używa tej samej logiki partycjonowania który `parallel_for` algorytm. `parallel_for_each` Algorytm podobny standardowa biblioteka C++ [std::for_each](../../standard-library/algorithm-functions.md#for_each) algorytmu, z wyjątkiem `parallel_for_each` algorytm wykonuje zadań jednocześnie.  
  
 [!code-cpp[concrt-openmp#10](../../parallel/concrt/codesnippet/cpp/how-to-convert-an-openmp-parallel-for-loop-to-use-the-concurrency-runtime_2.cpp)]  
  
## <a name="compiling-the-code"></a>Kompilowanie kodu  
 Skopiuj przykładowy kod i wklej go w projekcie programu Visual Studio lub wklej go w pliku o nazwie `concrt-omp-count-primes.cpp` , a następnie uruchom następujące polecenie w oknie Wiersz polecenia programu Visual Studio.  
  
 **concrt/OpenMP/ehsc cl.exe-omp — liczba primes.cpp**  
  
## <a name="see-also"></a>Zobacz też  
 [Migrowanie z OpenMP do współbieżności środowiska wykonawczego](../../parallel/concrt/migrating-from-openmp-to-the-concurrency-runtime.md)   
 [Algorytmy równoległe](../../parallel/concrt/parallel-algorithms.md)   
 [Równoległe kontenery i obiekty](../../parallel/concrt/parallel-containers-and-objects.md)

