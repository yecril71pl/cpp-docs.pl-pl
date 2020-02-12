---
title: 'Porady: konwertowanie pętli OpenMP używającej zmiennej redukcji do korzystania ze współbieżności środowiska wykonawczego'
ms.date: 11/04/2016
helpviewer_keywords:
- converting from OpenMP to the Concurrency Runtime, reduction variables
- reduction variables, converting from OpenMP to the Concurrency Runtime
ms.assetid: 96623f36-5e57-4d3f-8c13-669e6cd535b1
ms.openlocfilehash: ee0a600f4234c3ebf4681ad92b5e3623be5665c3
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/11/2020
ms.locfileid: "77141267"
---
# <a name="how-to-convert-an-openmp-loop-that-uses-a-reduction-variable-to-use-the-concurrency-runtime"></a>Porady: konwertowanie pętli OpenMP używającej zmiennej redukcji do korzystania ze współbieżności środowiska wykonawczego

W tym przykładzie pokazano, jak przekonwertować [równoległą](../../parallel/concrt/how-to-use-parallel-invoke-to-write-a-parallel-sort-routine.md#parallel)pętlę OpenMP[dla](../../parallel/openmp/reference/for-openmp.md) pętli [](../../parallel/openmp/reference/reduction.md) , która używa środowisko uruchomieniowe współbieżności.

Klauzula `reduction` OpenMP pozwala określić jedną lub więcej zmiennych prywatnych wątku, które podlegają operacji zmniejszania na końcu regionu równoległego. OpenMP wstępnie definiuje zestaw operatorów redukcji. Każda zmienna redukcyjna musi być skalarna (na przykład `int`, `long`i `float`). OpenMP definiuje również pewne ograniczenia dotyczące sposobu używania zmiennych redukcji w regionie równoległym.

Biblioteka równoległych wzorców (PPL) udostępnia klasę [concurrency::](../../parallel/concrt/reference/combinable-class.md) Merge, która zapewnia możliwość wielokrotnego użytku, Magazyn lokalny wątków, który umożliwia wykonywanie szczegółowych obliczeń, a następnie scalanie tych obliczeń w końcowy wynik. Klasa `combinable` to szablon, który działa na obu typach skalarnych i złożonych. Aby użyć klasy `combinable`, wykonaj obliczenia podrzędne w treści konstrukcji równoległej, a następnie Wywołaj metodę [concurrency:: kombinowane:: złącz](reference/combinable-class.md#combine) lub [concurrency:: kombinowane:: combine_each](reference/combinable-class.md#combine_each) , aby utworzyć wynik końcowy. Metody `combine` i `combine_each` każda z nich przyjmuje *funkcję Połącz* , która określa, jak połączyć każdą parę elementów. W związku z tym Klasa `combinable` nie jest ograniczona do ustalonego zestawu operatorów redukcji.

## <a name="example"></a>Przykład

W tym przykładzie używamy OpenMP i środowisko uruchomieniowe współbieżności, aby obliczyć sumę pierwszych 35 numerów Fibonacci.

[!code-cpp[concrt-openmp#7](../../parallel/concrt/codesnippet/cpp/convert-an-openmp-loop-that-uses-a-reduction-variable_1.cpp)]

Ten przykład generuje następujące dane wyjściowe.

```Output
Using OpenMP...
The sum of the first 35 Fibonacci numbers is 14930351.
Using the Concurrency Runtime...
The sum of the first 35 Fibonacci numbers is 14930351.
```

Aby uzyskać więcej informacji na temat klasy `combinable`, zobacz [Parallel Containers and Objects](../../parallel/concrt/parallel-containers-and-objects.md).

## <a name="compiling-the-code"></a>Kompilowanie kodu

Skopiuj przykładowy kod i wklej go w projekcie programu Visual Studio lub wklej go w pliku o nazwie `concrt-omp-fibonacci-reduction.cpp` a następnie uruchom następujące polecenie w oknie wiersza polecenia programu Visual Studio.

> **CL. exe/EHsc/OpenMP ConcRT-OMP-Fibonacci-Reduction. cpp**

## <a name="see-also"></a>Zobacz też

[Migrowanie z OpenMP do środowiska uruchomieniowego współbieżności](../../parallel/concrt/migrating-from-openmp-to-the-concurrency-runtime.md)<br/>
[Równoległe kontenery oraz obiekty](../../parallel/concrt/parallel-containers-and-objects.md)
