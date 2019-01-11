---
title: 'Instrukcje: Tworzenie wystąpień unique_ptr i korzystanie'
ms.custom: how-to
ms.date: 11/19/2018
ms.topic: conceptual
ms.assetid: 9a373030-e587-452f-b9a5-c5f9d58b7673
ms.openlocfilehash: 48e459b69592bf4c231407c2a378a7b7e01ff4ae
ms.sourcegitcommit: a1fad0a266b20b313364a74b16c9ac45d089b1e9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/11/2019
ms.locfileid: "54220585"
---
# <a name="how-to-create-and-use-uniqueptr-instances"></a>Instrukcje: Tworzenie wystąpień unique_ptr i korzystanie

A [unique_ptr](../standard-library/unique-ptr-class.md) nie udostępnia swojego wskaźnika. Nie można skopiować do innego `unique_ptr`, przekazać przez wartość do funkcji lub używany w ramach dowolnego algorytmu biblioteki standardowej języka C++, który wymaga wykonania kopii. A `unique_ptr` mogą być przenoszone. Oznacza to, że własność zasobu pamięci jest przenoszona do innego `unique_ptr` a oryginalny wskaźnik `unique_ptr` już nie jest właścicielem. Zalecamy, aby ograniczyć obiekt do jednego właściciela, ponieważ wiele własności zwiększa złożoność logiki programu. W związku z tym, jeśli potrzebujesz inteligentnego wskaźnika dla zwykłego obiektu języka C++ użyj `unique_ptr`, a podczas konstruowania `unique_ptr`, użyj [make_unique](../standard-library/memory-functions.md#make_unique) funkcji pomocnika.

Poniższy diagram ilustruje przeniesienie prawa własności między dwoma `unique_ptr` wystąpień.

![Przenoszenie własności unikatową&#95;ptr](../cpp/media/unique_ptr.png "przeniesienie własności unikatową&#95;ptr")

`unique_ptr` jest zdefiniowany w `<memory>` nagłówka w standardowej biblioteki języka C++. Jest dokładnie tak wydajna, jak wskaźnik surowy i mogą być używane w przypadku kontenerów standardowej biblioteki języka C++. Dodanie `unique_ptr` wystąpień kontenerów standardowej biblioteki języka C++ jest efektywne ponieważ Konstruktor przenoszący `unique_ptr` eliminuje potrzebę operacji kopiowania.

## <a name="example"></a>Przykład

Poniższy przykład pokazuje, jak utworzyć `unique_ptr` wystąpień i przekazywać je między funkcjami.

[!code-cpp[stl_smart_pointers#210](../cpp/codesnippet/CPP/how-to-create-and-use-unique-ptr-instances_1.cpp)]

Przykłady te pokazują podstawową cechę `unique_ptr`: go może zostać przeniesiony, ale nie kopiować. "Przejście" przeniesienie własności na nowe `unique_ptr` i usuwa stare `unique_ptr`.

## <a name="example"></a>Przykład

Poniższy przykład pokazuje, jak utworzyć `unique_ptr` wystąpień i korzystać z nich w wektorze.

[!code-cpp[stl_smart_pointers#211](../cpp/codesnippet/CPP/how-to-create-and-use-unique-ptr-instances_2.cpp)]

W zakresie dla pętli, zwróć uwagę, że `unique_ptr` jest przekazywany przez odwołanie. Jeśli próbujesz przekazać wartość do tego, kompilator będzie sygnalizować błąd, ponieważ `unique_ptr` Konstruktor kopiujący został usunięty.

## <a name="example"></a>Przykład

Poniższy przykład pokazuje, jak zainicjować `unique_ptr` oznacza jest składową klasy.

[!code-cpp[stl_smart_pointers#212](../cpp/codesnippet/CPP/how-to-create-and-use-unique-ptr-instances_3.cpp)]

## <a name="example"></a>Przykład

Można użyć [make_unique](../standard-library/memory-functions.md#make_unique) do utworzenia `unique_ptr` do tablicy, ale nie można użyć `make_unique` do zainicjowania elementów tablicy.

[!code-cpp[stl_smart_pointers#213](../cpp/codesnippet/CPP/how-to-create-and-use-unique-ptr-instances_4.cpp)]

Aby uzyskać więcej przykładów, zobacz [make_unique](../standard-library/memory-functions.md#make_unique).

## <a name="see-also"></a>Zobacz także

[Wskaźniki inteligentne (Modern C++)](../cpp/smart-pointers-modern-cpp.md)<br/>
[make_unique](../standard-library/memory-functions.md#make_unique)
