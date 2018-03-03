---
title: "Porady: Korzystanie z wyników połączonych do poprawiania wydajności | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- combinable class, example
- improving parallel performance with combinable [Concurrency Runtime]
ms.assetid: fa730580-1c94-4b2d-8aec-57c91dc0497e
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: dea28bd31812449e34bb481d316070f8f21aaede
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="how-to-use-combinable-to-improve-performance"></a>Porady: korzystanie z wyników połączonych do poprawiania wydajności
Ten przykład przedstawia sposób użycia [concurrency::combinable](../../parallel/concrt/reference/combinable-class.md) klasy do obliczenia wartości w [std::array](../../standard-library/array-class-stl.md) obiekt, który jest pierwsze. `combinable` Klasy zwiększa wydajność przez wyeliminowanie udostępniania stanu.  
  
> [!TIP]
>  W niektórych przypadkach równoległe mapy ([concurrency::parallel_transform](reference/concurrency-namespace-functions.md#parallel_transform)) i ograniczyć ([współbieżności:: parallel_reduce —](reference/concurrency-namespace-functions.md#parallel_reduce)) oferuje ulepszenia wydajności za pośrednictwem `combinable`. Na przykład, że używa mapowania i zmniejszanie operacji do działają tak samo jak w tym przykładzie, zobacz [algorytmy równoległe](../../parallel/concrt/parallel-algorithms.md).  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie użyto [std::accumulate](../../standard-library/numeric-functions.md#accumulate) funkcji do obliczenia sumę elementów w tablicy, które są pierwsze. W tym przykładzie `a` jest `array` obiektu i `is_prime` funkcji określa, czy jego wartość wejściowa jest pierwsze.  
  
 [!code-cpp[concrt-parallel-sum-of-primes#1](../../parallel/concrt/codesnippet/cpp/how-to-use-combinable-to-improve-performance_1.cpp)]  
  
## <a name="example"></a>Przykład  

 W poniższym przykładzie przedstawiono prosty sposób parallelize w poprzednim przykładzie. W tym przykładzie użyto [concurrency::parallel_for_each](reference/concurrency-namespace-functions.md#parallel_for_each) algorytm przetworzyć tablicy równolegle i [concurrency::critical_section](../../parallel/concrt/reference/critical-section-class.md) obiektu synchronizujący dostęp do `prime_sum` zmiennej . W tym przykładzie nie działa, ponieważ każdy wątek musi czekać na zasób udostępniony stanie się dostępne.  
  
 [!code-cpp[concrt-parallel-sum-of-primes#2](../../parallel/concrt/codesnippet/cpp/how-to-use-combinable-to-improve-performance_2.cpp)]  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie użyto `combinable` obiekt, aby poprawić wydajność w poprzednim przykładzie. W tym przykładzie eliminuje potrzebę stosowania obiektów synchronizacji; skaluje się ponieważ `combinable` obiektu umożliwia każdy wątek do wykonywania swoich zadań niezależnie.  
  
 A `combinable` obiekt jest zwykle używany w dwóch krokach. Po pierwsze produktu szereg szczegółowych obliczenia wykonywania pracy równolegle. Następnie połączyć (lub Zmniejsz) obliczenia do końcowego wyniku. W tym przykładzie użyto [concurrency::combinable::local](reference/combinable-class.md#local) metodę, aby uzyskać odwołania do zsumowania lokalnego. Następnie używa [concurrency::combinable::combine](reference/combinable-class.md#combine) — metoda i [std::plus](../../standard-library/plus-struct.md) obiektu Połączenie lokalne obliczenia do końcowego wyniku.  

  
 [!code-cpp[concrt-parallel-sum-of-primes#3](../../parallel/concrt/codesnippet/cpp/how-to-use-combinable-to-improve-performance_3.cpp)]  
  
## <a name="example"></a>Przykład  
 Poniższy przykład pełną oblicza sumę liczb pierwszych zarówno szeregowe i równolegle. Przykład drukuje do konsoli czasu wymaganego do wykonania obu obliczenia.  
  
 [!code-cpp[concrt-parallel-sum-of-primes#4](../../parallel/concrt/codesnippet/cpp/how-to-use-combinable-to-improve-performance_4.cpp)]  
  
 Następujące przykładowe dane wyjściowe jest dla komputera, który ma cztery procesory.  
  
```Output  
1709600813  
serial time: 6178 ms  
 
1709600813  
parallel time: 1638 ms  
```  
  
## <a name="compiling-the-code"></a>Kompilowanie kodu  
 Aby skompilować kod, skopiuj go i następnie wklej go w projekcie programu Visual Studio lub wklej go w pliku o nazwie `parallel-sum-of-primes.cpp` , a następnie uruchom następujące polecenie w oknie Wiersz polecenia programu Visual Studio.  
  
 **Cl.exe/ehsc równoległe — Suma elementu primes.cpp**  
  
## <a name="robust-programming"></a>Niezawodne programowanie  
 Na przykład, że używa mapowania i zmniejszanie operacji w celu uzyskania tego samego wyników, zobacz [algorytmy równoległe](../../parallel/concrt/parallel-algorithms.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Równoległe kontenery i obiekty](../../parallel/concrt/parallel-containers-and-objects.md)   
 [combinable — klasa](../../parallel/concrt/reference/combinable-class.md)   
 [critical_section, klasa](../../parallel/concrt/reference/critical-section-class.md)
