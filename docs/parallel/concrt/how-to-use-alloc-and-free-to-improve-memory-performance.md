---
title: 'Porady: używanie z funkcji Alloc i Free do poprawiania wydajności pamięci'
ms.date: 11/04/2016
helpviewer_keywords:
- Alloc and Free, using [Concurrency Runtime]
- Using Alloc and Free [Concurrency Runtime]
ms.assetid: e1fab9e8-a97d-4104-bead-e95958db79f9
ms.openlocfilehash: 8438e833262d42c6083f48f759501c573a35c772
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/11/2020
ms.locfileid: "77142785"
---
# <a name="how-to-use-alloc-and-free-to-improve-memory-performance"></a>Porady: używanie z funkcji Alloc i Free do poprawiania wydajności pamięci

W tym dokumencie przedstawiono sposób korzystania z funkcji [concurrency:: Alloc](reference/concurrency-namespace-functions.md#alloc) i [concurrency:: Free](reference/concurrency-namespace-functions.md#free) w celu zwiększenia wydajności pamięci. Porównuje czas wymagany do odwrócenia elementów tablicy równolegle dla trzech różnych typów, które określają operatory `new` i `delete`.

`Alloc` i `Free` funkcje są najbardziej przydatne, gdy wiele wątków często wywołuje zarówno `Alloc`, jak i `Free`. Środowisko uruchomieniowe utrzymuje oddzielną pamięć podręczną pamięci dla każdego wątku; w związku z tym środowisko uruchomieniowe zarządza pamięcią bez użycia blokad lub barier pamięci.

## <a name="example"></a>Przykład

W poniższym przykładzie pokazano trzy typy, które określają operatory `new` i `delete`. Klasa `new_delete` używa operatorów globalnych `new` i `delete`, Klasa `malloc_free` używa funkcji [malloc](../../c-runtime-library/reference/malloc.md) i [Free](../../c-runtime-library/reference/free.md) środowiska uruchomieniowego języka C, a Klasa `Alloc_Free` używa funkcji środowisko uruchomieniowe współbieżności `Alloc` i `Free`.

[!code-cpp[concrt-allocators#1](../../parallel/concrt/codesnippet/cpp/how-to-use-alloc-and-free-to-improve-memory-performance_1.cpp)]

## <a name="example"></a>Przykład

W poniższym przykładzie przedstawiono funkcje `swap` i `reverse_array`. Funkcja `swap` wymienia zawartość tablicy w określonych indeksach. Przydziela pamięć ze sterty dla zmiennej tymczasowej. Funkcja `reverse_array` tworzy dużą tablicę i oblicza czas wymagany do odwrócenia tablicy kilka razy równolegle.

[!code-cpp[concrt-allocators#2](../../parallel/concrt/codesnippet/cpp/how-to-use-alloc-and-free-to-improve-memory-performance_2.cpp)]

## <a name="example"></a>Przykład

W poniższym przykładzie pokazano funkcję `wmain`, która oblicza czas wymagany do działania funkcji `reverse_array` w przypadku `new_delete`, `malloc_free`i `Alloc_Free` typów, z których każdy korzysta z innego schematu alokacji pamięci.

[!code-cpp[concrt-allocators#3](../../parallel/concrt/codesnippet/cpp/how-to-use-alloc-and-free-to-improve-memory-performance_3.cpp)]

## <a name="example"></a>Przykład

Kompletny przykład.

[!code-cpp[concrt-allocators#4](../../parallel/concrt/codesnippet/cpp/how-to-use-alloc-and-free-to-improve-memory-performance_4.cpp)]

Ten przykład generuje następujące przykładowe dane wyjściowe dla komputera, który ma cztery procesory.

```Output
Took 2031 ms with new/delete.
Took 1672 ms with malloc/free.
Took 656 ms with Alloc/Free.
```

W tym przykładzie typ, który używa funkcji `Alloc` i `Free` zapewnia najlepszą wydajność pamięci, ponieważ funkcje `Alloc` i `Free` są zoptymalizowane pod kątem często przypisywania i zwalniania bloków pamięci z wielu wątków.

## <a name="compiling-the-code"></a>Kompilowanie kodu

Skopiuj przykładowy kod i wklej go w projekcie programu Visual Studio lub wklej go w pliku o nazwie `allocators.cpp` a następnie uruchom następujące polecenie w oknie wiersza polecenia programu Visual Studio.

> **/EHsc. cpp. exe**

## <a name="see-also"></a>Zobacz też

[Funkcje zarządzania pamięcią](../../parallel/concrt/memory-management-functions.md)<br/>
[Alloc — funkcja](reference/concurrency-namespace-functions.md#alloc)<br/>
[Free — funkcja](reference/concurrency-namespace-functions.md#free)
