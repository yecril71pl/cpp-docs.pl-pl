---
title: "Porady: Korzystanie z kontenerów równoległych do zwiększania wydajności | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- increasing efficiency with parallel containers [Concurrency Runtime]
- concurrent_queue class, examples
- concurrent_vector class, examples
ms.assetid: bd00046d-e9b6-4ae1-b661-3995f671b867
caps.latest.revision: "13"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: c6fd904db5d01bf1464da522d7209f8d15502556
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="how-to-use-parallel-containers-to-increase-efficiency"></a>Porady: korzystanie z kontenerów równoległych do zwiększania wydajności
W tym temacie pokazano, jak przy użyciu kontenerów równoległych wydajne przechowywanie i uzyskać dostęp do danych równolegle.  
  
 Przykładowy kod oblicza zestaw północnej i numery Carmichael równolegle. Następnie dla każdego numeru Carmichael kod oblicza podstawowe składniki ten numer.  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie przedstawiono `is_prime` funkcji, która określa, czy wartości wejściowej jest liczba pierwsza, i `is_carmichael` funkcji, która określa, czy wartość wejściowa jest liczbą Carmichael.  
  
 [!code-cpp[concrt-carmichael-primes#1](../../parallel/concrt/codesnippet/cpp/how-to-use-parallel-containers-to-increase-efficiency_1.cpp)]  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie użyto `is_prime` i `is_carmichael` funkcji do obliczenia zestawy północnej i Carmichael cyfr. W przykładzie użyto [concurrency::parallel_invoke](reference/concurrency-namespace-functions.md#parallel_invoke) i [concurrency::parallel_for](reference/concurrency-namespace-functions.md#parallel_for) algorytmy do obliczenia każdego ustawić równolegle. Aby uzyskać więcej informacji na temat algorytmy równoległe, zobacz [algorytmy równoległe](../../parallel/concrt/parallel-algorithms.md).  
  
 W tym przykładzie użyto [concurrency::concurrent_queue](../../parallel/concrt/reference/concurrent-queue-class.md) obiektu do przechowywania zbiór Carmichael numery ponieważ później użyje tego obiektu jako kolejki pracy. Używa [concurrency::concurrent_vector](../../parallel/concrt/reference/concurrent-vector-class.md) obiektu do przechowywania zbiór liczb pierwszych, ponieważ później będzie Iterowanie za pomocą tego zestawu można znaleźć głównego czynników.  
  
 [!code-cpp[concrt-carmichael-primes#2](../../parallel/concrt/codesnippet/cpp/how-to-use-parallel-containers-to-increase-efficiency_2.cpp)]  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie przedstawiono `prime_factors_of` funkcji, która korzysta z wersji próbnej dzielenia można znaleźć wszystkie główne składniki danej wartości.  
  
 Funkcja ta używa [concurrency::parallel_for_each](reference/concurrency-namespace-functions.md#parallel_for_each) algorytm do iterowania po kolekcji liczb pierwszych. `concurrent_vector` Obiektu umożliwia równoległej pętli jednocześnie dodać główne czynniki do wyniku.  
  
 [!code-cpp[concrt-carmichael-primes#3](../../parallel/concrt/codesnippet/cpp/how-to-use-parallel-containers-to-increase-efficiency_3.cpp)]  
  
## <a name="example"></a>Przykład  
 W tym przykładzie przetwarza każdy element w kolejce numery Carmichael przez wywołanie metody `prime_factors_of` funkcji do obliczenia jego podstawowym czynników. Używa grupy zadań do wykonania tej pracy równolegle. Aby uzyskać więcej informacji na temat grupy zadań, zobacz [równoległość zadań](../../parallel/concrt/task-parallelism-concurrency-runtime.md).  
  
 W tym przykładzie drukowane główne czynniki dla każdego numeru Carmichael, jeśli ten numer ma więcej niż cztery główne czynniki.  
  
 [!code-cpp[concrt-carmichael-primes#4](../../parallel/concrt/codesnippet/cpp/how-to-use-parallel-containers-to-increase-efficiency_4.cpp)]  
  
## <a name="example"></a>Przykład  
 Poniższy kod przedstawia pełny przykład używa kontenerów równoległych do wyliczenia główne czynniki Carmichael liczb.  
  
 [!code-cpp[concrt-carmichael-primes#5](../../parallel/concrt/codesnippet/cpp/how-to-use-parallel-containers-to-increase-efficiency_5.cpp)]  
  
 W tym przykładzie tworzy następujące przykładowe dane wyjściowe.  
  
```Output  
Prime factors of 9890881 are: 7 11 13 41 241.  
Prime factors of 825265 are: 5 7 17 19 73.  
Prime factors of 1050985 are: 5 13 19 23 37.  
```  
  
## <a name="compiling-the-code"></a>Kompilowanie kodu  
 Skopiuj przykładowy kod i wklej go w projekcie programu Visual Studio lub wklej go w pliku o nazwie `carmichael-primes.cpp` , a następnie uruchom następujące polecenie w oknie Wiersz polecenia programu Visual Studio.  
  
 **Cl.exe/ehsc carmichael-primes.cpp**  
  
## <a name="see-also"></a>Zobacz też  
 [Równoległe kontenery i obiekty](../../parallel/concrt/parallel-containers-and-objects.md)   
 [Równoległość zadania](../../parallel/concrt/task-parallelism-concurrency-runtime.md)   
 [concurrent_vector — klasa](../../parallel/concrt/reference/concurrent-vector-class.md)   
 [concurrent_queue — klasa](../../parallel/concrt/reference/concurrent-queue-class.md)   
 [parallel_invoke — funkcja](reference/concurrency-namespace-functions.md#parallel_invoke)   
 [parallel_for — funkcja](reference/concurrency-namespace-functions.md#parallel_for)   
 [task_group — klasa](reference/task-group-class.md)
