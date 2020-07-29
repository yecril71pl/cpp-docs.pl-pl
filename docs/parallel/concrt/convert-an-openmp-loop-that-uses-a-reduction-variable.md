---
title: 'Porady: konwertowanie pętli OpenMP używającej zmiennej redukcji do korzystania ze współbieżności środowiska wykonawczego'
ms.date: 11/04/2016
helpviewer_keywords:
- converting from OpenMP to the Concurrency Runtime, reduction variables
- reduction variables, converting from OpenMP to the Concurrency Runtime
ms.assetid: 96623f36-5e57-4d3f-8c13-669e6cd535b1
ms.openlocfilehash: 15ec81fb4fafd7850162a1feab28e72d469aff91
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87206006"
---
# <a name="how-to-convert-an-openmp-loop-that-uses-a-reduction-variable-to-use-the-concurrency-runtime"></a>Porady: konwertowanie pętli OpenMP używającej zmiennej redukcji do korzystania ze współbieżności środowiska wykonawczego

W tym przykładzie pokazano, jak przekonwertować [równoległą](../../parallel/concrt/how-to-use-parallel-invoke-to-write-a-parallel-sort-routine.md#parallel)pętlę OpenMP[dla](../../parallel/openmp/reference/for-openmp.md) pętli [reduction](../../parallel/openmp/reference/reduction.md) , która używa środowisko uruchomieniowe współbieżności.

Klauzula OpenMP `reduction` pozwala określić jedną lub więcej zmiennych prywatnych wątku, które podlegają operacji zmniejszania na końcu regionu równoległego. OpenMP wstępnie definiuje zestaw operatorów redukcji. Każda zmienna redukcyjna musi być skalarna (na przykład,, **`int`** **`long`** i **`float`** ). OpenMP definiuje również pewne ograniczenia dotyczące sposobu używania zmiennych redukcji w regionie równoległym.

Biblioteka równoległych wzorców (PPL) udostępnia klasę [concurrency::](../../parallel/concrt/reference/combinable-class.md) Merge, która zapewnia możliwość wielokrotnego użytku, Magazyn lokalny wątków, który umożliwia wykonywanie szczegółowych obliczeń, a następnie scalanie tych obliczeń w końcowy wynik. `combinable`Klasa to szablon, który działa na obu typach skalarnych i złożonych. Aby użyć `combinable` klasy, wykonaj obliczenia podrzędne w treści konstrukcji równoległej, a następnie Wywołaj metodę [concurrency:: kombinowane:: złącz](reference/combinable-class.md#combine) lub [concurrency:: kombinowane:: combine_each](reference/combinable-class.md#combine_each) , aby utworzyć wynik końcowy. `combine`Metody i `combine_each` przyjmują *funkcję Połącz* , która określa, jak połączyć każdą parę elementów. W związku z tym `combinable` Klasa nie jest ograniczona do ustalonego zestawu operatorów redukcji.

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

Aby uzyskać więcej informacji na temat `combinable` klasy, zobacz [Parallel Containers and Objects](../../parallel/concrt/parallel-containers-and-objects.md).

## <a name="compiling-the-code"></a>Kompilowanie kodu

Skopiuj przykładowy kod i wklej go w projekcie programu Visual Studio lub wklej go w pliku o nazwie, `concrt-omp-fibonacci-reduction.cpp` a następnie uruchom następujące polecenie w oknie wiersza polecenia programu Visual Studio.

> **cl.exe/EHsc/OpenMP ConcRT-OMP-Fibonacci-Reduction. cpp**

## <a name="see-also"></a>Zobacz także

[Migrowanie z OpenMP do współbieżności środowiska wykonawczego](../../parallel/concrt/migrating-from-openmp-to-the-concurrency-runtime.md)<br/>
[Równoległe kontenery i obiekty](../../parallel/concrt/parallel-containers-and-objects.md)
