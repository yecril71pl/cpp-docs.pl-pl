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
ms.openlocfilehash: 499e2d4a99152e08f50159c4c952eb882c9fd425
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50481149"
---
# <a name="memory-management-resizable-memory-blocks"></a>Zarządzanie pamięcią: bloki pamięci o zmiennych rozmiarach

**Nowe** i **Usuń** operatorów, opisaną w artykule [zarządzanie pamięcią: przykłady](../mfc/memory-management-examples.md), są odpowiednie dla alokowanie i dealokowanie bloki pamięci o stałym rozmiarze i obiekty. Czasami aplikacja może wymagać bloki pamięci o zmiennych rozmiarach. Należy użyć standardowych funkcji biblioteki wykonawczej C [— funkcja malloc](../c-runtime-library/reference/malloc.md), [realloc](../c-runtime-library/reference/realloc.md), i [bezpłatne](../c-runtime-library/reference/free.md) Zarządzanie bloki pamięci o zmiennych rozmiarach na stosie.

> [!IMPORTANT]
>  Mieszanie **nowe** i **Usuń** operatory za pomocą funkcji alokacji pamięci o zmiennych rozmiarach, w tym samym bloku pamięci będzie skutkować uszkodzony pamięci w wersji debugowania MFC. Nie należy używać **realloc** na blok pamięci przydzielony przy użyciu **nowe**. Podobnie, nie należy przydzielić blok pamięci z **nowe** operatora i usuń ją za pomocą **bezpłatne**, lub użyj **Usuń** operatora na blok pamięci przydzielony przy użyciu **— funkcja malloc**.

## <a name="see-also"></a>Zobacz też

[Zarządzanie pamięcią: alokacja sterty](../mfc/memory-management-heap-allocation.md)

