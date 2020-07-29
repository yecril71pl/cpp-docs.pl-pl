---
title: 'Zarządzanie pamięcią: bloki pamięci o zmiennych rozmiarach'
ms.date: 11/04/2016
helpviewer_keywords:
- memory blocks [MFC], resizable
- memory [MFC], corruption
- memory allocation [MFC], memory block size
- memory blocks [MFC], allocating
- blocks [MFC], memory allocation
- resizable memory blocks [MFC]
ms.assetid: f0efe6f4-a3ed-4541-9195-51ec1291967a
ms.openlocfilehash: 308b5aa00aeb1f0e7887ad90bad79a28b361d7c7
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87217925"
---
# <a name="memory-management-resizable-memory-blocks"></a>Zarządzanie pamięcią: bloki pamięci o zmiennych rozmiarach

**`new`** Operatory i **`delete`** , opisane w temacie [Zarządzanie pamięcią artykułu: przykłady](memory-management-examples.md), są przydatne do przydzielania i cofania przydziału bloków pamięci o ustalonym rozmiarze i obiektów. Czasami aplikacja może potrzebować bloków pamięci o zmiennym rozmiarze. Aby zarządzać blokami pamięci o zmiennym rozmiarze na stercie, należy użyć standardowej biblioteki wykonawczej C funkcji [malloc](../c-runtime-library/reference/malloc.md), [realloc](../c-runtime-library/reference/realloc.md)i [Free](../c-runtime-library/reference/free.md) .

> [!IMPORTANT]
> Mieszanie **`new`** operatorów i **`delete`** o zmiennym rozmiarze alokacji pamięci w tym samym bloku pamięci spowoduje uszkodzenie pamięci w debugowanej wersji biblioteki MFC. Nie należy używać **realloc** w bloku pamięci przydzielonym za pomocą **`new`** . Podobnie nie należy przydzielać bloku pamięci z **`new`** operatorem i usuwać go z opcją **Free**ani używać **`delete`** operatora w bloku pamięci przydzielonej za pomocą funkcji **malloc**.

## <a name="see-also"></a>Zobacz także

[Zarządzanie pamięcią: Alokacja sterty](memory-management-heap-allocation.md)
