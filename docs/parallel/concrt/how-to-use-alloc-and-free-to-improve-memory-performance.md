---
title: 'Porady: używanie z funkcji Alloc i Free do poprawiania wydajności pamięci'
ms.date: 11/04/2016
helpviewer_keywords:
- Alloc and Free, using [Concurrency Runtime]
- Using Alloc and Free [Concurrency Runtime]
ms.assetid: e1fab9e8-a97d-4104-bead-e95958db79f9
ms.openlocfilehash: d91734859cd7d3499979566f427c10a0f026941b
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50467824"
---
# <a name="how-to-use-alloc-and-free-to-improve-memory-performance"></a>Porady: używanie z funkcji Alloc i Free do poprawiania wydajności pamięci

Ten dokument przedstawia sposób użycia [concurrency::Alloc](reference/concurrency-namespace-functions.md#alloc) i [concurrency::Free](reference/concurrency-namespace-functions.md#free) funkcje do poprawiania wydajności pamięci. Porównuje czas, który jest wymagany, aby odwrócić elementy tablicy w sposób równoległy dla trzech różnych typów, które każdy określa `new` i `delete` operatorów.

`Alloc` i `Free` funkcje są najbardziej przydatne w przypadku, gdy często wywołać wiele wątków `Alloc` i `Free`. Środowisko uruchomieniowe przechowuje w oddzielnych pamięci podręcznej dla każdego wątku; w związku z tym środowisko uruchomieniowe zarządza pamięcią bez użycia blokad lub barier pamięci.

## <a name="example"></a>Przykład

W poniższym przykładzie przedstawiono trzy typy, w których każdy określa `new` i `delete` operatorów. `new_delete` Klasa korzysta z globalnej `new` i `delete` operatorów, `malloc_free` klasa używa środowiska uruchomieniowego C [— funkcja malloc](../../c-runtime-library/reference/malloc.md) i [bezpłatne](../../c-runtime-library/reference/free.md) funkcje i `Alloc_Free` Klasa korzysta ze współbieżności środowiska wykonawczego `Alloc` i `Free` funkcji.

[!code-cpp[concrt-allocators#1](../../parallel/concrt/codesnippet/cpp/how-to-use-alloc-and-free-to-improve-memory-performance_1.cpp)]

## <a name="example"></a>Przykład

W poniższym przykładzie przedstawiono `swap` i `reverse_array` funkcji. `swap` Funkcja wymienia zawartość tablicy w określonej indeksów. Go przydziela pamięć ze stosu dla zmiennej tymczasowej. `reverse_array` Funkcja tworzy dużą tablicę i oblicza czas, który jest wymagany, aby wycofać tę tablicę kilka razy w sposób równoległy.

[!code-cpp[concrt-allocators#2](../../parallel/concrt/codesnippet/cpp/how-to-use-alloc-and-free-to-improve-memory-performance_2.cpp)]

## <a name="example"></a>Przykład

W poniższym przykładzie przedstawiono `wmain` funkcji, która oblicza czas, który jest wymagany dla `reverse_array` funkcja zajmującym się `new_delete`, `malloc_free`, i `Alloc_Free` typów, z których każdy wykorzystuje schemat alokacji pamięci różnych.

[!code-cpp[concrt-allocators#3](../../parallel/concrt/codesnippet/cpp/how-to-use-alloc-and-free-to-improve-memory-performance_3.cpp)]

## <a name="example"></a>Przykład

Pełny przykład poniżej.

[!code-cpp[concrt-allocators#4](../../parallel/concrt/codesnippet/cpp/how-to-use-alloc-and-free-to-improve-memory-performance_4.cpp)]

Ten przykład generuje następujące przykładowe dane wyjściowe dla komputera, który ma cztery procesory.

```Output
Took 2031 ms with new/delete.
Took 1672 ms with malloc/free.
Took 656 ms with Alloc/Free.
```

W tym przykładzie typ, który używa `Alloc` i `Free` functions zapewnia najlepszą wydajność pamięci, ponieważ `Alloc` i `Free` funkcje są zoptymalizowane pod kątem często przydzielanie i zwalnianie bloki pamięci z wielu wątki.

## <a name="compiling-the-code"></a>Kompilowanie kodu

Kopiuj przykładowy kod i wklej go w projekcie programu Visual Studio lub wklej go w pliku o nazwie `allocators.cpp` , a następnie uruchom następujące polecenie w oknie wiersza polecenia programu Visual Studio.

**Cl.exe/ehsc allocators.cpp**

## <a name="see-also"></a>Zobacz też

[Funkcje zarządzania pamięcią](../../parallel/concrt/memory-management-functions.md)<br/>
[ALLOC — funkcja](reference/concurrency-namespace-functions.md#alloc)<br/>
[Free — funkcja](reference/concurrency-namespace-functions.md#free)

