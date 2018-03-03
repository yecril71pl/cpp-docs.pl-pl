---
title: "Porady: Korzystanie z wyników połączonych w celu łączenia zestawów | Dokumentacja firmy Microsoft"
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
- combining sets with combinable [Concurrency Runtime]
ms.assetid: 66ffe8e3-6bbb-4e9f-b790-b612922a68a7
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 8bbd36e9536707bc639e8f80cc019b7fda18f793
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="how-to-use-combinable-to-combine-sets"></a>Porady: korzystanie z wyników połączonych w celu łączenia zestawów
W tym temacie przedstawiono sposób użycia [concurrency::combinable](../../parallel/concrt/reference/combinable-class.md) klasy do obliczenia zbiór liczb pierwszych.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład oblicza zbiór liczb pierwszych dwa razy. Każdy obliczeń przechowuje wyniki w [std::bitset](../../standard-library/bitset-class.md) obiektu. Przykład najpierw oblicza zestaw pojedynczo, a następnie oblicza zestaw równolegle. Przykład drukuje do konsoli również czasu wymaganego do wykonania obu obliczenia.  
  
 W tym przykładzie użyto [concurrency::parallel_for](reference/concurrency-namespace-functions.md#parallel_for) algorytmu i `combinable` obiektu można wygenerować zestawów lokalnej wątku. Następnie używa [concurrency::combinable::combine_each](reference/combinable-class.md#combine_each) metoda łączenia lokalnej wątku zestawów do ostatecznego zestawu.  

  
 [!code-cpp[concrt-parallel-combine-primes#1](../../parallel/concrt/codesnippet/cpp/how-to-use-combinable-to-combine-sets_1.cpp)]  
  
 Następujące przykładowe dane wyjściowe jest dla komputera, który ma cztery procesory.  
  
```Output  
serial time: 312 ms  
 
parallel time: 78 ms  
```  
  
## <a name="compiling-the-code"></a>Kompilowanie kodu  
 Skopiuj przykładowy kod i wklej go w projekcie programu Visual Studio lub wklej go w pliku o nazwie `parallel-combine-primes.cpp` , a następnie uruchom następujące polecenie w oknie Wiersz polecenia programu Visual Studio.  
  
 **Cl.exe/ehsc równoległe — łączenie primes.cpp**  
  
## <a name="see-also"></a>Zobacz też  
 [Równoległe kontenery i obiekty](../../parallel/concrt/parallel-containers-and-objects.md)   
 [combinable — klasa](../../parallel/concrt/reference/combinable-class.md)   
 [combinable::combine_each — metoda](reference/combinable-class.md#combine_each)


