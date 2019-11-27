---
title: 'Instrukcje: Tworzenie wystąpień unique_ptr i korzystanie z nich'
ms.custom: how-to
ms.date: 11/19/2018
ms.topic: conceptual
ms.assetid: 9a373030-e587-452f-b9a5-c5f9d58b7673
ms.openlocfilehash: 4b3362f71d1ccab0efb03d7e8705c6b3f25f9780
ms.sourcegitcommit: 654aecaeb5d3e3fe6bc926bafd6d5ace0d20a80e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/20/2019
ms.locfileid: "74246524"
---
# <a name="how-to-create-and-use-unique_ptr-instances"></a>Instrukcje: Tworzenie wystąpień unique_ptr i korzystanie z nich

[Unique_ptr](../standard-library/unique-ptr-class.md) nie udostępnia swojego wskaźnika. Nie można go skopiować do innego `unique_ptr`, przekazywać przez wartość do funkcji ani używać w żadnym C++ algorytmie biblioteki standardowej, który wymaga wykonanych kopii. `unique_ptr` można przenieść tylko. Oznacza to, że własność zasobu pamięci jest przenoszona do innego `unique_ptr`, a oryginalny `unique_ptr` nie jest już właścicielem. Zalecamy, aby ograniczyć obiekt do jednego właściciela, ponieważ wiele własności zwiększa złożoność logiki programu. W związku z tym, jeśli potrzebujesz inteligentnego wskaźnika dla C++ zwykłego obiektu, użyj `unique_ptr`i podczas konstruowania `unique_ptr`Użyj funkcji pomocnika [make_unique](../standard-library/memory-functions.md#make_unique) .

Na poniższym diagramie przedstawiono przeniesienie własności między dwoma wystąpieniami `unique_ptr`.

![Przeniesienie własności unikatowej&#95;wartości PTR](media/unique_ptr.png "Przeniesienie własności unikatowej&#95;wartości PTR")

`unique_ptr` jest zdefiniowany w nagłówku `<memory>` w C++ standardowej bibliotece. Jest on dokładnie tak wydajny jak wskaźnik surowy i może być używany C++ w kontenerach biblioteki standardowej. Dodanie wystąpień `unique_ptr` do C++ kontenerów biblioteki standardowej jest wydajne, ponieważ konstruktor przenoszenia `unique_ptr` eliminuje potrzebę operacji kopiowania.

## <a name="example-1"></a>Przykład 1

Poniższy przykład pokazuje, jak utworzyć wystąpienia `unique_ptr` i przekazać je między funkcjami.

[!code-cpp[stl_smart_pointers#210](codesnippet/CPP/how-to-create-and-use-unique-ptr-instances_1.cpp)]

W tych przykładach przedstawiono podstawowe cechy `unique_ptr`: można je przenieść, ale nie skopiować. "Przenoszenie" przenosi własność do nowego `unique_ptr` i resetuje stary `unique_ptr`.

## <a name="example-2"></a>Przykład 2

Poniższy przykład pokazuje, jak tworzyć wystąpienia `unique_ptr` i używać ich w wektorze.

[!code-cpp[stl_smart_pointers#211](codesnippet/CPP/how-to-create-and-use-unique-ptr-instances_2.cpp)]

W zakresie dla pętli należy zauważyć, że `unique_ptr` jest przekazywany przez odwołanie. Jeśli spróbujesz przekazać wartość tutaj, kompilator zgłosi błąd, ponieważ `unique_ptr` Konstruktor kopiujący jest usuwany.

## <a name="example-3"></a>Przykład 3

Poniższy przykład pokazuje, jak zainicjować `unique_ptr`, który jest elementem członkowskim klasy.

[!code-cpp[stl_smart_pointers#212](codesnippet/CPP/how-to-create-and-use-unique-ptr-instances_3.cpp)]

## <a name="example-4"></a>Przykład 4

Za pomocą [make_unique](../standard-library/memory-functions.md#make_unique) można utworzyć `unique_ptr` do tablicy, ale nie można użyć `make_unique`, aby zainicjować elementy tablicy.

[!code-cpp[stl_smart_pointers#213](codesnippet/CPP/how-to-create-and-use-unique-ptr-instances_4.cpp)]

Aby uzyskać więcej przykładów, zobacz [make_unique](../standard-library/memory-functions.md#make_unique).

## <a name="see-also"></a>Zobacz także

[Wskaźniki inteligentne (Modern C++)](smart-pointers-modern-cpp.md)<br/>
[make_unique](../standard-library/memory-functions.md#make_unique)
