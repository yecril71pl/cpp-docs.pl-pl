---
title: 'Porady: konwertowanie paraleli OpenMP dla pętli do korzystania ze współbieżności środowiska wykonawczego'
ms.date: 11/04/2016
helpviewer_keywords:
- converting from OpenMP to the Concurrency Runtime, parallel for loops
- converting from OpenMP to the Concurrency Runtime, parallel loops
- parallel for loops, converting from OpenMP to the Concurrency Runtime
- parallel loops, converting from OpenMP to the Concurrency Runtime
ms.assetid: d8a7b656-f86c-456e-9c5d-a7d52f94646e
ms.openlocfilehash: 9ab80df8bfe4c06ee36e0a60db4800be68576909
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50488568"
---
# <a name="how-to-convert-an-openmp-parallel-for-loop-to-use-the-concurrency-runtime"></a>Porady: konwertowanie paraleli OpenMP dla pętli do korzystania ze współbieżności środowiska wykonawczego

W tym przykładzie opisano sposób konwertowania podstawowe pętli, która używa OpenMP [równoległe](../../parallel/concrt/how-to-use-parallel-invoke-to-write-a-parallel-sort-routine.md#parallel) i [dla](../../parallel/openmp/reference/for-openmp.md) dyrektywy do korzystania ze współbieżności środowiska wykonawczego [concurrency::parallel_for](reference/concurrency-namespace-functions.md#parallel_for) algorytm.

## <a name="example"></a>Przykład

W tym przykładzie używa OpenMP i środowisku uruchomieniowym współbieżności: do obliczenia liczby liczb pierwszych, w tablicy wartości losowych.

[!code-cpp[concrt-openmp#1](../../parallel/concrt/codesnippet/cpp/how-to-convert-an-openmp-parallel-for-loop-to-use-the-concurrency-runtime_1.cpp)]

Ten przykład generuje następujące dane wyjściowe.

```Output
Using OpenMP...
found 107254 prime numbers.
Using the Concurrency Runtime...
found 107254 prime numbers.
```

`parallel_for` Algorytmu i OpenMP 3.0 umożliwiają dla typu indeksu jako typ całkowity ze znakiem lub nieoznaczoną liczbę całkowitą. `parallel_for` Algorytm również sprawdza, czy określony zakres nie przepełnienia typ ze znakiem. OpenMP w wersji 2.0 i 2.5 Zezwalaj na podpisane indeksu typu całkowitego tylko dla typów. OpenMP również nie można zweryfikować z zakresem indeksu.

Używa także wersja tego przykładu, który korzysta ze współbieżności środowiska wykonawczego [concurrency::combinable](../../parallel/concrt/reference/combinable-class.md) obiektu zamiast [atomic](../../parallel/openmp/reference/atomic.md) dyrektywy, aby zwiększyć wartość licznika, bez konieczności Synchronizacja.

Aby uzyskać więcej informacji na temat `parallel_for` i innych równoległych algorytmów, zobacz [algorytmy równoległe](../../parallel/concrt/parallel-algorithms.md). Aby uzyskać więcej informacji na temat `combinable` klasy, zobacz [równoległe kontenery oraz obiekty](../../parallel/concrt/parallel-containers-and-objects.md).

## <a name="example"></a>Przykład

Ten przykład modyfikuje poprzedni, aby działać na [std::array](../../standard-library/array-class-stl.md) zamiast obiektu na tablicy natywnej. OpenMP w wersji 2.0 i 2.5 jest dozwolone dla podpisanej typów całkowitych indeksu tylko w `parallel_for` konstrukcji, nie można użyć Iteratory do dostępu do elementów kontenera standardowej biblioteki języka C++ w sposób równoległy. Biblioteka równoległych wzorców (PPL) zapewnia [concurrency::parallel_for_each](reference/concurrency-namespace-functions.md#parallel_for_each) algorytmu, który wykonuje zadania, w sposób równoległy, iteracyjne kontenera, takie jak te oferowane przez standardowej biblioteki języka C++. Używa ona tę samą logikę partycjonowania, `parallel_for` używa algorytmu. `parallel_for_each` Algorytm przypomina standardowej biblioteki C++ [std::for_each](../../standard-library/algorithm-functions.md#for_each) algorytmu, chyba że `parallel_for_each` algorytm wykonuje zadania jednocześnie.

[!code-cpp[concrt-openmp#10](../../parallel/concrt/codesnippet/cpp/how-to-convert-an-openmp-parallel-for-loop-to-use-the-concurrency-runtime_2.cpp)]

## <a name="compiling-the-code"></a>Kompilowanie kodu

Kopiuj przykładowy kod i wklej go w projekcie programu Visual Studio lub wklej go w pliku o nazwie `concrt-omp-count-primes.cpp` , a następnie uruchom następujące polecenie w oknie wiersza polecenia programu Visual Studio.

**concrt/OpenMP/ehsc cl.exe-omp — liczba primes.cpp**

## <a name="see-also"></a>Zobacz też

[Migrowanie z OpenMP do środowiska uruchomieniowego współbieżności](../../parallel/concrt/migrating-from-openmp-to-the-concurrency-runtime.md)<br/>
[Algorytmy równoległe](../../parallel/concrt/parallel-algorithms.md)<br/>
[Równoległe kontenery oraz obiekty](../../parallel/concrt/parallel-containers-and-objects.md)

