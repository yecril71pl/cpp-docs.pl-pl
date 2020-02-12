---
title: 'Porady: konwertowanie paraleli OpenMP dla pętli do korzystania ze współbieżności środowiska wykonawczego'
ms.date: 11/04/2016
helpviewer_keywords:
- converting from OpenMP to the Concurrency Runtime, parallel for loops
- converting from OpenMP to the Concurrency Runtime, parallel loops
- parallel for loops, converting from OpenMP to the Concurrency Runtime
- parallel loops, converting from OpenMP to the Concurrency Runtime
ms.assetid: d8a7b656-f86c-456e-9c5d-a7d52f94646e
ms.openlocfilehash: 2d96ba23582368fe72e61003823826a6f3ab807a
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/11/2020
ms.locfileid: "77141766"
---
# <a name="how-to-convert-an-openmp-parallel-for-loop-to-use-the-concurrency-runtime"></a>Porady: konwertowanie paraleli OpenMP dla pętli do korzystania ze współbieżności środowiska wykonawczego

W tym przykładzie pokazano, jak przekonwertować pętlę podstawową, która używa algorytmu "OpenMP [Parallel](../../parallel/concrt/how-to-use-parallel-invoke-to-write-a-parallel-sort-routine.md#parallel) and [for](../../parallel/openmp/reference/for-openmp.md) ", aby użyć algorytmu środowisko uruchomieniowe współbieżności [concurrency::p arallel_for](reference/concurrency-namespace-functions.md#parallel_for) .

## <a name="example---prime-count"></a>Przykład — liczba podstawowa

W tym przykładzie używamy OpenMP i środowisko uruchomieniowe współbieżności, aby obliczyć liczbę pierwszych numerów w tablicy wartości losowych.

[!code-cpp[concrt-openmp#1](../../parallel/concrt/codesnippet/cpp/how-to-convert-an-openmp-parallel-for-loop-to-use-the-concurrency-runtime_1.cpp)]

Ten przykład generuje następujące dane wyjściowe.

```Output
Using OpenMP...
found 107254 prime numbers.
Using the Concurrency Runtime...
found 107254 prime numbers.
```

Algorytm `parallel_for` i OpenMP 3,0 Zezwalaj na typ indeksu jako typ całkowity ze znakiem lub bez typu całkowitego. Algorytm `parallel_for` sprawdza również, czy określony zakres nie przepełnił typu ze znakiem. Wersje OpenMP 2,0 i 2,5 zezwalają tylko na podpisane typy indeksów całkowitych. OpenMP nie sprawdza także zakresu indeksu.

Wersja tego przykładu, która używa środowisko uruchomieniowe współbieżności używa również obiektu [concurrency::Binding](../../parallel/concrt/reference/combinable-class.md) zamiast dyrektywy [atomowej](../../parallel/openmp/reference/atomic.md) , aby zwiększyć wartość licznika bez konieczności synchronizacji.

Aby uzyskać więcej informacji na temat `parallel_for` i innych algorytmów równoległych, zobacz [algorytmy równoległe](../../parallel/concrt/parallel-algorithms.md). Aby uzyskać więcej informacji na temat klasy `combinable`, zobacz [Parallel Containers and Objects](../../parallel/concrt/parallel-containers-and-objects.md).

## <a name="example---use-stdarray"></a>Przykład — użyj std:: Array

Ten przykład modyfikuje poprzednią wartość, aby działać na obiekcie [std:: Array](../../standard-library/array-class-stl.md) zamiast w tablicy natywnej. Ze względu na to, że wersje OpenMP 2,0 i 2,5 zezwalają na podpisane typy indeksów całkowitych tylko w konstrukcji `parallel_for` nie można użyć iteratorów C++ , aby uzyskać dostęp do elementów kontenera biblioteki standardowej równolegle. Biblioteka równoległych wzorców (PPL) zapewnia algorytm [concurrency::p arallel_for_each](reference/concurrency-namespace-functions.md#parallel_for_each) , który wykonuje zadania równolegle, w kontenerze iteracyjnym, takim jak te dostarczone przez bibliotekę C++ standardową. Używa tej samej logiki partycjonowania, której używa algorytm `parallel_for`. Algorytm `parallel_for_each` jest podobny do C++ algorytmu standardowej biblioteki [std:: for_each](../../standard-library/algorithm-functions.md#for_each) , z tą różnicą, że algorytm `parallel_for_each` wykonuje zadania współbieżnie.

[!code-cpp[concrt-openmp#10](../../parallel/concrt/codesnippet/cpp/how-to-convert-an-openmp-parallel-for-loop-to-use-the-concurrency-runtime_2.cpp)]

## <a name="compiling-the-code"></a>Kompilowanie kodu

Skopiuj przykładowy kod i wklej go w projekcie programu Visual Studio lub wklej go w pliku o nazwie `concrt-omp-count-primes.cpp` a następnie uruchom następujące polecenie w oknie wiersza polecenia programu Visual Studio.

> **CL. exe/EHsc/OpenMP ConcRT-OMP-Count-primes. cpp**

## <a name="see-also"></a>Zobacz też

[Migrowanie z OpenMP do środowiska uruchomieniowego współbieżności](../../parallel/concrt/migrating-from-openmp-to-the-concurrency-runtime.md)<br/>
[Algorytmy równoległe](../../parallel/concrt/parallel-algorithms.md)<br/>
[Równoległe kontenery oraz obiekty](../../parallel/concrt/parallel-containers-and-objects.md)
