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
ms.openlocfilehash: b048b60a5512ecc54750cb980ca67e2373e2c837
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81364776"
---
# <a name="memory-management-resizable-memory-blocks"></a>Zarządzanie pamięcią: bloki pamięci o zmiennych rozmiarach

**Nowe** i **usuń** operatorów, opisane w artykule [Zarządzanie pamięcią: Przykłady](../mfc/memory-management-examples.md), są dobre do przydzielania i usuwania bloków pamięci o stałym rozmiarze i obiektów. Od czasu do czasu aplikacja może wymagać bloków pamięci o zmiennym rozmiarze. Aby zarządzać blokami pamięci o zmiennym rozmiarze na stercie, należy użyć standardowych funkcji biblioteki wyłowionej c [malloc](../c-runtime-library/reference/malloc.md), [realloc](../c-runtime-library/reference/realloc.md)i [wolnych](../c-runtime-library/reference/free.md) do zarządzania blokami pamięci o zmiennym rozmiarze.

> [!IMPORTANT]
> Mieszanie **nowych** i **usuń** operatorów z funkcji alokacji pamięci o zmiennym rozmiarze w tym samym bloku pamięci spowoduje uszkodzenie pamięci w wersji debugowania MFC. Nie należy używać **ponownego lokowania** w bloku pamięci przydzielonym z **nowym**programem . Podobnie nie należy przydzielić bloku pamięci z **nowym** operatorem i usunąć go **za pomocą bezpłatnego**, lub użyć operatora **usuwania** na bloku pamięci przydzielonym **z malloc**.

## <a name="see-also"></a>Zobacz też

[Zarządzanie pamięcią: alokacja sterty](../mfc/memory-management-heap-allocation.md)
