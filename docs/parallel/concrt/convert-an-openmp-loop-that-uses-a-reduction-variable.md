---
title: 'Porady: konwertowanie pętli OpenMP używającej zmiennej redukcji do korzystania ze współbieżności środowiska wykonawczego | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-concrt
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- converting from OpenMP to the Concurrency Runtime, reduction variables
- reduction variables, converting from OpenMP to the Concurrency Runtime
ms.assetid: 96623f36-5e57-4d3f-8c13-669e6cd535b1
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 0191f88eea47d21c730172ddb3594db7655006ca
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/07/2018
ms.locfileid: "33692772"
---
# <a name="how-to-convert-an-openmp-loop-that-uses-a-reduction-variable-to-use-the-concurrency-runtime"></a>Porady: konwertowanie pętli OpenMP używającej zmiennej redukcji do korzystania ze współbieżności środowiska wykonawczego
W tym przykładzie pokazano, jak przekonwertować OpenMP [równoległych](../../parallel/concrt/how-to-use-parallel-invoke-to-write-a-parallel-sort-routine.md#parallel)[dla](../../parallel/openmp/reference/for-openmp.md) pętli, które używa [redukcji](../../parallel/openmp/reference/reduction.md) klauzuli do korzystania ze współbieżności środowiska wykonawczego.  
  
 OpenMP `reduction` klauzuli pozwala określić jedną lub więcej zmiennych prywatnego wątku, które podlegają operacji zmniejszenia na końcu równoległego regionu. OpenMP — powoduje wstępne definiowanie zestaw operatorów odstępu. Każdej zmiennej redukcji musi być wartością skalarną (na przykład `int`, `long`, i `float`). OpenMP — definiuje również kilka ograniczeń na używania zmienne redukcji w równoległego regionu.  
  
 Biblioteka równoległych wzorców (PLL) zapewnia [concurrency::combinable](../../parallel/concrt/reference/combinable-class.md) klasy, która dostarcza magazynu wielokrotnego użytku, lokalnej wątku, który pozwala przeprowadzić obliczenia szczegółowych, a następnie scalić tych obliczeń do ostatecznej wynik. `combinable` Klasy to szablon, który działa na zarówno skalarne i złożone typy. Aby użyć `combinable` klasy wykonać obliczenia podrzędne w treści konstrukcję równoległego, a następnie wywołać [concurrency::combinable::combine](reference/combinable-class.md#combine) lub [concurrency::combinable::combine_each](reference/combinable-class.md#combine_each) Metoda do utworzenia końcowego wyniku. `combine` i `combine_each` każdej metody przyjmują *połączyć funkcja* , który określa sposób łączenia każda para elementów. W związku z tym `combinable` klasy nie jest ograniczone do ustalony zbiór operatory odstępu.  
  
## <a name="example"></a>Przykład  
 W tym przykładzie używane zarówno OpenMP, jak i współbieżności środowiska wykonawczego do obliczenia sumy najpierw 35 liczb Fibonacci.  
  
 [!code-cpp[concrt-openmp#7](../../parallel/concrt/codesnippet/cpp/convert-an-openmp-loop-that-uses-a-reduction-variable_1.cpp)]  
  
 W tym przykładzie tworzy następujące dane wyjściowe.  
  
```Output  
Using OpenMP...  
The sum of the first 35 Fibonacci numbers is 14930351.  
Using the Concurrency Runtime...  
The sum of the first 35 Fibonacci numbers is 14930351.  
```  
  
 Aby uzyskać więcej informacji na temat `combinable` , zobacz [równoległe kontenery oraz obiekty](../../parallel/concrt/parallel-containers-and-objects.md).  
  
## <a name="compiling-the-code"></a>Kompilowanie kodu  
 Skopiuj przykładowy kod i wklej go w projekcie programu Visual Studio lub wklej go w pliku o nazwie `concrt-omp-fibonacci-reduction.cpp` , a następnie uruchom następujące polecenie w oknie Wiersz polecenia programu Visual Studio.  
  
 **concrt/OpenMP/ehsc cl.exe-omp-fibonacci-reduction.cpp**  
  
## <a name="see-also"></a>Zobacz też  
 [Migrowanie z OpenMP do współbieżności środowiska wykonawczego](../../parallel/concrt/migrating-from-openmp-to-the-concurrency-runtime.md)   
 [Równoległe kontenery oraz obiekty](../../parallel/concrt/parallel-containers-and-objects.md)

