---
title: 'Porady: używanie z funkcji Alloc i Free do poprawiania wydajności pamięci'
ms.date: 11/04/2016
helpviewer_keywords:
- Alloc and Free, using [Concurrency Runtime]
- Using Alloc and Free [Concurrency Runtime]
ms.assetid: e1fab9e8-a97d-4104-bead-e95958db79f9
ms.openlocfilehash: e5e5207fe435e73df60b757d4f595aacbb70fe72
ms.sourcegitcommit: 94893973211d0b254c8bcdcf0779997dcc136b0c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/28/2020
ms.locfileid: "91414025"
---
# <a name="how-to-use-alloc-and-free-to-improve-memory-performance"></a>Porady: używanie z funkcji Alloc i Free do poprawiania wydajności pamięci

W tym dokumencie przedstawiono sposób korzystania z funkcji [concurrency:: Alloc](reference/concurrency-namespace-functions.md#alloc) i [concurrency:: Free](reference/concurrency-namespace-functions.md#free) w celu zwiększenia wydajności pamięci. Porównuje czas wymagany do odwrócenia elementów tablicy równolegle dla trzech różnych typów, które określają `new` `delete` Operatory i.

`Alloc`Funkcje i `Free` są najbardziej przydatne, gdy wiele wątków często wywołuje jednocześnie `Alloc` i `Free` . Środowisko uruchomieniowe utrzymuje oddzielną pamięć podręczną pamięci dla każdego wątku; w związku z tym środowisko uruchomieniowe zarządza pamięcią bez użycia blokad lub barier pamięci.

## <a name="example-types-that-specify-new-and-delete-operators"></a>Przykład: typy określające operatory New i DELETE

W poniższym przykładzie pokazano trzy typy, które określają `new` Operatory i `delete` . `new_delete`Klasa używa `new` operatorów globalnych i `delete` , `malloc_free` Klasa używa funkcji [malloc](../../c-runtime-library/reference/malloc.md) i [Free](../../c-runtime-library/reference/free.md) środowiska uruchomieniowego języka C, a `Alloc_Free` Klasa używa środowisko uruchomieniowe współbieżności `Alloc` i `Free` funkcji.

[!code-cpp[concrt-allocators#1](../../parallel/concrt/codesnippet/cpp/how-to-use-alloc-and-free-to-improve-memory-performance_1.cpp)]

## <a name="example-swap-and-reverse_array-functions"></a>Przykład: funkcje zamiany i reverse_array

W poniższym przykładzie przedstawiono `swap` funkcje i `reverse_array` . `swap`Funkcja wymienia zawartość tablicy w określonych indeksach. Przydziela pamięć ze sterty dla zmiennej tymczasowej. `reverse_array`Funkcja tworzy dużą tablicę i oblicza czas wymagany do odwrócenia tablicy kilka razy równolegle.

[!code-cpp[concrt-allocators#2](../../parallel/concrt/codesnippet/cpp/how-to-use-alloc-and-free-to-improve-memory-performance_2.cpp)]

## <a name="example-wmain-function"></a>Przykład: funkcja wmain

Poniższy przykład pokazuje `wmain` funkcję, która oblicza czas wymagany do `reverse_array` działania funkcji na `new_delete` , `malloc_free` , i `Alloc_Free` , z których każdy używa innego schematu alokacji pamięci.

[!code-cpp[concrt-allocators#3](../../parallel/concrt/codesnippet/cpp/how-to-use-alloc-and-free-to-improve-memory-performance_3.cpp)]

## <a name="complete-code-example"></a>Pełny przykład kodu

Kompletny przykład.

[!code-cpp[concrt-allocators#4](../../parallel/concrt/codesnippet/cpp/how-to-use-alloc-and-free-to-improve-memory-performance_4.cpp)]

Ten przykład generuje następujące przykładowe dane wyjściowe dla komputera, który ma cztery procesory.

```Output
Took 2031 ms with new/delete.
Took 1672 ms with malloc/free.
Took 656 ms with Alloc/Free.
```

W tym przykładzie typ, który korzysta z `Alloc` funkcji i `Free` zapewnia najlepszą wydajność pamięci, ponieważ `Alloc` `Free` funkcje i są zoptymalizowane pod kątem często przypisywania i zwalniania bloków pamięci z wielu wątków.

## <a name="compiling-the-code"></a>Kompilowanie kodu

Skopiuj przykładowy kod i wklej go w projekcie programu Visual Studio lub wklej go w pliku o nazwie, `allocators.cpp` a następnie uruchom następujące polecenie w oknie wiersza polecenia programu Visual Studio.

> **cl.exe przy/EHsceń. cpp**

## <a name="see-also"></a>Zobacz także

[Funkcje zarządzania pamięcią](../../parallel/concrt/memory-management-functions.md)<br/>
[Alloc — funkcja](reference/concurrency-namespace-functions.md#alloc)<br/>
[Free — funkcja](reference/concurrency-namespace-functions.md#free)
