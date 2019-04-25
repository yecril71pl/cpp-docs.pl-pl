---
title: 'Zarządzanie pamięcią: Bloki pamięci o zmiennych rozmiarach'
ms.date: 11/04/2016
helpviewer_keywords:
- memory blocks [MFC], resizable
- memory [MFC], corruption
- memory allocation [MFC], memory block size
- memory blocks [MFC], allocating
- blocks [MFC], memory allocation
- resizable memory blocks [MFC]
ms.assetid: f0efe6f4-a3ed-4541-9195-51ec1291967a
ms.openlocfilehash: 124a2599e1523d5393fcf6255c88de0fd8cd72cd
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62219145"
---
# <a name="memory-management-resizable-memory-blocks"></a>Zarządzanie pamięcią: Bloki pamięci o zmiennych rozmiarach

**Nowe** i **Usuń** operatorów, opisaną w artykule [zarządzanie pamięcią: Przykłady](../mfc/memory-management-examples.md), są odpowiednie dla alokowanie i dealokowanie bloki pamięci o stałym rozmiarze i obiektów. Czasami aplikacja może wymagać bloki pamięci o zmiennych rozmiarach. Należy użyć standardowych funkcji biblioteki wykonawczej C [— funkcja malloc](../c-runtime-library/reference/malloc.md), [realloc](../c-runtime-library/reference/realloc.md), i [bezpłatne](../c-runtime-library/reference/free.md) Zarządzanie bloki pamięci o zmiennych rozmiarach na stosie.

> [!IMPORTANT]
>  Mieszanie **nowe** i **Usuń** operatory za pomocą funkcji alokacji pamięci o zmiennych rozmiarach, w tym samym bloku pamięci będzie skutkować uszkodzony pamięci w wersji debugowania MFC. Nie należy używać **realloc** na blok pamięci przydzielony przy użyciu **nowe**. Podobnie, nie należy przydzielić blok pamięci z **nowe** operatora i usuń ją za pomocą **bezpłatne**, lub użyj **Usuń** operatora na blok pamięci przydzielony przy użyciu **— funkcja malloc**.

## <a name="see-also"></a>Zobacz także

[Zarządzanie pamięcią: Alokacja sterty](../mfc/memory-management-heap-allocation.md)
