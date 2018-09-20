---
title: 'Zarządzanie pamięcią: Bloki pamięci o zmiennych rozmiarach | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- memory blocks [MFC], resizable
- memory [MFC], corruption
- memory allocation [MFC], memory block size
- memory blocks [MFC], allocating
- blocks [MFC], memory allocation
- resizable memory blocks [MFC]
ms.assetid: f0efe6f4-a3ed-4541-9195-51ec1291967a
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 92582e4255c88b9cc78368a635b27772f2e51a30
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2018
ms.locfileid: "46443907"
---
# <a name="memory-management-resizable-memory-blocks"></a>Zarządzanie pamięcią: bloki pamięci o zmiennych rozmiarach

**Nowe** i **Usuń** operatorów, opisaną w artykule [zarządzanie pamięcią: przykłady](../mfc/memory-management-examples.md), są odpowiednie dla alokowanie i dealokowanie bloki pamięci o stałym rozmiarze i obiekty. Czasami aplikacja może wymagać bloki pamięci o zmiennych rozmiarach. Należy użyć standardowych funkcji biblioteki wykonawczej C [— funkcja malloc](../c-runtime-library/reference/malloc.md), [realloc](../c-runtime-library/reference/realloc.md), i [bezpłatne](../c-runtime-library/reference/free.md) Zarządzanie bloki pamięci o zmiennych rozmiarach na stosie.

> [!IMPORTANT]
>  Mieszanie **nowe** i **Usuń** operatory za pomocą funkcji alokacji pamięci o zmiennych rozmiarach, w tym samym bloku pamięci będzie skutkować uszkodzony pamięci w wersji debugowania MFC. Nie należy używać **realloc** na blok pamięci przydzielony przy użyciu **nowe**. Podobnie, nie należy przydzielić blok pamięci z **nowe** operatora i usuń ją za pomocą **bezpłatne**, lub użyj **Usuń** operatora na blok pamięci przydzielony przy użyciu **— funkcja malloc**.

## <a name="see-also"></a>Zobacz też

[Zarządzanie pamięcią: alokacja sterty](../mfc/memory-management-heap-allocation.md)

