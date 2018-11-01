---
title: 'Porady: konwertowanie pętli OpenMP używającej zmiennej redukcji do korzystania ze współbieżności środowiska wykonawczego'
ms.date: 11/04/2016
helpviewer_keywords:
- converting from OpenMP to the Concurrency Runtime, reduction variables
- reduction variables, converting from OpenMP to the Concurrency Runtime
ms.assetid: 96623f36-5e57-4d3f-8c13-669e6cd535b1
ms.openlocfilehash: b58f6025c41091b39375c566d2c1d4b4798437b2
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50633080"
---
# <a name="how-to-convert-an-openmp-loop-that-uses-a-reduction-variable-to-use-the-concurrency-runtime"></a>Porady: konwertowanie pętli OpenMP używającej zmiennej redukcji do korzystania ze współbieżności środowiska wykonawczego

W tym przykładzie opisano sposób konwertowania OpenMP [równoległe](../../parallel/concrt/how-to-use-parallel-invoke-to-write-a-parallel-sort-routine.md#parallel)[dla](../../parallel/openmp/reference/for-openmp.md) pętli, która używa [redukcji](../../parallel/openmp/reference/reduction.md) klauzuli do korzystania ze współbieżności środowiska wykonawczego.

OpenMP `reduction` klauzuli pozwala określić jedną lub więcej zmiennych prywatnego wątku, które podlegają operacji zmniejszenia na końcu równoległego regionu. OpenMP powoduje wstępne definiowanie zestaw operatorów redukcji. Każda zmienna redukcji musi być wartością skalarną (na przykład `int`, `long`, i `float`). OpenMP definiuje również kilka ograniczeń dotyczących użycia zmienne redukcji w równoległego regionu.

Biblioteka równoległych wzorców (PPL) zapewnia [concurrency::combinable](../../parallel/concrt/reference/combinable-class.md) klasy, która dostarcza magazynu wielokrotnego użytku, lokalnej wątku, który pozwala wykonywać precyzyjną obliczeń, a następnie scalić tych obliczeń do ostatecznej wynik. `combinable` Klasy jest szablon, który działa dla typów skalarnych i złożone. Aby użyć `combinable` klasy wykonują obliczenia podrzędnych w treści konstrukcja równoległa, a następnie wywołać [concurrency::combinable::combine](reference/combinable-class.md#combine) lub [concurrency::combinable::combine_each](reference/combinable-class.md#combine_each) Metoda, aby wygenerować ostateczny rezultat. `combine` i `combine_each` każdej metody przyjmują *łączenie funkcji* , który określa sposób łączenia każdego pary elementów. W związku z tym `combinable` klasy nie jest ograniczona do stały zestaw operatorów redukcji.

## <a name="example"></a>Przykład

W tym przykładzie używa OpenMP i środowisku uruchomieniowym współbieżności: Aby obliczyć sumę liczb Fibonacci najpierw 35.

[!code-cpp[concrt-openmp#7](../../parallel/concrt/codesnippet/cpp/convert-an-openmp-loop-that-uses-a-reduction-variable_1.cpp)]

Ten przykład generuje następujące dane wyjściowe.

```Output
Using OpenMP...
The sum of the first 35 Fibonacci numbers is 14930351.
Using the Concurrency Runtime...
The sum of the first 35 Fibonacci numbers is 14930351.
```

Aby uzyskać więcej informacji na temat `combinable` klasy, zobacz [równoległe kontenery oraz obiekty](../../parallel/concrt/parallel-containers-and-objects.md).

## <a name="compiling-the-code"></a>Kompilowanie kodu

Kopiuj przykładowy kod i wklej go w projekcie programu Visual Studio lub wklej go w pliku o nazwie `concrt-omp-fibonacci-reduction.cpp` , a następnie uruchom następujące polecenie w oknie wiersza polecenia programu Visual Studio.

**concrt/OpenMP/ehsc cl.exe-omp — fibonacci-reduction.cpp**

## <a name="see-also"></a>Zobacz też

[Migrowanie z OpenMP do środowiska uruchomieniowego współbieżności](../../parallel/concrt/migrating-from-openmp-to-the-concurrency-runtime.md)<br/>
[Równoległe kontenery oraz obiekty](../../parallel/concrt/parallel-containers-and-objects.md)

