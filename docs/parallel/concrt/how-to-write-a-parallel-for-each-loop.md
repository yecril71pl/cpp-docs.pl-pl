---
title: "Porady: pisanie pętli parallel_for_each | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- writing a parallel_for_each loop [Concurrency Runtime]
- parallel_for_each function, example
ms.assetid: fa9c0ba6-ace0-4f88-8681-c7c1f52aff20
caps.latest.revision: "15"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: c3d641fe0437e371fdd45e2d497fbf865e41fa3c
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="how-to-write-a-parallelforeach-loop"></a>Porady: pisanie pętli parallel_for_each
Ten przykład przedstawia sposób użycia [concurrency::parallel_for_each](reference/concurrency-namespace-functions.md#parallel_for_each) algorytm obliczania liczby liczb pierwszych w [std::array](../../standard-library/array-class-stl.md) obiektu równolegle.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład oblicza liczbę elementów w tablicy pierwsze dwa razy. W przykładzie najpierw użyto [std::for_each](../../standard-library/algorithm-functions.md#for_each) algorytm obliczania liczby pojedynczo. W przykładzie następnie użyto `parallel_for_each` algorytmu do wykonania tego samego zadania równolegle. Przykład drukuje do konsoli również czasu wymaganego do wykonania obu obliczenia.  
  
 [!code-cpp[concrt-parallel-count-primes#1](../../parallel/concrt/codesnippet/cpp/how-to-write-a-parallel-for-each-loop_1.cpp)]  
  
 Następujące przykładowe dane wyjściowe jest dla komputera, który ma cztery procesory.  
  
```Output  
serial version:  
found 17984 prime numbers  
took 6115 ms  
 
parallel version:  
found 17984 prime numbers  
took 1653 ms  
```  
  
## <a name="compiling-the-code"></a>Kompilowanie kodu  
 Aby skompilować kod, skopiuj go i następnie wklej go w projekcie programu Visual Studio lub wklej go w pliku o nazwie `parallel-count-primes.cpp` , a następnie uruchom następujące polecenie w oknie Wiersz polecenia programu Visual Studio.  
  
 **Cl.exe/ehsc równoległe — liczba primes.cpp**  
  
## <a name="robust-programming"></a>Niezawodne programowanie  
 Wyrażenie lambda, które przykładzie przekazuje do `parallel_for_each` algorytm używa `InterlockedIncrement` funkcji, aby włączyć równoległych iteracji pętli, aby zwiększyć licznik jednocześnie. Jeśli używasz funkcji takich jak `InterlockedIncrement` synchronizujący dostęp do udostępnionych zasobów, wąskich gardeł wydajności można przedstawić w kodzie. Mechanizm zwolnić blokady synchronizacji, można użyć na przykład, [concurrency::combinable](../../parallel/concrt/reference/combinable-class.md) klasy, aby wyeliminować jednoczesny dostęp do zasobów udostępnionych. Na przykład, który używa `combinable` w ten sposób, zobacz [porady: Korzystanie z wyników połączonych do poprawiania wydajności](../../parallel/concrt/how-to-use-combinable-to-improve-performance.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Algorytmy równoległe](../../parallel/concrt/parallel-algorithms.md)   
 [parallel_for_each — funkcja](reference/concurrency-namespace-functions.md#parallel_for_each)


